# 8. Virtual Private Cloud – VPC (Sanal Özel Bulut)

Amazon Virtual Private Cloud (Amazon VPC); kaynak ayırma, bağlantı ve güvenlik dahil olmak üzere sanal ağ ortamınız üzerinde size tam kontrol sağlar. VPC'nizi AWS hizmeti konsolunda ayarlayarak başlayabilirsiniz. Ardından, Amazon Elastic Compute Cloud (EC2) ve Amazon Relational Database Service (RDS) bulut sunucuları gibi kaynaklar ekleyebilirsiniz. Son olarak, VPC'lerinizin hesaplarda, erişilebilirlik alanlarında veya AWS bölgelerinde birbirleriyle nasıl iletişim kuracağını tanımlayabilirsiniz. Aşağıdaki örnekte, ağ trafiği her bölgedeki iki VPC arasında paylaşılmaktadır.

![262](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/df238f31-fd6d-4056-891b-7423cd6c32cc)

Veri merkezi, birden fazla makinenin ve çeşitli donanımsal cihazların bir arada bulunduğu ve birbirleri arasında dış dünyadaki diğer cihazlar ile iletişim kurduğu fiziksel topluluktur. Fiziksel haberleşme, ağ kabloları ile bağlı bulunan, switch, router, repeater, firewall, load balancer gibi cihazlarla oluşturduğumuz; fiziksel ağlar üzerinde konuşlanmış mantıksal ağ yapıları ile sağlanır. 

Bulutta erişilen fiziksel bir ağ bulunmamaktadır. Bu fiziksel ağı simüle eden ve üzerinde mantıksal yapılar kurmamıza imkân tanıyan yapılara VPC yani Türkçe karşılığı ile sanal özel ağ denir. Oluşturulan sanal ağ, kullanıcıya özeldir. Kullanıcı izin vermedikçe buraya konuşlanan kaynaklara kimse erişemez. 

EC2 alt yapısını, bu sanal özel ağ altında konuşlandırıp bu cihazların hem kendi aralarında hem de dış dünya ile veri alışverişini sağlayabiliriz.

AWS hesabındaki her region bir tane varsayılan VPC ile gelir. Her region için 5 VPC daha üretilebilir. Eğer VPC gereklilik sayısı beşten fazla ise AWS’den talep edilebilir. Her VPC, kullanıcılar için önceden tanımlı olan bir IP aralığına sahiptir. Yani bir özel ağ içerisinde kullanılabilecek IP aralığı tanımlanmıştır. VPC’de en geniş özel CDR ``10.0.0.0/16``’dır. IP değeri ``10.0.0.0 – 10.0.255.255`` arasında bir değer alabilir. VPC’ler public veya private olacak şekilde alt ağlara bölünebilir. Bu alt ağlar (subnet) belirli bir AZ’de durur. Bir alt ağ birden fazla AZ’ye genişletilemez. 

VPC içerisinde tüm trafik yönlendirmesini “Routing Table” ile yapılır. Bu tanımlar X alt ağından Y alt ağına, Z alt ağından internete nasıl gidileceğini anlatan konfigürasyonları içerir. 

Güvenlik için ağ alt yapısında hangi alt ağ, hangi trafiğe gidebilsin veya hangi alt ağ hangi trafik ile dışarı çıkabilsin gibi kurallar tanımlanır. Bu kuralların bütününe network access control list (ACL) denir. 

Public alt ağlarını internet erişimini sağlayan evimizdeki ADSL yönlendiriciler gibi Internet Gateway bulunur. Kendi şirket ağ alt yapısı ile bu VPC arasında direkt bir bağlantı olacak olan VPN bağlantısını sonlandırmak için VPN Gateway kullanılır. S3 veya DynamoDB gibi diğer AWS servislerine bu VPC’den direkt ulaşmak adına private end point (özel son nokta) linkleri de yaratılabilir.

Hem kullanıcıların kendi hesabındaki diğer VPC’ler hem de başka hesaplarda bulunan VPC’ler ile “pear” denilen ayarlamalar ile VPC’ler arası direkt bağlantı kurulur. Peer bağlantıları ile farklı VPC’ler arasında kaynakların birbirine erişmesini sağlar.

## 8.1. VPC Kullanımı
Bu başlık altında kılavuzun bundan sonraki kısımlarında kullanabilmek üzere varsayılan VPC yanına yeni bir VPC oluşturalım. 

Bir VPC oluşturulurken IP aralığı iyi seçilmelidir, AWS daha sonra bu aralığı genişletmeye izin vermez. Oluşturulacak VPC aşağıdaki Şekil: 43’teki gibi tasarlanacaktır. VPC, 3 public ve 3 tane private olmak üzere toplamda 6 tane alt ağ içerecektir. Her alt ağ için IP aralığı yine Şekil: 43 üzerinde belirtilmiştir. Örneğin AZ-A’da bulunan “Public Subnet 1A” için IP aralığı 10.10.10.0/24 olarak verilmiştir. Bu tanımlama 10.10.10.0 - 10.10.10.255 arasındaki tüm IP değerlerini kapsar. Toplamda 256 adet IP adresi tanımlanmıştır. Ancak 10.10.10.0 adresi alt ağın adını belirlediği ve 10.10.10.255 broadcast yani genel yayın IP adresi olarak tanımlandığı için bu IP değerleri kullanılamaz. Bununla beraber 10.10.10.1 IP değeri VPC router için, 10.10.10.2 IP değeri DNS için, 10.10.10.3 IP değeri ise reserve olarak ayrılmış olduğu için bu IP değerleri kullanılamaz. Bu yüzden tanımlı olan alt ağda 256 - 5 olmak üzere toplam 251 adet IP değeri kullanılabilir.

![263](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/76bf34fe-7830-497f-82e6-7decbbfe77ea)

## 8.2. İlk VPC Oluşturma
Yeni bir VPC oluşturmak için ilk olarak VPC servisinin kontrol paneline erişilir. “Create VPC” butonu kullanılarak varsayılan olarak gelen haricinde ilk VPC oluşturulmaya başlanabilir.

- Resources to create alanında VPC and more seçili kalır. 
- Name “tag” kısmına bu kılavuz kapsamında “ilkVPC” adını verelim. 
- IPv4 CIDR block değeri olarak yukarıdaki şemada görüldüğü gibi 10.10.0.0/16 değerini girelim ve “no IPv6 CIDR block” opsiyonu seçili iken devam edelim. 
- Tenancy bilgisini varsayılan olarak bırakalım. 
- Number of AZs alanında, kaç AZ üzerinde kullanılabileceğini belirtmemiz gerekiyor. Yukarıda verilen Şekil: 43’te 3 AZ bulunduğu için bu değeri 3 yapalım.
- Public subnet, private subnet, NAT gateway ve VPC endpoints değerlerini bekleyen alanları 0 veya None olarak seçelim. Bu kısımları bu kılavuz kapsamında adım adım oluşturacağız.
- En altta bulunan DNS opsiyonlarından “Enable DNS hostnames” seçili olmalıdır. Bu işlemin seçili olmaması durumunda VPC altında barınan EC2’lere DNS host-name değeri verilmez. Haliyle bu makineler DNS host-name olmadan birbirleriyle haberleşemeyecektir. 
- Create VPC diyerek işlemler tamamlanır ve “ilkVPC” adında sanal bulut ağı oluşturulmuş olur.

VPC kontrol paneline girdiğimizde, az önce oluşturulan ilkVPC ve varsayılan olarak AWS tarafından atanmış VPC görünmektedir. Bu aşamadan sonra Şekil: 44’te görünen sol menüleri kullanarak VPC için gerekli bileşenleri tanımlama başlayacağız.

![264](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/4a3eb36e-383f-4fe9-b260-57513f75e392)

## 8.3. Internet Gateway Oluşturma
İlk olarak VPC ile internet arasında bağlantı kurmak üzere bir Internet Gateway oluşturmamız gerekiyor. Bu işlem için solda bulunan “Internet Gateway”e tıklayalım ve sonrasında “Create internet gateway” diyelim.

- İsim etiketi olarak “ilkIG” diyelim ve oluşturalım. 
-  Oluşturulmuş olan gateway seçili iken Actions → Attach to VPC seçeneklerini takip ederek az önce oluşturulan “ilkVPC”ye bu gateway’i bağlayalım.

Gateway oluşturduktan sonra VPC’ye dış dünyaya gidecek paketleri az önce yaratılan yönlendiriciye (Interget Gateway) teslim et, o dış dünyaya göndersin yapılandırması yapılmalıdır. Bu işlem için yine ekranın solunda bulunan “Route tables” seçeneği kullanılır. ilkVPC için otomatik oluşturulan route table seçili iken Actions → Edit routes seçenekleri takip edilir. Varsayılan bir yönlendirme tanımlaması bulunmaktadır. Bu hedef yerel ağ ise target değerinin local olduğunu yani ağ içerisinde olduğunu belirtir. Add route seçeneği ile yeni bir yönlendirme ekleyelim ve destination değerini 0.0.0.0/0 ve target değerini az önce oluşturulan “ilkIG” isimli Internet Gateway olarak belirleyelim. “Save changes” diyerek yapılan değişiklikler kaydedilir. Yeni eklenen yönlendirme kuralı ile destination değeri yerel ağ IP değeri olmadığı tüm durumlarda internete erişmek için kullanılacak olan Internet Gateway’e yönlendirme sağlanmış olur.

## 8.4. Alt Ağlar Oluşturma
Bu aşamadan sonra alt ağların oluşturulması gerekmektedir. Bu işlem için ekranın solunda bulunan “Subnets” seçeneği kullanılır. Bu seçeneğe tıklandığında 3 adet alt ağ listelenmektedir. Bu alt ağlar varsayılan olarak gelen VPC’ye ait alt ağlardır. “Create subnet” diyerek yeni alt ağlar oluşturulabilir

- Alt ağın hangi VPC için tanımlandığı belirtilir bu aşamada “ilkVPC” isimli sanal özel bulut seçilir. 
- İsim etiket değeri için “eu-west-1a-public” diyelim. 
- AZ olarak “eu-west-1a” seçeneğini kullanabiliriz.
- IPv4 CIDR block alanına Şekil: 45’te belirtildiği gibi 10.10.10.0/24 tanımlamasını uygulayalım. 
- Create subnet diyerek ilk AZ’de bulunan public subnet oluşturulmuş olur. 
- Sırada yine aynı AZ’de bulunan private subnet’i oluşturalım. Public subnet’te olduğu gibi “ilkVPC” ismine sahip VPC’yi seçelim.
- İsimlendirme olarak “eu-west-1a-private” tanımlaması yapalım. 
- AZ olarak yine “eu-west-1a” seçeneğini kullanabiliriz. 
- IPv4 CIDR block alanına Şekil: 45’te belirtildiği gibi 10.10.11.0/24 tanımlamasını uygulayalım. Create subnet diyerek ilk AZ’de bulunan private alt ağ da oluşturulmuş olur.

Bu işlemleri “eu-west-1b” AZ’si için de public Ipv4 CIDR değerleri 10.10.20.0/24 (public subnet) ve 10.10.21.0/24 (private) olacak şekilde tekrarlayalım. Son AZ için de IPv4 CIDR değerleri 10.10.30.0/24 (public) ve 10.10.31.0/24 (private) olacak şekilde aynı işlemleri uygulayalım. Tüm işlemler bittikten sonra VPC üzerinde barınan üç public ve üç private olmak üzere toplamda altı tane alt ağ oluşturulmuş olur. Tüm işlemler tamamlandığında Şekil: 45’teki gibi alt ağlara sahip oluruz.

![265](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/56d56721-a02d-4424-9cfd-81117d1f1890)

## 8.5. Private Alt Ağları Kısıtlama
Şu anda altı tane subnet (alt ağ) her özelliğiyle aynı. Public ve private olarak isimlendirdik ancak bu alt ağların kısıtlarını nasıl tanımlayacağız? Bu işlem için yönlendirme tabloları (route tables) kullanılır. Bu aşamada bizim istediğimiz üç alt ağın internete girebilirken diğer üçünün erişmemesini istiyoruz. Solda bulunan menüden “Route Tables” seçeneğini kullanarak private alt ağlar için yeni yönlendirme kuralları tanımlayalım. İsim olarak “ilkRT-Private” ve VPC değeri olarak ise listeden oluşturduğumuz “ilkVPC” seçilir.

Oluşturulmuş olan route table seçili iken altta açılan ekrandan Subnet associations → Edit subnet associations seçenekleri takip edilir. Tüm private olan alt ağlar seçilir ve kaydedilir.  Oluşturulmuş olan route table zaten varsayılan olarak sadece yerel (local) istekleri kullanır bundan dolayı ekstra bir konfigürasyon yapmamıza gerek yoktur.

Alt ağların listelendiği ekrana dönelim ve public olan alt ağlardan birini seçelim. Sonrasında sırasıyla Actions →Edit subnet settings → Auto-assign IP setting başlığı altında bulunan “Enable auto-assign public IPv4 adress” kutucuğu seçili hale getirip işlemleri kaydedelim.

## 8.6. Alt Ağlara EC2 Sanal Makineler Oluşturma
Bu aşamadan sonra “eu-west-1a-public” ve “eu-west-1a-private” alt ağları için birer EC2 sanal makinesi kuracağız. Oluşturulan public alt ağında bulunan EC2 sanal makinesi varsayılan route table’ı kullanacaktır. Yani router’a (Internet Gateway) gidecek. Private alt ağında bulunan EC2 sanal makinesi ise private için oluşturulan router table kullanacaktır. Yani sadece yerel (local) ağ içinde kullanılacaktır. 

Ancak private 1A ağında kurulacak olan bir sanal makineye bir public IP olmadan nasıl erişeceğiz? Bu durum için public alt ağlardan birinde “jumpbox” adı verilen bir sanal makine kurulur. Dış dünyadan bu jumpbox’a bağlanıp daha sonrasında private alt ağ bulunan makinelere bu yapılar üzerinden geçiş sağlayacağız.

EC2 kontrol paneline gidip “launch instance” diyerek sanal makineleri oluşturmaya başlayalım:

- “ilkPublicVM” ismini ataylım. 
- Application and OS Images alanında önceki başlıklarda oluşturulmuş olan “BaseAMI”ı seçelim. 
- Instance type olarak “t2.micro” seçili kalabilir. 
- Key pair olarak daha önceden oluşturulmuş olan anahtarı kullanacağımızı belirtiriz. 
- Network Setting alanında edit diyerek VPC’yi oluşturduğumuz “ilkVPC” olarak seçiyoruz. Subnet olarak “eu-west-1a-public” seçeneğini kullanalım. “Auto-assign public IP” seçeneğini enable yapalım. 
- Security group kısmında yeni bir güvenlik grubu oluşturalım. Çünkü security grouplar VPC’ler ile ilişkilendirilir. Daha önceki başlıklarda kullandığımız security group bu VPC için kullanılamaz. 
- “EC2-Sec-Group” adında bir güvenlik grubu oluşturuyoruz. (Varsayılan olarak gelen VPC’de de bu isimle oluşturmuştuk.) Açıklama alanına “ilkVPC icin sec group” yazalım. SSH, HTTP ve HTTPS için kurallar tanımlayalım ve hepsinin source alanını “0.0.0.0/0, ::/0” yapalım böylelikle bu kurallar hem IPv4 hem de IPv6 için her yerden gelen isteklere izin verecektir. 
- Advanced details kısmında bulunan “IAM Instance profile” alanını önceki başlıklar altında oluşturulmuş olan “EC2-S3-Full-Access” seçelim ve diğer ayarları varsayılan olarak bırakarak devam edelim.

Yukarıdaki adımlarının hepsini “ilkPrivateVM” isminde bir instance oluşturacak şekilde tekrar etmeliyiz. Farklı olan şey ise yeni bir güvenlik grubu oluşturmak yerine az önce oluşturulan “EC2-Sec-Group” seçilir ve bu sefer “Auto-assign public IP” seçeneği disable bırakılır. Sanal makinenin barınacağı ağı da “eu-west-1a-private” olarak seçmeyi unutmayalım.

Private alt ağda oluşturulan sanal makinenin özelliklerine bakarsak “Public IPv4” adres değeri yok. Private IPv4 bulunuyor. Bu sanal makine VPC içerisindeki sanal makinelere erişebilir ancak dış dünyadan erişilemeyecektir.

## 8.7. EC2 Sanal Makineler Arası Haberleşme Kontrolü
Sunucuların birbirine iletişim kurup kuramayacağı belirlemek için “ping” komutu kullanılır. Ancak özellikle EC2 kontrol paneli üzerinden az önce oluşturulan güvenlik grubuna yeni bir kural eklemeliyiz.

- EC2 kontrol paneli üzerinden solda bulunan menü yardımıyla “Security group” sekmesine geçilir. 
- “EC2-Security-Group” seçili iken altta açılan menüde “Inbound rules” seçeneği düzenle denir. 
- Tür olarak “All ICMP - IPv4” seçilir ve source olarak “``0.0.0.0/0``” ataması yapılır.

PuTTY yardımıyla public olan alt ağda bulunan EC2 sanal makineye bağlanalım.

``ping [PRIVATE_EC2_IP_ADDRESS]`` komutu ile public sanal makineden, private olan sanal makineye istekte bulunur. Ve ping komutu sonucunda haberleşmede bir sorun olmadığı görülecektir. Peki bu aşamadan sonra private olan sanal makineye nasıl bağlanacağız? Bu işlem için ilk olarak ``.pem`` uzantılı dosya metin belgesi olarak açılır ve içerisindeki tüm metin kopyalanır. Daha sonraki aşamada ise public sunucuda iken ``nano baglanti.pem`` komutu ile bir metin dosyası açılır ve kopyalanan içerik buraya yapıştırılır. ``CTRL + X ``,  ``y`` ve ``enter`` tuşlarına basılarak dosya kaydedilir. ``chmod 400 baglanti.pem`` komutu ile parolayı bulunduran dosyaya yetkilendirme verilir. ``ssh -i baglanti.pem ec2-user@[PRIVATE_EC2_IP_ADDRESS]``,  ``enter`` ve sonrasında gelen soruya ``yes`` diyerek private olan sanal makineye bağlanılır.

## 8.8. VPC’lerde Güvenlik
Bu başlık altında VPC’lerde AWS tarafından sağlanan güvenlik araçları incelenmektedir.

Network Access Control List - ACL (Ağ Erişim Kontrol Listesi), atandığı alt ağın, hangi kaynaktan, hangi türde trafiği kabul edeceğini, hangi hedefe hangi türde trafik göndereceğini belirlediğimiz kurallar bütünüdür.

Her alt ağ en azından bir tane ACL’e atanmak zorundadır. Hepsi için ayrı ayrı da tanımlanabilir, bir ACL birden fazla alt ağa da atanabilir. Bu kısım kullanıcının ağ tasarımına göre değişkenlik göstermektedir. ACL’ler alt ağ seviyesinde güvenlik grupları (security group) olarak düşünülebilir. Nasıl ki security gruplar, tek tek makina veya kaynaklara atıyor isek, ACL’ler de alt ağlara dolayısıyla alt ağ altında barınan kaynaklara atanmış olur. Aralarındaki en temel fark ise; ACL’ler alt ağlara atanır ve alt ağ bazında erişim kuralları belirlememizi sağlar. Güvenlik grupları ise makinelere ve kaynaklara atanır bu yüzden makine bazında erişimi tanımlar/sağlar.

Varsayılan güvenlik gruplarında bütün portlar kapalıdır. Güvenlik grubu içinde port ve protokol tanımlamaları ile artık belirli portlara erişime izin verilmiş olur.

İki network accees control list - ACL, bir alt ağa atanamaz ancak bir ACL birden fazla alt ağa bağlanabilir. Bir alt ağ belirli bir anda sadece bir ACL’ye sahiptir. ACL, atandığı alt ağdaki bütün kaynaklar üzerinde geçerlidir. ACL üzerinde kurallar X’ten Y’ye gelen bir istek kabul veya reddedilsin üzerine tasarlanmıştır. En temel kural ise, herhangi bir source’tan, herhangi bir destination’a, herhangi port üzerinden gider ise DENY yani engelledir. Bu kural en alttadır. Bu kuralın üstünde tanımlı kurallardan herhangi birine uymaz ise en alttaki bu kurala gelir ve istek reddedilir. Network ACL’ler, atandığı alt ağın içindeki makineler birbirleriyle erişmeleri durumunda bu ACL kuralları yine geçerli olacaktır.

## 8.8.1. ACL Oluşturulması
VCP kontrol panelinde solda bulunan menüden “Network ACLs” seçeneğine tıkladıktan sonra “Create Network ACL” diyerek ilk ağ erişim kontrol listesi tanımlamasına başlayalım:

- İsim olarak “denemeACL” ve VPC olarak da “ilkVPC” girdilerini kullanalım ve ACL’yi oluşturalım. 
- Oluşturulan “denemeACL” seçili iken aşağıda açılan menüde güvenlik gruplarına benzer şekilde “Inbounded rules”, “outbounded rules” ve bir alt ağa atamak için “Subnet associations” seçenekleri bulunur.
- “Inbounded rules” sekmesine gelerek düzenlemeye başlayalım. Varsayılan olarak gelen kuralda nereden veya hangi port üzerinden geldiği fark etmeksizin isteği reddetmeye dayalı bir kural bulunmaktadır. Bu kuralın üzerine yeni kurallar tanımlanmalıdır. Tanımlanan kurallar Şekil: 46’daki gibidir.
![266](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/9921f9c0-1e51-44e4-a8b5-bc79c0e0288f)

- Oluşturulan bu ACL’yi bir alt ağa atarsak artık o atanan alt ağda bulunan kaynaklara dış dünyadan erişmek isteyen tüm istekler ve paketler bu ACL süzgecinden geçer.
- Her paketin yukarıdan aşağıya doğru tek tek kurallara uygunluğu bakılır. Gelen paket veya istek ile ilgili tanım varsa o tanım uygulanır. Tanım yoksa en alttaki varsayılan kurala gelir ve istek reddedilir.
- Alt ağdan dışarı trafik çıkışı isteniyorsa “outbounded rules” üzerinden gerekli tanımlamaların yapılması da gerekmektedir.
- Tüm bunlardan sonra “Subnet Associations” üzerinden istenilen alt ağlara bu ACL ataması yapılabilir. Kılavuzun bu aşamasında oluşturulan ACL herhangi bir alt ağa atanmamaktadır.

## 8.9. Elastic IP Adresi Atanması
Bir EC2 sanal makinesi kapatılıp, tekrar açıldığında public IP adresi değişecektir. AWS dünyasında IP adresleri sabit ve makineye atanmış (dedicate) değildir. EC2 konsolu üzerinden spesifik bir IP değerini kendine alamazsınız. 

Bazı durumlarda bu IP değişimi sakıncalıdır. Bir lisans bu IP değerine atanabilir veya tanımlamalar bu IP adresine göre konfigüre edilmiş olabilir. 

Sabit bir IP adresine ihtiyacımız bu gibi durumlardan dolayı oluşabilir. VPC kontrol panelinde “Elastic IPs” seçeneğinde “Allocate new address” seçilir. Böylelikle AWS bize bir IP adresini dedicate yani atamış olur. Oluşturulan IP adresi seçili iken Actions → Associate Elastic IP addresses → Instance seçilir ve böylelikle o instance her zaman bu IP değerini kullanarak açılacaktır.

## 8.10. NAT Gateway Oluşturulması
VPC içinde alt ağlar oluştururken private ve public gibi sınıflandırmalar yapmıştık. Bu isimlendirmelerin işlevleri yönlendirme tablosu (route table) üzerinden sağlanmıştı. 0.0.0.0/0 değerine sahip Internet Gateway tanımlaması sayesinde de public alt ağda bulunan makineler internete erişebiliyor.

Bununla beraber private alt ağda bulunan sanal makinelerin internet erişimi bulunmamakta. Güncelleme ve bazı paket gereksinimi gibi durumlarda bu makinelerin internet erişimine ihtiyacı olacaktır. Bu sorunun üzerinden gelmek için ise NAT Gateway kullanılır. Bu NAT Gateway’i public alt ağlardan bir tanesine bağlarız. Daha sonrasında, private alt ağın yönlendirme tablosunda, internete erişmek istediği durumlarda NAT Gateway’e paketleri iletmesi için bir yönlendirme tanımlanır. Böylelikle private alt ağda bulunan sanal makineler internete erişebilir ancak Internet Gateway kullanmadığı için dışarıdan bu cihazlara erişilemez. Private alt ağlar için istenilen de tam olarak budur.

VPC kontrol panelinde solda bulunan ekrandan “NAT Gateways” seçeneğine tıklanır ve sonrasında “Create” diyerek yeni bir NAT Gateway oluşturulmaya başlanır.

- İlk olarak bir isim beklemektedir. “ilk-NAT-GW” diyerek bu adımı geçelim. 
- Oluşturulacak NAT Gateway’in hangi ağda barındırmak istediğinizi sorar. 
- Az önceki ekranda oluşturulan “Elastic IP” bir instance’a atadıysanız ilk olarak o IP’yi release etmeniz yani serbest bırakmanız gerekir. (Yeni bir Elastic IP adresi de üretilebilir.) Sonrasında NAT Gateway oluştururken bu elastic IP adresini “Elastic IP allocation ID” kısmında seçmemiz gerekir.
- Sonrasında oluşturma işlemleri tamamlanır. 
- VPC kontrol panelinde solda bulunan menüden “Route tables” sekmesine tıklanır.
- Private alt ağlar için oluşturduğumuz “ilkRT-Private” seçili iken alta açılan kısımdan routes ordan da edit routes seçenekleri ile yeni bir yönlendirme ekleme ekranına geçilir. 
- Public yönlendirme tablosunda destination değeri 0.0.0.0/0 iken target değerini Internet Gatewat seçmiştik. Private yönlendirme tablosunda ise 0.0.0.0/0 destination değeri için target değerini az önce oluşturulan NAT Gateway seçilir ve kaydedilir.

*Bu kılavuz kapsamında öğrenmek için bu adımları yapmanız durumunda NAT Gateway ve Elastic IP için AWS ödeme çıkaracaktır. Bu servisleri kullandıktan sonra kapatılmaması durumunda sürpriz faturalar ile karşılanabilir. Bu konuya dikkat etmenizi rica ederim.*

## 8.11. NAT EC2 Instance
Private alt ağda bulunan sanal makinelerin internete erişebilmesi için tek yöntem NAT Gateway değildir. Bu yöntem AWS tarafından yönetilir ve kullanıcı ekstra bir şey yapmaz. Bunun yerine kullanıcılar kendileri tarafından yönetilebilen ve arka planda bu işlemi EC2 üzerinden yapabilirler. Buna NAT EC2 Instance denilmektedir. VPC veya alt ağ yapımız büyük ise bazı TCP temelli ayarlamalar yapılması gerekmektedir. Bu gibi durumlarda NAT Instance kullanılmalıdır. Bu işlemler için aşağıdaki adımlar izlenmelidir:

- EC2 kontrol paneline erişilir ve “Launch instances” seçeneği ile yeni bir EC2 sanal makine oluşturulmaya başlanır. 
- Bir isim atanabilir, bu aşamada “ilk-NAT-EC2” ismini verelim. 
- Application and OS Images kısmında ise arama kısmına gelinir ve ilk olarak Community AMIs kısmında “NAT” araması yapılır. Sonuç olarak çıkan instance seçilir. 
-  Instance type olarak “t2.micro” yeterli olacaktır. 
- Key pair olarak var olan anahtarın kullanıldığı belirtilir. 
- Network settings alanında VPC olarak “ilkVPC”, subnet olarak “eu-west-1a-public”, güvenlik grubu olarak “EC2-Sec-Group” seçilir. 146 
- Configure storage bölümünde ise “General Purpuse SSD -gp2” seçilir. Bunun seçilme sebebi ise NAT Instance’ın hızlı olması gereksinimidir. 
- Instance’ı oluşturduktan sonra yapılması gereken ilk işlem, oluşturulan instance seçili iken Actions → Networking → Change source/destination check →stop işlemleri uygulanır. Bu işlem yapılmaz ise NAT instance kendisine gelen paket, kendisi ile ilgili değilse o paketi düşürür. Ancak bir NAT instance’a kendisi ile ilgili paket gelmese dahi bunu gerekli yönlendirmeler ile aktarmalıdır. Bu özelliğin durdurulma nedeni budur. 
-  VPC kontrol paneline dönelim ve route tables menüsüne geçelim. 
- Private alt ağlar için oluşturulmuş olan “ilkRT-Private” seçili iken aşağıda açılan menüde “Routes” ve sonrasında “Edit routes” seçenekleri takip edilir. NAT Gateway ile oluşturulan yönlendirme yerine destination değeri yine 0.0.0.0/0 olan ve target değeri ise Instance→ilk-NAT-EC2 seçilir.

Konuyu kısaca tekrar ele almak gerekirse bir private alt ağda bulunan EC2 sanal makinesinin internete erişebilmesi için iki yöntem bulunmaktadır:

- ***NAT Gateway:*** Tamamı AWS tarafından yönetilen bir hizmettir. 
- ***NAT Instance:*** Kullanıcı tarafından oluşturulup, ayarlanıp, yönetilir. Daha ucuzdur ve TCP temelinde bazı ayarlamalar yapmaya imkân tanır. Örneğin UDP paketlerine NAT Gateway izin vermemektedir, ancak gerektiği durumda kullanıcı NAT Instance üzerinden UDP paketlerine izin verecek bir tanımlama yapabilir.

## 8.12. End-point (Uç Nokta) Oluşturulması
Bu konuya bir senaryo üzerinden bakalım. Diyelim ki sanal makinalarımızın farklı görevleri var. Görevlerden biri bu makinelerin düzenli olarak AWS S3 servisine gidip bucketler’dan dosya alıyor veya yazıyor. Şu durumda VPC içindeki sanal makine, S3 servisine giderken nasıl bir yol izleyecek? Elbette normal bir bilgisayar gibi davranacak; internet üzerinden erişecektir. AWS bunun için end-point hizmetini sunmaktadır. Bu hizmet sayesinde, S3’e erişmek isteyen bu makine interneti dolaşıp servise gelmek yerine AWS’nin yerel ağı üzerinden erişim sağlayabilecektir. Bir end-point oluşturmak için şu adımlar izlenebilir:

- VPC kontrol panelinde solda bulunan menü üzerinden “Endpoints” sekmesine tıklanır ve “Create endpoint” butonu kullanılır. 
- İsim olarak “ilk-end-point” diyelim ve sonraki adıma geçelim. 
- Niçin yaratılmak istendiği sorulur. Bu aşamada AWS servisleri (AWS services) seçilir. 
- Aşağıdaki arama kısmına s3 (com.amazonaws.eu-west-1.s3) yazılır ve gerekli servis seçilir. 
- “ilkVPC” üzerinde kurulmak istendiği belirtilir. 
-  Oluşturulacak end-point’e göre hangi noktaların güncellenmesi istendiği sorulur. bu aşamada hem public alt ağ için olan hem de private alt ağ için olan yönlendirme tabloları seçilir. 
- Policy kısmı “Full access” seçili olarak bırakılır.

VPC kontrol paneli üzerinden yönlendirme tablolarına ulaşırsak her ikisine de yeni bir yönlendirmenin tanımlandığı görülür. Böylelikle makine S3 servisine erişmek istediğinde internete çıkmak yerine, AWS tarafından sunulan ağ içerisinde paket transferleri hızlıca tanımlanır. Gecikmeyi minimum düzeye indirir.

## 8.13. VPC Peering
VPC eşleme (peering) bağlantısı, iki VPC arasındaki trafiği özel IPv4 adresleri veya IPv6 adresleri kullanarak yönlendirmenizi sağlayan bir ağ bağlantısıdır. Her iki VPC'deki örnekler, aynı ağ içindeymiş gibi birbirleriyle iletişim kurabilir. Kendi VPC'leriniz arasında veya başka bir AWS hesabındaki bir VPC ile bir VPC eşleme bağlantısı oluşturabilirsiniz. VPC'ler farklı bölgelerde olabilir (bölgeler arası VPC eşleme bağlantısı olarak da bilinir). 

AWS, bir VPC eşleme bağlantısı oluşturmak için bir VPC'nin mevcut altyapısını kullanır. Ne bir ağ geçidi ne de bir VPN bağlantısıdır ve ayrı bir fiziksel donanıma bağlı değildir. İletişim veya bant genişliği darboğazı için tek bir hata noktası yoktur. 

Bir VPC eşleme bağlantısı, veri aktarımını kolaylaştırmanıza yardımcı olur. Örneğin, birden fazla AWS hesabınız varsa, bir dosya paylaşım ağı oluşturmak için VPC'leri bu hesaplar arasında eşleyebilirsiniz. Diğer VPC'lerin, sizin VPC'lerinizden birinde sahip olduğunuz kaynaklara erişmesine izin vermek için bir VPC eşleme bağlantısı da kullanabilirsiniz.

![267](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ff5e9bbf-e8aa-4b20-9d5c-a92246155509)

Yukarıda Şekil: 47’de, “EC2 instance B”, VPC-B ağının altında bulunan “EC2 instance Z” sanal makinesi ile iletişim kurmak isterse ve bu makineler public alt ağ içerisinde ise bu iletişim internet ile sağlanır. 

VPC-A ve VPC-B’yi tek bir network (ağ) gibi konuşlandırmak istersek; bu iki VPC arasında bir peer kurulur. Böylelikle VPC-A ve VPC-B arasında belirlenen kurallara göre iletişim kurulabilir. 

Yukarıda verilen Şekil: 47’de bir VPC-C ağı eklediğimizi düşünelim. VPC-A ile VPC-B peer bağlantısı ile birbirleri ile iletişim kuruyorlar. Buluta sonradan eklenen VPC-C ile de VPC-B arasında bir peer oluşturmamız durumunda; VPC-C’nin VPC-A ağına doğrudan erişebileceği anlamı **çıkarılamaz**. 

Şu an bu kılavuz kapsamında region’a atanan varsayılan VPC ve tarafımızca oluşturulan “ilkVPC” isimli VPC olmak üzere iki adet ağ bulunmaktadır. Bu iki ağı peer bağlantısı ile birbirlerine bağlayalım. Şu adımları izleyebiliriz:

- VPC kontrol panelinde sol tarafta bulunan “peering connections” seçeneğine tıklayalım ve “create peering connection” ile oluşturmaya başlayalım. 
- İsim olarak “ilk-Peer” diyelim. 
- VPC ID (Requester) olarak varsayılan (default) VPC’yi seçelim. 
- Hangi VPC ile bağlayacağımız seçilir. Peering region bazlı değildir. Bununla beraber VPC’lerin IP adres blokları çakışmamalıdır. VPC’ler paketlerin nereye gideceğini bilemez. Bu yüzden farklı CIDR değerleri olmalıdır. 
- Hangi VPC ile bağlayacağımızı seçmek için sırasıyla “My account” ve “This region” seçenekleri tıklanmış iken aşağıda açılan opsiyonlardan “ilkVPC” isimli VPC seçilir. 
- İki ağ da bize aittir. Bir hesap başka bir VPC üzerinde olsaydı bu konuda onay gerekmektedir. Ancak iki VPC’de bizim hesabımızda olduğu için “ilk-Peer” seçili iken Actions →Accept Request adımları izlenir. 
- Bu aşamadan sonra yönlendirme tabloları güncellenmelidir. Varsayılan VPC’ye ait yönlendirme tablosu seçili iken “Routes” ve “Edit routes” seçenekleri kullanılır. Sonrasında “ilkVPC”nin IPv4 CIDR değeri olan 10.10.0.0/16 girilir. Target değeri olarak “Peering connections” ve hemen ardından az önce oluşturulan “ilk-Peer” seçilir. 
- Aynı şekilde “ilkVPC” ağına ait yönlendirme tablosuna da varsayılan VPC’nin CIDR değeri olan 172.31.0.0/16 girilir. Target değeri olarak yine “Peering connections” ve hemen ardından az önce oluşturulan “ilk-Peer” seçilir.

Bu işlemlerin sonunda artık iki ağ aralarında internete çıkma gereksinimi duymadan iletişim kurabilecektir. VPC konusunda bu kılavuzda değinilecek konular bu şekilde sonlanmıştır.
