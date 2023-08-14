# 19. SNS (Simple Notification Service)
Amazon Simple Notification Service (Amazon SNS), hem uygulamadan uygulamaya (A2A) hem de uygulamadan kişiye (A2P) iletişim için tam olarak yönetilen bir mesajlaşma hizmetidir. 

A2A pub/sub işlevi; dağıtılmış sistemler, mikro hizmetler ve olay tabanlı sunucusuz uygulamalar arasında yüksek aktarım hızlı, gönderme tabanlı, çoktan çoğa mesajlaşmaya yönelik konular (topic) sunar. Yayıncı sistemleriniz, Amazon SNS konularını kullanarak mesajları paralel işleme için Amazon SQS kuyrukları, AWS Lambda işlevleri, HTTPS uç noktaları ve Amazon Kinesis Data Firehose gibi çok sayıda abone sistemine dağıtabilir. A2P işlevi kullanıcılara SMS, mobil anlık bildirimler ve e-posta yoluyla uygun ölçekte mesajlar göndermenizi sağlar. 

SNS servisi iki adet topic türü seçmemize imkân sunar:

- ***Standard Topics:*** Standart konular, uygulamanız birden fazla kez ve düzensiz gelen mesajları işleyebildiği sürece birçok senaryoda kullanılabilir, örneğin: mesajların medya kodlamasına yayılması, dolandırıcılık tespiti, vergi hesaplaması, arama indeksi ve kritik uyarı uygulamaları.
-- Maksimum aktarım hızı (Maximum throughput): Standart konular, saniyede neredeyse sınırsız sayıda mesajı destekler. 
-- En iyi çabayla sıralama (Best-effort ordering): Bazen mesajlar yayınlandıklarından farklı bir sırayla teslim edilebilir.

![283](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b05b0c7d-3891-4454-a90c-b1507ebb48c7)

-- En iyi çaba tekilleştirme (Best-effort deduplication): Bir mesaj en az bir kez teslim edilir, ancak bazen bir mesajın birden fazla kopyası teslim edilebilir. 
-- Birden çok abonelik türü (Multiple subscription types): Mesajlar, uygulamadan uygulama (A2A) uç noktalarına (Amazon SQS, Amazon Kinesis Data Firehose, AWS Lambda, HTTPS) ve uygulamadan kişi (A2P) uç noktalarına (SMS, mobil push, ve e-posta) gönderilebilir. 
-- Mesaj yayılımı (Message fanout): Her hesap 100.000 standart konuyu (topic) destekleyebilir ve her konu 12,5 milyona kadar aboneliği destekler.

- ***FIFO Topics:*** FIFO konuları, operasyonların ve olayların sırasının kritik olduğu veya yinelemelerin tolere edilemediği durumlarda, uygulamalar arasında mesajlaşmayı geliştirmek için tasarlanmıştır. Örneğin: mesajların banka işlem günlüğüne yayılması, stok izleme, uçuş takibi, envanter yönetimi ve fiyat uygulamaları güncellemesi.
-- Yüksek aktarım hızı (High throughput): FIFO konuları, FIFO konusu başına (hangisi önce gelirse) saniyede 300 veya 10 MB'a kadar iletiyi destekler. 
-- Kesin sıralama (Strict ordering): Mesajların yayınlandığı ve teslim edildiği sıra kesinlikle korunur (yani ilk giren ilk çıkar).

![284](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/546ac5f2-09d5-4de3-88d7-36242016da5d)

-- Kesin veri tekilleştirme (Strict deduplication): Yinelenen iletiler teslim edilmez. Veri tekilleştirme, mesajın yayınlanma zamanından itibaren 5 dakikalık bir aralık içinde gerçekleşir. 
-- SQS FIFO abonelikleri (SQS FIFO subscriptions): Mesajlar, Amazon SQS FIFO kuyruklarına teslim edilebilir.
-- Mesaj yayılımı (Message fanout): Her hesap 1.000 FIFO konusunu (topic) destekleyebilir ve her konu 100 adede kadar aboneliği destekler.

Olay güdümlü bilgi işlem, yayıncı hizmetleri tarafından tetiklenen olaylara yanıt olarak abone hizmetlerinin otomatik olarak iş gerçekleştirdiği bir modeldir. Bu paradigma, bu iş akışlarını yerine getirmek için toplu ve bağımsız olarak çalışan hizmetleri ayrıştırırken iş akışlarını otomatikleştirmek için uygulanabilir. Amazon SNS, çok çeşitli AWS olay kaynakları ve olay hedefleriyle yerel entegrasyona sahip, olay odaklı bir merkezdir.

![285](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c551cd7e-d48d-4f9d-b66c-485ea6b422ac)

Kısaca, Amazon SNS servisi, çeşitli hedeflere duyurular gönderilmesini sağlar. SNS, bir push yani itme tabanlı duyuru servisidir. Temelde kullanıcılar SNS servisinden talep etmez, SNS o kullanıcılara duyuruları iletir. 

SNS temelde üç bileşenden oluşur:

- **Publisher:** Duyuruyu gönderen kullanıcı veya gönderilmesi için tetikleyen servis.
- **Topic:** Hedef kitle olarak tanımlanabilir. Duyuruyu alacak grupların oluşturulmasını sağlar. 
- **Subscriber:** Oluşturulan topic’e abone olmuş kişiler veya yönlendirilen servisler.

CloudWatch servisini işlerken belirli şartların sağlanması durumunda alarm oluşturup SNS servisi ile iletmiştik. Bu durumda CloudWatch servisi publisher yani yayıncı konumundadır. Bu tarz durumlar için öncelikle bir topic oluşturulmalıdır. Sonrasında duyuruları almasını istediğimiz kaynakları bu topic’e abone yaparız. Böylelikle durum tetiklenmesinde ileti almalarını sağlarız.

## 19.1. SNS Servisinin Kullanımı
SNS kontrol paneline ulaştığımızda yan menüde dashboard, topics, subscriptions ve mobile alt başlıkları görünür. Topic ve subscription konularının ne olduğuna yukarıda değinmiştik. Mobile alt başlığında ise mobil uygulamalar ile duyuru oluşturma ve yayma, SMS servisi bulunmaktadır.

![286](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/97175407-1c9f-407b-b075-fc99b171fd7b)

Bu kılavuz kapsamında bir topic oluşturalım ve e-posta atmayı deneyelim. Bu işlemler aşağıdaki adımlar uygulanabilir:

- Topics alt başlığına gidelim ve ‘Create Topic’ butonu ile ilk konuyu oluşturmaya başlayalım. 
-  İlk olarak hangi tür bir topic oluşturmak istediğimiz sorulur. Bu kılavuz kapsamında standard türü kullanacağız. 
- Hizmet bir isim ataması bekler. İsim olarak ‘alarmlar2’ diyelim. 
-  Display name özelliği ise kullanıcılara yani abonelere e-posta attığımızda görünecek isimdir. ‘Seminer Alarm’ olarak belirleyebiliriz. 
- Şifreleme (Encryption) seçeneğini disable olarak belirleyelim. Özel veriler olması durumunda bu özelliğin aktif olması önem arz eder. 
- Erişimi türü başlığında ise metot olarak ‘Basic’ seçelim. Advanced seçmemiz durumunda bir JSON policy dosyası oluşturmamız gerekir. Bu aşamada basit bir SNS topic’i oluşturduğumuz için sorun olmayacaktır. 
- Bu topic üzerinden kimler mesaj iletebilir özelliği için “Only the topic owner” diyelim. Böylelikle sadece bu konuyu oluşturan kullanıcı bu topic üzerinden duyuru iletebilir. 
-  Bu konuya kimler abone olabilir kısmında ise “Everyone” diyerek ilerleyelim. Birazdan bir e-postayı abone yaparak e-posta ileteceğiz.
- Delivery retry policy (HTTP/S) başlığı altında bir HTTPS uç noktasına iletmemiz durumunda kaç deneme yapması gerektiğini, denemeler arasında ne kadar süre olmasını istediğimiz gibi değerleri tanımlarız. Bu aşamada bir uç noktaya duyurusu yapmayacağımız için varsayılan olarak bırakalım. 
- Delivery status logging başlığı altında ise duyurunun kullanıcıya iletilip iletilmediğine dair bilgi almak için kullanılır. Sunduğu seçeneklerde e-posta olmadığı için varsayılan ayarı ile bırakalım. Son olarak “Create” diyerek konuyu oluşturalım. 
- Subscriptions alt başlığına gidelim ve “Create subscriptions” diyelim. İlk olarak “topic” seçmemizi isteyecektir. Az önce oluşturulan “alarmlar2” konusunu seçelim. 
- Protocol olarak email ve end-point olarak ise dilediğiniz bir e-posta hesabınızı girebilirsiniz. Oluştur diyelim sonrasında girdiğimiz e-posta adresine gelen onay mailindeki talimatı (onay bağlantısı) uygulayarak konuya abone olalım.
- Topics alt başlığına geri dönelim ve oluşturulan “alamlar2” konusuna tıklayalım. 
- “Publish message” butonu ile ilk duyurumuzu oluşturalım. 
- İlk olarak bir konu belirleyelim. Bu aşamada “Deneme Konu” diyebiliriz. Sonrasında e-posta içeriğini girelim. Bu alana herhangi bir şey yazabilirsiniz.
- En altta ise “Message attributes” başlığı bulunmaktadır. Bu aşamada mail duyuruları için anlamsız gelse de HTTPS uç noktalarına bu attributes özelliği ile gerekli parametreleri geçmek için kullanabiliriz.
- “Publish message” butonu ilk duyurumuzu yayınlayalım. E-posta dakikalar içerisinde hedef e-posta adresine ulaşacaktır.

SNS servisinde kullanıcılar bu ara yüzü kullanarak e-posta atmazlar. Bunun yerine diğer AWS servisleri ile SNS servisinin tetiklenmesini sağlarlar. 

Mobile alt başlığında bulunan push notifications seçeneği mobil uygulamalara bildirim atmanıza imkân tanır. Google, Microsoft ve Apple gibi firmaların kendi push notification servisleri bulunur. Bu servisleri kullanarak AWS üzerinden bildirim atmanıza imkân tanır.
