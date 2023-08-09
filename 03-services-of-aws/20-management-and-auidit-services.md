# 21. Yönetim & Yönetişim (Denetim) Servisleri
## 21.1. Amazon CloudWatch
![183](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/37b50565-3a7f-4f87-bdc6-caede41ef561)

AWS kaynaklarınızın ve uygulamalarınızın AWS’de ve şirket içinde gözlemlenebilirliğini sağlayan AWS servisidir. 

Amazon CloudWatch; DevOps mühendisleri, geliştiriciler, saha güvenilirliği mühendisleri (SRE'ler), BT yöneticileri ve ürün sahipleri için geliştirilmiş bir izleme ve gözlemlenebilirlik hizmetidir. CloudWatch; uygulamalarınızı izlemenize, sistem genelindeki performans değişikliklerine müdahalede bulunmanıza ve kaynak kullanımını optimize etmenize yarayan veriler ve eyleme dönüştürülebilir öngörüler sağlar. CloudWatch, izleme verilerini ve operasyonel verileri günlükler, ölçümler ve olaylar biçiminde toplar. Operasyonel durum hakkında birleşik bir görünüme sahip olur, AWS'de ve şirket içinde çalışan AWS kaynaklarınız, uygulamalarınız ve hizmetleriniz için tam görünürlük elde edersiniz. CloudWatch'u kullanarak ortamlarınızdaki anormal davranışları algılayabilir, alarmlar kurabilir, günlükleri ve ölçümleri yan yana görselleştirebilir, otomatik eylemler gerçekleştirebilir, sorunları giderebilir ve uygulamalarınızı sorunsuz şekilde çalıştırmak için öngörüler edinebilirsiniz.

## 21.2. Amazon Managed Grafana
![184](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/33bfd41c-827a-4363-a596-50edf1d3ec38)

Operasyonel ölçümleriniz, günlükleriniz ve izlemeleriniz için ölçeklenebilir, güvenli ve yüksek düzeyde kullanılabilir veri görselleştirme servisidir. 

Amazon Managed Grafana, Grafana Labs ile iş birliği içinde geliştirilen açık kaynaklı Grafana için tam olarak yönetilen bir hizmettir. Grafana, nerede depolanırlarsa depolansınlar, ölçümlerinizi sorgulamanıza, görselleştirmenize, anlamanıza ve bunlar üzerinde uyarı işlemleri gerçekleştirmenize olanak tanıyan popüler bir açık kaynaklı analiz platformudur. 

Amazon Managed Grafana sayesinde, sunucu tedarik etmek, yazılım yapılandırmak ve güncellemek veya üretimde Grafana'yı güvende tutma ve ölçeklendirme ile ilgili ağır işleri yapmak zorunda kalmadan ölçümlerinizi, günlüklerinizi ve izlemelerinizi analiz edebilirsiniz. Gözlemlenebilirlik panoları oluşturabilir, keşfedebilir ve bunları ekibinizle paylaşabilir; Grafana altyapınızı yönetmek için daha az, uygulamalarınızın durumunu, performansını ve kullanılabilirliğini iyileştirmek için daha fazla zaman harcayabilirsiniz. Amazon Managed Grafana'yı, Amazon Managed Service for Prometheus, Amazon CloudWatch ve Amazon Elasticsearch Service gibi AWS veri kaynakları, Datadog ve Splunk gibi üçüncü taraf ISV'ler ve InfluxDB gibi kendi kendini yöneten veri kaynakları dahil olmak üzere gözlemlenebilirlik yığınınızdaki birden çok veri kaynağına bağlayın. Amazon Managed Grafana, AWS konsolunda birkaç tıklamayla birden fazla hesap ve bölge genelinde AWS verilerinizi güvenli bir şekilde ekleyebilmeniz, sorgulayabilmeniz, görselleştirebilmeniz ve analiz edebilmeniz için AWS hizmetleriyle yerel olarak entegre olur.

## 21.3. Amazon Managed Service for Prometheus
![185](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/8de1848b-9cfa-4a0d-a92b-200d980ce07d)

Container'larınız için yüksek oranda erişilebilir, güvenli ve yönetilen izleme sağlayan AWS servisidir. 

Amazon Managed Service for Prometheus, container içeren uygulamaları ve altyapıyı büyük ölçekte izlemeyi kolaylaştıran Prometheus uyumlu bir izleme ve uyarı hizmetidir. Cloud Native Computing Foundation'ın Prometheus projesi, container ortamları için optimize edilmiş popüler bir açık kaynak izleme ve uyarı çözümüdür. Amazon Managed Service for Prometheus ile, temel altyapıyı ölçeklendirmek ve çalıştırmak zorunda kalmadan container içeren iş yüklerinin performansını izlemek ve bunlar üzerinde uyarı işlemleri gerçekleştirmek için açık kaynaklı Prometheus sorgu dilini (PromQL) kullanabilirsiniz. Amazon Managed Service for Prometheus, iş yükleri büyüdükçe veya küçüldükçe operasyonel ölçümlerin alınmasını, depolanmasını, sorgulanmasını ve bunlar üzerinde uyarı işlemleri yürütülmesini otomatik olarak ölçeklendirir, verilere hızlı ve güvenli erişim sağlamak için AWS güvenlik hizmetleriyle entegre olur. Hizmet, Amazon Elastic Kubernetes Service (Amazon EKS), Amazon Elastic Container Service (Amazon ECS) ve AWS Distro for OpenTelemetry ile entegredir.

## 21.4. AWS Chatbot
![186](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/927a12a9-458b-4468-b0b9-9981b6f2b9cf)

AWS Chatbot, sohbet kanallarınızdaki AWS iş yüklerinizi izlemeyi, çalıştırmayı ve bunlarla ilgili sorunları gidermeyi kolaylaştıran etkileşimli bir aracıdır. AWS Chatbot ile uyarılar alabilir, tanılama bilgilerini almak için komutlar çalıştırabilir, AWS kaynaklarını yapılandırabilir ve iş akışlarını başlatabilirsiniz. Yalnızca birkaç tıklamayla, AWS bildirimleri alabilir ve AWS Command Line Interface (CLI) komutlarını sohbet kanallarınızdan güvenli ve verimli bir şekilde çalıştırabilirsiniz. AWS Chatbot, AWS hizmetleri ile Slack kanallarınız veya Amazon Chime sohbet odaları arasındaki entegrasyon ve güvenlik izinlerini yönetir. AWS Chatbot, ekibinizin güncel kalmasını, iş birliği yapmasını ve AWS ortamınızda çalışan uygulamalar için olaylara, güvenlik bulgularına ve diğer uyarılara hızla yanıt vermesini kolaylaştırır. Ekibiniz, bağlamı diğer AWS yönetim araçlarına geçirmeden AWS kaynaklarını güvenli bir şekilde yapılandırmak, olayları çözmek ve Slack kanallarından görevleri çalıştırmak için komutlar çalıştırabilir.

## 21.5. AWS CloudFormation
![187](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/d64f6cd5-321f-493b-97ba-365996646644)

Kod olarak altyapı ile bulut tedarikini hızlandırmanızı sağlayan AWS servisidir. Altyapınızı dünya çapında ölçeklendirebilir ve tüm AWS hesaplarındaki ve bölgelerindeki kaynakları tek bir operasyonla yönetmenizi sağlar. 

Altyapınızı CloudFormation Registry, geliştirici topluluğu ve kitaplığınızda yayınlanan bulut kaynaklarını içerecek şekilde genişletebilir ve yönetebilirsiniz. Kullanıma hazır uygulama dağıtımı ve yönetişim denetimleri sunan AWS hizmet entegrasyonlarıyla kuruluşunuzdaki kaynak yönetimini otomatikleştirir.

## 21.6. AWS CloudTrail
![188](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/06a817ee-b637-4058-b5a1-43062ada7cac)

Kullanıcı etkinliklerini ve API kullanımını izlemenizi sağlayan AWS servisidir. SOC, PCI ve HIPAA gibi düzenlemelere uygunluğu kanıtlamak için CloudTrail günlüklerini kullanarak kuruluşunuzu cezalardan koruyabilirsiniz. Amazon EventBridge ile kullanıcı etkinliğini ve olaylarını kaydederek güvenlik duruşunuzu iyileştirebilir ve otomatik iş akışı kuralları ayarlayabilirsiniz. AWS bölgeleri (region) ve hesaplar genelinde kullanıcı etkinliğini ve API kullanımını merkezi olarak kontrol edilen tek bir platformda yakalayıp ve birleştirebilirsiniz.

## 21.7. AWS Config
![189](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/658584ea-873d-46b8-a953-dc1e28ab007e)

AWS kaynaklarınızın yapılandırmalarını kaydedin ve değerlendirmenizi sağlayan AWS servisidir. AWS Config, AWS kaynaklarınızın yapılandırmalarını incelemenizi, denetlemenizi ve değerlendirmenizi sağlayan bir hizmettir. Config, devamlı olarak AWS kaynak yapılandırmalarınızı izler ve kaydeder; kayıtlı yapılandırmaları istenen yapılandırmalara göre değerlendirmenizi otomatikleştirmenizi sağlar. Config ile AWS kaynakları arasındaki ilişki ve yapılandırmalardaki değişiklikleri inceleyebilir, ayrıntılı kaynak yapılandırması geçmişlerine bakabilir ve dahili yönergelerinizde belirtilen yapılandırmalara göre genel uyumluluğunuzu belirleyebilirsiniz. Bu sayede mevzuat uyumluluğu denetimi, güvenlik analizi, değişiklik yönetimi ve operasyonel sorun gidermeyi daha basit hale getirebilirsiniz.

## 21.8. AWS Control Tower
![190](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/20e08d56-00d8-4cc2-b05f-fe1aa87bd1d6)

Güvenli ve çok hesaplı bir AWS ortamı oluşturmanın ve yönetmenin en kolay yolu olarak sunulan AWS servisidir. Birden fazla AWS hesabınız veya ekibiniz varsa bulut kurulumu ve yönetişimi, karmaşık ve zaman alıcı olabilir, hızlandırmak istediğiniz yenilik sürecini yavaşlatabilir. AWS Control Tower, “landing zone” adında güvenli ve çok hesaplı bir AWS ortamı oluşturup yönetmenin en kolay yolunu sunar. AWS Organizations'ı kullanarak landing zone'unuzu oluşturur ve hem buluta geçiş yapan binlerce müşteriyle çalışan AWS'nin deneyimine dayalı en iyi hayata geçirme uygulamalarını hem de sürekli hesap yönetimini ve yönetişimi beraberinde getirir. Siz hesaplarınızın şirket politikalarına uygun olmasının verdiği gönül rahatlığını yaşarken geliştiriciler birkaç tıklamayla yeni AWS hesapları tedarik edebilir. Yönetişimi yeni ya da mevcut hesapları kapsayacak şekilde genişletin ve bunların uygunluk durumları hakkında hızlıca görünürlük elde edin. Yeni bir AWS ortamı oluşturuyorsanız, AWS yolculuğunuza çıkıyorsanız ya da yeni bir bulut girişimi başlatıyorsanız AWS Control Tower, yerleşik yönetişim ve en iyi uygulamalarla hızlı bir başlangıç yapmanıza yardımcı olacaktır.

## 21.9. AWS Distro for OpenTelemetry
![191](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/710d79da-1cad-4b3c-8389-ef85218d3f6f)

Tahmin edilebilir performansa sahip, güvenli, üretime hazır, açık kaynaklı dağıtım servisidir. AWS Distro for OpenTelemetry; OpenTelemetry projesinin güvenli, üretime hazır, AWS destekli bir dağıtımıdır. Cloud Native Computing Foundation’ın bir parçası olan OpenTelemetry, uygulama izleme amacıyla kullanılabilecek dağıtılmış izleri ve ölçümleri toplamak için açık kaynaklı API’ler, kitaplıklar ve aracılar sağlar. AWS Distro for OpenTelemetry sayesinde uygulamalarınızı yalnızca bir kez kullanarak birden çok AWS ve çözüm ortağı izleme çözümüne ilişkili ölçümler ve izler gönderebilirsiniz. Kodunuzu değiştirmeden iz toplamak için otomatik kurma aracılarını kullanın. AWS Distro for OpenTelemetry ayrıca AWS kaynaklarınızdan ve yönetilen hizmetlerinizden meta veriler toplayarak size uygulama performansı verilerini temel altyapı verileriyle ilişkilendirme ve ortalama sorun çözme süresini kısaltma imkânı sunar. Amazon Elastic Compute Cloud (EC2), Amazon Elastic Container Service (ECS), EC2 üzerinde Amazon Elastic Kubernetes Service (EKS), AWS Fargate ve AWS Lambda üzerinde ve ayrıca yerinde çalışan uygulamalarınızı kurmak için AWS Distro for OpenTelemetry’yi kullanın.

## 21.10. AWS Launch Wizard
![192](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/3e94f611-9b71-4ce8-8ade-65e45d5bb9e8)

AWS'de üçüncü taraf uygulamalarını kolayca boyutlandırma, yapılandırma ve dağıtma hizmeti sunan servistir. 

AWS Başlatma Sihirbazı, Microsoft SQL Server Always On ve HANA tabanlı SAP sistemleri gibi üçüncü taraf uygulamalar için AWS kaynaklarını tek tek AWS kaynaklarını manuel olarak belirlemeye ve sağlamaya gerek kalmadan boyutlandırma, yapılandırma ve dağıtmanın rehberli bir yolunu sunar. Başlamak için, hizmet konsolunda performans, düğüm sayısı ve bağlantı dahil olmak üzere uygulama gereksinimlerinizi girersiniz. Başlatma Sihirbazı, uygulamanızı dağıtmak ve çalıştırmak için EC2 bulut sunucuları ve EBS birimleri gibi doğru AWS kaynaklarını tanımlar. Başlatma Sihirbazı, tahmini bir dağıtım maliyeti sağlar ve güncellenmiş bir maliyet değerlendirmesini anında görüntülemek için kaynaklarınızı değiştirmenize olanak tanır. AWS kaynaklarını onayladığınızda, Başlatma Sihirbazı, tam işlevli, üretime hazır bir uygulama oluşturmak için seçilen kaynakları otomatik olarak sağlar ve yapılandırır. 

AWS Başlatma Sihirbazı, sonraki dağıtımları hızlandırmak için temel olarak hizmet edebilecek CloudFormation şablonları da oluşturur. Başlatma Sihirbazı ek ücret ödemeden kullanılabilir. Yalnızca çözümünüzü çalıştırmak için sağlanan AWS kaynakları için ödeme yaparsınız.

## 21.11. AWS License Manager
![193](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/5967acb6-99eb-4219-8bd2-65b5f6a0aaf8)

Yazılım lisansı kullanımını yönetmek, keşfetmek ve raporlamak için kurallar belirleyebileceğiniz AWS servisidir. 

AWS License Manager, AWS ve şirket içi ortamlarda Microsoft, SAP, Oracle ve IBM gibi satıcılardan alınan yazılım lisanslarını yönetmenizi kolaylaştırır. AWS License Manager yöneticilerin, lisans sözleşmelerinin koşullarını yansıtan özelleştirilmiş lisans kuralları oluşturmasına olanak tanır. Yöneticiler bu kuralları kullanarak, bir sözleşmede belirtilenden daha fazla lisans kullanma gibi lisans ihlallerini önlemeye yardımcı olabilir. AWS License Manager'daki kurallar, bulut sunucusunun başlatılmasını durdurarak veya yöneticileri ihlal hakkında bilgilendirerek lisans ihlalini önlemeye yardımcı olur. Yöneticiler, AWS License Manager panosu sayesinde tüm lisanslarının kontrolünü ele alarak hepsini kolayca görebilir; uygunsuzluk, hatalı raporlama ve fazla lisans kullanımından kaynaklanan ek maliyetlerle karşı karşıya kalma riskini azaltır. Bağımsız yazılım satıcıları (ISV'ler) da AWS License Manager'ı kullanarak lisansları kolayca dağıtabilir ve takip edebilir. 

AWS License Manager, Amazon EC2 Tahsis Edilmiş Ana Sunucular gerektiren yazılım lisanslarınızın yönetimini de basitleştirir. Yöneticiler, AWS License Manager'da ana sunucu tahsisi ve ana sunucu kapasite kullanımı için Tahsis Edilmiş Ana Sunucu yönetimi tercihlerini belirleyebilir. Kurulumun ardından, bu idari işleri AWS License Manager'ın üstlenmesi sayesinde, tıpkı AWS'nin sağladığı lisanslarla EC2 bulut sunucusu başlatırken yaptığınız gibi bulut sunucularını sorunsuzca başlatabilirsiniz. 

AWS License Manager ek bir ücret olmadan sunulur. Yalnızca uygulamalarınızı çalıştırmak için kullandığınız AWS kaynakları için ödeme yaparsınız. Lisanslarınızı yönetmeye başlamak için AWS License Manager konsolunu ziyaret edin.

## 21.12. AWS Managed Services
![194](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f7a14494-5856-497f-96e4-06d29f5e1e76)

AWS alt yapınızı sizin adınıza işleten servistir. AWS Managed Services (AMS), AWS altyapınızı daha verimli ve güvenli bir şekilde çalıştırmanıza yardımcı olur. AWS hizmetlerinden ve büyüyen bir otomasyon, yapılandırma ve çalıştırma kitaplığından yararlanan AMS, hem yeni hem de mevcut AWS ortamlarında operasyonel yeteneklerinizi artırabilir ve optimize edebilir. Müşteriler ister yeni başlıyor ister bir veri merkezini taşıyor veya bulutta optimize edilmiş çözümler oluşturuyor olsun, devam eden operasyonel mükemmellik, bulutta başarının kritik bir bileşenidir. AMS, kısa vadeli hızlandırıcı veya uzun vadeli bir çözüm olarak bulut operasyonları becerilerinizi ve deneyiminizi artırmanıza yardımcı olabilir; uygulamalarınızı ve işinizi bulutta dönüştürmeye odaklanmanızı sağlar. AMS size operasyonel esneklik sağlar, güvenliği ve uyumluluğu artırır ve kapasiteyi optimize etmenize ve belirlenen maliyet tasarrufları için harekete geçmenize yardımcı olur. AMS, hem geleneksel hem de modernize edilmiş iş yükleri için dedektif korkuluklar, izleme, güvenlik ve olay yönetimi en iyi uygulamalarından yararlanarak tüm AWS filonuz için tutarlı bir işletim modeli sağlar.

## 21.13. AWS Management Console
![195](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/8969f03d-9c01-4e86-b596-0ad0ec083386)

AWS Cloud'a erişmek ve yönetmek için ihtiyaç duyduğunuz her şey tek bir web arabiriminde bulunur.

## 21.14. AWS Console Mobile Application
![196](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/db35ebc8-f1e6-4a70-a10e-56d8cb6290b5)

Hareket halindeyken AWS kaynaklarınıza bağlı kalmanızı sağlayan AWS servisidir. Amazon Web Services'ın sunduğu AWS Console Mobile Application, hareket halindeyken vaka yanıtı desteği sağlamak için belirli bir kaynak kümesini görüntülemenize ve yönetmenize olanak tanır. 

Console Mobile Application, tahsis edilmiş bir pano üzerinden kaynakları izlemenizi ve belirli AWS hizmetlerine yönelik yapılandırma ayrıntılarını, ölçümleri ve alarmları görüntülemenizi sağlar. Pano, izin verilen kullanıcılara Amazon CloudWatch ve AWS Health Dashboard'un yanı sıra AWS Faturalama ve Maliyet Yönetimi üzerindeki gerçek zamanlı verilerle birlikte hesap durumuna ilişkin genel bir bakış sunar. Devam eden sorunları görüntüleyebilir ve hem grafikleri hem de yapılandırma seçeneklerini içeren ayrıntılı bir görünüm için ilgili CloudWatch alarm ekranını takip edebilirsiniz. Ayrıca, belirli AWS hizmetlerinin durumunu kontrol edebilir, ayrıntılı kaynak ekranlarını görüntüleyebilir ve belirli eylemleri gerçekleştirebilirsiniz. 

Console Mobile Application'ı kullanmak için mevcut bir AWS hesabının bulunması gerekir. Kök Kullanıcı, IAM Kullanıcısı veya Birleştirilmiş Rol ile oturum açıldıktan sonra Console Mobile Application, kimlikler arasında kolayca geçiş yapabilmeniz için kimlik bilgilerinizi kaydeder. 

Düzenli olarak yeni özellikler içeren güncellemeler yayınlıyoruz. Konsol Mobil Uygulaması’nın Geri bildirim özelliği üzerinden, bize hangi özelliklere ihtiyaç duyduğunuzu ve bunları nasıl kullanacağınızı iletebilirsiniz. Size kulak veriyoruz.

## 21.15. AWS OpsWorks
![197](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/041fa3a0-5a87-4c5f-a68d-873a99e4f9c3)

Chef ve Puppet ile işlemlerinizi otomatikleştirmenizi sağlayan AWS servisidir. AWS OpsWorks, Chef ve Puppet'ın yönetilen bulut sunucularını sağlayan bir yapılandırma yönetimi hizmetidir. Chef ve Puppet, sunucularınızın yapılandırmalarını otomatikleştirmek için kod kullanmanızı sağlayan otomasyon platformlarıdır. OpsWorks, Chef ve Puppet'ı kullanarak sunucularınızın Amazon EC2 bulut sunucularınızda veya şirket içi bilişim ortamlarınızda yapılandırma, dağıtım ve yönetim biçimini otomatikleştirmenizi sağlar. OpsWorks üç teklife sahiptir: AWS Opsworks for Chef Automate, AWS OpsWorks for Puppet Enterprise ve AWS OpsWorks Stacks.

## 21.16. AWS Organizations
![198](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/a30676aa-a2a7-4822-8a7a-3c94b2a58259)

AWS kaynaklarınızı ölçeklendirirken ortamınızı merkezi olarak yönetebileceğiniz ve idare edebileceğiniz AWS servisidir. AWS Organizations, büyümeyle birlikte ortamlarınızı merkezi olarak yönetmenize ve idare etmenize ve AWS kaynaklarınızı ölçeklendirmenize yardımcı olur. AWS Organizations’ı kullanarak programlama yoluyla yeni AWS hesapları oluşturabilir ve kaynak ayırabilir, iş akışlarınızı düzenlemek için hesapları gruplandırabilir, yönetim amacıyla hesaplara veya gruplara politikalar uygulayabilir ve tüm hesaplarınız için tek bir ödeme yöntemi kullanarak faturalamayı basitleştirebilirsiniz. 

Ayrıca, AWS Organizations diğer AWS hizmetleriyle entegredir, bu nedenle merkezi yapılandırmaları, güvenlik mekanizmalarını, denetim gerekliliklerini ve kuruluşunuzda yer alan hesaplar arasındaki kaynak paylaşımını tanımlayabilirsiniz. AWS Organizations, herhangi bir ek ücret olmadan tüm AWS müşterileri tarafından kullanılabilir.

## 21.17. AWS Personal Health Dashboard
![199](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0056c5b0-f681-4ab0-99ba-f06ee8235538)

AWS ortamınızı etkileyen önemli olayları ve değişiklikleri görüntüleyen servistir. AWS Personal Health Dashboard, ortamınızı etkileyebilecek AWS olaylarına yönelik uyarılar ve rehberlik sağlar. Service Health Dashboard, AWS hizmetlerinin genel durumunu gösterirken Personal Health Dashboard, belirli AWS ortamınız hakkında proaktif ve şeffaf bildirimler sunar. 

Tüm AWS müşterileri Personal Health Dashboard'a erişebilir. Personal Health Dashboard, aktif olayları yönetmenize yardımcı olmak için son olayları gösterir ve programlanmış 85 etkinlikler için plan yapabilmeniz amacıyla proaktif bildirimler sağlar. AWS kaynaklarınızı etkileyebilecek değişiklikler hakkında bildirim almak için bu uyarıları kullanın ve ardından, sorunları belirleyip çözmek için kılavuzu takip edin.

## 21.18. AWS Proton
![200](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c7b0aa1a-8ee2-4a65-a8ca-72f7d2539b47)

Container dağıtımları ve sunucusuz dağıtımlar için container yönetimini otomatikleştiren AWS servisidir. Geliştiricilerin uygulamaları oluşturmasına ve dağıtmasına yardımcı olmak için, yönetilen ve onaylanmış yığınlarla korumalar ayarlamanızı sağlar. 

Tek bir arayüzde altyapı sağlama ve kod dağıtımıyla geliştirici üretkenliğini ve yeniliğini destekler. Kuruluşunuz genelinde tutarlı bir mimariyi kolayca sürdürmek için uygulamaları tek bir tıklamayla güncelleyebilirsiniz.

## 21.19. AWS Resilience Hub
![201](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/995014fa-f9ab-46dc-ac19-4e6d2a341709)

Uygulamalarınızı kesintilere karşı hazırlayan ve koruyan AWS servisidir. Kesintileri azaltmak için uygulama esnekliğini sürekli olarak doğrular ve izler. Dayanıklılık hedeflerini değerlendirir (Kurtarma Süresi Hedefi ve Kurtarma Noktası Hedefi). Sorunları üretimde ortaya çıkmadan önce tanımlayabilir ve çözer. Kurtarma maliyetlerini düşürürken iş sürekliliğini optimize eder.

## 21.20. AWS Service Catalog
![202](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/2c731272-a0d9-43da-8433-9d99c31f01c7)

AWS ürün kataloğunuzu oluşturmanıza, düzenlemenize ve yönetmenize yardımcı olan AWS servisidir. AWS Service Catalog, kurumların AWS'de kullanılması için onaylanmış olan BT hizmetlerinin kataloglarını oluşturmalarını ve yönetmelerini sağlar. Bu BT hizmetlerine sanal makine görüntüleri, sunucular, yazılımlar ve veri tabanlarından bütün çok katmanlı uygulama mimarilerine kadar her şey dâhildir. AWS Service Catalog dağıtılan BT hizmetlerini ve uygulamalarınızı, kaynaklarınızı ve meta verilerinizi merkezden yönetmenize olanak tanır. Bu durum süreçleri denetim altında tutmanıza ve mevzuat uyumluluğu gereksinimlerinizi karşılamanıza yardımcı olur ve kullanıcılarınızın yalnızca ihtiyaçları olan onaylı BT hizmetlerini hızlı bir şekilde dağıtmasını sağlar. AWS Service Catalog AppRegistry ile kuruluşlar AWS kaynaklarının uygulama içeriklerini anlayabilirler. Maliyet, performans, güvenlik, uygunluk ve operasyonel durumu uygulama düzeyinde takip etmek için uygulamalarınızı ve meta verilerini tanımlayıp yönetebilirsiniz.

## 21.21. AWS Systems Manager
![203](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/83726515-d1b4-4724-9088-b229f9f04e2f)

AWS kaynakları ve şirket içi kaynaklara yönelik operasyon öngörüleri edinmenizi sağlayan servistir. Bulutta, şirket içinde ve uç konumlarda görünürlüğü ve denetimi artırır. Operasyonel sorunları saptama ve çözme süresini kısaltır. Bulut sunucusunun düzeltme eki, yapılandırma ve özel politikanıza uygunluğunu korur. Uygulamalarınızın ve kaynaklarınızın yapılandırmasını ve sürekli yönetimini otomatikleştirir.

## 21.22. AWS Trusted Advisor
![204](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/4c1e6063-4484-4c01-96e9-304553f8f06e)

Maliyetleri azaltan, performansı ve güvenliği iyileştiren AWS servisidir. AWS Trusted Advisor, en iyi AWS uygulamalarını takip etmenize yardımcı olan öneriler sunar. Trusted Advisor, denetimler kullanarak hesabınızı değerlendirir. Bu denetimler, AWS altyapınızı optimize edecek, güvenliği ve performansı iyileştirecek, genel maliyetleri düşürecek ve hizmet sınırlarını izleyecek yollar belirler. Ardından, denetim önerilerini izleyerek hizmetlerinizi ve kaynaklarınızı optimize edebilirsiniz. 

AWS Basic Support ve AWS Developer Support müşterilerinin temel güvenlik denetimlerine ve hizmet sınırlarına ilişkin tüm denetimlere erişimi vardır. AWS Business Support ve AWS Enterprise Support müşterileri maliyet optimizasyonu, güvenlik, hata toleransı, performans ve hizmet sınırları dahil olmak üzere tüm denetimlere erişim sağlayabilmektedir.

## 21.23. AWS Well-Architected Tool
![205](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c2107eba-ad07-4095-84dd-0d5ee97fbfc2)

Mimarinizi gözden geçiren ve en iyi uygulamaları sizin için belirleyen AWS servisidir. AWS Well-Architected Tool, uygulamalarınızın ve iş yüklerinizin durumunu inceleyebilmeniz için tasarlanmıştır, ayrıca en iyi mimari uygulamalar ve rehberlik için merkezi bir yer sunar. AWS Well-Architected Tool, bulut mimarlarının güvenli, yüksek performanslı, dayanıklı ve verimli uygulama altyapıları oluşturmasına yardımcı olmak için geliştirilmiş AWS Well-Architected Framework'ü temel alır. Framework, AWS çözüm mimarları tarafından on binlerce iş yükü analizinde kullanılmıştır, bunun yanı sıra bulut mimarinizi değerlendirmek ve zamanla uygulama ihtiyaçlarınıza göre şekillenecek tasarımları hayata geçirmek için tutarlı bir yaklaşım sağlar. 

AWS Well-Architected Framework tarafından sunulan standart rehberliğin ve AWS tarafından geliştirilen lenslerin yanı sıra AWS Well-Architected Tool, özel lensler kullanarak spesifik en iyi uygulama rehberliği eklemenize olanak verir. Kuruluşunuzun en iyi uygulamaları vasıtasıyla kendi sorularınızı geliştirerek ve iş yüklerinizi değerlendirerek kendi sektörünüze özgü teknoloji ve yönetişim gerekliliklerine dayalı incelemeler yürütebilirsiniz. 

AWS Well-Architected Tool'u kullanmak için iş yükünüzü tanımlayın, AWS Well-Architected lenslerinden birini ya da kendi özel lensinizi kullanın ve incelemenize başlayın. Ardından araç, tanımlanmış en iyi uygulamalardan faydalanarak bulut için oluşturmanıza yardımcı olacak bir eylem planı sunar. AWS Well-Architected Tool, AWS Management Console'da ücretsiz olarak sunulur.

