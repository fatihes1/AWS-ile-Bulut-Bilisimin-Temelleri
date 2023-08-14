# 11. Amazon Route53
Route53 servisinin daha iyi anlaşabilmesi için DNS’in (Domian Name System) yani alan adı sisteminin ne olduğu anlaşılmalıdır.

## 11.1. DNS Nedir?
Etki Alanı Adı Sistemi (DNS), internetin telefon rehberidir. İnsanlar, bilgilere nytimes.com veya espn.com gibi alan adları aracılığıyla çevrimiçi olarak erişir. Web tarayıcıları, “İnternet Protokolü (IP)” adresleri aracılığıyla etkileşime girer. DNS, tarayıcıların internet kaynaklarını yükleyebilmesi için alan adlarını IP adreslerine çevirir. 

İnternete bağlı her cihazın, diğer makinelerin cihazı bulmak için kullandığı benzersiz bir IP adresi vardır. DNS sunucuları, insanların 192.168.1.1 (IPv4'te) gibi IP adreslerini veya 2400:cb00:2048:1::c629:d7a2 (IPv6'da) gibi daha karmaşık yeni alfa sayısal IP adreslerini ezberleme ihtiyacını ortadan kaldırır.

## 11.2. DNS Nasıl Çalışır?
DNS çözümleme süreci, bir ana bilgisayar adının (www.example.com gibi) bilgisayar dostu bir IP adresine (192.168.1.1 gibi) dönüştürülmesini içerir. İnternetteki her cihaza bir IP adresi verilir ve bu adres uygun internet cihazını bulmak için gereklidir- belirli bir evi bulmak için sokak adresinin kullanılması gibi. Bir kullanıcı bir web sayfası yüklemek istediğinde, kullanıcının web tarayıcısına yazdıkları (example.com) ile example.com web sayfasını bulmak için gereken makine dostu adres (IP adresi) arasında bir çeviri yapılmalıdır. 

DNS çözümlemesinin arkasındaki süreci anlamak için, bir DNS sorgusunun geçmesi gereken farklı donanım bileşenleri hakkında bilgi edinmek önemlidir. Web tarayıcısı için, DNS araması "perde arkasında" gerçekleşir ve ilk istek dışında kullanıcının bilgisayarından herhangi bir etkileşim gerektirmez.

## 11.3. DNS Aramasında Bulunan Adımlar
Çoğu durumda DNS, bir alan adının uygun IP adresine çevrilmesiyle ilgilenir. Bu sürecin nasıl çalıştığını öğrenmek için, bir web tarayıcısından, DNS arama sürecinden geçerken ve tekrar geri dönerken bir DNS aramasının yolunu takip etmek yardımcı olur. Adımlara bir göz atalım. 

Genellikle DNS arama bilgileri, sorgulayan bilgisayarın içinde yerel olarak veya DNS altyapısında uzaktan önbelleğe alınır. Bir DNS aramasında genellikle 8 adım vardır. DNS bilgileri önbelleğe alındığında, DNS arama sürecindeki adımlar atlanır, bu da onu daha hızlı hale getirir. Aşağıdaki örnek, hiçbir şey önbelleğe alınmadığında tüm 8 adımı özetlemektedir. 

DNS aramasındaki 10 adım:
![270](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b0691d41-8153-45bf-a1d7-29d531d439c9)

1. Bir kullanıcı bir web tarayıcısına 'example.com' yazar ve sorgu internete gider. Bir DNS özyinelemeli çözümleyici tarafından alınır. 
2. Çözümleyici daha sonra bir DNS kök ad sunucusunu sorgular. 
3. Kök sunucu daha sonra çözümleyiciye, etki alanları için bilgileri depolayan bir üst 4. düzey etki alanı (TLD) DNS sunucusunun (.com veya .net gibi) adresiyle yanıt verir. example.com’u ararken isteğimiz “.com” TLD’ye yönlendirilir. 
4. Çözümleyici daha sonra “.com” TLD’ye bir istekte bulunur. 
5.  TLD sunucusu daha sonra etki alanının ad sunucusunun IP adresi olan example.com ile yanıt verir. 
6. Son olarak, özyinelemeli çözümleyici, etki alanının ad sunucusuna bir sorgu gönderir. example.com için IP adresi daha sonra ad sunucusundan çözümleyiciye döndürülür.
7.  DNS çözümleyici daha sonra web tarayıcısına başlangıçta istenen etki alanının IP adresiyle yanıt verir. 
8.  DNS aramasının 8 adımı, example.com için IP adresini döndürdüğünde, tarayıcı web sayfası için istekte bulunabilir: 
9. Tarayıcı, IP adresine bir HTTP isteğinde bulunur. 
10. Bu IP’deki sunucu, tarayıcıda oluşturulacak web sayfasını döndürür.

## 11.4. Amazon Route53
Amazon Route 53, yüksek oranda erişilebilir ve ölçeklenebilir bir bulut etki alanı adı sistemi (DNS) web hizmetidir. www.example.com gibi adları bilgisayarların birbirine bağlanmak için kullandığı 192.0.2.1 gibi sayısal IP adreslerine çevirerek geliştiricilerin ve işletmelerin son kullanıcıları internet uygulamalarına yönlendirmesi için son derece güvenilir ve uygun maliyetli bir yöntem sunacak şekilde tasarlanmıştır. Amazon Route 53, IPv6 ile de tam olarak uyumludur. 

Amazon Route 53 trafik akışı, trafiği gecikme süresi tabanlı yönlendirme, coğrafi DNS, coğrafi yakınlık ve ağırlıklı gidiş-dönüş dahil olmak üzere çeşitli yönlendirme türleri üzerinden yönetmenizi kolaylaştırır ve bunların tümü, çeşitli düşük gecikme süreli, hataya dayanıklı mimariler oluşturulabilmesi için DNS yük devretme ile birleştirilebilir. Amazon Route 53 trafik akışının basit görsel düzenleyicisini kullanarak son kullanıcılarınızın tek bir AWS bölgesinde ya da dünyanın farklı yerlerinde olmasından bağımsız olarak uygulamalarınızın uç noktalarına nasıl yönlendirildiğini kolayca yönetebilirsiniz. Amazon Route 53 ayrıca etki alanı adı saydı da sunar. example.com gibi etki alanı adları satın alıp yönetebilirsiniz ve Amazon Route 53, etki alanlarınızın DNS ayarlarını otomatik olarak yapılandırır. 

Route 53 sadece bir DNS hizmeti değildir. İnternet trafiğini DNS sunucusu üzerinden, çeşitli kurallar ile dağıtma hizmeti de sağlar. Bir nevi “Load balencing” hizmeti sağlayan bu servis, gelen istekleri coğrafi olarak ya da gecikme bazlı dağıtma şansı da verir. Health check yani sağlık kontrolü özelliği sayesinde servis erişilmez durumda ise adresi yayınlanmayacaktır. Böylelikle kullanıcıların fail-over senaryoları kurmasına imkân tanır.

## 11.5. Route 53 Servisinin Kullanımı
Bu kılavuz kapsamında ve bu başlık altında yapılacak işlemler için ilk olarak EC2 kontrol panelinden daha önceki başlıklar altında oluşturulan BaseAMI seçilir. Actions → Copy AMI → US East (Virginia) yapılır. Böylelikle artık Virginia bölgesinde bir EC2 instance oluşturulurken bu AMI kullanılabilir hale gelir. Bu başlık altına iki tanesi EU- Irlanda ve bir tanesi US Virginia olmak üzere toplamda üç EC2 instance üzerinden ilerleyecektir. Bu aşamada yukarıda belirtilen 3 EC2 instance oluşturulur. 

İrlanda bölgesinde iken Route 53 servisinin kontrol merkezine erişelim. Domian registiration alanından bir adet domain name alalım. Bu kısım, bu doküman kapsamında isteğe bağlıdır. AWS bu kısımda belirtilen domain için ücret kesimi yapacaktır. Domain için gerekli kişisel bilgiler verildikten sonra bu domain adresi artık alan kullanıcıya ait olur. 

Route 53 kontrol panelinde iken “Create Hosted Zone” seçeneğini kullanarak domain için bir alan oluşturulmuş olur. Oluştur denildiğinde private ve public olmak üzere iki seçenek sunar. Public domain, dışarıdan erişime açıktır ve ekstra ücret talep eder. Private domain ise VPC içerisinde bulunan cihazlar için özel DNS çözümlemesi sunar. Private bir domain oluşturularak başlayalım. Aşağıdaki adımlar izlenebilir:

- Domain name değerini “seminer.local” olarak belirleyelim. Türü olarak ise private yani özel bir domain olsun. Hangi ağda olduğunu seçerken ise bu kılavuz içerisinde oluşturulan ilkVPC’yi seçelim.
- Oluşturulduğu anda SOA ve NS isimlendirme kuralları otomatik olarak oluşturulur. SOA (Start Of Authority), yönetimsel kayıtların bulunduğu kuralları tanımlar ve NS için bu zone üzerinde barındırılan yetkili sunucuları tutar. Her iki kayıt için de bir TTL değeri vardır. 
- Her DNS sunucusu hem zone içi varsayılan olarak hem de her kayıtta ayrı ayrı olmak üzere bir time to live (TTL) süresine sahiptir. DNS sunucudan bir sorgu atılıp cevap alınınca belirtilen TTL süresi kadar DNS sunucu bu kaydı üzerinde barındırır. Bu süre boyunca DNS sunucusuna yeni sorgu gitmez, böylelikle DNS sunucusuna yük binmemiş olur. Bununla beraber IP adresi sık sık değişiyor ise veya migration tarzı geçiş hizmeti yapılıyor ise TTL süresinin kısa olması tavsiye edilir.
- Create record set ile bir A kaydı oluşturalım. “name” değeri olarak “test”, TTL olarak 5 dakika, value olarak da 1.2.3.4 değerlerini belirtelim. A kaydı DNS’in en temel kaydıdır. Bu kayıt sayesinde bu DNS sunucusuna “test.seminer.local” adresinin IP adresi sorulur ise 1.2.3.4 değerini döndürür. 
- Bu kaydın başarılı olup olmadığını test etmek için “ilkVPC” ağında bulunan public EC2 instane’ına bağlanalım. ping test.seminer.local komutu ile iletişim kurmaya çalışalım. Dönen çıktıdan anlaşılacağı gibi EC2 instance, DNS sunucusundan kayda bakarak öğrendi ve istek atmayı denedi. Hosted zone bu VPC’ye atandığı için EC2 buraya sorgu atabilir hale geldi. Sorgusuna cevap olarak gelen IP ile pin komutu ile iletişim kurmaya çalıştı.

İlk A kaydı oluşturularak, bu kaydın aslında bir IP adresi yerine kullanılacak bir yerel domain name sağladığını görmüş olduk. Aşağıdaki adımları da takip ederek bir CNAME kaydı oluşturalım.

- Create record set ile bir CNAME kaydı oluşturalım. name değerini “www” olarak belirtelim. CNAME kaydının, A kaydından farkı oldukça basittir. A kaydı, bir nevi makine ismi ile IP adresini eşleştirir. CNAME kaydı ise bu IP adresine başka isimlerle de erişebilmesini sağlamaktır. Bu işlem zaten A kaydı ile yapılsa da IP adresi değiştiği an tüm kayıtlar tekrardan manuel olarak güncellemek zorunda kalacaktık. CNAME kaydı ile bu külfetli işten kurtulmuş oluruz.

Alias kaydı ise CNAME kaydının teoride aynısıdır. Farkı ise CNAME kaydı kullanıcı tarafından oluşturulur ve güncellenir. Alias kaydı ise AWS tarafından güncellenir. Örneğin alias kaydını bir yük dağıtıcısına bağlarsak (Load Balancer) ve yük dağıtıcısının IP adres değeri değişirse, alias kaydı otomatik olarak yeni IP ile tüm kayıtları günceller. CNAME kaydı ücretsiz iken alias kaydı ücretlendirilir. 

Şimdi ise Route 53 kontrol paneli üzerinden sağlık kontrolü oluşturalım. (Bu başlık altında bu kısımdan sonrası ücretli olan public domain ile ilgilidir.) Health check yani sağlık kontrolü sayesinde servisin veya kaynağın sağlıklı bir şekilde çalışıp çalışmadığını kontrol eder. Şu an da başlığın başında oluşturulan EC2 instance’ları için birer sağlık kontrolü oluşturalım. İlk sunucu için sağlık kontrolü oluştururken aşağıdaki işlemler izlenebilir:

- İsim olarak WebServerIr1 ve tür olarak end-point seçelim. 
- IP adresi üzerinden monitoring yapılmasını isteyelim ve protokol olarak HTTP protokolünü seçelim. 
- IP adresi alanına EC2 sanal makinesinin public IP değerini girelim. Port olarak HTTP istekleri için kullanılan 80 portunu belirtelim.

Yukarıdaki adımları diğer iki sunucu için da farklı isim ve sanal makinelerin IP adreslerine dikkat ederek tekrar oluşturalım. 

Public domain için create record set diyerek ilk olarak bir A kaydı oluşturalım. İsim değerini “website” olarak belirleyelim. Böylelikle alan adına ek olarak alan adının başında “website.” olan hali de bu hosted zone’da yer alır. 

Route 53 servisi temelde basit yük dengeleme (Load Balancing) hizmeti sunabilir. Bu kısım routing policy seçeneğindeki opsiyonlara göre şekillenir. İlk olarak ağırlıklı anlamına gelen “weighted” poliçesine göre bir kural tanımlayalım ve ilk olarak İrlanda konumunda bulunan sunuculardan birinin IP değerini kullanarak ve weight değeri 10 olacak şekilde bir kural tanımlayalım. Sonrasında yine aynı kayıt işlemini bu sefer Virginia konumundaki sanal makine IP adresi ve weight değeri 90 olarak oluşturalım. Bu kayıt sayesinde kullanıcılardan gelen 10 istekten biri Avrupa'da bulunan EC2 instance tarafından diğer dokuzu ise Amerika’da bulunan EC2 instance tarafından cevap verilecektir. Ağırlıklı olduğu gibi gecikme süresi ve konumlarına göre de kurallar tanımlanabilir. Böylelikle DNS seviyesinde bir load balancing işlemi uygulanmış olur. 

AWS bu şekilde tek tek tanımlanan kurallarda karmaşıklık oluşabileceğini fark ettiği için Route 53 kontrol panelinde bulunan “Traffic Policies” özelliğini devreye almıştır. Bu şekilde bir nevi görsel bir arayüz (GUI) kullanılarak tüm işlemler bir akış şeması gibi belirlenir. Bu özellik tanımlanan kuralların daha kolay anlaşılmasını sağlar.


