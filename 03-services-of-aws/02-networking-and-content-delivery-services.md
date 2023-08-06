# 3. Ağ İletişimi ve İçerik Teslimi Servisleri
## 3.1. Amazon CloudFront
![26](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/7f8b1368-34c7-4782-b40f-1047759377b5)

Verileri, otomatik ağ eşleme ve akıllı yönlendirme içeren, küresel olarak dağıtılmış 310'dan fazla varlık noktası (PoP) aracılığıyla sunarak gecikme süresini azaltır. Trafik şifreleme ve erişim denetimleri ile güvenliği iyileştirir ve AWS Shield Standard'ı kullanarak hiçbir ilave ücret ödemeden DDoS saldırılarına karşı savunma sağlar. Birleştirilmiş istekler, özelleştirilebilir fiyatlandırma seçenekleri ve sıfır ücretle AWS kaynaklarından dışarı veri aktarımı ile maliyetleri azaltır. Maliyeti, performansı ve güvenliği dengelemek için sunuların işlem özelliklerini kullanarak AWS içerik teslim ağı (CDN) ucunda çalıştırılan kodu özelleştirme imkânı sunar.

## 3.2. Amazon Route 53
![27](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/26e23e1d-dcbf-4d24-845a-0e6e29cff0e2)

Amazon Route 53, yüksek oranda erişilebilir ve ölçeklenebilir bir bulut etki alanı adı sistemi (DNS) web hizmetidir. “www.example.com” gibi adları bilgisayarların birbirine bağlanmak için kullandığı 192.0.2.1 gibi sayısal IP adreslerine çevirerek geliştiricilerin ve işletmelerin son kullanıcıları internet uygulamalarına yönlendirmesi için son derece güvenilir ve uygun maliyetli bir yöntem sunacak şekilde tasarlanmıştır. Amazon Route 53, IPv6 ile de tam olarak uyumludur. 

Amazon Route 53, kullanıcı isteklerini Amazon EC2 bulut sunucuları, Elastic Load Balancing yük dengeleyicileri veya Amazon S3 klasörleri gibi AWS'de çalışan altyapılara etkili bir şekilde bağlar ve kullanıcıları AWS dışındaki altyapılara yönlendirmek için de kullanılabilir. Amazon Route 53'ü kullanarak DNS durum denetimlerini yapılandırabilir ve ardından Route 53 uygulama kurtarma denetleyicisi ile uygulamanızın hatalardan kurtarma özelliğini sürekli olarak izleyebilir ve uygulama kurtarma işlemini kontrol edebilirsiniz. Amazon Route 53 trafik akışı, trafiği gecikme süresi tabanlı yönlendirme, coğrafi DNS, coğrafi yakınlık ve ağırlıklı gidiş-dönüş dahil olmak üzere çeşitli yönlendirme türleri üzerinden yönetmenizi kolaylaştırır. Bunların tümü, çeşitli düşük gecikme süreli, hataya dayanıklı mimariler oluşturulabilmesi için DNS yük devretme ile birleştirilebilir. 

Amazon Route 53 trafik akışının basit görsel düzenleyicisini kullanarak son kullanıcılarınızın tek bir AWS bölgesinde ya da dünyanın farklı yerlerinde olmasından bağımsız olarak uygulamalarınızın uç noktalarına nasıl yönlendirildiğini kolayca yönetebilirsiniz. Amazon Route 53 ayrıca etki alanı adı kaydı da sunar. “example.com” gibi etki alanı adları satın alıp yönetebilirsiniz ve Amazon Route 53, etki alanlarınızın DNS ayarlarını otomatik olarak yapılandırır.

## 3.3. Amazon Virtual Private Cloud – VPC (Sanal Özel Bulut)
![28](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ca26124e-c186-4793-85df-b640ced64b00)

Bağlantıları koruma altına almanızı ve izlemenizi sağlar, trafiği tarar ve sanal ağdaki bulut sunucularına erişimi kısıtlayabilir. Sanal ağı oluşturmak, yönetmek ve doğrulamak için daha az zaman harcamanızı hedefler. Kendi IP adresi aralığınızı seçerek, alt ağlar oluşturarak ve yol tablolarını yapılandırarak sanal ağınızı özelleştirebilirsiniz.

## 3.4. AWS App Mesh
![29](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/1967c27d-c518-47e8-9c1b-44f4c6e87b5b)

AWS App Mesh; hizmetlerinizin, birden çok türdeki işlem altyapısı üzerinde birbiriyle iletişim kurmasını kolaylaştırmak için uygulama düzeyinde ağ iletişimi sağlayan bir hizmet ağıdır. App Mesh, uygulamalarınız için uçtan uca görünürlük ve yüksek düzeyde erişilebilirlik sağlar. 

Modern uygulamalar genellikle birden fazla hizmetten oluşur. Her bir hizmet; Amazon EC2, Amazon ECS, Amazon EKS ve AWS Fargate gibi birden çok türde işlem altyapısı kullanılarak oluşturulabilir. Bir uygulamadaki hizmet sayısı arttıkça hataların yerini tam olarak tespit etmek, hatalardan sonra trafiği yeniden yönlendirmek ve kod değişikliklerini güvenli bir şekilde dağıtmak zorlaşır. Önceden bunun için izleme ve denetim mantığını doğrudan kodunuzda oluşturmanız ve her değişiklikte hizmetinizi yeniden dağıtmanız gerekiyordu. 

AWS App Mesh, tutarlı görünürlük ve ağ trafiği denetimleri sağlayarak, ayrıca güvenli hizmetler sunmanıza yardımcı olarak hizmetleri çalıştırmayı kolaylaştırır. App Mesh, izleme verilerinin nasıl toplandığını veya trafiğin hizmetler arasında nasıl yönlendirildiğini değiştirmek için uygulama kodunu güncelleme ihtiyacını ortadan kaldırır. App Mesh, her hizmeti izleme verilerini dışarı aktaracak şekilde yapılandırır ve uygulamanız genelinde tutarlı iletişim denetim mantığı uygular. 

App Mesh'i AWS Fargate, Amazon EC2, Amazon ECS, Amazon EKS ve AWS'de çalışan Kubernetes ile kullanarak uygulamanızı geniş ölçekte daha iyi çalıştırabilirsiniz. App Mesh, şirket içinde çalışan uygulamalarınız için de AWS Outposts ile entegre olur. App Mesh, açık kaynaklı Envoy proxy'sini kullandığından, çok çeşitli AWS çözüm ortağı araçları ve açık kaynaklı araçlar ile uyumludur.

## 3.5. AWS Cloud Map
![30](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f4ac6d1f-30bf-473a-a970-2c01088d1913)

AWS Cloud Map bir bulut kaynak keşfi hizmetidir. Cloud Map ile uygulama kaynaklarınız için özel adlar belirleyebilir ve dinamik olarak değişen bu kaynakların güncel konumlarını saklayabilirsiniz. Bu, web hizmetiniz daima kaynakların en güncel konumlarını keşfedeceği için uygulamanızın erişilebilirliğini artırır. 

Modern uygulamalar genel olarak bir API üzerinden erişilebilir olan ve belirli bir işlevi yerine getiren çeşitli hizmetlerden oluşur. Her bir hizmet; veri tabanları, kuyruklar, nesne depoları ve müşteri tarafından belirlenen mikro hizmetler gibi çeşitli başka kaynaklarla etkileşime girer. İşlevini yerine getirebilmek için bağımlı olduğu bütün altyapı kaynaklarının yerini bulabilmeye ihtiyaç duyar. Pek çok durumda, bütün bu kaynak adlarını ve konumlarını manuel olarak uygulama kodu içinde yönetirsiniz. Öte yandan manuel kaynak yönetimi, bağımlı altyapı kaynaklarının sayısı arttıkça ya da mikro hizmetlerin sayısı trafiğe bağlı olarak dinamik bir şekilde arttıkça/azaldıkça zaman alan ve hataya yatkın bir sürece dönüşür. Üçüncü taraf hizmet keşif ürünlerini de kullanabilirsiniz ancak bunlar için ek yazılım ve altyapı yükleyip yönetmeniz gerekir. 

Cloud Map; veri tabanları, kuyruklar, mikro hizmetler ve başka bulut kaynakları gibi uygulama kaynaklarını özel adlarla kaydedebilmenizi sağlar. Cloud Map, konumun güncel olduğundan emin olmak için sürekli olarak kaynakların durumunu kontrol eder. Daha sonra uygulama, uygulama sürümüne ve dağıtım ortamına dayalı olarak ihtiyaç duyulan kaynakların konumu için kayıt defterini sorgulayabilir.

## 3.6. AWS Cloud WAN
![31](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/fa13fbd2-fe1c-4905-b36d-8ada2422a3b8)

Karmaşıklığı azaltmak için AWS ve şirket içi ağlarınızı birleştirebilirsiniz. Hassas ağ trafiğini günlük verilerden izole etmek için ağı bölümlere ayırarak güvenliği artırabilir. Tüm ağınızı tek bir gösterge panosunda (dashboard) görüntüleyebilmenizi sağlar. Konumlarınızı ve kaynaklarınızı birbirine bağlamak için AWS küresel ağını kullanır.

## 3.7. AWS Direct Connect
![32](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/7fa44609-26ff-43b8-99bd-79d4a6509530)

AWS'ye doğrudan bağlanarak ve genel interneti kullanmak zorunda kalmadan uygulama performansını artırabilirsiniz. Verilerinizi birden çok şifreleme seçeneğiyle ağınız ile AWS arasında taşırken verilerinizin güvenliğini sağlamış olursunuz. AWS'nin veri aktarımı için talep ettiği düşük ücretlerle ağ iletişimi maliyetlerinizi azaltır.

## 3.8. AWS Global Accelerator
![33](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/5c45dd71-4012-4c46-899f-01483e03c183)

AWS Global Accelerator, Amazon Web Services'in küresel ağ altyapısını kullanarak kullanıcı trafiğinizin performansını %60'a kadar artıran bir ağ hizmetidir. AWS Global Accelerator, internet tıkandığında paket kaybını, sapmayı ve gecikmeyi sürekli olarak düşük tutmak için uygulamanızın yolunu optimize eder. 

Global Accelerator ile, uygulamanız için sabit bir giriş noktası görevi gören ve kullanılabilirliği artıran iki global statik genel IP sağlanır. Arka uçta, kullanıcıya yönelik değişiklikler yapmadan Application Load Balancer, Network Load Balancer'lar, EC2 bulut sunucuları ve esnek IP'ler gibi AWS uygulama uç noktalarınızı ekleyin veya kaldırın. Global Accelerator, uç nokta hatasını azaltmak için trafiğinizi otomatik olarak iyi durumdaki en yakın uç noktanıza yeniden yönlendirir.

## 3.9. AWS Private 5G
![34](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e91722ea-9aad-4467-afea-8ba8cfd4e3cd)

Özel bir 5G ağının düşük gecikme süresi ve yüksek bant genişliği ile binlerce cihazı/makineyi birbirine bağlama imkânı sunmaktadır. Uzun planlama döngüleri, karmaşık entegrasyonlar ve otomatik kurulum olmadan ağınızı günler içinde kurup hemen sonrasında çalıştırabilirsiniz. Tüm bağlı cihazlar için mevcut bilişim teknoloji (BT) politikalarıyla bütünleşmiş ayrıntılı erişim kontrolleriyle ağınızı güvence altına alırsınız. Ağ kapasitenizi isteğe bağlı olarak ölçeklendirebilir veya birkaç tıklamayla cihaz ekleyip ve yalnızca kullandığınız kapasite ve aktarım hızı için ödeme yaparsınız.

## 3.10. AWS PrivateLink
![35](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f1c555b2-2208-430b-8ddd-7adc1de017c6)

AWS PrivateLink, trafiğinizi genel kullanıma yönelik internete açmadan VPC'ler, AWS hizmetleri ve şirket içi ağlarınız arasında özel bağlantı sağlar. AWS PrivateLink, farklı hesaplar ve VPC'ler üzerinden hizmetlere bağlanmanızı kolaylaştırarak ağ mimarinizi önemli ölçüde basitleştirir. 

AWS PrivateLink tarafından sağlanan VPC uç noktaları (end-points) arabirimi, AWS çözüm ortakları tarafından sunulan hizmetlere ve AWS Marketplace'te bulunan çözümlere erişmenize olanak tanır. AWS PrivateLink, Gateway Load Balancer uç noktalarını sağlayarak sanal ağ gereçleriniz için aynı düzeyde güvenlik ve performans sağlar veya özel trafik denetim mantığı sunar.

## 3.11. AWS Transit Gateway
![36](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/fbd3dfd1-23b9-450d-8ea4-1d34117d5b63)

AWS Transit Gateway, Amazon Virtual Private Cloud’larınızı (VPCs) ve yerinde ağlarınızı bir merkez aracılığıyla bağlar. Ağınızı basitleştirir ve karmaşık eşleme ilişkilerini sonlandırır. Bulut yönlendiricisi olarak çalışır, her bağlantı yalnızca bir kez yapılır. 

Siz küresel olarak genişledikçe, bölgeler arası eşleme AWS küresel ağını kullanarak AWS Transit Gateway’leri bağlar. Verileriniz otomatik olarak şifrelenir ve asla herkese açık internette dolaşıma girmez. Ayrıca merkezi konumundan dolayı AWS Transit Gateway Network Manager, yazılım tabanlı geniş alan ağı (SD-WAN) cihazlarına bağlanırken bile ağınızın tamamı üzerinde benzersiz bir görüşe sahiptir.

## 3.12. AWS VPN
![37](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/3016f832-421f-4a65-be55-535be11d0d07)

AWS VPN (Sanal Özel Ağ) çözümleri, şirket içi ağlarınız, uzak ofisleriniz, istemci cihazlarınız ve AWS küresel ağı arasında güvenli bağlantılar kurar. AWS VPN iki hizmetten oluşur: AWS Siteden Siteye (Site-to-Site) VPN ve AWS Client VPN. Her hizmet, ağ trafiğinizi korumak için yüksek düzeyde kullanılabilir, yönetilen ve esnek bir bulut VPN çözümü sağlar. AWS Siteden Siteye VPN, ağınız ile Amazon Virtual Private Cloud'larınız veya AWS Transit Gateway'leriniz arasında şifreli tüneller oluşturur. AWS Client VPN, uzaktan erişimi yönetmek için bir VPN yazılım istemcisi kullanarak kullanıcılarınızı AWS'ye veya şirket içi kaynaklara bağlar.

## 3.13. Elastic Load Balancing (ELB)
![38](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c3ae023c-defe-4fb7-ae3a-e90b3242a76a)

Uygulamaların ölçeklenebilirliğini iyileştirmek için ağ trafiğini dağıtmanıza imkân sunar. Bütünleşmiş sertifika yönetimi, kullanıcı kimlik doğrulaması ve SSL/TLS şifre çözme ile uygulamalarınızın güvenliğini sağlayan hizmetleri sunar. Uygulamaları yüksek erişilebilirlik ve otomatik ölçeklendirme ile sunmanızı sağlar. Uygulamalarınızın durumunu ve performansını gerçek zamanlı olarak izleyebilir, sorunları ortaya çıkarın ve SLA uygunluğunu sürdürebilirsiniz

