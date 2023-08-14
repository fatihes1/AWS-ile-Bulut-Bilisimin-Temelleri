# 20. SQS (Simle Queue Service)
Amazon Simple Queue Service (SQS), dağıtılmış sistemleri ve sunucusuz uygulamaları birbirinden ayırmanıza ve ölçeklendirmenize imkân tanıyan, tam olarak yönetilen bir iletileri kuyruğa alma hizmetidir. SQS, mesajlaşmaya yönelik ara yazılımları yönetmenin ve işletmenin getirdiği karmaşıklık ile ek iş yükünü ortadan kaldırarak geliştiricilerin farklı işlere odaklanmasına imkân tanır. SQS ile ileti kaybı yaşamadan veya diğer hizmetlerin erişilebilir olmasına gereksinim duymadan yazılım bileşenleri arasında dilediğiniz hacimde ileti gönderebilir, depolayabilir ve alabilirsiniz. AWS Management Console, Command Line Interface veya tercih ettiğiniz SDK'yi ve üç basit komutu kullanarak SQS'yi dakikalar içinde kullanmaya başlayabilirsiniz.

SQS iki tür ileti kuyruğu sunar. **Standart kuyruklar** tarafından en yüksek aktarım hızı, en iyi çaba ilkesine göre sıralama ve en az bir kez teslim olanakları sunulur. SQS **FIFO kuyrukları,** iletilerin tam olarak bir kez ve tam olarak gönderildikleri sırada işlenmesi konusunda güvence sağlayacak şekilde tasarlanmıştır. 

Bu servis kapsamında SNS servisinde olduğu gibi standart ve FIFO olmak üzere iki kuyruk türü sunulmaktadır. 

Bu servisi bir senaryo üzerinden incelemek gerekirse, bir otel için online rezervasyon servisimiz olduğunu varsayalım. Bu konuya kadar gördüğümüz üzere front-end, back-end ve veri tabanı için sunucular barındırıyoruz. Kullanıcı client üzerinden rezervasyon seçimini yapıyor sonrasında bu seçimler back-end servisi üzerinde işlenerek veri tabanına yazılıyor ve kullanıcıya gerekli dönüt yapılıyor. 

Otel olarak bir kampanya yaptığımızı varsayalım. Sistem yoğun trafik altında kalacaktır ve bir süre sonra servis hizmet reddi verecektir. Kullanıcılar sistemin web sayfasına dahi giremeyecektir. Sistemin tasarımı Şekil: 66’daki gibi düşünülebilir.

![287](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b5915989-3548-436c-b070-c164114fba9a)

Bu sistemde kullanıcıların hata alması yerine başka bir çözüm bulunması gerekmektedir. Fronend web sunucularını ile back-end web sunucuları arasında bulunan Elactic Load Balancing servisini kaldırıp buraya boş bir kova koyduğumuzu düşünelim. Tüm istekler bu kovaya düşer ve back-end sunucu ve veri tabanı uygun oldukça kovadan gelen istekler çekilir. Böylelikle sisteme erişen kullanıcılara direkt hata vermek yerine “İşleminiz yapılıyor…” gibi bir ekran ile çok kısa bir süre bekleterek işlemi gerçekleştirebiliriz. 

AWS de bu kova işlemini SQS servisi yapmaktadır. Standart kuyrukta sıra garantisi yoktur ancak limitsizdir. FIFO kuyruğu içe sıraya önem verir ancak limit barındırır.

## 20.1. SQS Servisinin Kullanımı
![288](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/66604505-3675-4f35-a4e2-8ae2fd6fc8ca)

SQS kontrol paneline ulaşalım ve ilk kuyruğu oluşturmaya başlayalım. Bu işlem için aşağıdaki adımları takip edebiliriz:

- Create Queue diyerek ilk kuyruğumuzu oluşturmaya başlayalım. 
- Kuyruk türü olarak standard kuyruk seçeneğini kullanalım. 
- İsim olarak “ilkSQS” diyebiliriz.
- Konfigürasyon ayarlarında “Visibility timeout consumer” yani mesajı çekecek hizmet iletiyi çektiğinde bu iletici kuyrukta ne kadar kalsın ayarlamasıdır. Varsayılan olarak bırakalım. 
- “Message retention period” ise mesaj kaç güne kadar kuyrukta bekleyebilsin ayarlamasıdır.
- “Maximum message size” mesajın maksimum büyüklüğünü belirlediğimiz alandır. 
- “Delivery delay” seçeneğinde ise ileti kuyruğa alındığında ne kadar süre erişilmesine izin verilmemesi gerektiğini belirttiğimiz değerdir. 
- “Receive message wait time” bir istek kuyrukta ne kadar süre bekleyeceğini tanımlar. Yani ileti çekici kaç saniye aralıklarla bir ileti çekmelidir. 
- “Dead-letter queue” alt başlığında işlenemeyen bir iletinin belirli bir deneme sayısından sonra incelenmek üzere başka kuyruğa alınmasıdır. 
- Diğer ayarları varsayılan olarak bırakalım ve “Create queue” diyelim.
- SQS servisi normalde AWS SDK ile programın içine kod olarak eklenir. Ama simüle etmek için oluşturulan “ilkSQS” kuyruğu seçili iken; “send and receive messages” denilebilir. Sonra yine aynı butona tıklandığında en aşağıda “pull” diyerek az önce yayınlanan mesaj görüntülenebilir.
