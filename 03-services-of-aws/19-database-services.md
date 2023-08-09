# 20. Veri Tabanı Servisleri
## 20.1. Amazon Aurora
![174](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b0a4a394-d739-4ba3-9be7-b715f8ba017f)

Tam MySQL ve PostgreSQL uyumluluğuyla rakipsiz yüksek performans ve küresel ölçekte erişilebilirlik için tasarlanan AWS servisidir. Ticari veri tabanı maliyetinin onda biriyle tam MySQL ve PostgreSQL uyumluluğunu sürdürürken, yüksek performans gerektiren uygulamaları ve kritik iş yüklerini destekler. %99,99 çalışma süresi SLA'sıyla ve 1 dakikadan az sürede bölgeler arası olağanüstü durum kurtarma özelliği içeren küresel replikasyonla desteklenen Multi-AZ erişilebilirliği ile uygulamalar oluşturmanıza imkân tanır. Sunucusuz gibi yenilikler dahil olmak üzere tam olarak yönetilen bir veri tabanıyla üretkenliği artırıp toplam sahip olma maliyetini düşürerek kullanıcılarınızı memnun eden uygulamalar oluşturmaya odaklanırsınız. Standart araçlar kullanarak Aurora'ya ve Aurora'dan kolayca MySQL veya PostgreSQL veri tabanları geçirebilir ya da Babelfish for Aurora PostgreSQL ile eski SQL Server uygulamalarını minimum kod değişikliğiyle çalıştırırsınız.

## 20.2. Amazon DocumentDB
![175](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/30f65da0-240d-4623-a186-aaed3f3f1335)

Tam olarak yönetilen bir belge veri tabanı hizmeti kullanarak JSON iş yüklerini kolayca ölçeklendiren ve MongoDB ile uyumlu AWS servisidir. İşlem ve depolamayı birbirinden bağımsız olarak ölçeklendirerek saniyede milyonlarca belge okuma isteğini destekler. Donanım tedariki, düzeltme eki uygulama, kurulum ve diğer veri tabanı yönetim görevlerini otomatik hale getirir. Otomatik çoğaltma, sürekli yedekleme ve sıkı ağ yalıtımı ile %99,999999999 oranında dayanıklılık elde edersiniz. Apache 2.0 açık kaynak MongoDB 3.6 ve 4.0 API'leriyle mevcut MongoDB sürücülerini ve araçlarını kullanabilirsiniz.

## 20.3. Amazon DynamoDB
![176](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/5c708e3f-bca0-4496-b370-5615584aa3e4)

Her ölçekte on milisaniyenin altında gecikme süresi performansı için hızlı, esnek NoSQL veri tabanı hizmetidir. On milisaniyenin altında tutarlı gecikme süresi performansı, neredeyse sınırsız aktarım hızı ve depolama, ayrıca otomatikleştirilmiş çok bölgeli replikasyon ile uygulamaları teslim eder. Verilerinizi bekleme sırasında şifreleme, otomatik yedekleme ve geri yükleme, ayrıca %99,999'a varan erişilebilirliğe sahip bir SLA'nın sunduğu güvenilirlik garantisiyle korur. İhtiyaçlarınıza uyması için otomatik olarak yukarı ve aşağı yönlü ölçeklenen, tam olarak yönetilen sunucusuz bir veri tabanıyla inovasyona odaklanabilir ve maliyetleri optimize edersiniz. Verilerinizle daha fazlasını yapabilmek için AWS hizmetleriyle entegre edebilir. Analizler yapmak, öngörüler elde etmek ve trafik eğilimlerini izlemek için yerleşik araçları kullanabilirsiniz.

## 20.4. Amazon ElastiCache
![177](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/a46cc324-8f2c-4994-ba46-5550f2a69044)

Bellek içi önbelleğe alma özelliğiyle mikrosaniye düzeyinde gecikme süresine ulaşan ve ölçeklendiren AWS servisidir. Uygulama performansını artırarak gecikme süresini mikro saniye düzeyine indirir. İnternet ölçeğindeki en zorlu uygulamalarınızın gereksinimlerini karşılamak için yalnızca birkaç tıklamayla ölçeklendirilebilir. Kendi kendine yönetilen önbelleğe alma süreçlerinin getirdiği maliyetleri azaltır ve operasyonel iş yükünü ortadan kaldırır. İki popüler açık kaynaklı önbelleğe alma teknolojisi olan Redis veya Memcached arasında seçim yaparak oluşturabilirsiniz.

## 20.5. Amazon Keyspaces (for Apache Cassandra)
![178](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0abfbad1-be85-45fd-ae25-24e7b40a321b)

Ölçeklenebilir, yüksek oranda erişilebilir ve yönetilen bir Apache Cassandra uyumlu veri tabanı hizmetidir.

 Amazon Keyspaces (for Apache Cassandra); ölçeklenebilir, yüksek oranda erişilebilir ve yönetilen bir Apache Cassandra uyumlu veri tabanı hizmetidir. Amazon Keyspaces ile Cassandra iş yüklerinizi, bugün kullandığınız Cassandra uygulama kodu ve geliştirici araçlarını kullanarak AWS üzerinde çalıştırabilirsiniz. Herhangi bir sunucu tedarik etmenize, sunucuya düzeltme eki uygulamanıza veya sunucuyu yönetmenize ya da herhangi bir yazılım yüklemenize, bakım yapmanıza veya işletmenize gerek yoktur. Amazon Keyspaces, sunucusuz bir hizmettir. Bu nedenle, yalnızca kullandığınız kaynaklar için ödeme yaparsınız ve hizmet, uygulama trafiğine bağlı olarak tabloların ölçeklerini otomatik bir şekilde artırıp azaltabilir. Neredeyse sınırsız bir aktarım hızı ve depolama ile saniye başına binlerce istek sunan uygulamalar oluşturabilirsiniz. Veriler varsayılan olarak şifrelenir ve Amazon Keyspaces belirli bir noktaya kurtarma kullanarak sürekli olarak tablo verilerinizi yedeklemenizi sağlar. Amazon Keyspaces, iş açısından kritik Cassandra iş yüklerini uygun ölçekte çalıştırmanız için ihtiyacınız olan performansı, esnekliği ve kurumsal özellikleri sunar.

## 20.6. Amazon MemoryDB for Redis
![179](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/05ba4900-423e-4b6b-9127-edf5d5bb05c0)

Ultra hızlı performans için Redis uyumlu, dayanıklı, bellek içi veri tabanı hizmetidir. Arka arkaya beş yıl boyunca Stack Overflow'un en sevilen veri tabanı olan Redis ile uygulamaları hızla oluşturabilirsiniz. Ultra hızlı performansla verilere erişebilir, günde 13 trilyondan fazla ve saniyede 160 milyondan fazla istek işleyebilir. Hızlı veri tabanı kurtarma ve yeniden başlatma için Multi-AZ işlem günlüğü kullanan bellek içi depolama ile verileri dayanıklı bir şekilde depolar. Uygulamanızın gereksinimlerini karşılamak için küme başına birkaç gigabayttan yüz terabayttan fazla depolama alanına sorunsuz bir şekilde ölçeklendirebilir.

## 20.7. Amazon Neptune
![180](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/63e3bcff-c087-4929-b21d-c0af5b6eff12)

Grafik uygulamalarını yüksek oranda bağlı veri kümeleriyle oluşturabilen ve çalıştırabilen AWS servisidir. Kimlik, bilgi, dolandırıcılık grafiği ve diğer uygulamaları yüksek performansla oluşturup çalıştırır ve saniyede 100.000'den fazla sorgu yürütebilir. Gremlin, openCypher ve SPARQL gibi popüler açık kaynak kodlu API'leri kullanarak yüksek performanslı grafik uygulamaları dağıtır ve mevcut uygulamaları kolayca geçirebilir. Grafik veri tabanlarını donanım tedarik etme, yazılım düzeltme eki uygulama, kurulum, yapılandırma veya yedekleme kaygısı olmadan çalıştırabilir ve peşin lisanslama ücretleri ödemekten kurtulursunuz.

## 20.8. Amazon RDS
![181](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/4de5b211-2534-4bb9-b2c6-54dc4c3dcfc8)

Yalnızca birkaç tıklamayla bulutta bir ilişkisel veri tabanını kurun, çalıştıran ve ölçeklendiren AWS servisidir. Altyapı tedarik etmeye veya yazılım bakımına ihtiyaç olmadan verimsiz ve zaman alıcı veri tabanı yönetim görevlerini ortadan kaldırır. Seçtiğiniz ilişkisel veri tabanı altyapılarını bulutta veya şirket içinde dağıtır ve ölçeklendirir. Amazon RDS Multi-AZ dağıtımları ile yüksek düzeyde erişilebilirlik elde edebilirsiniz. Performansı kanıtlanmış on yıldan fazla operasyonel uzmanlığın, en iyi güvenlik uygulamalarının ve inovasyonun avantajlarından faydalanırsınız.

## 20.9. Amazon Redshift
Uygun ölçekte hızlı, kolay ve güvenli bulut veri ambarı sayesinde öngörü elde etme sürenizi kısaltan AWS servisidir. Herkes için kolay analizlerle verilerden saniyeler içinde öngörüler elde etmeye odaklanmanızı sağlar. Veri ambarı altyapınızı yönetme konusunu düşünmek zorunda kalmazsınız. Operasyonel veri tabanları, data-lake'ler, veri ambarları ve üçüncü taraf veri kümelerindeki tüm verilerinizi analiz eder. Sorgu hızını iyileştiren otomasyon sayesinde uygun ölçekte diğer bulut veri ambarlarından 3 kata kadar daha iyi fiyat performansı elde etmenizi sağlar.

## 20.10. Amazon Timestream
![182](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/6660be5b-db91-4578-bd95-3460027fb191)

Amazon Timestream, IoT uygulamaları ve operasyonel uygulamalar için, ilişkisel veri tabanlarının maliyetinin 1/10'u kadar düşük bir maliyetle ve günde trilyonlarca olayın 1.000 kata kadar daha hızlı depolanmasını ve analizini kolaylaştıran hızlı, ölçeklenebilir ve sunucusuz bir zaman serisi veri tabanı hizmetidir. Amazon Timestream, yakın tarihli verileri bellekte tutarak ve geçmiş verileri kullanıcı tanımlı politikalar temelinde maliyet açısından optimize edilmiş bir depolama katmanına taşıyarak zaman serisi verilerinin yaşam döngüsünü yönetmede size zaman ve maliyet tasarrufu sağlar. 

Amazon Timestream'in amaca yönelik sorgu motoru, sorguda verilerin bellekte mi yoksa maliyet açısından optimize edilmiş katmanda mı bulunduğunu açıkça belirtmenize gerek kalmadan yakın tarihli ve geçmiş verilere birlikte erişmenize ve bunları analiz etmenize olanak tanır. Amazon Timestream, verilerinizdeki eğilimleri ve kalıpları neredeyse gerçek zamanlı olarak belirlemenize yardımcı olan yerleşik zaman serisi analiz fonksiyonlarına sahiptir. Amazon Timestream sunucusuzdur ve kapasite ile performansı ayarlamak için ölçeği otomatik olarak artar veya azalır. Böylece temeldeki altyapıyı yönetmenize gerek kalmaz ve uygulamalarınızı oluşturmaya odaklanabilirsiniz.
