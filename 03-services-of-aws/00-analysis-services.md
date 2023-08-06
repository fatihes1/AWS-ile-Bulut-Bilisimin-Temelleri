# 1. Analiz Servisleri
## 1.1. Amazon Athena
![12](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f7acea74-526c-482a-a4eb-67ca19d4d2df)

Amazon Athena, Amazon S3'te standart SQL kullanarak veri analizi yapmanızı kolaylaştıran etkileşimli bir sorgu sistemidir. Athena sunucusuz (serverless) olduğundan yönetilmesi gereken bir altyapı yoktur ve yalnızca çalıştırdığınız sorgular için ödeme yaparsınız. 

Athena'nın kullanımı kolaydır. Basitçe Amazon S3'teki verilerinizi belirtin, şemayı tanımlayın ve standart SQL kullanarak sorgulamaya başlayın. Çoğu sonuç saniyeler içinde sunulur. Athena'da verilerinizi analize hazırlayacak karmaşık ETL (Extract, Transform, Load) işlerine gerek yoktur. Böylece SQL becerileri olan herkesin büyük ölçekli veri kümelerini hızlıca analiz etmesi kolaylaşır. 

Athena, AWS Glue Veri Kataloğu ile entegre olup çeşitli hizmetler arasında birleşik bir meta veri deposu oluşturmanıza, şemaları keşfedip kataloğunuzu yeni ve değiştirilmiş tablo ve bölüm tanımlarıyla doldurmak için veri kaynaklarını taramanıza ve şema sürümü oluşturmayı korumanıza olanak sağlar.

## 1.2. Amazon CloudSearch
![13](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/44d1db4c-5bf6-4e32-b6f8-7956720e3616)

Amazon CloudSearch, AWS Cloud'da web siteniz veya uygulamanız için bir arama çözümü kurmayı, yönetmeyi ve ölçeklendirmeyi hem basit hem de uygun maliyetli hale getiren bir yönetilen hizmettir. 

Amazon CloudSearch, 34 dilin yanı sıra vurgulama, otomatik tamamlama ve coğrafi mekânsal arama gibi popüler arama özelliklerini destekler.

## 1.3. Amazon EMR (Elastic Map Reduce)
![14](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/d6dbe527-d2ea-423d-b454-fb2d2c1f7849)

Büyük veri uygulamalarını ve petabayt ölçeğinde veri analizlerini daha hızlı hale getirir. Şirket içi çözümlerin yarısından daha az maliyetle çalıştırır. Özelleştirilmiş Amazon EC2 kümeleri, Amazon EKS, AWS Outposts veya Amazon EMR Sunucusuz üzerinde çalıştırma seçenekleriyle en yeni açık kaynaklı çerçeveleri kullanarak uygulamalar oluşturabilirsiniz. 

Spark, Hive ve Presto'nun performans için optimize edilmiş ve açık kaynaklı API uyumlu sürümleriyle öngörülere 2 kata kadar daha hızlı erişim imkânı sunmaktadır. EMR Studio'daki EMR Notebooks'u ve bilindik açık kaynaklı araçları kullanarak uygulamalarınızı kolayca geliştirmenize, görselleştirmenize ve uygulamalarınızdaki hataları ayıklamanıza imkân sunmaktadır.

## 1.4. Amazon FinSpace
![15](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/75a83422-54e1-4ab6-86e5-93ce7d4abdae)

Amazon FinSpace, finansal hizmetler endüstrisi (FSI - Financial Services Industry) için özel olarak oluşturulmuş bir veri yönetimi ve analitik hizmetidir. FinSpace, analize hazır olmak için petabaytlarca finansal veriyi bulmak ve hazırlamak için harcadığınız süreyi aylardan dakikalara indirir. 

Finansal hizmetler kuruluşları, portföy, aktüeryal ve risk yönetimi sistemleri gibi dahili veri depolarından gelen verileri ve ayrıca borsalardaki geçmiş menkul kıymet fiyatları gibi üçüncü 31 taraf veri akışlarından gelen petabaytlarca veriyi analiz eder. Doğru verilerin bulunması, verilere uyumlu bir şekilde erişim izinlerinin alınması ve analize hazırlanması aylar alabilir. FinSpace, finansal analitik için bir veri yönetim sistemi oluşturmanın ve sürdürmenin ağır yükünü ortadan kaldırır. 

FinSpace ile verileri toplar ve varlık sınıfı, risk sınıflandırması veya coğrafi bölge gibi ilgili iş kavramlarına göre kataloglarsınız. FinSpace, uyumluluk gereksinimlerinize uygun olarak kuruluşunuz genelinde verileri keşfetmeyi ve paylaşmayı kolaylaştırır. Veri erişim ilkelerinizi tek bir yerde tanımlarsınız ve FinSpace, uyumluluk ve etkinlik raporlamasına izin vermek için denetim günlüklerini tutarken bunları uygular. FinSpace ayrıca analiz için veri hazırlamanız için zaman çubukları ve Bollinger bantları gibi 100'den fazla fonksiyondan oluşan bir kitaplık içerir.

## 1.5. Amazon Kinesis
![16](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/cb55202c-b642-4366-8ccd-17819a4733d6)

Amazon Kinesis gerçek zamanlı akış verilerini toplamayı, işlemeyi ve analiz etmeyi kolaylaştırır. Bu yüzden zamanında öngörüler elde edebilir ve yeni bilgilere hızlı tepki verebilirsiniz. Amazon Kinesis her ölçekteki akış verilerini uygun maliyetle işlemeye yönelik önemli özellikler sunduğu gibi, uygulamanızın gereksinimlerine en uygun araçları seçme esnekliği de getirir. 

Amazon Kinesis ile makine öğrenimi, analiz ve diğer uygulamalar için video, ses, uygulama günlükleri, web sitesi tıklama akışları ve IoT telemetri verileri gibi gerçek zamanlı veriler alabilirsiniz. Amazon Kinesis gelen verileri hemen işlemenize, analiz etmenize ve bu verilere anında yanıt vermenize olanak tanır. İşleme sürecinin başlaması için tüm verilerinizin toplanmasını beklemek zorunda kalmazsınız.

## 1.6. Amazon Managed Streaming for Apache Kafka (MSK)
![17](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/9b72d0c5-3af4-4391-88af-a75f3f232a23)

Yüksek oranda erişilebilir Apache Kafka ve Kafka Connect kümelerinin tedariki, yapılandırması ve bakımı da dahil, operasyonel iş yükünü ortadan kaldırır. Apache Kafka için tasarlanan uygulama ve araçları olduğu gibi kullanmaya başlayabilir (kod değişikliği gerekmez) ve küme kapasitesini otomatik olarak ölçeklendirebilirsiniz. 

Yerel AWS entegrasyonlarını kullanarak güvenli, uygun ve üretime hazır uygulamaları kolayca dağıtabilirsiniz. Amazon MSK ile maliyetleri düşük tutun. Kullandıkça öde fiyatlandırması ile diğer sağlayıcıların maliyetinin 1/13'ü kadar düşük bir fiyatla sunulur.

## 1.7. Amazon OpenSearch Service
![18](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f6ed8e44-b3a2-47e4-967e-78ff8757f6f1)

Amazon OpenSearch Service, Amazon ElasticSearch servisi yerine geçmiştir. OpenSearch'ü topluluk odaklı, açık kaynaklı yazılımın önde gelen destekçisi ile çalıştırma imkânı sunar. İhtiyacınız olanı kolaylıkla bulmak için yapılandırılmamış ve yarı yapılandırılmış verilerinizde hızlı bir şekilde arama ve analiz yapabilirsiniz. Otomatik tedarik, yazılım yükleme, düzeltme eki uygulama, depolama katmanlama ve daha fazlasıyla operasyonel iş yükünü ortadan kaldırabilir ve maliyeti azaltabilirsiniz. Anormallikleri gerçek zamanlı olarak tespit etmek, kümelerinizi otomatik olarak ayarlamak ve arama sonuçlarınızı kişiselleştirmek için makine öğrenimini (ML) kullanabilirsiniz

## 1.8. Amazon QuickSight
![19](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/2edc9af4-81e2-4b0b-9ce8-ec3b6d0d1e84)

Amazon QuickSight, kuruluşunuzdaki herkesin doğal dilde sorular sorarak, etkileşimli panolar yoluyla inceleme yaparak veya makine öğrenimi destekli düzenleri ve aykırı değerleri otomatik olarak arayarak verilerinizi anlamasına olanak sağlar. QuickSight, müşteriler için her hafta milyonlarca pano görünümünü destekleyerek müşteri son kullanıcılarının veriye dayalı kararları daha sağlıklı şekilde almasına imkân verir.

## 1.9. Amazon RedShift
![20](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ed0bc8ab-f0e8-43a1-aa9a-27a11a271a5a)

Herkes için kolay analizlerle verilerden saniyeler içinde öngörüler elde etmeye odaklanın. Veri ambarı altyapınızı yönetme konusunu düşünmek zorunda kalmazsınız. Operasyonel veri tabanları, data-lake'ler, veri ambarları ve üçüncü taraf veri kümelerindeki tüm verilerinizi analiz edebilir. Sorgu hızını iyileştiren otomasyon sayesinde uygun ölçekte diğer bulut veri ambarlarından 3 kata kadar daha iyi fiyat performansı elde etme imkânı bulursunuz.

## 1.10. AWS Data Exchange
![21](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/760d3d6e-7f78-4308-b4a9-453ef6f199fe)

AWS Data Exchange, bulutta üçüncü taraf verilerini bulmayı, kullanmayı ve bunlara abone olmayı kolaylaştırır. Nitelikli veri sağlayıcılar arasında yılda birden fazla dilde 2,2 milyonun üzerinde benzersiz haber hikayesinden veri düzenleyen Reuters, yılda 14 milyar sağlık hizmeti işlemi ve 1 trilyon USD alacak işleyen ve anonimleştiren Change Healthcare, 330 milyondan fazla küresel iş kaydından oluşan veri tabanının bakımını sağlayan Dun & Bradstreet, 220 milyon benzersiz müşteriden konum verisi türeten ve 60 milyondan fazla küresel ticari mekân içeren Foursquare gibi kategori liderleri vardır. 

Bir veri ürününe abone olduktan sonra, AWS Data Exchange API'sini kullanarak verileri doğrudan Amazon Simple Storage Service'e (S3) yükleyebilir ve analiz etmek için bir dizi AWS analiz ve makine öğrenimi (ML) hizmetinden yararlanabilirsiniz. Örneğin, mülk sigortacıları farklı coğrafyalarda sigorta kapsama gereksinimlerini kalibre etme amacıyla geçmiş hava durumu verilerine abone olabilir; restoranlar, genişleme için ideal bölgeleri tanımlamak amacıyla nüfus ve konum verilerine abone olabilir; akademik araştırmacılar, iklim değişikliği ile ilgili çalışmalar yapmak için karbondioksit emisyon verilerine abone olabilir; sağlık uzmanları, araştırma faaliyetlerini hızlandırmak için geçmiş klinik çalışmalardan elde edilen toplu verilere abone olabilir. 

AWS Data Exchange, veri sağlayıcıları için veri depolama, teslim etme, faturalandırma ve yetkilendirme ihtiyacını ortadan kaldırarak buluta geçen milyonlarca AWS müşterisine erişmeyi kolaylaştırır.

## 1.11. AWS Data Pipeline
![22](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/5c9c935e-9350-45e3-9b7a-fbb26c12f4aa)

AWS Data Pipeline, verilerinizi belirli aralıklarla güvenilir bir şekilde işlemenize olanak sağlar. Farklı AWS işlem ve depolama hizmetlerinin yanı sıra şirket içi veri kaynakları arasında taşımanıza da yardımcı olan bir web hizmetidir. AWS Data Pipeline ile verilerinize depolandıkları yerde düzenli olarak erişebilir, uygun ölçekte dönüştürüp işleyebilir ve sonuçları Amazon S3, Amazon RDS, Amazon DynamoDB ve Amazon EMR gibi AWS hizmetlerine aktarabilirsiniz. 

AWS Data Pipeline, kolayca hata toleranslı, yinelenebilir ve yüksek oranda erişilebilir karmaşık veri işleme iş yükleri oluşturmanıza yardımcı olur. Kaynakların erişilebilir olmasını sağlama, görevler arası bağımlılıkları yönetme, tek tek görevlerde geçici hataları veya zaman aşımlarını yeniden deneme ya da bir hata bildirim sistemi oluşturma konusunda 33 endişelenmeniz gerekmez. AWS Data Pipeline, daha önce şirket içi veri silolarında kilitli kalan verileri taşımanıza ve işlemenize de imkân tanır.

## 1.12. AWS Glue
![23](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/083dd745-d55f-4e08-b6ae-ced43cc5cb3c)

AWS Glue; analiz, makine öğrenimi ve uygulama geliştirme için verilerin keşfedilmesini, hazırlanmasını ve birleştirilmesini kolay hale getiren sunucusuz bir veri entegrasyonu hizmetidir. AWS Glue, veri entegrasyonu için gereken tüm özellikleri sunar ve böylece verilerinizi analiz etmeye başlayabilir. Bu sayede aylar yerine dakikalar içinde verilerinizi kullanabilirsiniz. 

Veri entegrasyonu; analiz, makine öğrenimi ve uygulama geliştirme için verilerin hazırlanması ve birleştirilmesi işlemidir. Bu sürece farklı kaynaklardan veri keşfetme ve çıkarma, verileri zenginleştirme, temizleme, normalleştirme ve birleştirme; veri tabanlarından, veri ambarlarında ve data-lake’lerde verilerin yüklenmesi ve düzenlenmesi gibi birçok görev dâhildir. Bu görevler çoğu zaman farklı ürünler kullanan farklı kullanıcı tipleri tarafından yürütülür. 

AWS Glue, veri entegrasyonunu kolaylaştırmak için hem görsel hem kod tabanlı arayüzler sağlar. Kullanıcılar AWS Glue Data Catalog kullanarak verileri kolayca bulabilir ve bu verilere erişebilir. Veri mühendisleri ve ETL (çıkarma, dönüştürme ve yükleme) geliştiricileri, AWS Glue Studio içinde birkaç tıklamayla ETL iş akışlarını görsel olarak oluşturabilir, yürütebilir ve izleyebilirler. Veri analizcileri ve veri bilimcileri, kod yazmadan verileri görsel olarak zenginleştirmek, temizlemek ve normalleştirmek için AWS Glue DataBrew’i kullanabilirler. Uygulama geliştiricileri, farklı veri depolarında verileri birleştirmek ve çoğaltmak için AWS Glue Elastic Views ile tanıdık yapısal sorgulama dili olan SQL’i kullanabilirler.

## 1.13. AWS Lake Formation
![24](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f46f004a-5005-43c1-a260-d21f523db00c)

AWS Lake Formation, günler içinde güvenli bir data-lake kurmanızı kolaylaştıran bir hizmettir. Data-lake, tüm verilerinizi hem orijinal hem de analize hazır halinde depolayan, merkezi, düzenlenmiş ve güvenli bir depodur. Data-lake, veri depolarını ortadan kaldırmanızı, öngörü kazanmak ve daha iyi iş kararları vermek için farklı analiz türlerini birleştirmenizi sağlar. 

Günümüzde data-lake kurmak ve yönetmek birçok manuel, karmaşık ve zaman alan görev içermektedir. Bu görevler çeşitli kaynaklardan veri yüklemeyi, bu veri akışlarını izlemeyi, bölümler ayarlamayı, şifrelemeyi açmayı ve anahtarları yönetmeyi, dönüşüm işlerini tanımlamayı ve işlemlerini izlemeyi, verileri sütun biçiminde organize etmeyi, yedekli verileri tekilleştirmeyi ve bağlantılı kayıtları eşleştirmeyi içerir. Data-lake'e veri yüklendikten sonra veri kümelerine ayrıntılı erişim vermeniz, zaman içindeki erişimi çok çeşitli analiz ve makine öğrenimi (ML) araçları, hizmetleri genelinde denetlemeniz gerekir. 

Lake Formation ile data-lake oluşturmak veri kaynaklarını, hangi erişim ve güvenlik politikalarını uygulamak istediğinizi tanımlamak kadar basittir. Daha sonra Lake Formation, veri tabanlarından ve nesne depolarından veri toplamanıza ve kataloglamanıza, veriyi yeni Amazon Simple Storage Service (S3) data-lake'inize taşımanıza, makine öğrenimi algoritmalarını kullanarak verilerinizi temizlemenize ve sınıflandırmanıza ve sütun, satır ve hücre düzeylerinde ayrıntılı denetimler kullanarak hassas verilerinize erişimi güvenli hale getirmenize yardımcı olur. Kullanıcılarınız, mevcut veri kümelerini ve uygun kullanımlarını tanımlayan merkezi bir veri kataloğuna erişebilir. Kullanıcılar daha sonra bu veri kümelerini Amazon Redshift, Amazon Athena, Apache Spark için Amazon EMR ve Amazon QuickSight gibi tercih ettikleri analiz ve makine öğrenimi hizmetleriyle birlikte kullanabilir. Lake Formation, AWS Glue'daki özellikler temel alınarak oluşturulur.





