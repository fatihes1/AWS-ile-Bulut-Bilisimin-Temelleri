# 7. Amazon Elastic File System (EFS) Servisi Kullanımı
Amazon S3 başlığı altında, obje ve blok tabanlı iki çeşit depolama birimi olduğundan bahsetmiştik. EFS servisi üçüncü farklı bir depolama çeşidi değildir. EFS servisi temelinde block tabanlı bir disk yapılandırma servisidir. İşlemlerin arka planında EFS’yi oluşturan yapı ile EBS’i oluşturan yapı neredeyse aynıdır.

- EBS ile bir disk oluşturulur ve bu makineye disk olarak bağlanır, 
- EFS’te ise bir dosya sistemi oluşturulup makinedeki bir klasör veya noktaya bağlanarak kullanılır.

EC2’de bir sanal makineye atanan EBS tabanlı disk dolarsa veya yetersiz kalırsa manuel olarak disk boyutunun arttırılabildiğini önceki başlıklarda incelemiştik. EBS’in ilk sıkıntısı bu durumdur. Her gereksinim olduğunda manuel olarak yeni bir blok tabanlı disk oluşturmak zorunda kalırız. EBS ve diğer tüm blok tabanlı disk yapıları ortam sanal olsa bile spesifik bir boyutta oluşturulup, gereksinime göre genişletmeler manuel olarak yapılmalıdır. EBS tabanlı disklerin diğer bir kısıttı ise belirli bir zamanda sadece tek bir makineye atanabilir. Yani EBS tabanlı bir disk aynı andan birden fazla makineye atanamaz. EFS bu sorunlara çözüm olmak amacıyla üretilen depolama servisidir. 

EFS, EBS gibi belirli bir değer verilerek yaratılıp, manuel olarak genişletilmesi gereken bir depolama birimi değildir. Ne kadar dosya atılır ise sistem o kadar büyür, dosyaların silinmesi durumunda da sistem aynı şekilde küçülecektir.

EFS’ler, istenilen sayıda EC2 sanal makinesine ve yerel sunucuya aynı anda bağlı olabilir. EFS’in kullanımı bir senaryo üzerinden anlatmak gerekirse; önceki başlıklarda bir web sayfasını yüksek erişilebilirlik için birden fazla sanal makinede çalıştırmıştık. Bu yöntem teoride iyi olsa da web sayfasını güncellememiz gereken bir durumda nasıl bir aksiyon almamız gerekir? Tüm sanal makinelerde aynı güncelleme işlemi tek tek yapılmalıdır. Bu yorucu ve külfetli işlem yerine, web sayfasının tüm kaynak kodlarını tek bir yerde tutup, tüm sanal makinelerin bu depolanan alana erişmesini sağlamak çok daha verimli bir çözüm yöntemidir. Bu çözüm için Amazon, EFS’i kullanıcılarına sunmaktadır. 

EFS, bir disk değildir. Bu yüzden herhangi bir makineye bağlayıp üzerine işletim sistemi kurulamaz. Temelde ağ dosya sistemi (network file system) tabanlı bir dosya deposudur.

## 7.1. Amazon Elastic File System (EFS) Detayları
Bir EFS oluşturmadan önce EC2 kontrol paneline ulaşalım. Bu başlığın ilerleyen kısmında EFS üzerinden bir dosya sistemi kuracağız. Oluşturulan EFS’i bir güvenlik grubuna atayarak, bu güvenlik grubu sayesinde EC2 makinenin dosya sistemine erişimini sağlamış olacağız. 

Network & security başlığı altında, güvenlik grupları seçeneğine tıklayarak yeni bir tane oluşturmaya başlanır.

- İsim olarak “MountTarget” diyelim. 
- Açıklama kısmına ise “EFS mount target” diyerek devam edebiliriz. 
- Inbound kurallarda NFS seçilir, IP değeri belirtilen kaynak (source) alanında ise aramaya “ec2” yazılır ve çıkan seçeneklerden “Ec2-Security-Group” seçeneği kullanılır. 
- Şu ana kadar source alanına hep bir IP adresi yazarken bu aşamada bir güvenlik grubu seçtik. Bunun sebebi ise Ec2-Sec-Group, güvenlik grubuna dahil olanların oluşturulacak olan EFS’e erişebilmesini tanımlamak içindir.
- Servislerden EFS kontrol paneline erişilir ve yeni bir EFS oluşturulmaya başlanır. 
- AWS tarafından tanımlı gelen varsayılan VPC de devam edilir.  
- Erişilebilirlik olarak “regional” seçilerek bulunan region içerisinde bulunan tüm AZ’lerden erişilmesi sağlanır. Böylelikle bir AZ’de sorun çıksa bile diğer AZ’ler sayesinde veri kaybı yaşanmaz. Tüm AZ’lerde bulunan varsayılan güvenlik grubunu kaldırıp az önce oluşturduğumuz güvenlik grubunu tüm AZ’lere bağlayalım. 
- Lifecycle managment alanı Amazon S3 servisinde olduğu gibi dosyaların belirli zaman diliminde az erişilmesi halinde bulunduğu katmanı değiştirmeye dayanan bir sistemdir.
- Performans olarak “General Purpose” seçilmesi bu aşamada gayet yeterli olacaktır. Max I/O saniye başına çok daha fazla verim (throughput) sunar. 
- Verim modu olarak “bursting” seçeneği ile devam edelim. 
- Network Access adımında erişilebilirliği “regional” seçtiğimiz için üç AZ için de güvenlik grubu tanımlaması yapılmış olarak gelir. 
- AWS’nin yakın yıllarda sunduğu dosya sistemi poliçeleri vardır. Bu poliçeler gibi Amazon S3 servisindeki gibi, sadece okuma, sadece yazma gibi erişim kısıtlamaları tanımlanabilir. 
- Bir EFS oluşturma işleminin sonunda açılan sayfa da Amazon tarafından EFS’nin bir sanal makineye nasıl bağlanacağı hakkında talimatları çıkacaktır. Bu adımları izleyerek bağlama işlemi yapılabilir.

EFS’i sanal makinelere bağlamak için öncelikle EC2 kontrol paneline giderek iki adet sanal makine oluşturalım. Daha önceden oluşturulmuş olan sanal makineler “Auto Scaling” sırasında kullanıldığı için sıfırdan yenilerini oluşturmak bu kılavuz doğrultusunda daha sorunsuz olacaktır. Kılavuzun önceki başlıklarında oluşturulan baseAMI’ı kullanarak iki adet yeni sanal makine oluşturalım ve isimlerini “firstVM” ve “secondVM” olarak ayarlayalım. Sonrasında aşağıdaki işlemleri kullanarak bağlantıyı sağlayalım:

- PuTTY aracını kullanarak firstVM isimli sanal makineye bağlanalım. 
- ``sudo su`` komutu ile yetkilendirmeyi edinelim. 
- ``sudo yum install -y amazon-efs-utils``, komutu ile EFS gereksinimlerini temin edelim. 
- EFS’nin bir dizine/dosyaya (folder) bağlanması gereklidir. Bu yüzden ilk olarak ``mkdir efs`` komutu ile efs adında bir dizin oluşturalım. 
- Sonrasında ``sudo mount -t efs efs`` komutu ile EFS’i oluşturulan dizine bağlayalım. 
- ``cd efs`` komutu ile dizine ulaşalım ve sonrasında ``nano deneme.txt`` komutu ile bir dosya oluşturup içerisinde birkaç satır metin girelim. Metin girme işleminden sonra ``CTRL + X`` ve sonrasında ``Y`` ile kaydedip çıkalım. 
- EFS’e birden fazla sanal makine bağlantı sağlayabilir. Bunun için diğer sanal makineye PuTTY aracı ile bağlanalım ve sonrasında bu dizine de ``sudo mkdir efs`` komutu ile “efs” adında bir dizin oluşturalım. 
- Dizin oluşturulduktan sonra ``sudo mount -t efs <EFS_DNS_DEĞERİ>`` efs komutu ile bu dizini de EFS’e bağlayalım.
- ``cd efs`` komutu ile dizine girdikten sonra ``ls`` komutu ile dosyaları listelediğimizde diğer sanal makine tarafından oluşturulmuş olan dosya ve içerik erişilebilir olarak görünecektir.

Bu işlemler sonucunda bir EFS dosya sistemi birden fazla sanal makine tarafından erişilmiş olacaktır

