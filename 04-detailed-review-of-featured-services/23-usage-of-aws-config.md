# 24. AWS Config
AWS Config, AWS kaynaklarınızın yapılandırmalarını incelemenizi, denetlemenizi ve değerlendirmenizi sağlayan bir hizmettir. Config, devamlı olarak AWS kaynak yapılandırmalarınızı izler ve kaydeder; kayıtlı yapılandırmaları istenen yapılandırmalara göre değerlendirmenizi otomatikleştirmenizi sağlar. Config ile AWS kaynakları arasındaki ilişki ve yapılandırmalardaki değişiklikleri inceleyebilir, ayrıntılı kaynak yapılandırması geçmişlerine bakabilir ve dahili yönergelerinizde belirtilen yapılandırmalara göre genel uyumluluğunuzu belirleyebilirsiniz. Bu sayede mevzuat uyumluluğu denetimi, güvenlik analizi, değişiklik yönetimi ve operasyonel sorun gidermeyi daha basit hale getirebilirsiniz. 

AWS Config ile AWS kaynaklarınızın yapılandırma değişikliklerini sürekli izleme ve kaydetme imkânınız olur. Ayrıca, Config dilediğiniz zaman AWS kaynaklarınızın, bu kaynakların yapılandırmalarının ve EC2 bulut sunucuları içindeki yazılım yapılandırmalarının envanterini çıkarmanıza olanak tanır. Önceki bir duruma göre değişiklik algılandığında incelemeniz ve harekete geçmeniz için bir Amazon Simple Notification Service (SNS) bildirimi gönderilebilir.

![292](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/a431c790-85e8-4f55-b13c-7c6cfced43a0)

AWS Config, AWS kaynağı yapılandırmalarınızın kurumunuzun politikaları ve yönergeleriyle genel mevzuat uyumluluğu durumunu sürekli olarak denetlemenize ve değerlendirmenize imkân tanır. AWS Config, AWS kaynaklarını tedarik etmeye ve yapılandırmaya yönelik kurallar sağlama olanağı sunar. Bu kurallar bağımsız olarak sağlanabilir veya tek bir tıklamayla kuruluşunuzun tamamına dağıtılabilen bir paket (uyumluluk paketi olarak da bilinir) içinde uyumluluğu düzeltme eylemleriyle birleştirilmiş olabilir. Kurallarınızdan farklı olan kaynak yapılandırmaları veya yapılandırma değişiklikleri, sürekli olarak uyarı alabilmeniz için otomatik olarak Amazon Simple Notification Service (SNS) bildirimlerini ve Amazon CloudWatch events'i tetikler. Ayrıca, genel mevzuat uyumluluğu durumunuzu denetlemek ve mevzuata uyumlu olmayan kaynakları hızla tespit etmek için görsel panodan da yararlanabilirsiniz.

AWS Config ile kaynaklar arasındaki ilişkileri izleyebilir ve değişiklik yapmadan önce kaynak bağımlılıklarını inceleyebilirsiniz. Bir değişiklik gerçekleştiğinde kaynağın yapılandırma geçmişini hızla gözden geçirebilir ve geçmişteki herhangi bir noktada kaynağın yapılandırmasının nasıl göründüğünü öğrenebilirsiniz. Config, bir kaynak yapılandırmasında yapılan bir değişikliğin diğer kaynaklarınızı nasıl etkileyeceğini değerlendirmek için kullanabileceğiniz bilgiler sağlayarak değişiklikle ilgili olayların etkisinin en aza inmesini sağlar.

CloudTrail bölümünde, servis için kayıt defteri niteliğinde bir servis olduğundan bahsetmiştik. Config servisi ise ne işlem yapıldığını tutar. Farklı şöyle düşünebiliriz:

- CloudTrail: 
-- AWS hesabınızın yönetimini, uyumluluk, operasyonel denetim ve risk denetimini sağlayan biz hizmettir. CloudTrail ile, AWS altyapınızı kaydedebilir, sürekli izleyebilir ve koruyabilirsiniz.
-- CloudTrail servisi kayıtlarıyla “Kim?” sorusuna cevap verir. 
-- Operasyonel denetim ve risk denetimde kullanılabilir.

- AWS Config:
-- AWS kaynaklarınızın konfigürasyonlarını denetlemenizi ve değerlendirmenizi sağlayan bir hizmettir. Config, AWS kaynak konfigürasyonlarını sürekli olarak izler ve kaydeder. İstenen konfigürasyonların değerlendirmesini otomatikleştirir. 
-- Config servisi kayıtlarıyla, “Nasıl?” sorusunun cevabını verir. 
-- Bütünlük ve uyumluluk denetiminde kullanılabilir.

AWS Config, AWS kaynaklarının konfigürasyonlarını, gözlemenizi, denetlemenizi ve değerlendirmenizi sağlayan hizmettir. İki temel hizmet sunmaktadır:

- Devreye alındığı andan itibaren belirtilen kaynakları izler. Tüm konfigürasyon değişikliklerini not eder ve zaman çizelgesi içeren bir ekranda raporlar. Bir önceki gün sağlıklı çalışan bir servis bir sonraki gün çalışmıyor ise bu ekrandan inceleyerek sorunun neden oluştuğunu anlaşılabilir. ‒ 
- Uyumluluk kuralları yaratmaya imkân veren “Rules” hizmeti vardır. Config servisinin, bu uyumluluk kurallarına uyup uymadığını denetler. Örneğin, yaratılan tüm EBS volume’lerinin bir sanal makineye bağlı olma kuralı tanımlayıp kural dışına çıkıldığında bunu raporlaması sağlanır.

## 24.1. AWS Config Kullanımı
Öncelikle bu servisin çalışmasını simüle etmek için bir sanal makine oluşturalım. Bu iş için EC2 kontrol paneline gidelim ve “BaseAMI”ı kullanarak, t2.micro, varsayılan VPC de konuşlanan ve adı “AWSConfigDeneme” olan bir sanal makine oluşturalım. Güvenlik grubu olarak “Ec2-Sec-Group” seçilebilir. Sonrasında da bir tane Elastic IP oluşturalım ancak şu an için herhangi bir instance’a atamayalım. Sanal makine ve Elastic IP oluşturduktan sonra aşağıdaki adımları takip edebiliriz:

- AWS Config servisinin kontrol paneline ulaşalım ve “GetStarted” ile işlemlere başlayalım. 
- Kayıtları tüm kaynaklardan mı yoksa belirli bir kaynaktan mı çekmek istediğimizi belirtmemiz gerekiyor. Bu aşamada “Record all resources supported in this region” diyelim. Bir role seçebilir veya AWS’nin uygun bir rol oluşturmasına izin verebiliriz.“ Create AWS Config service-linked role” seçeneğini kullanarak yeni bir rol yaratmasını isteyelim. 
- Kayıtları nereye kaydetmemiz gerektiğini belirtmemiz gereken alanda “Create a bucket” diyerek yeni bir S3 bucket’ı oluşturmak istediğimizi belirtelim.
- “Stream configuration changes and notifications to an Amazon SNS topic” seçeneğini bu aşamada seçmemize gerek yok. 
- Diğer ayarları varsayılan olarak bırakarak “next” diyelim. 
- Karşımıza çıkan “AWS Managed Rules” ekranında arama çubuğuna “eip” yazalım ve “eip-attached” kuralını seçerek “next” diyelim.
- Son aşamada “Confirm” diyerek ilk konfigürasyonu (config) oluşturalım.

Bu aşamadan sonra oluşturulan config tüm kaynakları izleyecek ve bize raporlar oluşturacaktır. Normalde uzun süreçte oluşacak bazı aksiyonları arka arkaya yapıp bir nevi servisin kullanımını simüle edelim. Bu aşamada aşağıdaki adımları takip edebiliriz:

- EC2 kontrol paneline gidelim ve “AWSConfigDeneme” sanal makinesini durduralım. 
- EC2 kontrol paneli üzerinden sanal makinemizle aynı AZ’de bulunacak şekilde bir “volume” yaratalım. Actions’ı kullanarak bu volume’ü “AWSConfigDeneme” sanal makinesine bağlayalım. 
- EC2 kontrol paneli üzerinden adı “Deneme1” olan bir Network Interface oluşturalım. Auto assign IP, güvenlik grubu olarak varsayılan VPC güvenlik grubunu atayalım. Sonrasında ise bu interface’i “AWSConfigDeneme” sanal makinesine atayalım. 
- Instances ekranına geri dönerek sanal makineyi tekrar başlatalım. 
- Elastic IP’yi Action üzerinden az önce oluşturduğumuz “Deneme1” isimli Network Interface’e atayalım (bağlayalım). Sonrasında birkaç dakika sonra Elastic IP atamasını geri alalım.

AWS Config kontrol paneline döndüğümüzde bir saat içerisinde tüm kaynakların listelendiği görülecektir. EC2 Instances → AWSConfigDeneme sanal makinesinin ID değerine ait instance’ı seçelim. Configuration Timeline seçeneğinde verilen tutulduğunu ve bir zaman çizelgesi olarak raporlandığı görülecektir. 

Rules alt başlığında ise uyumsuzluk olduğunu belirtir. Çünkü oluşturulan Elastic IP herhangi bir sanal makine veya network interface’e bağlanmamış durumdadır. Böylelikle servis hakkında raporlarla ve kurallara sistemimiz ve kaynakların daha verimli kullanılması AWS Config servisi sayesinde sağlanmış olur.

