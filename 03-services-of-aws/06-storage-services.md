# 7. Depolama Servisler
## 7.1 Amazon Elastic Block Store (EBS)
![52](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/69ced4eb-6347-410e-8a16-26700d68a6d8)

SAP, Oracle ve Microsoft ürünleri gibi görev açısından kritik uygulamalar dahil olmak üzere birçok zorlu, yüksek performans gerektiren iş yükü için hızlı bir şekilde ölçeklendirir. Erişilebilirlik alanında (AZ'ler) replikasyon dahil %99,999 erişilebilirlik ve io2 “Block Express” birimleriyle %99,999 dayanıklılık ile hatalara karşı koruma sağlar. İş yükünüze en uygun depolama alanını seçebilirsiniz. Birimler, GB başına dolar maliyetinden en hızlı IOPS ve aktarım hızı ile yüksek performansa kadar değişkenlik gösterir.

## 7.2. Amazon Elastic File System (EFS)
![53](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/620379ee-43f3-4e13-8fa0-1b060a5ec7c3)

AWS işlem hizmetleri için paylaşılan dosya sistemlerini basit ve hızlı bir şekilde oluşturup yapılandırabilirsiniz. Tedarik, dağıtım, düzeltme eki uygulama veya bakım gerekmez. Dosyalar eklendikçe, kaldırıldıkça dosya sisteminizi otomatik olarak ölçeklendirir ve gerektiğinde daha yüksek aktarım hızı seviyelerine çıkarır. Yalnızca kullandığınız depolama alanı için ödeme yaparsınız ve sık erişilmeyen dosyaları otomatik olarak taşıyarak maliyetleri %92'ye kadar azaltır. %99,999999999 (11 adet 9) dayanıklılık ve %99,99'a (4 adet 9) kadar erişilebilirlik için tasarlanmış, tam olarak yönetilen dosya sistemiyle dosyalarınıza güvenli ve güvenilir bir şekilde erişirsiniz.

## 7.3. Amazon FSx
![54](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/6289a943-cf03-4428-b2cd-d217935adc60)

Amazon FSx, bulutta zengin özelliklere sahip, yüksek performanslı dosya sistemlerini başlatmayı, çalıştırmayı ve ölçeklendirmeyi kolay ve uygun maliyetli hale getirir. Güvenilirliği, güvenliği, ölçeklenebilirliği ve geniş yetenekleriyle çok çeşitli iş yüklerini destekler. Amazon FSx, yüksek performans ve daha düşük TCO sağlamak için en son AWS bilgi işlem, ağ iletişimi ve disk teknolojileri üzerine kurulmuştur. Tam olarak yönetilen bir hizmet olarak, donanım sağlama, düzeltme eki oluşturma ve yedekleme işlemlerini gerçekleştirerek uygulamalarınıza, son kullanıcılarınıza ve işinize odaklanmanızı sağlar. Yaygın olarak kullanılan dört dosya sistemi arasından seçim yapabilirsiniz: NetApp ONTAP, OpenZFS, Windows Dosya Sunucusu ve Lustre.

## 7.4. Amazon S3 Glacier
![55](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/341d1648-00de-4132-9961-fef9c63a1c8a)

Veri arşivleme için amaca özel olarak tasarlanan Amazon S3 Glacier depolama sınıfları en yüksek performansı, veri alımında en fazla esnekliği ve bulutta arşiv depolama için en düşük maliyeti sunar. Tüm S3 Glacier depolama sınıfları neredeyse sınırsız ölçeklenebilirlik sağlar ve %99,999999999 (11 adet dokuz) oranında veri dayanıklılığı hedefiyle tasarlanmıştır. S3 Glacier depolama sınıfları, arşiv verilerinize en hızlı erişim ve bulutta en düşük maliyetli arşiv depolama imkânı veren seçenekler sunar.

## 7.5. Amazon Simple Storage Service (S3)
![56](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0a5b57ca-51fd-496a-8066-890e606effd6)

Amazon S3, her yerden ve her boyutta veriyi almak için oluşturula nesne depolama alanıdır. Amazon Simple Storage Service (Amazon S3); sektör lideri ölçeklenebilirlik, veri erişilebilirliği, güvenlik ve performans sunan bir nesne depolama hizmetidir. Her büyüklükteki ve her sektörden müşteriler istedikleri miktarda veriyi data-lake, bulut temelli ve mobil uygulamalar gibi neredeyse her türlü kullanım örneği için depolayıp koruyabilir.

## 7.6. AWS Backup
![57](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/53454376-c32b-47bd-bd2d-a19a99bcb85d)

AWS Backup, verileri AWS hizmetleri ve hibrit iş yükleri genelinde tek bir merkezden ve otomatik olarak korumanızı sağlar. AWS Backup, uygun ölçekte veri korumayı daha da kolaylaştıran uygun maliyetli, tam olarak yönetilen, politikalara dayalı bir hizmet sunar. AWS Backup, veri korumaya yönelik mevzuata uygunluğunuzu veya iş politikalarınızı destekleme konusunda da size yardımcı olur. AWS Organizations ile birlikte AWS Backup, kuruluşunuzun AWS hesapları ve kaynakları genelinde yedekleme işlemlerinizi yapılandırmak, yönetmek ve kontrol etmek için veri koruma politikalarını tek bir merkezden dağıtmanızı sağlar. Kaynaklar arasında Amazon Elastic Compute Cloud (Amazon EC2) bulut sunucuları, Amazon Elastic Block Store (Amazon EBS) birimleri, Amazon Simple Storage Service (Amazon S3) klasörleri, Amazon Relational Database Service (Amazon RDS) veri tabanları (Amazon Aurora kümeleri dahil), Amazon DynamoDB tabloları, Amazon Neptune veri tabanları, Amazon DocumentDB (MongoDB uyumluluğuyla) veri tabanları, Amazon Elastic File System (Amazon EFS) dosya sistemleri, Amazon FSx for Lustre dosya sistemleri, Amazon FSx for Windows File Server dosya sistemleri ve AWS Storage Gateway birimleri ile şirket içinde ve VMware CloudTM on AWS'de yer alan VMware iş yükleri yer alır.

## 7.7. AWS Snow Family
![58](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/a5c8348a-42ed-4e4a-bf9b-9716ea82025c)

Uygulamalar günümüzde, hiç olmadığı kadar hızlı bir şekilde buluta taşınıyor. Yeni bir uygulama kategorisi, bulut uç konumunda, hatta ağ uç konumunun da ötesinde daha fazla özellik ve performans gerektirmektedir. 

AWS; akıllı, gerçek zamanlı duyarlılık sağlamak ve aktarılan veri miktarını daha etkin hale getirmek amacıyla veri işleme ve analiz süreçlerini, verinin oluşturulduğu konuma gerektiğince yaklaştıran uç altyapısı ve yazılımı sağlar. Bu, AWS tarafından yönetilen donanım ve yazılımın AWS bölgeleri (region) dışındaki konumlara ve hatta AWS Outposts'un dışında dağıtılmasını içerir. 

AWS Snow Family; basit, veri merkezi bulunmayan ortamlarda ve tutarlı bir ağ bağlantısının olmadığı yerlerde operasyonları yürütmeye ihtiyaç duyan müşterilere yardımcı olur. AWS Snowcone, AWS Snowball ve AWS Snowmobile'dan oluşan Snow Ailesi, çoğu yerleşik işlem özelliklerine sahip bir dizi fiziksel cihaz ve kapasite noktası sunar. Bu hizmetler, eksabayt düzeyine kadar veriyi AWS'nin içine ve dışına fiziksel olarak aktarmaya yardımcı olur. Snow Family cihazları, AWS'ye aittir ve AWS tarafından yönetilir, ayrıca AWS güvenlik, izleme, depolama yönetimi ve işlem özellikleriyle entegre olur.

## 7.8. AWS Storage Gateway
![59](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/cb585d0b-8ed8-4fb6-9181-fd4bb56f897f)

Neredeyse sınırsız bulut depolama alanına erişim ile şirket için uygulamalar oluşturmanızı sağlar. AWS'nin buluttaki çeviklik, ekonomi ve güvenlik özelliklerinden yararlanırken şirket içi uygulamalara düşük gecikme süreli veri erişimi sağlar. Kullanıcı ve uygulama iş akışlarını sürdürerek işinizde kesinti olmadan şirket içi uygulamaların bulut destekli depolamaya erişmesini mümkün kılar. Yeni depolama donanımı dağıtmadan kullanıcılara ve uygulamalara neredeyse sınırsız bulut depolama alanı sunar. Şifreleme, denetim günlüğü ve bir kez yaz çok kez oku (WORM) depolaması gibi önemli özelliklerle uygunluk çalışmalarınızı destekleyebilirsiniz.

## 7.9. CloudEndure Disaster Recovery
![60](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/3e8cd24b-5c15-4203-9365-ab8a815e89ce)

Boştaki kurtarma sitesi kaynaklarını kaldırarak maliyetlerden tasarruf edin ve tam olağanüstü durum kurtarma siteniz için yalnızca gerektiğinde ödeme yapmanızı sağlar. Uygulamalarınızı dakikalar içinde, en güncel durumlarından veya belirli bir noktadan kurtarır. Özel beceriler olmadan çok çeşitli uygulamaları test etmek, kurtarmak ve geri döndürmek için birleşik bir süreçten yararlanır.
