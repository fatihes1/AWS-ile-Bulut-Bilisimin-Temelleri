# 16. CloudWatch
CloudWatch, AWS dünyasının monitoring yani izleme servisidir. Bu konunun anlaşılması için monitoring teriminin ne olduğu anlaşılmalıdır.

## 16.1. Monitoring (İzleme) Nedir?
Modern işletmeye güç veren BT altyapısı, bir dizi karmaşık mimari form faktörü alabilir: sanallaştırılmış, yazılım tanımlı, hibrit ve çoklu bulut, şirket içi ve tesis dışı veri merkezi dağıtımları. BT kesintilerinin veya performans düşüşlerinin her saniyesi işletmelere milyonlarca dolarlık gelir fırsatlarına mal olabileceğinden, altyapının ne kadar iyi performans gösterdiğine dikkat etmek önemlidir. 

Bu, BT izlemeyi değerli bir uygulama haline getirir ve daha derin bir incelemeye değer. Bu makalede, ağ performansının hem iş hem de teknik yönlerini kapsayan geniş BT izleme kavramını keşfedeceğiz. 

BT izlemenin amacı, BT altyapınızın ve temeldeki bileşenlerin gerçek zamanlı olarak ne kadar iyi performans gösterdiğini belirlemektir. BT izleme, kaynak sağlama, BT güvenliği veya kullanım eğilimlerini değerlendirmek için iyi bilgilendirilmiş kararlar almak için kullanıcıların BT sorunlarını gerçek zamanlı olarak tanımlamasına olanak tanır.

BT izleme teknolojilerinin genellikle üç ana bileşeni vardır: 
-  Ağ düğümlerinden ham veri üreten sensörler 
- Bu verileri bilgiye dönüştüren analitik çözümler 
- Sezgisel ve anlayışlı raporları görselleştiren UI arayüzleri

## 16.2. CloudWatch Servisi
Amazon CloudWatch; AWS, hibrit ve şirket içi uygulamalarla altyapı kaynakları için veri ve eyleme dönüştürülebilir öngörüler sağlayan bir izleme ve yönetim hizmetidir. Tüm performans ve operasyon verilerinizi depolarda (sunucu, ağ veya veri tabanı) izlemek yerine günlük ve ölçüm biçiminde tek bir platformda toplayabilir ve bu verilere erişim sağlayabilirsiniz. CloudWatch yığınınızın (uygulamalar, altyapı ve hizmetler) tamamını izlemenizi ve otomatikleştirilmiş eylemler gerçekleştirip ortalama çözüm süresini (MTTR) kısaltmak için alarmları, günlükleri ve olay verilerini kullanmanızı sağlar. Bu sayede önemli kaynaklarınızı boşa çıkarabilir, uygulama geliştirme ve işletme değerini artırma alanlarına odaklanabilirsiniz. 

CloudWatch, uygulama performansını optimize etmenize, kaynak kullanımını yönetmenize ve sistem çapındaki operasyonel durumu anlamanıza yardımcı olan eyleme dönüştürülebilir öngörüler sunar. CloudWatch en fazla bir saniyelik ölçüm ve günlük verisi görünürlüğü, 15 ay veri saklama (ölçümler) ve ölçümleri temel alan hesaplamalar yapmanızı sağlar. Bu da maliyet optimizasyonu için geçmişe dönük analiz gerçekleştirmenin yanı sıra uygulamaları ve altyapı kaynaklarını optimize etmek amacıyla gerçek zamanlı öngörüler elde etmenizi mümkün kılar. Container'lı uygulamalarınızı ve mikro hizmetlerinizi izlemek, bunların sorunlarını gidermek ve bunlar hakkında uyarılar almak için CloudWatch Container Insights'ı kullanabilirsiniz. CloudWatch, DevOps mühendislerinin sorunları yalıtıp hızla çözmesine yardımcı olmak için CPU, bellek, disk ve ağ verileri gibi işlem kullanımı bilgilerinin yanı sıra container yeniden başlatma hataları gibi tanılama bilgilerini toplar ve özetler. Container Insights; Amazon ECS for Kubernetes (EKS), Amazon Elastic Container Service (ECS), AWS Fargate ve bağımsız Kubernetes (k8s) gibi container yönetim hizmetlerinden öngörüler sunar. 

Bulut üzerinde bir sistemin veya altyapının çalıştığını varsayalım. Bu sistemde bir sorun oluştuğunda tek tek tüm sunuculara bağlanıp tüm bileşenleri kontrol etmek zahmetli olacaktır. Büyük ve karmaşık yapılar için ise bu yöntem imkansızlaşır. 

Monitoring ile sistemlerde bulunan bileşenleri çeşitli ve önceden belirlenen özelliklerini izleyerek bu konuda rapor sunabiliriz. CloudWatch servisi CPU kullanımı, ağ bağlantı raporu gibi altyapı izlemede oldukça başarılıdır. Bununla beraber kısıtlı olarak da olsa uygulama izleme imkânı sunar. 

CloudWatch servisinin asıl gücü ise metriklerin ayarlanan varsayılan değerlerin dışına çıktığı anda SNS servisini kullanarak alarm verebiliyor olmasıdır. Bu alarmlar ile başka olaylar tetikleyebilirsiniz. Böylelikle sorun çözümü otomatize edilebilir.

## 16.3. CloudWatch Servisinin Kullanılması
CloudWatch servisini kullanmaya geçmeden önce bu kılavuz kapsamında birkaç ayarlama yapmalıyız. IAM kontrol paneline ulaşalım, burada sol menüde bulunan AMIs alt başlığına geçelim. Daha önceden oluşturduğumuz “baseAMI”’ı düzenleyelim ve “Monitoring Cloudwatch” seçeneğini kullanılabilir hale getirelim. Sonrasında bu AMI’ı kullanarak bir adet EC2 instance oluşturalım. İsim değerini “cloudWatchizleme” yapabiliriz.

EC2 instance oluşturduktan sonra CloudWatch kontrol paneline ulaşalım. Şimdi servisi tanımaya, özelliklerini kullanmaya başlayabiliriz.

![279](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/079a32f3-10a2-4b1a-9e10-57b60fd0e011)

Sol menüde bulunan alt başlıkları birer birer inceleyebiliriz.

### 16.3.1. Dashboard
Kendimize izleme için panolar oluşturabileceğimiz alt başlıktır. İzlemek istediğimiz tüm servisleri ve metrikleri belirleyerek bu alan üzerinden izleyebiliriz. İlk panomuzu oluşturalım.

- AWS ilk aşamada bir isim vermemizi istiyor. Bu adımda “ilkDashboard” ismini kullanalım ve sonrasında “Create dashboard” seçeneği ile ilk panomuzu oluşturalım.
![280](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/18568a53-0cd4-42ad-8365-8182f32d3ae5)

- Oluşturulabilecek birçok pano türü bulunmaktadır. Line, stacked area, number bunlardan sadece birkaçıdır. CPU üzerindeki yükü görmek için line widget’ı kullanmak mantıklı iken S3 bucket’ları içerisindeki obje sayısını görmek için number widget tipi daha uygun olacaktır. Bu aşamada ‘Line’ seçelim ve devam edelim. 
- Karşımıza çıkan ekranda verileri hangi kaynaktan alacağımızı sorar. “Metrics” ve “Logs” olan bu iki kaynaktan, ‘metrics’ seçeneği ile devam edelim. 
- Karşımıza çıkan ekranda aktif servislerimizin bulunduğu kategoriler görünecektir. Buradan EC2 sanal makinemizi seçelim. Sonrasında “Per-Instance Metric” ile devam edelim.
- Aşağıda tüm EC2 instaneler listelenecektir. Başlığın basında oluşturduğumuz “cloudWatchizleme” adlı instance’ı seçelim. Metric name olarak ise “CPUUtilization” opsiyonunu kullanabiliriz. 
- Grafik zamanla oluşacaktır ve sağ üstte bulunan zaman periyotları ile grafik periyodunu ölçeklendirebilirsiniz.
- Yeni bir widget daha ekleyelim ve bu widget için S3 servisini seçelim. Storage metric ve sonrasında istediğimiz bir S3 bucket ismini seçerek metric olarak “NumberOfObject”i seçekerek ilerleyelim. 
- Artık dashboard başlığı altında belirttiğimiz metric değerlerine göre izleme yapabiliriz.

### 16.3.2. Alarms
Burada olası durumlarda belirttiğimiz optimal değerler dışına çıkıldığında e-posta almamızı sağlayabiliriz. Create alarm diyerek başlayalım.

- “Select metric” dediğimizde aynı dashboard’da olduğu gibi karşımıza servisler gelecektir. EC2’yi seçip devam edelim ve sonrasında “Per-Instance Metric” diyelim. 
- Yine aynı şekilde “cloudWatchizleme” adlı instance’ı seçelim ve metric olarak “CPUUtilization” opsiyonu ile devam edelim. 
- Sontrasında “Conditions” başlığı altında istediğimiz koşulu belirleriz. Greater/Equal ve value olarak 80 belirleyelim. Bu alarm, seçtiğimiz instance’ın CPU kullanım oranı %80’ı geçtiğinde alarmı tetikleyecektir. 
- “Missing data treatment” başlığı altında veri akışı almadığında bu durumda ne yapsın bunu belirlememiz gerekir. “Treat missing data as good” olarak devam edebiliriz. Bu seçenekle bir veri gelmediğinde yine de izlemeye devam edecektir. “Treat missing data as bad” seçeneğinde veri gelmediğinde otomatik olarak alarmı tetikler. 
- “Notification” başlığı altında belirtiğimiz oluştuğunda bunu hangi durum olarak belirtmesi istediğini seçeriz. “In alarm” seçeneği ile devam edelim. 
- Bildirimi nasıl göndereceğini sorduğunda ise “Create new topic” diyerek bir SNS topic’i ve e-posta adresi girmemizi ister. Create topic dediğimizde onay için e-posta adresimize bir onay e-postası gelebilir. 
- Bu durum yaşandığında otomatik “Auto scaling actions” altında tetiklenebilir veya “EC2 actions” altında bu durum yaşandığında makineyi durdur, yeniden başlat gibi aksiyonlar alınabilir. 
- En son aşamada bir alarm name ve açıklama eklenir. Sonrasında alarm oluşturulmuş olur. Belirtilen koşul oluştuğunda otomatik olarak belirtilen e-posta adresine uyarı epostası gelecektir.

### 16.3.3. Events
Events başlığı altında aynı alarm için olduğu gibi, belirtilen bir durum olması durumunda başka bir olay tetiklenebilir. Alarm özelliğinden ayıran en önemli özellik ise spesifik olarak bir instance seçebilir veya herhangi bir instance diyerek instance’lardan herhangi birinde belirttiğiniz koşul yaşandığında başka bir olay tetikleyebilirsiniz. 

Bir diğer önemli fark ise alarm hizmeti üzerinden sadece SNS hizmeti ile bildirim servisi kullanılabilirken, events özelliği ile birlikte bir EC2 instance oluştuğunda otomatik olarak bir lambda (ileriki başlıklarda değinilecek) işlevini tetikleyebilirsiniz.

### 16.3.4. Metrics
Dashboard alt başlığındaki özelliğe oldukça benzerdir. Bu özellik ile bir dashboard oluşturmadan hızlı bir şekilde bir servis hakkında bir veya birden fazla metrik hakkında bilgi alabilirsiniz. 

Dashboard üzerinde özellikler yani metrikler önceden belirlenir ve düzenli olarak izlenir. Ancak metrics alt başlığında o an herhangi bir servisin istediğiniz bir metriğini görüntüleyebilirsiniz.

### 16.3.5. Logs
Bu alt özelliği bir senaryo üzerinden ele alalım. EC2 sanal makinesinde bir web sayfanız var ve bu web sayfasına dair bağlantı bilgilerinin nginx aracının access log kayıtlarında tutulduğunu varsayalım. Log kayıtlarını makinelere bağlanarak gerekli dizinde okuyabiliriz. Instance sayısı arttığında ise durum içinden çıkılmaz bir hal alabilir. Bu zahmetli iş yerine birkaç ayarlama ile log kayıtlarının otomatik olarak CloudWatch log sayfasına atılmasını sağlayabiliriz. 

Bu işlem için öncelikle bir IAM rol oluşturmalıyız. EC2 kontrol paneli üzerinden rol oluşturma ekranına gelelim. İzin (permission) olarak CloudWatchAgentAdmin yetkisini EC2 üzerinden erişilebilir hale getirecek bir rol oluşturduktan sonra bu role “cloudWatchAgent” ismini etiket olarak atayalım. EC2 kontrol panelinde daha önceden oluşturduğumuz “cloudWatchizleme” adlı instance’a bu rolü ‘Actions’ menüsü üzerinden ayarlayalım. 

Bu işlemlerden sonra CloudWatch kontrol paneline dönerek bir log grup oluşturabiliriz. Bu işlemi de yaptıktan sonra EC2 instance’ına PuTTY gibi bir yardımcı uygulama ile bağlanabiliriz. Bağlandıktan sonra aşağıdaki adımları takip edelim.

- İlk olarak gerekli agent’i makineye indirmek için ``wget https://s3.amazonaws.com/amazoncloudwatchagent/amazon_linux/amd64/latest/amazon-cloudwatch-agent.rpm`` komutunu kullanabiliriz. 
- Sonrasında bu agent’i rpm yardımıyla, şu kodu kullanarak kuralım: ``sudo rpm -U ./amazon-cloudwatch-agent.rpm ``
- Kurulum işlemi de tamamlandıktan sonra ``sudo /opt/aws/amazon-cloudwatchagent/bin/amazon-cloudwatch-agent-config-wizard``kod parçası ile wizard’ı çalıştırabiliriz.
- Bu aşamadan sonra agent birçok soru soracaktır. Bu soruları istediğimiz şekilde ayarlarız. 
- Sorular devam ederken wizard tarafından herhangi bir log dosyasını monitor etmek isteyip istemediğimizi soran bir soru gelecektir. Bu soruya evet diyerek nginx’in log konumu ile ilerleyeceğiz. 
- Log dosyasının nerede olduğunu soracaktır. ``/var/log/nginx/access.log`` dosya yolunu bu soruya cevap olarak gireriz. 
- Log grup ismi olarak az önce oluşturduğumuz grubun ismini girebiliriz. Bu aşamadan sonra stream ismi, başka bir log dosyası isteyip istemediğimizi sorar. Başka bir log dosyasını izlemek istemediğimizi belirtiriz. 
- Hangi AWS credential’ı kullanacağımızı sorduğunda SDK ile devam edebiliriz. Sonunda config dosyamız hazır durumdadır. 
- Bir sonraki aşamaya geçmeden önce ilk olarak ``mkdir /usr/share/colletd`` komutu ile bir dizin oluşturulur. Sonrasında ``cd /usr/share/colletd`` komutu ile oluşturulan dizine gidilir ve ``touch types.db`` komutu ile ``types.db`` adında bir dosya oluşturulur. 
- En son aşamada ise ``sudo /opt/aws/amazon-cloudwatch-agent/bin/amazoncloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazoncloudwatch-agent/bin/config.json -s ``komutu ile işlemler tamamlanır.

Yukarıda işlemleri tamamlandıktan sonra CloudWatch kontrol panelinde bulunan “Logs” alt başlığına kayıtlar bir süre sonra yüklenmeye başlayacaktır ve log kayıtları güncellendikçe, CloudWatch üzerindeki kayıtlar da güncellenecektir.
