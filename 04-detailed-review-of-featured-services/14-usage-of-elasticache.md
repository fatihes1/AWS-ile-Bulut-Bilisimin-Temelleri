# 15. ElastiCache
AWS tarafından sunulan, in-memory cache, yani hafıza içi ön bellekleme servisidir. Amazon ElastiCache, esnek ve gerçek zamanlı kullanım örneklerini destekleyen, tam olarak yönetilen bir bellek içi önbelleğe alma hizmetidir. ElastiCache'i uygulama ve veri tabanı performansını yükselten önbelleğe alma işlemi için veya oturum depoları, oyun puan tabloları, akış ve analiz gibi veri dayanıklılığı gerektirmeyen kullanım örneklerine yönelik birincil veri deposu olarak kullanabilirsiniz. ElastiCache, Redis ve Memcached ile uyumludur.

![278](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/fe9182fd-1ac5-404b-bc4e-f9e49cf4bad0)

Amazon ElastiCache for Redis'teki Global Datastore, tam olarak yönetilen, hızlı, güvenilir ve güvenli bölgeler arası çoğaltma sağlar. Global Datastore ile, bir bölgede ElastiCache for Redis kümenize yazabilir ve verilerin diğer iki bölgeler arası çoğaltma kümesinden okunabilmesini sağlayarak, bölgeler arasında düşük gecikmeli okumalara ve olağanüstü durum kurtarmaya olanak sağlayabilirsiniz. 

Küresel ayak izine sahip gerçek zamanlı uygulamalar için tasarlanan Redis için Global Datastore, tipik olarak 1 saniyenin altındaki bölgeler arası çoğaltma gecikmesini destekler ve son kullanıcılara daha yakın coğrafi yerel okumalar sağlayarak uygulamalarınızın yanıt verme hızını artırır. Beklenmedik bir bölgesel bozulma durumunda, sağlıklı bölgeler arası çoğaltma kümelerinden biri, tam okuma/yazma yeteneklerine sahip birincil küme haline gelebilir. Bir kez başlatıldığında, promosyon genellikle 1 dakikadan daha kısa sürede tamamlanarak başvurularınızın kullanılabilir durumda kalmasına olanak tanır. Bölgeler arası veri aktarım trafiğini güvence altına almak için Global Datastore, aktarım sırasında şifreleme kullanır.

Mevcut bir kümeyle başlayarak veya birincil olarak kullanılacak yeni bir küme oluşturarak global veri deposu kurabilirsiniz. Global Datastore oluşturmak, ElastiCache için AWS Management Console'da yalnızca birkaç tıklama alır veya en son AWS SDK veya CLI indirilerek otomatikleştirilebilir. Global Datastore, Amazon CloudFormation'da da desteklenir. 

Bu servisi de bir senaryo üzerinden anlamlandırmak gerekirse; bir web mağazamız olduğunu düşünelim, her giren kullanıcıya ana sayfada en çok satın alınan ürünler listelensin. Siteye günde 10 000 ziyaretçi gelse sistem 10 000 defa veri tabanı üzerinden en çok satılan ürünler sorgulanacaktır. Bu durum veri tabanına ağır yük verecektir. 

Bu durumdaki gibi sık kullanılan ve aynı işin tekrarlandığı durumlar sorun teşkil eder, BT dünyası bu duruma çözüm olarak **hafıza içi önbellek** servislerini sunmuştur. 

Web uygulaması ile veri tabanı arasına in-memory cache barındıran bir makine bağlanır ve aynı soru geldiğinde cevabı önbellekten otomatik olarak verir. Böylelikle hem gecikme süresi hem de total veri dönüş süresi kısalacaktır. Böylelikle veri tabanı üzerindeki yük de azalacaktır. 

Bu teknolojinin en çok kullandığı alanlardan biri de oturum (session) bilgilerinin tutulmasıdır. Bu bilgiler önbellekte tutulur. In-memory cache; bu tarz hızlı erişilmesi gereken, geçici ortak kullanıma uygun verilerin tutulması için de oldukça sık kullanılır. 

ElastiCache servisi, en popüler iki in-memory caching servisi olan “Memcached” ve “Redis” desteğine sahiptir. Bu iki yapının özellikleri ise şöyledir:

- Memcached
-- Sadece string veri tutabilir. 
-- Basit ve hızlı in-memory cache ihtiyaçlarını karşılamak için kullanılır. 
-- Multi thread yapısı sayesinde dikey genişlemeye imkân tanımaktadır 
- Redis
-- String dışında list, array gibi veri tiplerini de barındırabilir. 
-- Kompleks in-memory cache ihtiyaçlarını karşılamak için kullanılır. -- Single thread yapısı nedeniyle yatay genişlemeye imkân tanır. 
-- Multi-AZ master-slave cluster yapıları kurabilir.

## 15.1. ElastiCache Servisi Kullanımı
ElastiCache kontrol paneline gidelim ve “Get started” diyerek ön bellekleme servisini oluşturmaya başlayalım. Sonrasında şu adımlar izlenebilir:

- Oluşturduğumuz “ilkVPC” adında iki VPC’ye sahip olduğumuz için “Create Cluster” ile devam edelim. 
-  “Create Cluster” dedikten sonra Memcached olan seçeneği kullanalım. 
- İsim olarak “ilkMemcached” diye devam edelim. 
- Versiyon olarak 1.5.10’u seçelim ve portu varsayılan olan “11211” olarak bırakalım. 
- Paramater group seçeneğini varsayılan değeri ile bırakalım, node type değerini ise “cache.t2.micro” olarak seçelim. 
-  Node sayısını bir (1) olarak bırakalım. 
- Yeni bir alt ağ oluşturuyor, alt ağ adı olarak “my-subnet-memcached” diyelim. VPC olarak da oluşturduğumuz “ilkVPC”yi seçelim. 
- AZ olarak spesifik bir AZ belirtmeyelim. 
- Güvenlik grubu olarak “Ec2-Sec-Group” seçelim; ilerleyen kısımda bu grup için bir inbounded rule ekleyeceğiz. 
- Maintenance window seçeneğini no preference olarak seçelim. 
- Ve oluşturma işlemini tamamlayalım. 
- EC2 kontrol paneli → Security Groups → Ec2-Sec-Group için Inbounded rule ekleyelim. Custom TPC, 11211 portu ve source olarak anywhere seçelim ve tamamlayalım işlemleri.

Bu aşamadan sonra işlemler tamamlanacaktır. VPC başlığı altında oluşturduğumuz public instance’lardan birine bağlanalım. Bağlandıktan sonra yum install telnet komutu ile bağlantı için gerekli olan paketi indirelim. ElastiCache’in end-point noktasını kopyalayalım ve sonrasında. EC2 instance üzerinde ``telnet [ELASTICACHE_ENDPOINT] 11211`` komutunu girelim ve elasticache servisi ile bağlantıyı tamamlayalım. 

Komut olarak ``set a 0 0 7`` komutunu girelim. Sonrasında “merhaba” string değerini girelim. Sonrasında get a komutunu girdiğimizde “merhaba” string değeri karşımıza çıkar. Bu ``a`` gibi tüm veriler RAM üzerinde tutulur ve veri tabanı önünde konumlandırılmıştır.

