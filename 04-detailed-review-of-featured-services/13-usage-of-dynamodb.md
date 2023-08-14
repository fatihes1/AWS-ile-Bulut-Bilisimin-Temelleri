# 14. DynomoDB
DynamoDB hizmetinin ne olduğunu daha iyi anlamak için ilişkisel olmayan veri tabanının ne olduğunu anlaşılmalıdır.

## 14.1. İlişkisel Olmayan Veri Tabanları
NoSQL veri tabanları, belirli veri modelleri için özel olarak tasarlanmıştır ve modern uygulamalar oluşturmaya yönelik esnek şemalara sahiptir. NoSQL veri tabanları uygun ölçekte geliştirme kolaylığı, işlevselliği ve performansıyla geniş çaplı olarak kabul görmüştür. 

NoSQL veri tabanlarında, verilere erişmek ve onları yönetmek için çeşitli veri modelleri kullanılır. Bu tür veri tabanları, özellikle büyük veri hacmi, düşük gecikme süresi ve esnek veri modelleri gerektiren uygulamalar için optimize edilmiştir. Bu gereksinimler, diğer veri tabanlarının veri tutarlılığı kısıtlamalarının bir kısmı esnetilerek karşılanır. 

Basit bir kitap veri tabanının şemasını modelleme örneğini ele alalım: 

İlişkisel bir veri tabanında genellikle bir kitap kaydı gizlenerek (veya “normalleştirilerek”) ayrı tablolarda depolanırken, ilişkiler birincil ve yabancı anahtar kısıtlamaları tarafından tanımlanır. Bir örnek üzerinden ele almak istersek; bu örnekte Books (Kitaplar) tablosu ISBN, Book Title (Kitap Başlığı) ve Edition Number (Baskı Sayısı) sütunlarına; Authors (Yazarlar) tablosu AuthorID (Yazar Kimliği) ve Author Name (Yazar Adı) sütunlarına; Author-ISBN (YazarISBN) tablosu ise AuthorID (Yazar Kimliği) ve ISBN sütunlarına sahiptir. İlişkisel model, veri tabanının yedekliliği azaltacak şekilde normalleştirilmiş ve genel olarak depolama için optimize edilmiş tablolar arasında başvurusal bütünlük uygulamasına imkân tanıyacak şekilde tasarlanmıştır. 

Bir NoSQL veri tabanında, kitap kaydı genellikle bir JSON belgesi olarak saklanır. Her kitap için öğe, ISBN, Book Title (Kitap Başlığı), Edition Number (Baskı Sayısı), Author Name (Yazar Adı) ve AuthorID (Yazar Kimliği) bilgileri tek bir belgede öznitelikler olarak depolanır. Bu modelde, veriler sezgisel yazılım geliştirme ve yatay ölçeklenebilirlik için optimize edilir. 

NoSQL veri tabanları, harika kullanıcı deneyimleri sunulması amacıyla esnek, ölçeklenebilir, yüksek performanslı ve yüksek oranda işlevsel veri tabanları gerektiren mobil, web ve oyun gibi birçok modern uygulama için idealdir.

- ***Esneklik:*** NoSQL genellikle daha hızlı ve daha fazla yinelemeli yazılım geliştirmeyi mümkün kılan esnek şemalar sağlar. Esnek veri modeli sayesinde NoSQL veri tabanları yarı yapılandırılmış ve yapılandırılmamış veriler için idealdir.
- ***Ölçeklenebilirlik:*** NoSQL veri tabanları genellikle pahalı ve kalıcı sunucular eklenerek ölçeği artırılabilecek şekilde değil, dağıtılmış donanım kümeleri kullanılarak ölçeği genişletilebilecek şekilde tasarlanır. Bazı bulut sağlayıcıları bu işlemleri arka planda, tam olarak yönetilen bir hizmet olarak gerçekleştirir.
- ***Yüksek performans:*** NoSQL veri tabanları, benzer işlevlerin ilişkisel veri tabanlarıyla gerçekleştirilmesi ile karşılaştırıldığında daha yüksek performansı mümkün kılan belirli veri modelleri ve erişim desenleri için optimize edilmiştir.
- ***Yüksek oranda işlevsel:*** NoSQL veri tabanları, her biri ilgili veri modeli için özel olarak tasarlanmış yüksek oranda işlevsel API'ler ve veri türleri sağlar.

## 14.2. DynamoDB Servisi
AWS, SQL tabanlı hizmetlerdeki gibi birden fazla veri tabanı motoru desteği yerine AWS tarafından oluşturulmuş sıfırdan NoSQL bir veri tabanı hizmetidir. 

RDS’ten farklı olarak, instance boyutu (size) seçmeyi ya da kendi VPC’niz içine koyacağınız bir sunucudan hizmet vermek gibi bir hizmet sunmaz. Altyapısı tamimiyle AWS tarafından yönetilmektedir. Read ve write kapasitesine göre ölçeklendirir. 

Bu servisi de bir senaryo üzerinden ele alalım. Bir mobil uygulamamız olduğunu ve bu mobil uygulamanın veri tabanına günde 5 milyon okuma, 5 milyon yazma işlemi yaptığını düşünelim. Toplam veri tabanı boyutunun 8 GB ve günün her anında trafiğin neredeyse aynı olduğunu varsayarsak aşağıdaki işlemler yapılabilir. Ve her yazma ve okuma işleminin maksimum 1KB olduğunu varsayalım. 

Bir gün 24 saat = 86 400 saniye eder.

- Yazma işlemi için ödenecek tutar:
-- 5 milyon / 86 400 = 57.87 saniyedeki yazma işlemi sayısıdır. 1 yazma kapasitesi ile 1 KB’lık 1 yazma işlemi yapabilir.
-- 58 x 0.47 $ = 27.26 $ / Ay → Aylık yazma işlemi için 27.26 $ ödenir.

- Okuma işlemi için ödenecek tutar:
-- 5 milyon / 86 400 = 57.87 saniyedeki okuma işlemi sayısıdır. 1 okuma kapasitesi ile 1KB’lik 2 okuma işlemi yapılabilmektedir.
-- 29 x 0.09 $ = 2.61 $ / Ay → Aylık okuma işlemi için 2.61 $ ödenir.

Totalde 8 GB boyuta sahipti veri tabanı → 8 x 0.25 $ = 2 $ / Ay ödenir. 

Totalde 27.26 $ + 2.61 $ + 2$ = 31.87 $ dolar ödenir.

DynamoDB’nin en önemli özelliği global-table’dır. Multi region’da okuma/yazma işlemi sağlar. Streams özelliği aktif edilmelidir. Streams ile yapılan her işlemin kaydı tutulur. Tabloya kayıt girince e-posta atılacak uygulamalar gibi tetiklenebilir. Streams, transaction log’a benzer. DynamoDB, accelerator ile in-memory caching sağlar. Hız arttırmaktadır. 35 güne kadar otomatik yedeklemenin yanı sıra manuel yedekleme imkânı da sunmaktadır. Bununla beraber kayıtlara TTL değeri atanabilir. Bu TTL değeri geldiğinde kayıt otomatik olarak silinecektir.

## 14.3. DynamoDB Kullanılması
DynamoDB kontrol paneline gidelim ve sonrasında “Create table” diyelim. Sonrasında aşağıdaki işlemler izlenebilir:

- İsim alanını RDS’te olduğu gibi “calisanlardb” olarak belirleyelim. 
- Partition key alanına “personel_no” ve türünü de “number” seçelim. 
- Default settings seçeneğini değiştirelim ve Customize settings diyelim. 
- Capacity calculator başlığı altında kaç read ve write kapasite değerine sahip olmak istediğimizi belirtiriz. 
- Şifrelemeyi ve diğer seçenekleri varsayılan olarak bırakalım ve devam edelim.

Veri tabanını oluşturduktan sonra bilgileri görüntülerken bir PORT bilgisi veya sunucu bilgisinin olmadığı fark edilir. Sadece ARN (Amazon Resource Name) bulunmaktadır. Yani DynamoDB ile bağlantı kurmanın tek yolu AWS SDK ile direkt olarak bağlanmaktır. 

TTL özelliği için “attr” olarak ‘ttl’ olarak belirtelim böylelikle verilere ‘ttl’ adlı bir key verdiğimizde bu değere ulaşıldığında veri otomatik olarak silinecektir. Global tables özelliği, Multi AZ’nin ve read replicanın bir benzeri olarak düşünülebilir. 

Back-up’tan geri yükleme işlemi yapılırken aynı RDS’te olduğu gibi **yeni bir tablo oluşturulur** ve back-up oradan başlatılır. 

Ekranın solunda DAX adında bir alt başlık bulunur. DynomoDB 10 milisaniye gibi bir sürede yazma/okuma yapabilir. Ama bazı durumlarda bu değer bile yüksektir. Bu durumlarda DAX kullanılır. DAX, DyanmoDB ile uygulama arasına konuşlanır ve bir cacheing cluster olarak düşünülebilir.

