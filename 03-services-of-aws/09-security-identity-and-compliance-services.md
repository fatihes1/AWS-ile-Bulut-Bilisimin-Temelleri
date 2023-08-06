# 10. Güvenlik, Kimlik ve Uygunluk Servisleri
## 10.1. Amazon Cognito
![84](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b83a7721-b504-4a05-be9d-c2c178d16c5b)

Amazon Cognito, web ve mobil uygulamalarınıza hızlı ve kolayca kullanıcı kaydı, oturum açma ve erişim denetimi eklemenize olanak sağlar. Amazon Cognito, milyonlarca kullanıcıya ölçeklenir ve Apple, Facebook, Google, Amazon gibi sosyal kimlik sağlayıcılarının yanı sıra SAML 2.0 ve OpenID Connect aracılığıyla kurumsal kimlik sağlayıcıları ile oturum açmayı destekler.

## 10.2. Amazon Detective
![85](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/60852794-9611-414b-8a8d-8aceb112dfc6)

Amazon Detective, olası güvenlik sorunlarını veya şüpheli etkinlikleri analiz etmeyi, incelemeyi ve bunların temel nedenini belirlemeyi kolaylaştırır. Amazon Detective, günlük verilerini AWS kaynaklarınızdan otomatik olarak toplar, daha hızlı ve verimli güvenlik araştırmaları yapmanızı sağlayan bağlantılı bir veri seti oluşturmak için makine öğrenimi, istatistiksel analiz ve grafik teorisini kullanır. 

Amazon GuardDuty, Amazon Macie ve AWS Security Hub gibi AWS güvenlik hizmetlerinin yanı sıra çözüm ortağı güvenlik ürünleri, olası güvenlik sorunlarını veya bulgularını belirlemek için kullanılabilir. Bu hizmetler, bir şeyler ters gittiğinde sizi uyarma ve bu sorunu düzeltmek için nereye gideceğinizi belirtme konusunda son derece faydalıdır. Ancak kimi zaman, temel nedeni yalıtmak ve harekete geçmek için daha derine inmeniz ve daha fazla bilgiyi analiz etmeniz gereken bir güvenlik bulgusu olabilir. Güvenlik bulgularının temel nedenini belirlemek, genellikle pek çok farklı veri kaynağından günlüklerin toplanmasını ve birleştirilmesini, verileri düzenlemek için ayıklama, dönüştürme ve yükleme (ETL) araçlarını veya özel betik oluşturmayı ve ardından güvenlik analistlerinin verileri analiz edip uzun araştırmalar yapmasını içeren karmaşık bir süreç olabilir. 

Amazon Detective, güvenlik ekiplerinizin kolayca araştırma yapmasını ve bir bulgunun temel nedenine hızla ulaşmasını sağlayarak bu süreci basitleştirir. Amazon Detective; Virtual Private Cloud (VPC) Akış Günlükleri, AWS CloudTrail ve Amazon GuardDuty gibi birden çok veri kaynağından trilyonlarca olayı analiz edebilir ve otomatik olarak kaynaklarınız, kullanıcılarınız ve bunlar arasında zaman içinde gerçekleşen etkileşimlere ilişkin birleştirilmiş, etkileşimli bir görünüm oluşturur. Bu birleştirilmiş görünüm sayesinde, tüm ayrıntıları ve bağlamı tek bir yerde görselleştirerek bulguların altında yatan nedenleri belirleyebilir, ilgili geçmiş etkinlikleri ayrıntılı bir şekilde inceleyebilir ve temel nedeni hızla belirleyebilirsiniz.

## 10.3. Amazon GuardDuty
![86](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/64b164df-80f2-4816-93e3-b0d2893e8ab5)

Olası tehditleri sadece birkaç tıklamayla kuruluş çapında görünür hale getirir. AWS tehdit zekâsı, davranış modelleri ve üçüncü taraf güvenlik akışları ile tehditleri hızlı bir biçimde açığa çıkarır. Otomatik yanıtları tetikleyerek tehditleri erken aşamalarda hafifletir.

## 10.4. Amazon Inspector
![87](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/34140443-1009-4e39-85e7-6dcac7cd6ed8)

Amazon Inspector, AWS üzerinde dağıtılmış olan uygulamaların güvenlik ve mevzuat uyumluluğu seviyesini geliştirmeye yardımcı olan otomatik güvenlik değerlendirmesi hizmetidir. Amazon Inspector, uygulamaları güvenlik açıkları ve en iyi uygulamalardan sapma açısından otomatik olarak değerlendirir. Bu değerlendirmenin ardından Amazon Inspector, önem düzeyine göre önceliklendirilmiş olan ayrıntılı bir güvenlik bulguları listesi oluşturur. Bu bulgular doğrudan veya Amazon Inspector konsolu ya da API aracılığıyla kullanıma sunulan ayrıntılı değerlendirme raporlarıyla birlikte incelenebilir. 

Amazon Inspector güvenlik değerlendirmeleri, Amazon EC2 bulut sunucularınız için istenmeyen ağ erişimlerini ve bu EC2 bulut sunucularındaki güvenlik açıklarını denetlemenize yardımcı olabilir. Amazon Inspector değerlendirmeleri yaygın güvenlik en iyi uygulamaları ve güvenlik açığı tanımlarına göre belirlenmiş önceden tanımlı kural paketleri olarak sunulur. Yerleşik kuralların arasında EC2 bulut sunucularınıza internet erişimin, uzaktan kök kullanıcıyla oturum açma özelliğinin etkin olup olmadığının veya güvenlik açığına sahip yazılım sürümlerinin yüklenip yüklenmediğinin kontrolü gibi örnekler mevcuttur. Bu kurallar AWS güvenlik araştırmacıları tarafından düzenli aralıklarla güncellenir.

## 10.5. Amazon Macie
![88](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f0eea2b8-440f-42f1-a03e-c47134cd1cd2)

Amazon Macie, AWS'deki hassas verilerinizi keşfetmek ve korumak için makine öğrenimi ve desen eşlemeyi kullanan, tamamen yönetilen bir veri güvenliği ve veri gizliliği hizmetidir. 

Kuruluşlar giderek artan veri hacimlerini yönetirken uygun ölçekte hassas verilerini tanımlamak ve korumak her geçen gün daha karmaşık, pahalı ve zaman alan bir iş olabilir. Amazon Macie, uygun ölçekte hassas verilerin keşfedilmesini otomatik hale getirir ve verilerinizi koruma maliyetini düşürür. Macie, AWS Organizations'da tanımladıklarınız hariç olmak üzere şifrelenmemiş klasörler, genel erişime açık klasörler ve AWS hesaplarıyla paylaşılan klasörlerin bir listesini içeren bir Amazon S3 klasörleri envanterini otomatik olarak sağlar. Ardından Macie, makine öğrenimi ve desen eşleme tekniklerini tanımlanması için seçtiğiniz klasörlere uygular ve kişiyi tanımlayabilir bilgiler (PII) gibi hassas veriler konusunda sizi uyarır. 

Macie'nin uyarıları veya bulguları, AWS Management Console'da aranıp filtrelenebilir ve mevcut iş akışları ya da olay yönetimi sistemleriyle kolay entegrasyon için daha önce Amazon CloudWatch Events olarak adlandırılan Amazon EventBridge'e gönderilebilir. Ayrıca, otomatik iyileştirme eylemlerini gerçekleştirmek için AWS Step Functions gibi AWS hizmetleriyle birlikte kullanılabilir. Bu, Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) ve Genel Veri Gizliliği Yönetmeliği (GDPR) gibi düzenlemeleri karşılamaya yardımcı olabilir.

## 10.6. AWS Artifact
![89](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/9c4b0cd6-03f0-4c39-9989-a33f1538fb54)

AWS Artifact, sizin için önemli olan uyumlulukla ilgili bilgiler için gideceğiniz merkezi kaynağınızdır. AWS'nin güvenlik ve uyumluluk raporları ile bazı çevrimiçi anlaşmalara isteğe bağlı erişim sunar. AWS Artifact'te yer alan raporlar hizmet kuruluşu denetimi (SOC) raporları, payment card industry (PCI) raporları ve AWS güvenlik denetimlerinin uygulama ve işletme etkililiğini doğrulayan coğrafyalar ve uyumluluk dikey öğelerinde akreditasyon kuruluşlarından alınan sertifikaları içerir. AWS Artifact'te yer alan anlaşmalar iş ortağı ekini (BAA) ve gizlilik anlaşmasını (NDA) içerir.

## 10.7. AWS Audit Manager
![90](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ac582a9d-d00f-470e-a95e-9604a12d2dfc)

AWS Audit Manager, yönetmelikler ve sektör standartları ile ilişkili riskleri ve uyumluluğu değerlendirme şeklinizi basitleştirmek için AWS kullanımınızı sürekli olarak denetlemenize yardımcı olur. Audit Manager, denetimlerde sıklıkla yaşanan “herkes iş başına” manuel yaklaşımını azaltmak için kanıt toplamayı otomatik hale getirir ve işiniz büyüdükçe bulutta denetim yeteneğinizi ölçeklendirmenize olanak tanır. Politika, prosedür ve faaliyetlerinizin (yani kontrollerin) etkin bir şekilde işleyip işlemediğini değerlendirmek Audit Manager ile oldukça kolaydır. Bir denetim yapma zamanı geldiğinde AWS Audit Manager, kontrollerinize ilişkin paydaş incelemelerini yönetmenize yardımcı olur ve çok daha az manuel çabayla denetime hazır raporlar oluşturmanızı sağlar. 

AWS Audit Manager’ın önceden oluşturulmuş çerçeveleri, AWS kaynaklarınızı CIS AWS Foundations Benchmark, “Genel Veri Koruma Yönetmeliği” (GDPR) ve “Ödeme Kartı Sektörü Veri Güvenliği Standardı” (PCI DSS) gibi sektör standartları veya yönetmeliklerdeki gerekliliklerle eşleştirerek bulut hizmetlerinden elde edilen kanıtların denetçi dostu raporlara dönüştürülmesine yardımcı olur. Ayrıca, kişisel iş gereklilikleriniz için bir çerçeveyi ve kontrollerini tamamen özelleştirebilirsiniz. Seçtiğiniz çerçeveye bağlı olarak Audit Manager, AWS hesaplarınızdan ve kaynaklarınızdan ilgili kanıtları (kaynak yapılandırma anlık görüntüleri, kullanıcı etkinliği ve uyumluluk denetimi sonuçları gibi) sürekli olarak toplayan ve düzenleyen bir değerlendirme başlatır.

## 10.8. AWS Certificate Manager (ACM)
![91](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/9073f334-5497-46ab-b9ba-3af9203a5093)

AWS Certificate Manager, AWS hizmetleriyle ve dahili bağlantılı kaynaklarınızla kullanmak üzere genel ve özel “Güvenli Yuva Katmanı/Aktarım Katmanı Güvenliği” (SSL/TLS) sertifikalarını kolayca tedarik etmenize, yönetmenize ve dağıtmanıza olanak sağlayan bir hizmettir. SSL/TLS sertifikaları, ağ iletişimlerinin güvenliğini sağlamak ve özel ağlar üzerindeki kaynakların yanı sıra İnternet üzerinden web sitelerinin kimliğini oluşturmak için de kullanılır. AWS Certificate Manager, kullanıcının kendisinin yaptığı zaman alıcı SSL/TLS sertifikası satın alma, karşıya yükleme ve yenileme işlemlerini ortadan kaldırır. 

AWS Certificate Manager ile hızlı şekilde bir sertifika isteyip Elastic Load Balancing, Amazon CloudFront dağıtımları ve Amazon API Gateway üzerindeki API'ler gibi, ACM ile bütünleşmiş AWS kaynaklarında sertifikayı dağıtabilir ve AWS Certificate Manager'ın sertifika yenileme işlemlerini gerçekleştirmesini sağlayabilirsiniz. Aynı zamanda, dahili kaynaklarınız için özel sertifikalar oluşturmanıza ve sertifika yaşam döngüsünü merkezi olarak yönetmenize olanak sağlar.

## 10.9. AWS CloudHSM
![92](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/8964d2fc-e0a0-493b-9ed5-9eb45b8368f3)

AWS CloudHSM, AWS Bulut'ta kendi şifreleme anahtarlarınızı kolayca oluşturmanızı ve kullanmanızı sağlayan bulut tabanlı donanım güvenlik modülüdür (HSM). CloudHSM ile FIPS 140-2 Düzey 3 doğrulamalı HSM'leri kullanarak kendi şifreleme anahtarlarınızı yönetebilirsiniz. CloudHSM tarafından PKCS#11, Java Cryptography Extensions (JCE) ve Microsoft CryptoNG (CNG) kitaplıkları gibi endüstri standardı API'ler kullanılarak uygulamalarınızla entegrasyon olanağı sağlanır. 

CloudHSM standartlarla uyumludur ve yapılandırmalarınıza bağlı olarak tüm anahtarlarınızı piyasadaki diğer çoğu HSM'ye aktarmanıza imkân tanır. Donanım tedarik etme, yazılım düzeltme eki uygulama, yüksek erişilebilirlik ve yedeklemeler gibi zaman alan yönetim görevlerinizi otomatikleştiren, tam olarak yönetilen bir hizmettir. CloudHSM, peşin maliyet olmaksızın isteğe bağlı bir biçimde HSM kapasitesini artırıp azaltarak hızla ölçeklendirmenize de imkân tanır.

## 10.10. AWS Directory Service
![93](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/6840544d-2245-4fb3-a7e7-f12f7feee6d6)

AWS Managed Microsoft Active Directory (AD) olarak da bilinen Microsoft Active Directory için AWS Directory Service, dizin bilgilerini kullanan iş yüklerinizin ve AWS kaynaklarınızın AWS’de yönetilen Active Directory'i (AD) kullanmasına imkân tanır. AWS Managed Microsoft AD, Microsoft AD'nin kendisi temel alınarak oluşturulmuştur ve mevcut Active Directory'nizdeki verileri bulutla eşitlemenizi ya da buluta çoğaltmanızı gerektirmez. Standart AD yönetim araçlarını kullanabilir, Grup İlkesi ve tek oturum açma gibi yerleşik AD özelliklerinden yararlanabilirsiniz. AWS Managed Microsoft AD ile Amazon EC2 ve Amazon RDS for SQL Server bulut sunucularını kolayca etki alanınıza katabilir ve AWS End User Computing (EUC) hizmetlerini (Amazon WorkSpaces gibi) AD kullanıcıları ve gruplarıyla kullanabilirsiniz.

## 10.11. AWS Firewall Manager
![94](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e11925e2-77e4-4993-8c31-6a4e0b43303f)

AWS Güvenlik Duvarı Yöneticisi, AWS Organizations’taki hesaplarınız ve uygulamalarınız genelinde güvenlik duvarı kurallarını merkezi olarak yapılandırmanıza ve yönetmenize olanak tanıyan bir güvenlik yönetimi hizmetidir. Yeni uygulamalar oluşturuldukça, AWS Firewall Manager, ortak bir güvenlik kuralları kümesi uygulayarak yeni uygulamaları ve kaynakları uyumluluğa getirmeyi kolaylaştırır. Artık, merkezi bir yönetici hesabından güvenlik duvarı kuralları oluşturmak, güvenlik ilkeleri oluşturmak ve bunları tüm altyapınız genelinde tutarlı, hiyerarşik bir şekilde uygulamak için tek bir hizmetiniz var. 

AWS Firewall Manager'ı kullanarak Application Load Balancer'larınız, API Gateway'leriniz ve Amazon CloudFront dağıtımlarınız için AWS WAF kurallarını kolayca kullanıma sunabilirsiniz. Application Load Balancer'larınız, ELB Classic Load Balancer'larınız, Elastic IP Adresleriniz ve CloudFront dağıtımlarınız için AWS Shield Advanced korumaları oluşturabilirsiniz. Ayrıca yeni Amazon Virtual Private Cloud (VPC) güvenlik gruplarını yapılandırabilir ve Amazon EC2, Application Load Balancer (ALB) ve ENI kaynak türleriniz için mevcut VPC güvenlik gruplarını denetleyebilirsiniz. AWS Web Application Firewall kuruluşunuzdaki hesaplar ve VPC'ler arasında dağıtabilirsiniz. Son olarak, AWS Güvenlik Duvarı Yöneticisi ile VPC'lerinizi Amazon Route 53 çözümleyicileri DNS güvenlik duvarı kurallarıyla da ilişkilendirebilirsiniz

## 10.12. AWS Identity and Access Management (IAM)
![95](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/1eacb745-2949-411b-9f76-da3a98621952)

AWS Identity and Access Management (IAM), tüm AWS genelinde ayrıntılı erişim denetimi sağlar. IAM ile kimlerin hangi hizmet ve kaynaklara hangi koşullarda erişebileceğini belirleyebilirsiniz. IAM politikalarıyla, en az ayrıcalıklı izinleri sunmak için iş gücünüze ve sistemlerinize ilişkin izinleri yönetmenizi sağlar.

## 10.13. AWS Key Management Service (AWS KMS)
![96](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/592884a3-ff5b-4041-8954-5bdd09b4232d)

AWS Key Management Service (AWS KMS), birçok AWS hizmetinde ve uygulamalarınızda şifreleme anahtarları oluşturup yönetmenizi ve bunların kullanımını denetlemenizi kolaylaştırır. AWS KMS, anahtarlarınızı korumak için FIPS 140-2 kapsamında doğrulanmış veya doğrulanma sürecinde olan donanım güvenlik modüllerini kullanan güvenli ve dayanıklı bir hizmettir. AWS KMS, düzenleme ve mevzuat uyumluluğu gereksinimlerinizi karşılamanıza yardımcı olmak amacıyla tüm anahtar kullanımlarının günlüklerini sağlamak için AWS CloudTrail ile entegredir.

## 10.14. AWS Network Firewall
![97](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/4191bfcd-b705-492d-9303-71b3fd5a71db)

AWS Ağ Güvenlik Duvarı, tüm Amazon Sanal Özel Bulutlarınız (VPC'ler) için temel ağ korumalarını dağıtmayı kolaylaştıran yönetilen bir hizmettir. Hizmet yalnızca birkaç tıklamayla kurulabilir ve ağ trafiğinize göre otomatik olarak ölçeklenebilir, böylece herhangi bir altyapıyı dağıtma ve yönetme konusunda endişelenmenize gerek kalmaz. AWS Ağ Güvenlik Duvarı'nın esnek kural motoru, kötü amaçlı etkinliklerin yayılmasını önlemek için giden sunucu ileti bloğu (SMB) isteklerini engellemek gibi ağ trafiği üzerinde size ayrıntılı denetim sağlayan güvenlik duvarı kuralları tanımlamanıza olanak tanır. Ayrıca, ortak açık kaynak kural biçimlerinde önceden yazdığınız kuralları içe aktarabilir ve AWS iş ortakları tarafından sağlanan yönetilen zekâ akışlarıyla entegrasyonları etkinleştirebilirsiniz. AWS Ağ Network Firewall, AWS Ağ Güvenlik Duvarı kurallarına dayalı politikalar oluşturabilmeniz ve ardından bu ilkeleri VPC'leriniz ve hesaplarınız arasında merkezi olarak uygulayabilmeniz için AWS Güvenlik Duvarı Yöneticisi ile birlikte çalışır. 

AWS Ağ Güvenlik Duvarı, yaygın ağ tehditlerine karşı koruma sağlayan özellikler içerir. AWS Ağ Güvenlik Duvarı'nın durum bilgisi olan güvenlik duvarı, VPC'lerinizin yetkisiz bir protokol kullanarak etki alanlarına erişmesini önleme gibi ilkeleri uygulamak için bağlantıları izleme ve protokol tanımlama gibi trafik akışlarından gelen bağlamı içerebilir. AWS Network Firewall’in izinsiz giriş önleme sistemi (IPS), imza tabanlı algılamayı kullanarak güvenlik açığından yararlanma durumlarını belirleyebilmeniz ve engelleyebilmeniz için aktif trafik akışı denetimi sağlar. AWS Network Firewall, kötü olduğu bilinen URL'lere giden trafiği durdurabilen ve tam nitelikli etki alanı adlarını izleyebilen web filtrelemesi de sunar.

## 10.15. AWS Resource Access Manager
![98](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/522cde30-7f0e-47e2-b7d4-d9cee58feac9)

AWS Resource Access Manager (RAM); kaynaklarınızı AWS hesapları, kuruluşunuz veya AWS Organizations'ta yer alan kuruluş birimleriniz (OU) genelinde, desteklenen kaynak türleri için IAM rolleri ve IAM kullanıcıları ile güvenli şekilde paylaşmanıza yardımcı olur. Transit gateway'ler, alt ağlar, AWS License Manager lisans yapılandırmaları, Amazon Route 53 Resolver kuralları ve diğer kaynak türlerini paylaşmak için AWS RAM'i kullanabilirsiniz. 

Birçok kuruluş, idari yalıtım veya faturalama yalıtımı oluşturmak ve hataların etkisini sınırlandırmak için birden çok hesap kullanmaktadır. AWS RAM sayesinde, birden fazla AWS hesabında yinelenen kaynaklar oluşturmanız gerekmez. Bu, sahip olduğunuz hesapların her birinde kaynak yönetmenin operasyonel iş yükünü azaltır. Bunun yerine, birden çok hesaplı ortamınızda bir kaynağı bir kez oluşturabilir ve sonrasında kaynak paylaşımı oluşturarak, bu kaynağı hesaplar arasında paylaşmak için AWS RAM'ii kullanabilirsiniz. Bir kaynak paylaşımı oluşturduğunuzda paylaşılacak kaynakları seçer, her kaynak türü için AWS RAM tarafından yönetilen izinleri belirler ve kaynaklara kimlerin erişmesini istediğinizi tayin edersiniz. AWS RAM ücretsiz olarak sunulur.

## 10.16. AWS Secrets Manager
![99](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/20ad78e4-56e2-479d-aff8-e818d6848020)

AWS Secrets Manager uygulamalarınıza, hizmetlerinize ve BT kaynaklarınıza erişmek için gerekli olan gizli dizileri korumanıza yardımcı olur. Hizmet veri tabanı kimlik bilgilerini, API anahtarlarını ve diğer gizli dizileri yaşam döngüleri boyunca kolayca rotasyona sokmanızı, yönetmenizi ve almanızı sağlar. Kullanıcılar ve uygulamalar gizli dizileri Secrets Manager API'lerine yaptıkları çağrıyla aldığından, hassas bilgileri düz metin halinde kodlamanıza gerek kalmaz. Secrets Manager; Amazon RDS, Amazon Redshift ve Amazon DocumentDB için sağladığı yerleşik entegrasyon sayesinde gizli dizi rotasyon özellikleri sunar. Hizmet, API anahtarları ve OAuth belirteçleri gibi diğer gizli dizi türleri için de kullanılacak şekilde genişletilebilir. Secrets Manager buna ek olarak AWS Cloud’daki, üçüncü taraf hizmetlerdeki ve şirket içindeki kaynaklar için tek bir merkezden ayrıntılı izin ve denetim gizli dizisi rotasyon özelliklerini kullanarak gizli dizi erişimini denetlemenizi sağlar.

## 10.17. AWS Security Hub
![100](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/50c3e9a1-294e-40a0-9a9b-1a15d8f636e6)

En iyi güvenlik uygulamalarından sapmaları tek tıklamayla tespit edebilirsiniz. Güvenlik bulgularını AWS ve çözüm ortağı hizmetlerinden standartlaştırılmış veri biçiminde otomatik olarak toplar. Ortalama çözüm süresini otomatik müdahale ve düzeltme eylemleriyle hızlandırır.

## 10.18. AWS Shield
![101](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/69ed7123-a310-402a-a2fc-1aae1d14e151)

AWS Shield, AWS üzerinde çalışan uygulamaları koruyan bir yönetilen Dağıtılmış Hizmet Engelleme (DDoS) koruması hizmetidir. AWS Shield tarafından sunulan, uygulama kesinti ve gecikme süresini en aza indiren her zaman açık algılama ve otomatik satır içi risk azaltma özellikleri sayesinde DDoS korumasından yararlanmak için AWS Support ekibine ulaşmanıza gerek kalmaz. AWS Shield'in Standard ve Advanced olmak üzere iki katmanı vardır. 

Tüm AWS müşterileri, ek ücret ödemeden AWS Shield Standard'ın otomatik koruma özelliklerinden yararlanabilir. AWS Shield Standard, web sitenizi ve uygulamalarınızı hedefleyen en yaygın, en sık karşılaşılan ağ ve aktarım katmanı DDoS saldırılarına karşı savunma sağlar. AWS Shield Standard hizmetini Amazon CloudFront ve Amazon Route 53 ile birlikte kullandığınızda bilinen tüm altyapı (3. ve 4. katman) saldırılarına karşı geniş kapsamlı erişilebilirlik korumasına sahip olursunuz. 

Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator ve Amazon Route 53 kaynakları üzerinde çalışan uygulamalarınızı hedef alan saldırılara karşı daha üst düzey koruma sağlamak için AWS Shield Advanced çözümüne abone olabilirsiniz. AWS Shield Advanced, Standard katmanla gelen ağ ve aktarım katmanı korumalarına ek olarak büyük çaplı ve sofistike DDoS saldırılarına karşı ek algılama ve risk azaltma özellikleri, saldırılar için neredeyse gerçek zamanlı görünürlük ve web uygulamalarına yönelik bir güvenlik duvarı olan AWS WAF ile entegrasyon olanağı sunar. AWS Shield Advanced ayrıca AWS Shield Response Team (SRT) ekibine 7/24 erişimin yanı sıra Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator ve Amazon Route 53 ücretlerinizdeki DDoS kaynaklı ani artışlara karşı koruma sağlar. 

AWS Shield Advanced tüm Amazon CloudFront, AWS Global Accelerator ve Amazon Route 53 uç konumlarında genel kullanıma sunulmuştur. Uygulamanızın önünde Amazon CloudFront'u dağıtarak dünyanın herhangi bir yerinde barındırılan web uygulamalarınızı koruyabilirsiniz. Kaynak sunucularınız Amazon Simple Storage Service (S3), Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB) veya AWS dışındaki özel bir sunucu olabilir. İsterseniz AWS Shield Advanced çözümünü şu AWS bölgelerinde Elastic Load Balancing veya Amazon EC2 üzerinde doğrudan etkinleştirebilirsiniz: Kuzey Virginia, Ohio, Oregon, Kuzey California, Montreal, Sao Paulo, İrlanda, Frankfurt, Londra, Paris, Stockholm, Singapur, Tokyo, Sidney, Seul, Mumbai, Milan ve Cape Town.

## 10.19. AWS Single Sign-On
![102](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f5817442-e379-407b-a9f1-f12ebe4a751f)

AWS Single Sign-On (AWS SSO), AWS'de iş gücü kimliklerinizi bir kez oluşturduğunuz veya bağladığınız ve AWS kuruluşunuz genelinde erişimi merkezi olarak yönettiğiniz yerdir. Yalnızca AWS hesaplarınıza veya bulut uygulamalarınıza erişimi yönetmeyi seçebilirsiniz. Kullanıcı kimliklerini doğrudan AWS SSO'da oluşturabilir veya bunları Microsoft Active Directory'nizden veya Okta Universal Directory veya Azure AD gibi standartlara dayalı bir kimlik sağlayıcıdan getirebilirsiniz. AWS SSO ile ayrıntılı erişim tanımlamak, özelleştirmek ve atamak için birleşik bir yönetim deneyimi elde edersiniz. İş gücü kullanıcılarınız; kendilerine atanan tüm AWS hesaplarına, Amazon EC2 Windows bulut sunucularına veya bulut uygulamalarına erişmek için bir kullanıcı portalına sahip olur. AWS SSO, AWS IAM aracılığıyla AWS hesap erişim yönetimiyle birlikte çalışacak veya bunun yerini alacak şekilde esnek bir şekilde yapılandırılabilir

## 10.20. AWS WAF – Web Uygulaması Güvenlik Duvarı
![103](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e352627b-cf08-42b2-8ce8-5029c6b29aa3)

AWS WAF, web uygulamalarınızı veya API'lerinizi erişilebilirliği etkileyebilecek, güvenliği tehlikeye atabilecek veya aşırı kaynak kullanabilecek yaygın web açıklarına ve botlara karşı korumanıza yardımcı olan bir web uygulaması güvenlik duvarıdır. AWS WAF, bot trafiğini kontrol eden ve SQL ekleme veya siteler arası betik oluşturma gibi yaygın saldırı modellerini engelleyen güvenlik kuralları oluşturmanızı mümkün kılarak trafiğin uygulamalarınıza nasıl ulaştığını kontrol etmenizi sağlar. Ayrıca, belirli trafik modellerini filtreleyen kuralları da özelleştirebilirsiniz. OWASP 10 önemli güvenlik riski ve aşırı kaynak tüketen, ölçümlerde dengesizlik yaratan ya da kesinti süresine neden olabilen otomatik botlar gibi sorunlara yönelmek için AWS ya da AWS Marketplace Satıcıları tarafından yönetilen bir önceden yapılandırılmış kurallar seti olan Managed rules for AWS Web Application Firewall’i kullanarak hızlıca başlayabilirsiniz. Yeni sorunlar ortaya çıktıkça bu kurallar düzenli olarak güncellenmektedir. AWS WAF; güvenlik kuralları oluşturma, dağıtma ve bunların bakımını yapma işlemlerini otomatikleştirmek için kullanabileceğiniz tam özellikli bir API içerir. 

REST API'leriniz için EC2, Amazon API Gateway veya GraphQL API'leriniz için AWS AppSync'ta çalışan web sunucularınızı veya kaynak sunucularınızı yöneten Application Load Balancer olan CDN çözümünüzün bir parçası olarak Amazon CloudFront'ta AWS WAF dağıtabilirsiniz. AWS WAF ile sadece kullandıklarınız için ödeme yaparsınız ve fiyatlandırma, dağıttığınız kural ve uygulamanızın aldığı web isteği sayısına göre belirlenir.
