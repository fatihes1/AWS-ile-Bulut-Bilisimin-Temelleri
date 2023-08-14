# 23. Amazon Kinesis
Amazon Kinesis gerçek zamanlı akış verilerini toplamayı, işlemeyi ve analiz etmeyi kolaylaştırdığından, zamanında öngörüler elde edebilir ve yeni bilgilere hızlı tepki verebilirsiniz. Amazon Kinesis her ölçekteki akış verilerini uygun maliyetle işlemeye yönelik önemli özellikler sunduğu gibi, uygulamanızın gereksinimlerine en uygun araçları seçme esnekliği de getirir. Amazon Kinesis ile makine öğrenimi, analiz ve diğer uygulamalar için video, ses, uygulama günlükleri, web sitesi tıklama akışları ve IoT telemetri verileri gibi gerçek zamanlı veriler alabilirsiniz. Amazon Kinesis gelen verileri hemen işlemenize, analiz etmenize ve bu verilere anında yanıt vermenize olanak tanır. İşleme sürecinin başlaması için tüm verilerinizin toplanmasını beklemek zorunda kalmazsınız.

Kinesis servisini bir senaryo üzerinden ele almak istersek şu senaryoya bakabiliriz; bir banka sistemimiz var ve müşterilerin yaptığı her işlem sonucu ortada bir dolandırıcılık var mı diye kontrol ediyoruz. Dolandırıcılık var ise kartı bloke etmemiz ve müşteriye bilgi verilmesi gerekiyor. Yani bir “fraud detection” işlemi yapıyoruz.

Fraud detection her alışverişle ilgili kart bilgisi, lokasyon gibi değerleri tutar. Diyelim ki bu bilgileri bir veri tabanına kaydediyor. Algoritma belli aralıklarla analiz yapıp dolandırıcılık olup olmadığına karar veriyor. Bu senaryoda veri toplaması, düzenlenmesi ve kaydedilmesi bu sürece ekstra külfet ekliyor. Diğer bir sorun ise gerçek zamanlı bir analizin yapılamıyor olmasıdır. Belirli aralıklarla yapılan kontrolün sonucu, tespit için sistem geç kalmış olabilir.

AWS Kinesis veri üreticisi ile veri tüketici arasında mesajları yayınlamak için kanal görevi gören, gerçek zamanlı veri toplama-dağıtma servisidir. SQS kuyruklarına benzerdir ve 3 temel bileşene sahiptir.

- EC2 Instances, Client, Server gibi **veri üreten sistemler,** 
- SQS kuyruğuna benzer yapıda olan ve Shard adı verilen kayıtlardan oluşan **Kinesis kuyruğu**,
- Ve **verileri okuyan** EC2 Instances gibi cihazlar. Sonrası bu okunan veriler S3, DynomoDB, RedShift gibi diğer servislere aktarılabilir.

Amazon Kinesis altında Video Streams, Data Streams, Data Firehouse ve Data Analytics olmak üzere dört ayrı özellik barındırır.

## 23.1. Kinesis Video Streams
Amazon Kinesis Video Streams, bağlantılı cihazlardan AWS'ye analiz, makine öğrenimi (ML), kayıttan yürütme ve diğer işlemler için video akışını kolaylaştırır. Kinesis Video Streams, milyonlarca cihazdan akışa alınan video verilerini almak için gereken tüm altyapıyı otomatik olarak sağlar ve esnek şekilde ölçekler. Akışlarınızdaki video verilerini dayanıklı şekilde depolar, şifreler ve dizinler, kullanımı kolay API’ler aracılığıyla verilerinize erişmenize olanak sağlar. Kinesis Video Streams, canlı ve istek üzerine görüntüleme için videoları kayıttan yürütmenin yanı sıra Amazon Rekognition Video ile entegrasyon ve Apache MxNet, TensorFlow ve OpenCV gibi makine öğrenimi çerçeveleri için kitaplıklar aracılığıyla görüntü işleme ve video analizinden yararlanan uygulamaları hızlı bir şekilde oluşturmanızı mümkün kılar. Kinesis Video Streams, basit API’ler aracılığıyla web tarayıcıları, mobil uygulamalar ve bağlantılı cihazlar arasında gerçek zamanlı medya akışını ve etkileşimleri mümkün kılan açık kaynaklı WebRTC projesini de destekler. Görüntülü sohbet ve eşler arası medya akışı, yaygın kullanım alanlarından bazılarıdır. 

Kullanmaya başlamak için AWS Management Console'dan birkaç tıklamayla bir Kinesis video akışı oluşturun. Daha sonra cihazlarınızda Kinesis Video Streams SDK’sını yükleyebilir ve kayıttan yürütme, depolama ve analiz için AWS’ye medya akışını başlatabilirsiniz. Kinesis Video Streams ile yalnızca kullandığınız kadar ödersiniz. Peşin taahhüt ya da minimum ücret yoktur. 

Kısaca; video ve ses akışlarını AWS bulutuna aktarılarak daha sonra makine öğrenmesi uygulamaları gibi uygulamalar tarafından işlenmesine imkân tanır.

## 23.2. Kinesis Data Streams
Amazon Kinesis Data Streams, büyük ölçüde ölçeklenebilir, dayanıklı ve düşük maliyetli bir veri akışı hizmetidir. Kinesis Veri Akışları, web sitesi tıklama akışları, veri tabanı olay akışları, finansal işlemler, sosyal medya akışları, BT günlükleri ve konum izleme olayları gibi yüz binlerce kaynaktan saniyede gigabaytlarca veriyi sürekli olarak yakalayabilir. Toplanan veriler, gerçek zamanlı gösterge tabloları, gerçek zamanlı anormallik algılama, dinamik fiyatlandırma gibi gerçek zamanlı analitik kullanım durumlarına izin vermek için milisaniyeler içinde sunulur. 

Amazon Kinesis Data Streams'te yönetmeniz gereken bir sunucu yoktur. İstek üzerine modu, çalışan uygulamalar için gereken kapasiteyi tedarik etme veya yönetme ihtiyacını ortadan kaldırır. Kapasitenizi Kinesis Data Streams ile saniyede gigabaytlarca veri akışı sağlayacak şekilde ayarlayın. İstek üzerine moduyla otomatik tedarik ve ölçeklendirmeye erişin. 

Kinesis Data Streams'te saatlik 0,015 USD'den başlayan fiyatlarla yalnızca kullandığınız kadar ödeme yapın. İstek üzerine modu sayesinde, fazla tedarik etme konusunda endişelenmenize gerek yoktur. AWS'de hızla analiz, sunucusuz ve uygulama entegrasyonu çözümleri oluşturmak için diğer AWS hizmetleriyle yerleşik entegrasyonları kullanın. 

Kısaca; bir anahtar (key) kullanarak, kayıtların yönlendirilmesi sıralanması, **birden fazla istemcinin** gelen iletileri aynı anda okumasını ve 7 güne kadar geçmiş mesajların tekrarlanmasını sağlar. Birden fazla istemcinin okumasındaki en önemli sebep ise bir istemci fraud detection yaparken diğer bir istemci demografik ayrım yapan grafikler oluşturabilir. 

SQS’in asıl amacı ise birden fazla servis arasında mesaj alışverişine tampon olmaktı. Bir mesaj gelir, saklanır, tek bir tüketici okuyabilir ve sonrasında silinir.

## 23.3. Kinesis Data Firehouse
Amazon Kinesis Data Firehose, akış verilerini veri depolarına ve analiz araçlarına yüklemenin en kolay yoludur. Kinesis Data Firehose, yüz binlerce kaynaktan gelen büyük hacimli akış verilerini yakalamayı, dönüştürmeyi ve Amazon S3, Amazon Redshift, Amazon OpenSearch Service, Kinesis Data Analytics, genel HTTP uç noktaları ve bunlara yüklemeyi kolaylaştıran tam olarak yönetilen bir hizmettir. Datadog, New Relic, MongoDB ve Splunk gibi servis sağlayıcılar, neredeyse gerçek zamanlı analitik ve içgörü sağlar. 

Akış verilerini kolayca yakalamanızı, dönüştürmenizi ve yüklemenizi sağlar. Bir teslim akışı oluşturur, hedefinizi seçer ve yalnızca birkaç tıklamayla gerçek zamanlı veri akışını başlatabilirsiniz. İşlem, bellek ve ağ kaynaklarını sürekli yönetim olmadan otomatik olarak tedarik edilir ve ölçeklendirilir. 

Ham akış verilerini Apache Parquet gibi formatlara dönüştürebilir ve kendi işleme hatlarınızı oluşturmadan akış verilerini dinamik olarak bölümlere ayırabilirsiniz. Amazon Simple Storage Service (S3) ve Amazon Redshift gibi 30’dan fazla tam olarak entegre edilmiş AWS hizmeti ve akış hedefiyle bağlantı kurmanıza imkân tanır. 

Kısaca; Akışlı verileri düzenleyip S3 ya da RedShift gibi hedeflere kaydeder ve otomatik olarak gereksinimlere göre genişleyebilir.

## 23.4. Kinesis Data Analytics
Apache Flink uygulamalarınızı sürekli çalıştırır ve hiçbir kurulum maliyeti ve sunucu yönetme ihtiyacı olmadan otomatik olarak ölçeklendirir. Amazon Kinesis Data Streams ve Amazon MSK gibi veri kaynaklarından saniyenin altında gecikme süreleriyle veri işleyebilir ve olaylara gerçek zamanlı olarak müdahale edebilirsiniz. 

Yönetilen Apache Zeppelin not defterlerini Kinesis Data Analytics Studio ile kullanarak akış verilerini etkileşimli bir şekilde analiz etmenize imkân tanır. SQL, Java, Python veya Scala'da uygulamalar geliştirebilir. Zaman aralıklarında birleştirme, filtreleme, toplama ve diğer işlemleri gerçekleştirebilirsiniz. 

Kısaca; Firehouse ve Streams servislerin bir araya getirilmiş hali olarak düşünülebilir. Akışlı veriler üstünde standart SQL sorguları çalıştırma imkânı verir
