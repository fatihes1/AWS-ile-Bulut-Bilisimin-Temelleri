# 25. AWS OpsWork
AWS OpsWorks, Chef ve Puppet'ın yönetilen bulut sunucularını sağlayan bir yapılandırma yönetimi hizmetidir. Chef ve Puppet, sunucularınızın yapılandırmalarını otomatikleştirmek için kod kullanmanızı sağlayan otomasyon platformlarıdır. OpsWorks, Chef ve Puppet'ı kullanarak sunucularınızın Amazon EC2 bulut sunucularınızda veya şirket içi bilişim ortamlarınızda yapılandırma, dağıtım ve yönetim biçimini otomatikleştirmenizi sağlar. 

Bir senaryo üzerinden servisi daha somut olarak anlamayı deneyelim. Bir web mağazası yönettiğimizi varsayalım. Ortamda; 6 tane front-end, 5 tane back-end ve 2 tane veri tabanı sunucusu bulunduğunu varsayalım. CloudFormation template ile bunun birkaç tık ile kurulacağından bahsetmiştik. Sunucular kurulduktan sonra;

- Nginix kurulumunun tamamlanması,
- Web uygulamasının sisteme yüklenmesi, 
- Web uygulamasının ilgili ayarlamalarının yapılması, 
-  Veri tabanı bağlantısı ayarlamalarının yapılması, 
- Ortam değişkenlerinin ayarlanması, 
- Gerekli diğer servislerin kurulması, 
- Gereksiz servislerin kapatılması, 
- Kullanılmayan portların kapatılması vb.

Sunucu konfigürasyonu birçok adımdan oluşan zahmetli bir iştir. Manuel yapılan işlemler hata yapılmasına zemin hazırlayabilir. En önemlisi ise aynı işi tekrar tekrar yapılması zaman kaybına yol açacaktır. Sektör bu soruna çözüm olarak “Configuration Management” araçları oluşturmuştur. Bu araçlar sayesinde tek bir merkezden otomatize etme imkânı tanınır. Bu araçlar sayesinde yukarıda sayılan manuel işler otomatize edilir. Altyapı kod haline getirilir. (Infrastructure as a Code) Sistemin belirtilen durumları reçete olarak tutulur. Sektörde popüler olan iki araç bulunmaktadır: CHEF ve PUPPET 

OpsWorks üç teklife sahiptir: AWS Opsworks for Chef Automate, AWS OpsWorks for Puppet Enterprise ve AWS OpsWorks Stacks.

## 25.1. AWS OpsWorks for Chef Automate
AWS OpsWorks for Chef Automate, yapılandırma yönetimi, mevzuat uyumluluğu, güvenlik ve sürekli dağıtım için Chef otomasyon araçlarından oluşan bir paket olan Chef Automate'i kullanan tam olarak yönetilen bir yapılandırma yönetimi hizmetidir. OpsWorks, Chef sunucunuzda otomatik olarak düzeltme eki uygulama, güncelleme ve yedekleme işlemlerini gerçekleştirerek sunucunuzun bakımını da yapar. OpsWorks, kendi yapılandırma yönetimi sistemlerinizi çalıştırma veya altyapısının bakımını yapma konusunda endişelenmemenizi sağlar. OpsWorks, yapılandırma ve mevzuat uyumluluğu yönetimi gibi tüm Chef Automate özelliklerine erişerek bu özellikleri Chef konsolundan veya Knife gibi komut satırı araçlarından yönetmenizi sağlar. Bu sistem ayrıca mevcut Chef tarif kitaplarınızla da sorunsuz bir şekilde çalışır.

## 25.2. AWS OpsWorks for Puppet Enterprise
AWS OpsWorks for Puppet Enterprise, Puppet tarafından sağlanan altyapı ve uygulama yönetimi otomasyon araçlarından oluşan Puppet Enterprise paketini barındıran tam olarak yönetilen yapılandırma yönetimi hizmetidir. OpsWorks, Puppet ana sunucunuzda otomatik olarak düzeltme eki uygulama, güncelleme ve yedekleme işlemlerini gerçekleştirerek sunucunuzun bakımını da yapar. OpsWorks, kendi yapılandırma yönetimi sistemlerinizi çalıştırma veya altyapısının bakımını yapma konusunda endişelenmemenizi sağlar. OpsWorks, Puppet konsolundan yönetilen tüm Puppet Enterprise özelliklerine erişim sağlar. Bu sistem ayrıca mevcut Puppet kodlarınızla da sorunsuz bir şekilde çalışır.

## 25.3. AWS OpsWorks Stacks
AWS OpsWorks Stacks bir uygulama ve sunucu yönetimi hizmetidir. OpsWorks Stacks ile uygulamanızı yük dengeleme, veri tabanı ve uygulama sunucusu gibi farklı katmanlardan oluşan bir yığın şeklinde modelleyebilirsiniz. Her bir katman içinde Amazon EC2 bulut sunucuları tedarik edebilir, otomatik ölçeklendirmeyi etkinleştirebilir ve bulut sunucularınızı Chef Solo kullanarak Chef tarifleriyle yapılandırabilirsiniz. Bu sayede paket yükleme, dilleri veya çerçeveleri programlama, yazılımları yapılandırma ve benzer birçok görevi otomatikleştirebilirsiniz.


