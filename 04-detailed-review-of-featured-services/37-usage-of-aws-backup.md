# 38. AWS Backup
![303](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e9673ffc-8fbb-45cc-8d1f-036865669a84)

Verileri AWS hizmetleri ve hibrit iş yükleri genelinde tek bir merkezden ve otomatik olarak korumak için AWS Backup'ı kullanabilirsiniz. AWS Backup, uygun ölçekte veri korumayı daha da kolaylaştıran uygun maliyetli, tam olarak yönetilen, politikalara dayalı bir hizmet sunar. AWS Backup, veri korumaya yönelik mevzuata uygunluğunuzu veya iş politikalarınızı destekleme konusunda da size yardımcı olur. AWS Organizations'ta, yedekleme etkinliğini şirketinizin AWS hesapları ve kaynakları genelinde yapılandırmak, yönetmek ve idare etmek amacıyla veri koruma politikalarını merkezi olarak dağıtmak için AWS Backup'ı kullanabilirsiniz. Desteklenen kaynaklar şunları içerir:

- Amazon Elastic Compute Cloud (Amazon EC2) Bulut Sunucuları
- Amazon EC2 üzerinde Windows Volume Shadow Copy Service (VSS) destekli uygulamalar (Windows Server, Microsoft SQL Server ve Microsoft Exchange Server dahil)
- Amazon Elastic Block Store (Amazon EBS) birimleri 
- Amazon Simple Storage Service (Amazon S3) klasörleri 210 
- Amazon Relational Database Service (Amazon RDS) veritabanları (Amazon Aurora kümeleri dahil) 
- Amazon DynamoDB tabloları
- Amazon Neptune veritabanları
- Amazon DocumentDB (MongoDB uyumlu) veritabanları 
- Amazon Elastic File System (Amazon EFS) dosya sistemleri 
- Amazon FSx for NetApp ONTAP dosya sistemleri 
- Amazon FSx for Lustre dosya sistemleri 
- Amazon FSx for Windows File Server dosya sistemleri 
- Amazon FSx for OpenZFS dosya sistemleri 
- AWS Storage Gateway birimleri 
- Amazon Outposts ve VMware CloudTM on AWS'de şirket içi VMware iş yükleri

Özetle; AWS halihazırda zaten EC2, RDS, EBS gibi servislerde snapshot üzerinden back-up alınabiliyordu. Bu servisle birlikte tüm bu back-up’ların tek bir merkezden yönetilmesi amaçlanmaktadır. Bu servislerin back-up alma işlemleri hala kendi kontrol panelleri altında bulunmaktadır. Bu servis temelde tüm yedekleme ve geri yükleme araçlarını bir nokta üzerinden izlemenizi ve yönetmenizi amaçlar.
