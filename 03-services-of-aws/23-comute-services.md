# 24. İşlem Servisleri
## 24.1. Amazon EC2
![219](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/62a8c20e-db27-408a-97bd-e1f0ac1c879a)

Neredeyse tüm iş yükleri için güvenli ve yeniden boyutlandırılabilir işlem kapasitesi sunan AWS servisidir. Amazon Elastic Compute Cloud (Amazon EC2), 500'den fazla bulut sunucusu ve iş yükü ihtiyaçlarınızı en iyi şekilde karşılamanıza yardımcı olacak en son işlemci, depolama alanı, ağ iletişimi, işletim sistemi ve satın alma modeli seçenekleri sayesinde en geniş ve kapsamlı işlem platformunu sunar. Intel, AMD ve Arm işlemcileri destekleyen ilk büyük bulut sağlayıcısı, istek üzerine EC2 Mac bulut sunucuları ve 400 Gbps Ethernet ağ iletişimi sunan tek bulut hizmetiyiz. Makine öğrenimi eğitimi için en iyi fiyat performansının yanı sıra buluttaki çıkarım bulut sunucuları başına en düşük maliyeti sunuyoruz. Diğer bulut sağlayıcılarına kıyasla AWS'de daha fazla SAP, yüksek performanslı bilişim (HPC), makine öğrenimi ve Windows iş yükleri çalıştırılıyor.

## 24.2. Amazon EC2 Auto Scaling
![220](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/369b21c0-44cc-4667-9afc-211ff1643a91)

Değişen talebi karşılamak için işlem kapasitesi ekleme veya kaldırma yapabilen AWS servisidir. 

Amazon EC2 Auto Scaling uygulama erişilebilirliğini korumanıza yardımcı olur ve EC2 bulut sunucularını tanımladığınız koşullara göre otomatik olarak eklemenize veya kaldırmanıza olanak tanır. Filonuzun sağlığını ve erişilebilirliğini korumak için EC2 Auto Scaling'in filo yönetim özelliklerini kullanabilirsiniz. EC2 bulut sunucularını eklemek veya kaldırmak için EC2 Auto Scaling'in dinamik ve tahmini ölçeklendirme özelliklerini de kullanabilirsiniz. Dinamik ölçeklendirme, değişen talebe cevap verir ve tahmini ölçeklendirme, öngörülen talebe göre doğru sayıda EC2 bulut sunucusunu otomatik olarak zamanlar. Dinamik ölçeklendirme ve tahmini ölçeklendirme, daha hızlı ölçeklendirmek için birlikte kullanılabilir.

## 24.3. Amazon Lightsail
![221](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/27946014-dfdc-4c2c-aba9-403dfcea43e1)

Düşük maliyetli, önceden yapılandırılmış bulut kaynaklarıyla uygulamaları ve web sitelerini hızla oluşturmanızı sağlayan AWS servisidir. Yalnızca birkaç tıklamayla bir web sitesi veya uygulama oluşturabilirsiniz. Ağ iletişimi, erişim ve güvenlik ortamlarını otomatik olarak yapılandırır. Büyüdükçe kolayca ölçeklendirin veya kaynaklarınızı Amazon EC2 gibi daha geniş AWS ekosistemine taşıyabilirsiniz.

## 24.4. AWS App Runner
![222](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/7600e01c-a6e5-4912-bee2-fe396685705c)

Geliştiriciler için geniş ölçekte üretim web uygulamaları kolaylaştıran AWS servisidir. AWS App Runner, geliştiricilerin container’lı web uygulamalarını ve API’leri uygun ölçekte ve altyapı deneyimi gerekmeden hızla dağıtmasını kolaylaştıran, tam olarak yönetilen bir hizmettir. Kaynak kodunuz veya container görseli ile başlayın. App Runner, web uygulamasını otomatik olarak oluşturur ve dağıtır, trafiği şifrelemeyle dengeler, trafik ihtiyaçlarınızı karşılayacak şekilde ölçeklendirir ve hizmetlerinizin özel bir Amazon VPC’sinde çalışan diğer AWS hizmetleri ve uygulamalarıyla iletişim kurmasını kolaylaştırır. App Runner ile sunucular veya ölçeklendirme üzerine düşünmek yerine, uygulamalarınıza odaklanmanız için daha fazla vaktiniz olur.

## 24.5. AWS Auto Scaling
![223](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e3224317-4797-4ab4-9cd6-8c781e94de19)

Performans ve maliyet optimizasyonu için uygulama ölçeklendirme imkânı veren AWS servisidir. 

AWS Auto Scaling, uygulamalarınızı izler ve kapasiteyi mümkün olan en düşük maliyet üzerinden kararlı, öngörülebilir performansı koruyacak şekilde otomatik olarak ayarlar. AWS Auto Scaling ile birden çok hizmette birden çok kaynak için uygulama ölçeklendirme kurulumu yapmak kolaydır. Hizmet tarafından Amazon EC2 bulut sunucuları ve Spot Filoları, Amazon ECS görevleri, Amazon DynamoDB tabloları ve dizinleri ile Amazon Aurora Replikaları gibi kaynaklar için ölçeklendirme planları oluşturmanıza imkân tanıyan basit, güçlü bir kullanıcı arabirimi sağlanır. AWS Auto Scaling, performansı veya maliyeti optimize etmenize ya da bunlar arasında bir denge sağlamanıza imkân tanıyan önerilerle ölçeklendirme işlemini basitleştirir. Zaten Amazon EC2 bulut sunucularınızı dinamik olarak ölçeklendirmek için Amazon EC2 Auto Scaling kullanıyorsanız artık bunu AWS Auto Scaling ile birleştirerek diğer AWS hizmetleri için ek kaynakları ölçeklendirebilirsiniz. AWS Auto Scaling ile uygulamalarınız hep doğru zamanda, doğru kaynaklara sahip olur. 

AWS Auto Scaling'i AWS Management Console, Komut Satırı Arabirimi (CLI) veya SDK aracılığıyla kullanmaya başlamak kolaydır. AWS Auto Scaling ek ücret olmaksızın sunulur. Yalnızca uygulamalarınızı çalıştırmak için gerekli olan AWS kaynakları ve Amazon CloudWatch izleme ücretleri karşılığında ödeme yaparsınız.

## 24.6. AWS Batch
![224](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0ad29c18-da9a-4adb-9dcf-4737a0795796)

Her ölçekte tam olarak yönetilen batch processing yapma imkânı tanıyan AWS servisidir. AWS Batch geliştiricilerin, bilim insanlarının ve mühendislerin AWS'de kolayca yüz binlerce toplu işlem işi çalıştırmasına imkân tanır. AWS Batch, gönderilen toplu işin hacmine ve özel kaynak gereksinimlerine bağlı olarak en uygun miktarda ve türde işlem kaynağını (ör. CPU veya bellek için optimize edilmiş bulut sunucuları) dinamik olarak tedarik eder. AWS Batch ile işleri çalıştırmak için kullandığınız toplu bilgi işlem yazılımlarını veya sunucu kümelerini yükleyip yönetmeniz gerekmediğinden, sonuçları analiz etmeye ve sorunları çözmeye odaklanabilirsiniz. AWS Batch, toplu bilgi işlem iş yüklerinizi AWS Fargate, Amazon EC2 ve Spot Bulut Sunucuları gibi AWS işlem hizmetleri ve özelliklerinin tamamında planlar, zamanlar ve yürütür. 

AWS Batch için ek ücret uygulanmaz. Yalnızca toplu işlerinizi depolamak ve çalıştırmak amacıyla oluşturduğunuz AWS kaynakları (ör. EC2 bulut sunucuları veya Fargate işleri) için ücret ödersiniz.

## 24.7. AWS Compute Optimizer
![225](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/14c3821e-33f3-4532-a8f3-3db7a728b95a)

Maliyetleri azaltmak ve iş yükleriniz için performansı artırmak amacıyla ideal AWS kaynaklarını öneren servistir.

AWS Compute Optimizer, geçmiş kullanım ölçümlerini analiz etmek için makine öğrenimini kullanarak maliyetleri azaltmak ve performansı artırmak amacıyla iş yükleriniz için optimum AWS kaynakları önerir. Kaynakların gereğinden fazla sağlanması, gereksiz altyapı maliyetine yol açarken, kaynakların yetersiz sağlanması da zayıf uygulama performansına neden olabilir. Compute Optimizer, kullanım verilerinize göre Amazon Elastic Compute Cloud (EC2) bulut sunucusu tipleri, Amazon Elastic Block Store (EBS) birimleri ve AWS Lambda işlevleri gibi üç tür AWS kaynağı için en uygun yapılandırmaları seçmenize yardımcı olur. 

Compute Optimizer, bulutta çeşitli iş yüklerini çalıştıran Amazon'un kendi deneyiminden elde edilen bilgileri uygulayarak iş yükü modelleri belirler ve optimum AWS kaynakları önerir. Compute Optimizer; yoğun CPU kullanıp kullanmadığı, günlük bir model sergileyip sergilemediği veya bir iş yükünün yerel depolamaya sık sık erişip erişmediği gibi düzinelerce tanımlayıcı özelliği belirlemek için iş yükünüzün yapılandırmasını ve kaynak kullanımını analiz eder. Hizmet bu özellikleri işler ve iş yükünün gerektirdiği donanım kaynağını tanımlar. Compute Optimizer, öneriler sunmak için iş yükünün çeşitli donanım platformlarında (örneğin Amazon EC2 bulut sunucusu tipleri) veya farklı yapılandırmalar (örneğin Amazon EBS birim IOPS ayarları ve AWS Lambda işlevi bellek boyutları) kullanarak nasıl performans gösterebileceğini tahmin eder.

## 24.8. AWS Elastic Beanstalk
![226](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/a8093dbd-6bcc-4758-9dd5-a8e3e80f9973)

AWS Elastic Beanstalk; Apache, Nginx, Passenger ve IIS gibi bilindik sunucular üzerinde Java, .NET, PHP, Node.js, Python, Ruby, Go ve Docker ile geliştirilmiş web uygulamalarını ve hizmetleri dağıtıp ölçeklendirmek için kullanımı kolay bir hizmettir. 

Tek yapmanız gereken kodunuzu yüklemektir; kapasite tedariği, yük dengeleme ve otomatik ölçeklendirmeden uygulama durumunu izlemeye kadar dağıtımın her aşaması Elastic Beanstalk tarafından otomatik olarak gerçekleştirilir. Öte yandan, uygulamanızı destekleyen AWS kaynakları üzerindeki denetim tamamen sizde kalır ve temel kaynaklara dilediğiniz zaman erişebilirsiniz. 

Elastic Beanstalk için ek ücret uygulanmaz. Yalnızca uygulamalarınızı depolamak ve çalıştırmak için gerekli AWS kaynaklarına ödeme yaparsınız.

## 24.9. AWS Lambda
![227](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f4769e0f-5ab3-459c-b7ee-0421cb3ad958)

Sunucuları veya kümeleri düşünmek zorunda kalmadan kod çalıştırabileceğiniz AWS servisidir. Altyapı tedarik etmek veya yönetmek zorunda kalmadan kod çalıştırabilirsiniz. Kod yazıp “.zip” dosyası veya container görüntüsü olarak yüklemeniz yeterlidir. Günde onlarca olaydan saniyede yüz binlerce olaya kadar her ölçekte kod yürütme isteklerine otomatik olarak yanıt verir. En yüksek kapasite için altyapıyı önceden tedarik etmek yerine yalnızca kullandığınız işlem süresi için (milisaniye başına) ödeme yaparak maliyetlerden tasarruf etmenizi sağlar. Doğru işlev belleği boyutuyla kod yürütme süresini ve performansını optimize eder. Tedarik edilen eş zamanlılık ile yüksek talebe çift haneli milisaniye cinsinden yanıt verir.

## 24.10. AWS Outposts Ailesi
![228](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/63ea5d58-f315-445a-a8f4-9786fe80253a)

Gerçekten tutarlı bir hibrit deneyim için AWS altyapısını ve hizmetlerini şirket içinde çalıştırmanıza olanak tanır. 

AWS Outposts, gerçekten tutarlı bir hibrit deneyim için AWS altyapısını ve hizmetlerini neredeyse tüm şirket içi veya uç konumlara sağlayan, tam olarak yönetilen çözümlerden oluşan bir ailedir. Outposts çözümleri, yerel AWS hizmetlerini şirket içinde çalıştırarak kullanımını genişletmenize olanak tanır. Ayrıca, 1U ve 2U Outposts sunucularından 42U Outposts raflarına ve birden çok raf dağıtımlarına kadar çeşitli form faktörlerinde mevcuttur. 

AWS Outposts'ta bazı AWS hizmetlerini yerel olarak çalıştırabilir ve yerel AWS bölgesinde sunulan çok sayıda hizmete bağlanabilirsiniz. Bilinen AWS hizmetleri, araçları ve API'lerini kullanarak uygulamaları ve iş yüklerini şirket içinde çalıştırın. Outposts, şirket içi sistemlere düşük gecikmeli erişim gerektiren iş yüklerini ve cihazları, yerel veri işlemeyi, veri yerleşimini ve yerel sistem bağımlılıklarıyla uygulama geçişini destekler.

## 24.11. AWS Serverless Application Repository
![229](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e11e3688-054f-44b6-b81f-c8ee74e02543)

Sunucusuz uygulamalar bulma, dağıtma ve yayımlama imkânı tanıyan AWS servisidir. 

AWS Serverless Application Repository, sunucusuz uygulamalara yönelik bir yönetilen depodur. Ekiplerin, kuruluşların ve bireysel yazılım geliştiricilerin yeniden kullanılabilir uygulamaları depolayıp paylaşmalarına ek olarak sunucusuz mimarileri yeni ve etkili yöntemlerle kolay bir şekilde derleyip dağıtmalarını sağlamaktadır. Serverless Application Repository hizmetini kullandığınızda uygulamanızı dağıtmadan önce kaynak kodunuzu AWS üzerinde kopyalamanıza, derlemenize, paketlemenize veya yayımlamanıza gerek kalmaz. Bunun yerine Serverless Application Repository içindeki önceden derlenmiş uygulamaları sunucusuz mimarilerinizde kullanarak ekiplerinizin aynı işleri birden fazla kez yapma ihtimalini azaltabilir, kuruluşunuzun en iyi uygulamalarına bağlı kalabilir ve piyasaya daha hızlı bir giriş yapabilirsiniz. AWS Identity and Access Management (IAM) entegrasyonu her uygulama için kaynak düzeyinde kontrol sağlayarak uygulamaları herkese açık olarak veya belirli AWS hesaplarıyla özel olarak paylaşmanızı sağlar. Oluşturduğunuz bir uygulamayı paylaşmak için AWS Serverless Application Repository’de yayımlayın. 

Her uygulama, kullanılan AWS kaynaklarını tanımlayan bir AWS Serverless Application Model (SAM) şablonuyla paketlenir. Genel olarak paylaşılan uygulamalar, uygulamanın kaynak koduna bir bağlantı da içerir. Serverless Application Repository kullanımı ek ücrete tabi değildir. Yalnızca dağıttığınız uygulamalarda kullanılan AWS kaynakları için ödeme yaparsınız.

## 24.12. AWS Wavelength
![230](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/075c5042-ec5c-4248-bfa0-cd2ceca364ce)

5G cihazlar için ultra düşük gecikme süreli uygulamalar sağlamanızı mümkün kılan AWS servisidir. Bildiğiniz AWS hizmetlerini, API'leri ve araçları kullanarak herhangi bir eğitim ihtiyacı olmadan yeni nesil uygulamalar oluşturabilirsiniz. Uygulamaları bir kez geliştirir ve küresel 5G ağlarında yer alan birden çok Wavelength Alanına dağıtımları ölçeklendirirsiniz. Yenilikçi 5G uç uygulama geliştirme sürecini hızlandırmak için performansı kanıtlanmış AWS altyapısı ve hizmetlerinden yararlanırsınız.

## 24.13. VMware Cloud on AWS
![231](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/66e2901f-f713-4746-8f18-163b4df8a9c9)

200’den fazla AWS hizmet yelpazesi ile daha hızlı bir şekilde buluta geçiş yapmanızı ve her yerden güvenli bir şekilde çalışmanızı sağlayan AWS servisidir. 

AWS, tüm vSphere temelli iş yükleri için VMware'ın öncelikli açık bulut çözüm ortağıdır. VMware ve AWS çözüm ortaklığı, hibrit bulut için daha hızlı, daha kolay ve uygun maliyetli bir yol sunmanın yanı sıra müşterilerin daha hızlı pazara ulaşmasını ve inovasyon hızını artırmasını sağlayan uygulamaları modernleştirmesine imkân tanır. Çalışanlarınızın herhangi bir yerden güvenli şekilde çalışmasını sağlamak üzere Sanal Masaüstü Altyapısı (VDI) çözümlerimizle güvenli sanal uygulamalar ve masaüstleri sunmak için mevcut becerilerinizi, süreçlerinizi ve yönetişiminizi kullanın. VMware Cloud™ on AWS için Intel® Xeon® Ölçeklenebilir işlemciler tarafından desteklenen yeni Amazon EC2 i3en.metal bulut sunucuları yüksek ağ aktarım hızı ve düşük gecikme süresi sağlar. Böylece hızlı veri merkezi tahliyesi, olağanüstü durum kurtarma ve uygulama modernizasyonu için veri merkezlerini buluta taşıyabilirsiniz. 

4 yılı aşkın ortak mühendislik sayesinde VMware ve AWS, kuruluşlara çözüme entegre edilen gelişmiş VMware işlevlerinin yanı sıra destek ve hizmet entegrasyonu için tek bir iletişim noktası sunmaktadır. Bu nedenle VMware Cloud on AWS, tüm vSphere iş yükleri için tercih ettiğimiz hizmettir.
