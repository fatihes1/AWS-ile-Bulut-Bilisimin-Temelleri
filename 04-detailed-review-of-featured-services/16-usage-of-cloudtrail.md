# 17. CloudTrail
AWS CloudTrail, denetim, güvenlik izleme ve operasyonel sorun giderme sağlar. CloudTrail, AWS hizmetlerinde kullanıcı etkinliğini ve API çağrılarını olay olarak kaydeder. CloudTrail etkinlikleri, "kim, neyi, nerede ve ne zaman yaptı?" sorularını yanıtlamanıza yardımcı olur.

CloudTrail iki tür olayı kaydeder: 
- Amazon Simple Storage Service (Amazon S3) paketleri oluşturma veya silme gibi kaynaklar üzerinde kontrol düzlemi eylemlerini yakalayan yönetim olayları.
- Amazon S3 nesnesini okuma veya yazma gibi bir kaynak içindeki veri düzlemi eylemlerini yakalayan veri olayları. 

CloudTrail bu olayları üç özellikte kullanır:

- Olay geçmişi, hiçbir ek ücret ödemeden 90 günlük kontrol düzlemi eylemleri geçmişi sağlar. Temel denetim yeteneklerinin bir parçası olarak CloudTrail, değişmezliği etkinleştirmek için şifreleme ve günlük dosyası doğrulaması için müşteri tarafından yönetilen anahtarlar sağlar. Yalnızca ücretli özellikleri kullandığınız kadar ödersiniz. Aşağıdaki özelliklerden bazıları ücretsiz olarak sağlanmaktadır. Asgari ücret veya ön taahhüt gerekmez. 
- CloudTrail Lake, denetim ve güvenlik amacıyla AWS'de kullanıcı ve API etkinliğini yakalamak, depolamak, erişmek ve analiz etmek için yönetilen bir veri gölüdür. Etkinlik günlüklerinizi (kontrol düzlemi ve veri düzlemi) yedi yıla kadar toplayabilir, değişmez bir şekilde saklayabilir ve arama ve analiz için günlükleri saniyeler içinde sorgulayabilirsiniz. BT denetçileri, denetim gereksinimlerini karşılamak için CloudTrail Lake'i tüm etkinliklerin değişmez bir kaydı olarak kullanabilir. Güvenlik yöneticileri, kullanıcı etkinliğinin dahili ilkelere uygun olmasını sağlayabilir ve DevOps mühendisleri, yanıt vermeyen bir Amazon Elastic Compute Cloud (EC2) örneği veya erişimin reddedilen bir kaynak gibi operasyonel sorunları giderebilir. 
- İzler, Amazon CloudWatch Logs ve Amazon EventBridge'e isteğe bağlı teslimat ile bu olayları Amazon S3'te teslim edip depolayarak AWS hesap etkinliklerinin kaydını yakalar. Bu olaylar, güvenlik izleme çözümlerinize eklenebilir. CloudTrail tarafından yakalanan günlükleri aramak ve analiz etmek için kendi üçüncü taraf çözümlerinizi veya Amazon Athena gibi çözümlerinizi kullanabilirsiniz. AWS Organizations'ı kullanarak tek bir AWS hesabı veya birden çok AWS hesabı için yollar oluşturabilirsiniz. AWS CloudTrail Insights, API çağrı hacimlerindeki anormal davranışlar için kontrol düzlemi olaylarını analiz eder ve kaynak sağlamadaki ani artışlar veya periyodik aktivitedeki boşluklar gibi olağandışı etkinlikleri tespit edebilir.

CloudTrail ile CloudWatch servisinin karıştırılmamasına dikkat edilmelidir. **CloudTrail** servisi AWS hesabınızın **yönetim, uyumluluk ve operasyonel risk denetimini** sağlarken **CloudWatch** AWS hesabınızdaki kaynakların **performans ve hatalarını izlemeyi** sağlayan monitoring servisidir.

## 17.1. CloudTrail Servisinin Kullanımı
![281](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f3c9a8eb-061b-4c09-80e0-128d9bcea749)

CloudTrail kontrol paneline ulaştığımızda Şekil: 60’takı gibi bir ekran bizi karşılar. Dashboard alt başlığı altında son 90 günlük ana olayların kaydı bulunur. Benzer şekilde Event History alt başlığında da 90 günlük kayıtların tamamı bulunur. Dashboard buradan ana kayıtları çeker ve kendi üzerinde gösterir. 

Trails başlığı altında ise trail oluşturulur. Bazı durumlarda kayıtların 90 günden fazla tutulması gerekmektedir. Bu kayıtların toplanıp S3 bucket’larında saklanmasını trail hizmeti sağlar. 90 günden fazla kayıt tutulmadaki temel sebepler ise firma politikaları veya güvenlik amaçlı olabilmektedir. 

“Create a trail” diyerek ilk trail’i oluşturmaya başlayabiliriz. Sonrasında aşağıdaki adımlar izlenebilir:

- İlk olarak bu hizmet için bir isim beklemektedir. “ilkTrail” olarak atama yapalım.
- Sonrasında depolama konumu isteyecektir. Yeni bir S3 bucket oluştur seçeneğini kullanalım.
- “Customer managed AWS KMS key” alanında “New” diyelim ve girdi alanına “cloudWatckKey” girelim. 
- Events başlığı altında hangi tip kayıtların tutulmasını istediği soruları. Data-event ve Insights event isteğe göre tutulabilir. Bu aşamada sadece “Managment events” seçeneği ile devam edelim. 
- “API activity” olarak hem Read (Okuma) hem de Write (Yazma) işlemlerinin kayıtlarını tutmak istediğimizi belirtelim. ‒ En son aşamada “Create” ile oluşturalım. 
- S3 servisine gittiğimizde logların tutulması için bir bucket oluşturulduğu görünür. Bölge, yıl, ay ve günlere göre klasör edilmiştir. Kayıtlara ulaştığımızda JSON formatında kayıt dosyalarımızın oluştuğu görülecektir.

Bu adımlar sayesinde 90 günü aşan kayıtlar tutulabilir.
