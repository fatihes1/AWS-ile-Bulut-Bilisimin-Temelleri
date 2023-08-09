# 3. S3 (Simple Storage Service) Servisi Kullanımı
Amazon Simple Storage Service (Amazon S3); sektör lideri ölçeklenebilirlik, veri erişilebilirliği, güvenlik ve performans sunan bir nesne depolama hizmetidir. Her büyüklükteki ve her sektörden müşteriler istedikleri miktarda veriyi data-lake, bulut temelli ve mobil uygulamalar gibi neredeyse her türlü kullanım örneği için depolayıp koruyabilir. Uygun maliyetli depolama sınıfları ve kullanımı kolay yönetim özellikleri sayesinde maliyetlerinizi optimize edebilir, verilerinizi düzenleyebilir ve hassas ayarlanmış erişim denetimlerini belirli iş, kuruluş ve uygunluk gereksinimlerini karşılayacak şekilde yapılandırabilirsiniz.

![242](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/237d1486-b9af-4559-af11-473eb16de28f)

AWS tarafından sunulan başka bir servis olan Amazon Elastic Block Store ile farkları şu şekildedir:
- Amazon EBS blok tabanlıdır, Amazon S3 ise obje tabanlıdır. 
- Amazon EBS’de veriler disk imajları şeklindedir, Amazon S3’te ise objeler ve meta datalar olarak depolanabilir. 
- Amazon EBS’de bir bilgisayara bağlanarak işletim sistemi, uygulama, veri tabanı vb. kurulabilirken Amazon S3’te kurulamaz.

Amazon S3 servisi günümüzde popüler olan OneDrive, GoogleCrive, ICloud gibi SaaS servislerine benzer ancak çok daha fazlasıdır. 

Kullanıcılar Amazon S3 üzerinde sınırsız depolamaya sahiptir, tek şart tek bir dosyanın boyutunun 5 TB’den fazla olmamasıdır. S3 depolama birimlerine bucket yani kova denmektedir. S3 üzerinde oluşturulan ilk şey bucket’lardır. Bucket nihayetinde nesnelerin depolanacağı konteynerlerdir. Kullanıcılar bir veya daha fazla bucket’a sahip olabilir. Bucket’lar region yani bölge bazlıdır. Bir bucket nesne deposunun yanı sıra meta datalar da tutar. Meta data nesnelerin özelliklerini belirleyen “veri hakkında veri” olarak düşünülebilir. Örnek olarak; objenin yaratılma tarihi, boyutu, dosya türü gibi değerler o obje ile tutulan meta datalardır.

## 3.1. Amazon S3 Bucket Oluşturma ve Temel İşlemler
![243](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/5fe94d80-8238-4f37-8a73-7ae4f59e2a9e)

1. Bir bucket oluşturulurken ilk aşamada bucket için bir isim belirlenmelidir. Bucket’lar unique yani benzersiz bir isme sahip olmalıdır.
2. İsim belirlendikten sonra hangi bölgede oluşturulmak istendiği seçilir. Bucket’lar region bazlıdır; yani bir bucket bir bölgede tutulabilir, bölgeler arası dağıtılamaz.
3. Opsiyonlu olarak bucket oluşturma kısmındaki diğer ayarlar ile uğraşmak yerine daha önceden oluşturulmuş bir bucket için seçilen ayarların kopyalanması tercih edilebilir.
4. Nesne sahipliği kısmında, Diğer AWS hesaplarından bu pakete yazılan nesnelerin sahipliğini ve erişim kontrol listelerinin (ACL’ler- Access Control Lists) kullanımını kontrol edebilirsiniz. Nesne sahipliği, nesnelere erişimi kimlerin belirleyebileceğini belirler. 
5. Geçtiğimiz yıllarda genel erişime açık bucket’larda birçok sorun çıkmasından dolayı AWS varsayılan olarak bu bucket’ların genel (public) erişime kapalı oluşturur. Bucket oluşturulurken bu ayar değiştirilebilir.
![244](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/303335a2-7d72-4cc8-bda6-2bc2d12761ca)

6. Sürüm oluşturma, bir nesnenin birden çok varyantını aynı kovada tutmanın bir yoludur. Amazon S3 klasörünüzde depolanan her nesnenin her sürümünü korumak, almak ve geri yüklemek için sürüm oluşturmayı kullanabilirsiniz. Sürüm oluşturma ile hem istenmeyen kullanıcı eylemlerinden hem de uygulama hatalarından kolayca kurtulabilirsiniz. Bu hizmet sayesinde yanlışlıkla silinen bir dosyanın eski versiyonuna kolaylıkla dönülebilir. 
7. Bucket’ı etiketleyerek depolama maliyetini veya diğer kriterleri takip edebilirsiniz. 
8. Bu pakette depolanan yeni nesneleri otomatik olarak şifreleyin seçeneği ile depolanan her dosyanın şifrelenmesini sağlarsınız. 
9. Nesne kilidi (Object Lock) seçeneğini etkinleştirerek; nesnelerin belirli bir süre veya süresiz olarak silinmesini veya üzerine yazılmasını önlemenize yardımcı olmak için bir kez yaz çok oku (WORM) modelini kullanarak nesneleri depolamaya devam edersiniz. 

Bu aşamalar sonunda bucket oluşturulmuş olur. Bucket’ların listelendiği alanda bucket’a giriş yapılabilir ve sonrasında dilenirse ekranın sağında bulunan, turuncu “Upload” butonuyla dosya yüklenebilir. 

Yüklenen bir dosya hakkındaki meta-data’lar aşağıdaki görselde belirtilmiştir. 

![245](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/127c925a-6326-44f2-8a88-779ec14d5dee)

Bu meta veriler sistem tarafından tanımlıdır. Kullanıcılar dosyalarına diledikleri durumunda “anahtar:değer” ikilisi şeklinde meta data tanımlayabilir ve sonrasında meta dataya göre dosya getirme işlemleri uygulanabilir. 

AWS S3 yapısal olarak 3 farklı depolama çözümüne sahiptir. Bu çözümler alt yapı olarak çeşitli farklılıklar içermektedir.

- ***S3 Standard:*** Varsayılan depolama çözümüdür. Depolanan her obje 3 farklı erişilebilirlik alanı arasında kopyalanır. Servis %99,999999999 (11 tane 9) erişilebilirlik sunar. 24 saat içerisinde maksimum 8 saniye erişememe yaşanabilir. Aynı zamanda 1 milyar dosyanın sadece 1’i bozulabilir ve kaybolabilir. 105 
- ***S3 Standard-IA:*** Çok sık erişilmeyen ancak ihtiyaç duyulması durumunda da çok süre geçmeden erişilmesi istenen dosyalar bu katmanda bulunur. Servis %99,999999999 (11 tane 9) erişilebilirlik sunar. Günde maksimum 1 dakika 26 saniye bir kesilme yaşanabilir. Standard katmana göre daha ucuzdur ancak dosyalara erişim başına ekstra ücretlendirilir. 
- ***S3 One Zone-IA:*** Yukarıda belirtilen iki katmanın aksine tek bir erişilebilirlik alanında tutulur. Günde 7 dakika 30 saniyeye kadar kesinti yaşanabilir. Nadir erişilen ve kaybolması durumunda kriz yaratmayacak verilere burada yer verilir.

2018 sonuna kadar bu 3 katman bulunurken 2018 yılında AWS yeni bir özellik tanıttı. S3 Intelligent-Tiering ile depolanan objelerin bu üç katman arası transfer ve yönetimini kullanıcıdan alıp otomatik hale getirmeye başlamıştır. 

Bununla beraber bir katman gibi görünen S3 Glacier, S3’ten tamamen bağımsızdır. Uzun dönem ve sık erişilmeyen dosyaları saklamak için kullanılır. Firmaların birkaç yıl bünyesinde tutma zorunluluğu olduğu arşiv dosyaları burada tutulabilir. Talep edildiği durumda birkaç saat içerisinde hazırlanır ve kullanıcıya sunulur. 

Objeleri bu farklı tier’larda yani katmanlarda konumlandırmanın birden fazla yolu vardır:

- Obje upload edilirken seçilebilir. 
- Upload edilen dosyanın sonrasında özelliklerinden düzenlenebilir.
- Bir kurala bağlanarak belirli süre erişilmeyen objelerin daha ucuz katmanlara geçişi sağlanabilir.

S3 fiyatlandırmada üç temel metriğe göre hesaplanır:

- GB cinsinden toplam depolanan veri boyutuna, 
- S3’ten dış dünyaya transfer edilen (indirme, erişme vb.) veri boyutuna,
- Toplam obje erişim isteği, kriterlerine göre fiyatlandırılır. Genel anlamda dosya tutmak oldukça ucuz olsa da tutulan dosyalara erişmek pahalıdır.

Amazon S3’e dosyalar upload edildikten hemen sonra erişime açılırken, daha önce upload edilmiş bir dosyada yapılan silme ve düzenleme gibi işlemlerin sonucuna erişmek zaman (milisaniye) alacaktır. Bunun sebebi birçok cihazda güncelleme yapma zorunluluğudur. 

Amazon S3’ün gücü Dropbox, Google Drive gibi dosya depolama servisinden ziyade bu hizmetin çok uygun fiyatlara yazılımların içine gömülme imkânı sunmasıdır.

## 2.3. S3 Bucket Özellikleri
![246](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/59b9ca05-7c66-4565-99d5-bd3622ac346e)

Bir bucket açıldığında yukarıdaki görseldeki gibi bir ekran kullanıcıyı karşılar. Properties yani özellikler sekmesini bu başlık altında derinlemesine inceleyelim.

### 3.2.1. Genel Bakış
Bu bölüm altında bucket’ın hangi bölge (region) altında barındığı, ARN (Amazon Resource Name) yani amazon kaynak ismi bilgisi ve bucket’ın oluşturulma tarihi gibi bilgilere yer verilmiştir. ARN servislerin birbirleriyle iletişim kurmasını sağlayan kimliktir.

### 3.2.2. Bucket Versiyonlama
Bir bucket üzerinde aktif edilmesi durumunda tekrar kapatılamayan bir özelliktir. Sadece durdurulabilir. S3 bucket obje tabanlı dosya deposudur. Dosyaların yanlışlıkla silinmesine karşı önlem olarak versiyonlama kullanılabilir. S3 bucket bu özellik açıldığında dosyada yapılan her değişiklikte eski ve yeni halini tutar. Örneğin daha önceden S3 bucket’ına atılmış bir dosyada değişiklik yaptınız, S3 iki versiyonu da tutacaktır. Dosyayı sil dediğimizde ise dosyaya “delete marker” adı verilen bir işaretçi konulacaktır. Bu dosya kullanıcı tarafından görünmeyecektir ve bir API isteği atıldığında dosya listelenmeyecektir. Ancak dosya S3 bucket’ı içerisinde durmaya devam edecektir. Dosyanın geri yüklenmesi gerektiğinde ise konuşlanmış olan delete marker’ın silinmesi yeterli olacaktır. Objelerin listelendiği alanda versiyonları göster seçeneğine tıklanırsa dosyanın eski versiyonları da görünür. Dosyanın eski versiyonun obje URL bilgisi değiştirilmiştir. İşin temelinde silmek için konulan işaretçi de bir yeni versiyon gibi görünmektedir.

### 3.2.3. Etiketler
Bucket’ı etiketleyerek depolama maliyetini veya diğer kriterleri takip edebilme imkânı sunar.

### 3.2.4. Varsayılan şifreleme
Bu pakette depolanan yeni nesneleri otomatik olarak şifrelemenizi sağlayan özelliktir. Şifrelemek için iki farklı yöntem sunmaktadır. Amazon S3 tarafından yönetilen anahtarlar (SSE-S3); Amazon S3'ün sizin için oluşturduğu, yönettiği ve kullandığı bir şifreleme anahtarıdır. AWS Key Management Service anahtarı (SSE-KMS); AWS Key Management Service (AWS KMS) tarafından korunan bir şifreleme anahtarıdır.

### 3.2.5. Akıllı Katmanlama Arşivi Yapılandırmaları
Akıllı katmanlı depolama sınıfında depolanan nesnelerin, uzun süreler boyunca nadiren erişilecek nesneler için optimize edilmiş arşiv erişimi (Archive Access) katmanına veya derin arşiv erişimi katmanına (Deep Archive Access) indirgenmesini sağlar. 

2021’den sonra S3’e katılmış bir özelliktir. Bucket içerisinde tutulan bazı dosyalara az erişilirken bazılarına erişim çok fazla ise bu dosyaları farklı katmanlarda tutmak maddi açıdan önem arz etmektedir. Ne sıklıkla eriştiğini kullanıcı tarafından el yordamıyla kontrol edilmesi yerine, bu özellik sayesinde az erişilen dosyalar alt katmanlara doğru otomatik olarak indirilir. Bu otomatikleştirme işlemi ise sadece katman sınıfı olarak “Intelligent-Tiering” olarak ayarlanan dosyalarda aktif olacaktır.

### 3.2.6. Sunucu Erişim Günlüğü
Paketinize erişim isteklerini günlüğe kaydetmenizi sağlayan özelliktir. S3 bucket’larına birçok obje yüklüyoruz, bu objelere de kullanıcılar istek atıyor. Eğer ki dosyaya kim ne zaman, nereden erişmiş gibi kayıtları tutmak istersek bu özelliği aktif hale getirmeliyiz. Bu işlem için bu günlük bilgilerin yazılacağı yeni bir bucket’a ihtiyaç duyulacaktır.

### 3.2.7. AWS CloudTrail Veri Olayları
CloudTrail konsolunda Amazon S3 nesne düzeyinde API işlemlerini günlüğe kaydetmek için CloudTrail veri olaylarını yapılandırabileceğiniz özelliktir. Yani API erişimi kim tarafından sağlanmış gibi verileri tutmanızı sağlar.

### 3.2.8. Olay Bildirimi
Bu servisi kullanırken ilk olarak bir isim belirlenmelidir. Sonrasında istenirse prefix veya suffix değeri belirtilerek dosya filtrelenebilir. Özellik aktifleştirildiğinde ise S3 bucket içerisinde dosya oluşturma, silme, düzenleme gibi eylemlerin yapılması durumunda e-posta atma gibi değişik yöntemlerle yönetici hesabının bilgilendirilmesi sağlanır.

### 3.2.9. Aktarım İvmesi
Daha hızlı veri aktarımları için hızlandırılmış bir uç nokta kullanılmasını sağlayan özelliktir. Müşterinin 2 TB gibi yüksek ölçekli bir arşive sahip olduğunu varsayalım ve kullanıcı bu arşivi S3 bucket’ına atmak istiyor. Bu işlem normal upload işlemi ile oldukça uzun bir süre alacaktır. 

Bu özelliğin açılması ile normal CLI veya konsol üzerindeki upload url bilgisi yerine Amazon kendi CDN ağını kullanarak dosya aktarımı hızlandırmaya çalışacaktır. Eğer ki Amazon dosya aktarım süresini belirli bir ölçekte azaltırsa ekstra ücretlendirme uygulayacaktır.

### 3.2.10. Object Lock
Nesnelerin belirli bir süre veya süresiz olarak silinmesini veya üzerine yazılmasını önlemenize yardımcı olmak için bir kez yaz çok oku (WORM) modelini kullanarak nesnelerin depolanmasını sağlayan servistir. Temel mantıkta versiyonlamaya benzer olsa da aslında versiyonlama özelliği açık olan bir dosya yine de silinebilir. Silinmemesi için belirli bir süre belirtilebilir veya sonsuza kadar silinmemesi talep edilebilir. Bu özellik sadece S3 bucket’ı oluşturulurken açılabilmektedir.

### 3.2.11. Talep Eden Öder
Etkinleştirildiğinde, istek sahibi, istekleri ve veri aktarım maliyetlerini öder ve bu pakete anonim erişim devre dışı bırakılır. Çünkü Amazon anonim erişimi kime ücretlendireceğini belirleyemez.

### 3.2.12. Static Web Hosting
S3 obje tabanlı depolama çözümü olsa da statik web sayfalarını host edebilir. S3 bir sunucu olmadığı için dinamik web sayfalarını host edemez. Bir statik web sayfasını canlıya almak için ilk olarak web sayfası dosyaları S3 bucket’ına upload edilir. “Static web hosting” özelliği aktif hale getirilir ve index sayfasının ve hata sayfasının yol (path) bilgileri verildikten sonra web sayfası birkaç saniye içerisinde erişilebilir olacaktır.

## 3.3. İzinler
### 3.3.1. Genel Bakış
Bu bölümde bucket’ın izinleri özetlenmektedir.

### 3.3.2. Genel Erişimi Engelle (Bucket Ayarları)
Bucket’lara ve nesnelere erişim kontrol listeleri (ACLs), paket ilkeleri, erişim noktası ilkeleri veya tümü aracılığıyla genel erişim verilir. Tüm S3 klasörlerinize ve nesnelerinize genel erişimin engellendiğinden emin olmak için tüm genel erişimi engelle seçeneğini açın. Bu ayarlar yalnızca bu paket ve erişim noktaları için geçerlidir. AWS, tüm genel erişimi engelle özelliğini açmanızı önerir, ancak bu ayarlardan herhangi birini uygulamadan önce uygulamalarınızın herkese açık erişim olmadan düzgün şekilde çalışacağından emin olmalısınız. Paketlerinize veya içindeki nesnelere bir düzeyde genel erişime ihtiyacınız varsa, belirli depolama kullanım durumlarınıza uyacak şekilde bireysel ayarları özelleştirebilirsiniz.

### 3.3.3. Bucket Poliçeleri
JSON'da yazılan bucket politikası, bucket’ta depolanan nesnelere erişim sağlar. Paket politikaları, diğer hesapların sahip olduğu nesneler için geçerli değildir. ACL yani erişim kontrol listelerinde sadece bu kullanıcı şu yetkiye sahip olsun gibi basit koşullandırmalar ayarlanabilir. Ancak örneğin sadece belirli IP aralığından erişime izin verilmesi veya şu kullanıcılar sadece okurken, şu kullanıcılar sadece yazma erişimine sahip olsun gibi ayarlamalar bu özellik sayesinde yapılabilir. Özetle; daha karmaşık bir erişim kontrolü ayarlanmak istenirse bu ayarlamalar erişim kontrol listeleri üzerinden değil de bucket poliçeleri üzerinden yapılabilir.

### 3.3.4. Bucket Ownership
Diğer AWS hesaplarından bu pakete yazılan nesnelerin sahipliğini ve erişim kontrol listelerinin (ACL'ler) kullanımını kontrol etmenizi sağlayan özelliktir. Nesne sahipliği (Bucket Ownership), nesnelere erişimi kimlerin belirleyebileceğini belirtirsiniz.

### 3.3.5. Erişim Kontrol Listesi 
(Access Control List- ACL) Bucketa kimlerin erişebileceğinin belirtildiği yerdir. Objeleri listeleme, yeni obje yazma ve aynı zamanda okuma/yazma gibi yetkiler tanımlanabilir.

### 3.3.6. Kaynaklar Arası Kaynak Paylaşımı (Croos-origin Resource Sharing - CORS) 
JSON'da yazılan CORS yapılandırması, bir etki alanında yüklenen istemci web uygulamalarının farklı bir etki alanındaki kaynaklarla etkileşime girmesi için bir yol tanımlar. Bu özelliği bir senaryo üzerinden özetlemek gerekirse; www.abc.com ve www.def.com olmak üzere iki alan adı olduğunu varsayalım. “abc.com” bazı kaynakları “def.com” üzerinden çekmek istiyor. Bu durum varsayılan olarak def.com tarafından engellenmiş olarak kabul edelim. CORS kuralları nedeniyle, def.com, abc.com tarafından gelen isteklerine yanıt vermelidir. Bu özelliğin S3 içerisinde yer edinme nedeni ise, S3 static web sayfalarını host edebilir. Bu durumda S3 bucket’ı sunucu gibi davranarak CORS ayarlarına bakarak izin verir veya reddeder.

## 3.4. Metrikler
### 3.4.1. Bucket Metrikleri
Paketinizdeki kullanım, istek ve veri aktarımı etkinliği için ölçümleri keşfedebileceğiniz bir özelliktir. Metrikler ayrıca Amazon CloudWatch'ta da mevcuttur.

![247](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c0609879-b4cf-49c8-b01c-00e4fcfb2d27)

### 3.4.2. Depolama Sınıfı Analizi
Nesneleri uygun depolama sınıfına ne zaman geçireceğinize karar vermenize yardımcı olması için depolama erişim modellerini analiz etmenizi sağlayan özelliktir. Bu özellik sayesinde bir bucket seçersiniz ve S3 tüm dosyalar ile ilgili analizi yapıp “.csv” formatı ile belirtilen bucket’a yazacaktır.

### 3.4.3. Çoğaltma Metrikleri
S3 çoğaltma metrikleri, çoğaltma yapılandırmanızdaki çoğaltma kuralları için ayrıntılı ölçümler sağlar. Çoğaltma ölçümleriyle, bekleyen baytları, bekleyen işlemleri ve çoğaltma gecikmesini izleyerek çoğaltmanın dakika dakika ilerlemesini izleyebilirsiniz.

## 3.5. Yönetim
### 3.5.1. Yaşam Döngüsü Kuralları 
Nesnelerin başka bir depolama sınıfına geçişi, arşivlenmesi veya belirli bir süre sonra silinmesi gibi bir nesnenin ömrü boyunca Amazon S3'ün gerçekleştirmesini istediğiniz eylemleri tanımlamak için yaşam döngüsü kurallarını kullanırız. Objelerin depolama sınıfları (standard, glacier vb.) arası geçinin otomatik kurallara bağlanabilmesini sağlayan kurallar burada yazılır.

### 3.5.2. Çoğaltma Kuralları Amazon 
S3'ün sunucu tarafı şifreleme, replika sahipliği, replikaları başka bir depolama sınıfına geçirme ve daha fazlası gibi replikasyon sırasında uygulamasını istediğiniz seçenekleri tanımlamak için replikasyon kurallarını kullanılır. Her S3 bucket’ı sadece bir bölgede durur. Başka bir bölge de bir bucket yaratılarak ve çoğaltma kuralları tanımlanarak ana bucket üzerinde yapılan her işlemin, yeni oluşturulmuş bucket için de gerçekleşmesi sağlanır. Bu özellik sayesinde bucket yedeği alırken aynı zamanda farklı lokasyondaki pazarlardan erişimi kolaylaştırır.

### 3.5.3. Envanter Yapılandırmaları 
Nesnelerinizin ve meta verilerinizin düz bir dosya listesini oluşturmak için bir pakette envanter yapılandırmaları oluşturabilirsiniz. Bu zamanlanmış raporlar, paketteki tüm nesneleri içerebilir veya paylaşılan bir önekle (prefix) sınırlandırılabilir. Örneğin, bucket üzerinde bulunan bir milyon veriyi belirli özelliklerini görebileceğiniz şekilde bir “.csv”, Apache ORC veya Apache Parquest formatında dosya oluşturmanızı sağlar.

## 3.6. Erişim Noktaları 
Amazon S3 erişim noktaları, S3'teki paylaşılan veri kümeleri için uygun ölçekte veri erişimini yönetmeyi kolaylaştırır. Erişim noktaları, S3 nesne işlemlerini gerçekleştirmek için kullanabileceğiniz paketlere eklenen ağ uç noktaları olarak adlandırılır. Bir erişim noktası diğer bir erişim noktası ARN'si ile aynı işlevselliği sağlar ve normalde veri erişimi için bir S3 grup adının kullanıldığı her yerde kullanım için ikame edilebilir. Erişim noktaları yeni bir S3 bucket’ı açılmış gibidir. Kendisine ait poliçe, erişim kontrol listesi değerlerine sahiptir. Bununla beraber yine kendisine ait url ve ARN yani amazon kaynak ismine sahiptir. S3 bucket’ına erişen her bir uygulama için, bir erişim noktası oluşturularak karmaşanın önüne geçilir.
