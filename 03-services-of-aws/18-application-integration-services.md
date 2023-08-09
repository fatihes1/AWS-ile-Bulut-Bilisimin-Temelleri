# 19. Uygulama Entegrasyonu Servisleri
## 19.1. Amazon AppFlow
![167](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/fdf170c2-4344-4f83-900b-5649dc3823dd)

Üçüncü taraf uygulamaları ve AWS hizmetlerini kod olmadan güvenli bir şekilde entegre ederek veri akışlarını otomatikleştiren AWS servisidir. 

Amazon AppFlow; Salesforce, SAP, Zendesk, Slack ve ServiceNow gibi Hizmet Olarak Yazılım uygulamaları ile Amazon S3 ve Amazon Redshift gibi AWS hizmetleri arasında sadece birkaç tıklamayla güvenli veri aktarımı yapmanıza olanak tanıyan, tam olarak yönetilen bir entegrasyon hizmetidir. AppFlow sayesinde, veri akışlarını kurumsal ölçekte ve seçtiğiniz sıklıkta (programlı biçimde, bir iş olayına yanıt olarak veya istek üzerine) çalıştırabilirsiniz. Filtreleme ve doğrulama gibi veri dönüştürme özelliklerini yapılandırarak ilave adımlar olmadan akışın bir parçası olarak zengin ve kullanıma hazır veriler üretebilirsiniz. AppFlow, hareket halindeki verileri otomatik olarak şifreler ve kullanıcılara, AWS PrivateLink ile entegre olan SaaS uygulamaları için verilerin genel internet üzerinden akışını kısıtlayarak güvenlik tehditlerine maruz kalma riskini azaltma olanağı sunar.

## 19.2. Amazon EventBridge
![168](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0008276c-79cb-4d4e-b3ea-9f8b4d131af6)

AWS, mevcut sistemler veya SaaS uygulamaları genelinde uygun ölçekte olay odaklı uygulamalar geliştirmenize ortam sağlayan AWS servisidir. 

Amazon EventBridge sahip olduğunuz uygulamalar, entegre Hizmet Olarak Yazılım (SaaS) uygulamaları ve AWS hizmetleri tarafından oluşturulan olayları kullanarak uygun ölçekte olay odaklı uygulamalar geliştirmeyi kolaylaştıran sunucusuz bir olay veri yoludur. EventBridge; Zendesk veya Shopify gibi olay kaynaklarından AWS Lambda ve diğer SaaS uygulamaları gibi hedeflere gerçek zamanlı veri akışı sağlar. Olay yayıncısı ve tüketici tamamen ayrıştırılmış haldeyken veri kaynaklarınıza gerçek zamanlı olarak yanıt veren uygulama mimarileri oluşturmak üzere verilerinizin nereye gönderileceğine karar vermek için yönlendirme kuralları ayarlayabilirsiniz.

## 19.3. Amazon Managed Workflows for Apache Airflow (MWAA)
![169](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/70c1e81d-9a3d-47c3-bf1f-a93cc2aab25a)

Apache Airflow için yüksek düzeyde kullanılabilir, güvenli ve yönetilen iş akışı düzenlemesini sağlayan AWS servisidir. 

Apache Airflow için Amazon Tarafından Yönetilen İş Akışları (MWAA), bulutta uçtan uca veri ardışık düzenlerini uygun ölçekte kurmayı ve çalıştırmayı kolaylaştıran, Apache Airflow için yönetilen bir düzenleme hizmetidir. Apache Airflow, "iş akışları" olarak adlandırılan süreç ve görev dizilerini programlı olarak yazmak, planlamak ve izlemek için kullanılan açık kaynaklı bir araçtır. Yönetilen İş Akışları ile, ölçeklenebilirlik, kullanılabilirlik ve güvenlik için temel altyapıyı yönetmek zorunda kalmadan iş akışları oluşturmak için Airflow ve Python'u kullanabilirsiniz. Yönetilen İş Akışları, iş akışı yürütme kapasitesini ihtiyaçlarınızı karşılayacak şekilde otomatik olarak ölçeklendirir ve verilere hızlı ve güvenli erişim sağlamanıza yardımcı olmak için AWS güvenlik hizmetleriyle entegredir.

## 19.4. Amazon MQ
![170](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/747481a4-dc50-4be9-9ebd-51fec3b8d877)

AWS tarafından sunulan tam olarak yönetilebilir açık kaynak mesaj aracısı hizmetidir. Amazon MQ, Apache ActiveMQ ve RabbitMQ için AWS’de mesaj aracıları ayarlayıp çalıştırmayı kolaylaştıran bir yönetilen mesaj aracısı hizmetidir. Amazon MQ sizin için ileti aracılarının tedarik, kurulum ve bakım işlemlerini yöneterek operasyonel yükünüzü azaltır. Amazon MQ mevcut uygulamalarınıza endüstride standart olan API’ler ve protokollerle eriştiği için kodu yeniden yazmak zorunda kalmadan AWS’ye kolayca aktarım gerçekleştirebilirsiniz.

## 19.5. Amazon Simple Notification Service
![171](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/d1181ead-32d8-4d3c-b5fb-e2600cd88d0f)

Tümüyle yönetilen pub/sub mesajlaşma, SMS, e-posta ve mobil anlık bildirimler servisidir. Amazon Simple Notification Service (Amazon SNS), hem uygulamadan uygulamaya (A2A) hem de uygulamadan kişiye (A2P) iletişim için tam olarak yönetilen bir mesajlaşma hizmetidir. 

A2A pub/sub işlevi; dağıtılmış sistemler, mikro hizmetler ve olay tabanlı sunucusuz uygulamalar arasında yüksek aktarım hızlı, gönderme tabanlı, çoktan çoka mesajlaşmaya yönelik konular sunar. Yayıncı sistemleriniz, Amazon SNS konularını kullanarak mesajları paralel işleme için Amazon SQS kuyrukları, AWS Lambda işlevleri, HTTPS uç noktaları ve Amazon Kinesis Data Firehose gibi çok sayıda abone sistemine dağıtabilir. A2P işlevi kullanıcılara SMS, mobil anlık bildirimler ve e-posta yoluyla uygun ölçekte mesajlar göndermenizi sağlar.

## 19.6. Amazon Simple Queue Service
![172](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/553673f0-9645-43e8-8585-e1c47018e148)

Mikro hizmetler, dağıtılmış sistemler ve sunucusuz uygulamalar için tümüyle yönetilen ileti kuyrukları servisidir. Amazon Simple Queue Service (SQS), dağıtılmış sistemleri ve sunucusuz uygulamaları birbirinden ayırmanıza ve ölçeklendirmenize imkân tanıyan, tam olarak yönetilen bir iletileri kuyruğa alma hizmetidir. SQS, mesajlaşmaya yönelik ara yazılımları yönetmenin ve işletmenin getirdiği karmaşıklık ile ek iş yükünü ortadan kaldırarak geliştiricilerin farklı işlere odaklanmasına imkân tanır. SQS ile ileti kaybı yaşamadan veya diğer hizmetlerin erişilebilir olmasına gereksinim duymadan yazılım bileşenleri arasında dilediğiniz hacimde ileti gönderebilir, depolayabilir ve alabilirsiniz. AWS Management Console, Command Line Interface veya tercih ettiğiniz SDK'yi ve üç basit komutu kullanarak SQS'yi dakikalar içinde kullanmaya başlayabilirsiniz. 

SQS iki tür ileti kuyruğu sunar. Standart kuyruklar tarafından en yüksek aktarım hızı, en iyi çaba ilkesine göre sıralama ve en az bir kez teslim olanakları sunulur. SQS FIFO kuyrukları, 77 iletilerin tam olarak bir kez ve tam olarak gönderildikleri sırada işlenmesi konusunda güvence sağlayacak şekilde tasarlanmıştır.

## 19.7. AWS Step Functions
![173](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/1ebb87a8-0e0f-4bf2-bbe0-6551158d2790)

Modern uygulamalar için görsel iş akışları sağlayan AWS servisidir. AWS Step Functions, geliştiricilerin dağıtılmış uygulamalar oluşturmak, BT ve iş süreçlerini otomatikleştirmek ve AWS hizmetlerini kullanarak veri ve makine öğrenimi işlem hatları oluşturmak için kullandığı az kod kullanımlı, görsel bir iş akışı hizmetidir. İş akışları, geliştiricilerin daha yüksek değerli iş mantığına odaklanabilmesi için hataları, yeniden denemeleri, paralelleştirmeyi, hizmet entegrasyonlarını ve gözlemlenebilirliği yönetir.
