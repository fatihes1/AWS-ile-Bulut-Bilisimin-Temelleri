# 12. Amazon Relational Database Service (RDS)
En temelde AWS tarafından sunulan ve yönetilen SQL veri tabanı hizmetidir

## 12.1. İlişkisel Veri Tabanı Nedir?
İlişkisel bir veri tabanı, aralarında önceden tanımlanmış ilişkiler bulunan bir veri öğeleri topluluğudur. Bu öğeler, sütunlar ve satırlar içeren bir dizi tablo olarak düzenlenir. Tablolar, veri tabanında temsil edilecek nesneler hakkında bilgi tutmak için kullanılır. Bir tablodaki her sütun belirli bir tür veriyi tutar ve bir alan, bir özniteliğin gerçek değerini depolar. Tablodaki satırlar, bir nesnenin veya varlığın ilgili değerlerinin bir koleksiyonunu temsil eder. Bir tablodaki her satır, birincil anahtar adı verilen benzersiz bir tanımlayıcı ile işaretlenebilir ve yabancı anahtarlar kullanılarak birden çok tablo arasındaki satırlar ilişkilendirilebilir. Bu verilere, veri tabanı tablolarının kendilerini yeniden düzenlemeden birçok farklı yoldan erişilebilir.

## 12.2. AWS RDS Nedir?
Amazon RDS, size tanıdık gelecek şu altı veri tabanı altyapısı arasından seçim yapma imkânı sağlayan yönetilen bir ilişkisel veri tabanıdır: Amazon Aurora, MySQL, MariaDB, PostgreSQL, Oracle ve Microsoft SQL Server. Bu, mevcut veri tabanlarınız ile kullandığınız kodun, uygulamaların ve araçların Amazon RDS ile kullanılabileceği anlamına gelir. Amazon RDS; tedarik, düzeltme eki uygulama, yedekleme, kurtarma, hata tespiti ve onarım gibi rutin veri tabanı görevlerini üstlenir. 

Amazon RDS, üretim iş yüklerinizi erişilebilirlik ve güvenilirlik açısından geliştirmek için çoğaltma hizmetini daha kolay bir şekilde kullanmanızı sağlar. Multi-AZ dağıtım seçeneğini kullanırken görev açısından kritik iş yüklerini yüksek erişilebilirliğin yanı sıra birincil veri tabanınızdan zaman uyumlu olarak çoğaltılan ikincil veri tabanınıza otomatik ve yerleşik yük devretme özelliklerinden faydalanarak çalıştırabilirsiniz. Okuma replikalarını kullanarak, yoğun okuma gerektiren veri tabanı iş yüklerinin ölçeğini tek bir veri tabanı dağıtımının kapasitesini aşacak şekilde genişletebilirsiniz. 

RDS servisinde, veri tabanının çalıştığı makinenin yönetimi ve bakımı AWS sorumluluğundadır. 

RDS kullanılırken ilk aşamada kullanılacak veri tabanı motoru seçilir. Sonrasında ise kullanılacak disk tipi seçilmelidir. Veri tabanlarında kullanılacak diskin I/O değeri önem arz eder. RDS bu konuda iki tip disk sunmaktadır.

- ***General Purpose (SSD):*** GB başında 3 iops ve maksimum 3000 iops seçeneği 157
- ***Provisioned IOPS (SSD):*** 20 GB ile 64 TB arası depolama desteği ve maksimum 40000 iops seçeneği

RDS özelliklerinin bazılarını sıralamak gerekirse:

- On-Demand ve Reserved Instance 2018 sonunda Aurora ile Serverless imkânı da getirmiştir. 
- Instance durdurma ve başlatma imkânı sunar. 7 gün sonra otomatik olarak terminate olur. 
- Birkaç tıklama ile instance boyutu küçültülebilir ya da büyütülebilir. 
- Kesintisiz depolama genişletme imkânı sunar. 
- Otomatik bakım ve güncelleme AWS tarafından sağlanır. 
- Otomatik yedekleme, manuel yedekleme, snapshot ve snapshot kullanılarak yeni veri tabanı oluşturma özellikleri sunar. 
- Günün istenilen anına yedekten geri dönme imkânı sunmaktadır. Bu özelliği “Transaction Logs” sayesinde sağlar. 
- Yedekten geri yüklenirken bulunan veri tabanı üzerine değil **yeni bir veri tabanı** oluşturarak devam eder.

RDS’in en popüler iki özelliği şu şekildedir:

- ***Multi AZ:*** Bir tanesi aktif bir tanesi pasif olmak üzere iki veri tabanı barındırır. Sadece aktif olan çalışır. Aktif olanın bulunduğu AZ’de oluşan bir senaryoda pasif olan hizmete devam eder. Böylelikle kullanıcılara olan hizmette kesinti minimum tutulur. 
-- Veri tabanının aynı bölge (region) içerisinde bulunan farklı bir AZ’de senkron bir kopyası oluşturulur. 
-- Aktif-Pasif cluster özelliğini kullanır. 
-- Otomatik fail-over imkanına sahiptir. 
-- Kesintisiz çalışma ve felaketten kurtarma senaryoları için kullanılır. 
-- Performans artışı sağlamaz. 
- ***Read Replica:*** Veri tabanları genellikle veri okuma amacıyla kullanılır. Okuma işlemi sayısı veri tabanına yazma işlemine kıyasla çok daha yüksektir. 
-- Veri tabanının aynı veya farklı bölgede (region) oluşturulan bir veya birden fazla asenkron kopyasıdır. 
-- Bir cluster değildir. 
-- READ Only özelliğinde bir kopyadır. 
-- Performans artışı sağlamak için kullanılır.

## 12.3. AWS RDS Kullanımı
![271](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/acd7df87-d216-4705-aa6e-8076d19874a5)

RDS kullanırken bu kılavuz kapsamında aşağıdaki adımlar izlenebilir:

- Veri tabanı oluşturma yöntemi olarak seçili olan “Standard create” ile devam edelim. 
- Veri tabanı motoru (engine) olarak MySQL seçelim. MySQL’in hangi versiyonunu ile ilerlemek istediğimizi soran alanda en son sürümü kullanarak ilerleyelim. 
-  “Templates” alanında kılavuz kapsamı boyunca ekstra fazla ücret ödemek istemediğimiz için “Free tier” seçeneğini kullanalım. Bu seçeneği kullanmamızdan ötürü birçok RDS özelliği kullanılamayacaktır. Aynı zamanda servisi kullanırken ekstra bir ücret ödememize de engel olur. 
-  “DB Instance Identifer” alanında bir isim belirlememiz gerekecek: “calisanlardb” ile devam edelim. 
- Veri tabanına bağlanmak için kullanıcı adı ve parola belirlememiz gerekecektir. İstediğiniz kullanıcı adı ve parola ikilisini kullanabilirsiniz. 
-  Instance tipi olarak “db.t2.micro” ile devam edelim. 
- Depolama tipi olarak “General Purpose (SSD)” ve boyut olarak ise 20 GB belirleyelim. 
- Hangi VPC üzerinde barındırmak istediğimizi soracaktır. Default VPC ve subnet ile devam edelim. 
- Normalde veri tabanlarına public access olmaz ancak bu kılavuz kapsamında yaptıklarımızı izleyebilmek için bu seçeneği evet olarak işaretleyelim. 
- Güvenlik grubu için “Create New” seçeneği ile devam edelim. Güvenlik grubu ismi olarak “firstRSDsecGroup” diyelim. 
- AZ olarak “eu-west-1a” seçeneğini kullanalım. 
- Veri tabanı doğrulaması olarak “Password authentication” seçeneği ile devam edelim. Böylelikle birkaç adım önce oluşturulan kullanıcı adı ve parola ile bağlanılabilecektir. 
- “Additional configuration” başlığı altında bir veri tabanı oluşturabiliriz. İsim değeri olarak “personalbilgi” girelim ve diğer seçenekleri varsayılan olarak bırakalım. 
- Back-up seçenekleri altında belirlediğiniz bir zamanda yedeklemeleri otomatik almasını sağlayabilirsiniz. 
- Create diyerek ilk RDS servisini ve veri tabanını oluşturalım.

Veri tabanının kurulması ve ayağa kalkması biraz zaman alabilir. Bu sürede veri tabanına bağlanacağımız aracı indirebiliriz. https://www.mysql.com/products/workbench/ bu URL üzerinden MySQL Workbench aracı ücretsiz olarak indirilebilir. İndirme işleminden sonra normal bir uygulama kurar gibi uygulama kurulur. 

RDS kontrol paneli üzerinde, databases sekmesinde az önce oluşturulan veri tabanı aktif olana kadar bekleyelim. Enable olduğunda ilk olarak bu veri tabanına bağlanmak için güvenlik grubuna bir kural eklememiz gerekecektir. Bu işlem için; EC2 kontrol paneli → Güvenlik Grupları → Veri tabanı için oluşturulan güvenlik grubu (firstRSDsecGroup) → Inbounded Rules → Edit, adımları takip edilir. Bulunduğumuz makineden otomatik bağlanma için makine IP adres ile bir kural tanımlanmış durumda. O kuralı düzenleyelim ve “Source” alanını “Anywhere - IPv4” ve “Anywhere - IPv6” seçeneklerini ekleyelim. 

MySQL Workbench aracını açalım ve “MySQL Connections” yazısının yanındaki + tuşuna basalım.

![272](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/fc903c41-1a15-4b48-8a1a-cae793c1f366)

Gelen pencerede Connection Name alanına bir isim atayalım: “AWS RDS” diyerek ilerleyelim. Sonrasında “Hostname” alanı için ilk olarak RDS kontrol panelinde veri tabanlarının listelendiği alanda calisanlardb veri tabanını bulalım ve tıklayalım. Karşımıza gelen ekrandan veri tabanına ait end-point değerini hostname kullanarak kullanalım. Kullanıcı adı ve parola alanını RDS servisini oluştururken belirlediğimiz ikiliyi kullanarak devam edelim. “OK” diyelim ve sonrasında veri tabanına bağlanalım. Sol üstte bulunan personelbilgi bizim veri tabanımız olacaktır. Altında listelenen seçeneklerden “Tables”a sağ tık yaparak yeni bir tablo oluşturalım. Tablo adı ve tabloya eklenecek sütunları aşağıdaki Şekil: 53’te verilmiştir.

![273](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/154b49d2-301f-4617-a3ca-f5a8906330e6)

Apply dedikten sonra aşağıdaki Şekil: 54’te görüldüğü gibi bu tablonun SQL dili ile kodlanmış hali verilecektir. Tekrar “Apply” diyerek tabloyu oluşturmuş oluruz.

![274](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b57b0856-3e5f-46c4-9e38-01155b7f7e5c)

Sonrasında yukarıda bulunan Query ekranına şu komutu girelim: ``INSERT INTO personeller (personal_no, ad ,soyad, dogum_tarihi) VALUES (1, "Fatih", "ES", "12-02-199"); ``bu komutla oluşturulan tabloya bir kayıt eklenecektir. Kaydı görmek için ise ``SELECT * FROM personalbilgi.personeller; ``komutu kullanılabilir.

## 12.4. Multi AZ ve Read Replica Özelliklerin Kullanılması
RDS’in en önemli özelliklerini kullanmaya geçmeden önce RDS kontrol panelini detaylı tanıyalım. Bu detaylandırma işlemime kontrol panelinde sol tarafta bulunan alt başlıklar ile başlayalım.

![275](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e20caebc-6938-4fc3-a5a1-1b1544c5651c)

- ***Dashboard:*** Yaratılan instance vb. bilgileri veren ana ekrandır. 
- ***Databases:*** Yaratılan veri tabanları görüntülenir. 
- ***Performance insights:*** Veri tabanı işlemlerinin büyük bir çoğunluğu veri tabanının verimli çalışması ile ilgilidir. AWS bu başlık altında öneriler verir. 
- ***Snapshots:*** Veri tabanı yedekleme işlemidir. Oluşan yedekler (back-up) burada listelenir. Öncelikle yedekler alınır sonrasında yapılan işlemler ise transaction loglar olarak kaydedilir. Bu aşamada bu başlık altında bir tane manueal olarak oluşturalım. 
- ***Automated backups:*** Yedekleme ayarlamaları ve istenilen spesifik bir başlığa dönme işlemleri bu başlık altında yapılır. 
- ***Reserved instances:*** Bir veri tabanı instance’ı belirli bir süreliğine rezerve edilerek daha ucuza mal edilebilir. 
- **Subnet groups:** Bu veri tabanını bu alt ağlarda çalıştır, gibi ayarlamalar yapılabilir.
- ***Parameter groups:*** Veri tabanı instance (MySQL, MSSQL vb.) birçok alt özellik barındırabilir. Yeni instance’ler bu ayarlamalar ile AMI hizmetinde olduğu gibi oluşturulabilir.
- ***Option groups:*** Parameter groups ile aynıdır. Sadece farklı ayarlamaları tutarlar.
- ***Events:*** Veri tabanı ile ilgili yapılmış olayların raporları tutulur.
- ***Event subscriptions:*** SNS yardımıyla kullanılır. Oluşan güncel olayları SNS servisi ile size bildirmesini sağlayabilirsiniz. 
- ***Recommendations:*** AWS tarafından veri tabanınız için verilen önerileri kapsar.

Bu alt başlıkları inceledikten sonra Databases→calisanlardb→Actions seçeneklerini tanıyalım.

![276](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/bb6ce72c-433a-478d-95e1-0a22bbeca083)

- Stop, reboot ve delete İngilizce isimlerinden de anlaşılacağı üzere instance’ı durdurmak, yeniden başlamak ve silmek için kullanılır. 
- Create read replica ise önceki başlıkta değindiğimiz READ only kopya oluşturmak için kullanılır. 
- Create Aurora read replica ise bulunan veri tabanını Amazon Aurora Engine’ı üzerinden kopyalamak için kullanılır. 
- Take snapshot seçeneği ile veri tabanı instance’ının o anda bir kopya kaydı oluşturulur.
- Restore to point in time seçeneği daha önceden oluşturulmuş bir snapshot’a dönmek için kullanılır. 
- Migrate snapshot seçeneği ise RDS’in başka bir veri tabanı Engine’ı ile yeniden oluşturmasını sağlar.

Kontrol panelindeki alt başlıkları incelerken bir snapshot almıştık, bunu kullanarak belirli özelliklerin nasıl kullanılacağını adım adım görelim.

- İlk olarak restore to point in time diyelim. 
- RDS üzerinden alınan bir back-up ile birebir aynı RDS’e dönülemeyeceğini belirtmiştik. Bir back-up’tan dönmek için her seferinde yeni bir instance yaratılır bu yüzden sanki sıfırdan bir RDS instance oluşturuluyor gibi seçenekler sunulur. 
- Geri dönüş işlemi sırasında ilk önce alınan back-up’a dönülür sonrasında ise belirtilen zamana kadar uygulanmış tüm transaction logları yeni oluşturulan instance üzerinde uygular.

### 12.4.1. Multi AZ Özelliğinin Kullanılması
“calisanlardb” adlı RDS instance seçili iken modify diyelim ve Availability & durability seçeneği altında bulunan “Multi AZ deployment” seçeneğini aktif hale getirelim. Şimdi mi uygulansın diye sorduğunda ise evet diyelim. Bir süre sonra status seçeneği available olduğunda calisanlardb→Actions→Reboot→Reboot with failover diyelim. Bu durumda aktif instance kapatıldığı an diğer AZ’de bulunan instance çalışmaya başlayacaktır.

### 12.4.2. Read Replica Özelliğinin Kullanılması
Veri tabanının okuma işlemlerine hız katmak yani veri tabanının performansını arttırmak için “Read Replica” özelliği kullanılır bu özelliği kullanmak için şu adımlar izlenebilir: 
- RDS kontrol paneli → Databases → calisanlardb → Actions → create read replica seçeneklerini takip edelim. 
- DB instance identifier alanına “calisanlardb-frankfurt” diyelim. 
- Bölge olarak “EU (Frankfurt)” seçeneğini kullanalım. 
- Imstance type olarak yine db.t2.micro seçelim. 
- Volume tip olarak General Purpose (SSD), ‒ Multi-AZ seçeneğini kapalı tutalım. 
- Public access’e izin verelim. 
- Database authentication seçeneğini yine “Password authentication” seçelim. Böylelikle ana veri tabanına bağlanırken kullandığımız kullanıcı adı parola ikilisi ile bağlanabiliriz. 
- Ve create read replica diyerek işlemleri tamamlayalım.

AWS kontrol paneli üzerinden bölgeyi “EU (Frankfurt)” olarak değiştirelim. Sırasıyla RDS kontrol paneli → Databases → calisanlardb-frankfurt seçeneklerini takip edelim. Status alanı erişilebilir olduğu anda daha önceden bağlandığımız gibi MySQL Workbench aracı üzerinden yeni oluşan veri tabanına bağlanalım. ``INSERT INTO personeller (personal_no, ad ,soyad, dogum_tarihi) VALUES (2, "X adı", "Y soyadı", "DD-MM-YYYY"); ``girelim ve ver itabanı bize hata fırlatacaktır. Hata olarak, ``Error Code:1290. The MySQL server is running with the – read-only option so it connot execute this statment. ``Bu hatadan anlaşılacağı üzere read replica ile oluşan veri tabanlarından sadece okuma işlemi yapılabilmektedir. Yazma işlemi uygulanamaz. 

Bu konu altında bilinmesi gereken son şey ise bir veri tabanı silindikten sonra o veri tabanına ait otomatik oluşturulan snapshot’larda **silinir**. Ancak kullanıcı tarafından elle oluşturulmuş snapshot’lar **silinmez**.




