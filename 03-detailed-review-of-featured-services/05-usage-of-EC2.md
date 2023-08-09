# 6. Amazon Elastic Compute Cloud (EC2) Servisi Kullanımı
Amazon EC2, zorlu iş ihtiyaçlarını karşılamak için güvenli, stabil, yüksek performanslı ve uygun maliyetli işlem altyapısı sağlar. En önemli ve en çok kullanılan AWS hizmetidir. AWS tarafından sunulan sanal sunucu yaratılmasını sağlayan IaaS hizmetidir.

## 6.1. EC2 Fiyatlandırma
Amazon EC2'yi ücretsiz deneyebilirsiniz. Amazon EC2 bulut sunucuları için ödeme yapmanın beş yolu vardır: İstek üzerine, savings plans, rezerve edilmiş bulut sunucuları ve spot bulut sunucuları. Kullanımınız için tahsis edilmiş fiziksel sunucularda EC2 bulut sunucusu kapasitesi sağlayan “Tahsis Edilmiş Konak Sunucular” için de ödeme yapabilirsiniz.

- ***İstek Üzerine:*** İstek üzerine bulut sunucularını kullanırken hangi bulut sunucularını çalıştırdıysanız ona göre saatlik veya saniyelik olarak işlem kapasitesi ücreti ödersiniz. Uzun vadeli taahhüt veya peşin ödeme gerekmez. Uygulamanızın gereksinimlerine bağlı olarak işlem kapasitenizi artırıp azaltabilir ve yalnızca kullandığınız bulut sunucusu için belirtilen saatlik ücretleri ödersiniz. İsteğe Bağlı bulut sunucuları aşağıdakiler için önerilir:
-- Peşin ödeme veya uzun vadeli taahhüt olmaksızın Amazon EC2'nin düşük maliyetini ve esnekliğini tercih eden kullanıcılar. 
-- Kesintiye uğratılamayan kısa vadeli, ani artışlara yol açan veya tahmin edilemeyen iş yüklerine sahip uygulamalar. 
-- Amazon EC2 üzerinde ilk kez geliştirilen veya test edilen uygulamalar.

- ***Spot Bulut Sunucuları:*** Amazon EC2 spot bulut sunucuları, isteğe bağlı seçeneğine göre %90'a kadar indirimli fiyatlar karşılığında yedek Amazon EC2 işlem kapasitesi talep etmenize imkân tanır. Spot bulut sunucuları aşağıdakiler için önerilir:
-- Başlangıç ve bitiş zamanı esnek olan uygulamalar. 
-- Ticari açıdan yalnızca işlem fiyatları çok düşük olduğunda makul olan uygulamalar. 
-- Çok miktarda ek kapasite konusunda acil bilişim gereksinimleri olan kullanıcılar.

- ***Savings Plans:*** Savings plans, 1 veya 3 yıl boyunca sürekli bir kullanım tutarına (USD / saat olarak ölçülen) taahhüt etmeye karşılık olarak EC2 ve Fargate kullanımında düşük fiyatlar sunan esnek bir fiyatlandırma modelidir.
- ***Tahsis Edilmiş Konaklar:*** Tahsis edilmiş konaklar, kullanımınıza tahsis edilen fiziksel EC2 sunucularıdır. Tahsis edilmiş konaklar, kendi lisans koşullarınıza tabi olan Windows Server, SQL Server ve SUSE Linux Enterprise Server gibi mevcut sunucu sınırlamalı yazılım lisanslarınızı kullanmanıza imkân tanıyarak maliyetlerinizi düşürmenize ve aynı zamanda uyumluluk gereksinimlerinizi karşılamanıza yardımcı olabilir.
-- İsteğe bağlı olarak (saatlik) satın alınabilir. 
-- İsteğe bağlı seçeneğine göre %70'e kadar indirimli bir fiyat karşılığında rezervasyon olarak satın alınabilir.
- ***Rezerve Edilmiş Bulut Sunucuları:*** Amazon EC2 rezerve bulut sunucuları (RI), isteğe bağlı fiyatlandırmaya kıyasla önemli ölçüde bir indirim (%72'ye kadar) sağlar ve belirli bir erişilebilirlik alanında (AZ) kullanıldığında kapasite rezervasyonu sunar. Rezerve bulut sunucuları, isteğe bağlı bulut sunucusu fiyatlandırmasına kıyasla önemli oranlarda (%72'ye kadar) indirim sağlar. Bir yandan Dönüştürülebilir Rezerve Bulut Sunucularını kullanırken rezerve bulut sunucusu fiyatlandırması avantajından yararlanırken diğer yandan da aileleri, işletim sistemi türlerini ve kiracıları değiştirme esnekliğine sahip olursunuz.

## 6.2. Amazon EC2 Bulut Sunucusu Tipleri
Amazon EC2, farklı kullanım örnekleri için optimize edilmiş çok sayıda bulut sunucusu tipi seçeneği sunar. Bulut sunucusu türleri çeşitli CPU, bellek, depolama ve ağ iletişimi kapasitesi birleşimlerinden oluşur ve uygulamalarınız için uygun kaynak karışımını seçebilme esnekliği sağlar. Her bulut sunucusu türü bir veya daha fazla bulut sunucusu boyutu içerir. Böylece kaynaklarınızı hedef iş yükünüze göre ölçeklendirebilmenize imkân tanır.

- ***Genel Amaçlı:*** Genel amaçlı bulut sunucuları; işlem, bellek ve ağ kaynakları arasında denge sağlar ve çeşitli iş yükleri için kullanılabilir. Web sunucuları ve kod depoları gibi bu kaynakları eşit oranlarda kullanan uygulamalar için bu bulut sunucuları idealdir. Xcode IDE üzerinde iOS, iPadOS, macOS, WatchOS ve tvOS uygulamaları geliştirme, üretme, test etme ve bunlarda oturum açma gibi kullanım örnekleri mevcuttur.
-- T, M ve A tipi sunucular bu kategoridedir. 
-- M6g bulut sunucuları, A1 bulut sunucuları, T2 bulut sunucuları ve m3.medium dışında her vCPU, Intel Xeon veya AMD EPYC çekirdeğinin bir iş parçacığıdır. 
-- T4g ve M6g bulut sunucuları üzerindeki her vCPU, AWS Graviton2 işlemcinin bir çekirdeğidir. 
-- A1 bulut sunucuları üzerindeki her vCPU, “AWS Graviton İşlemcinin” bir çekirdeğidir. 114 
-- AVX, AVX2 ve gelişmiş ağ iletişimi yalnızca HVM AMI'ler ile başlatılan bulut sunucularında bulunur. 
-- Bu sayı, bu bulut sunucusu tipi için varsayılan ve en yüksek vCPU sayısıdır. Bu bulut sunucusu türünü başlatırken özel bir vCPU sayısı belirtebilirsiniz. Geçerli vCPU sayısı ve bu özelliği kullanmaya başlama hakkında daha ayrıntılı bilgi edinmek için CPU optimizasyonu belgelerinin yer aldığı bu sayfayı ziyaret edin. 
-- Bu M4 bulut sunucuları bir Intel Xeon E5-2686 v4 (Broadwell) işlemci üstünde başlatılabilir. 
-- Belirli bir ağ bant genişliğine "Varan" şeklinde işaretlenen bulut sunucuları, bir taban bant genişliğine sahiptir ve taban ağ genişliklerinin ötesine elden gelen en iyi şekilde artış için bir ağ G/Ç kredisi mekanizması kullanabilirler.

- ***İşlem İçin Optimize Edilmiş***: İşlem için optimize edilmiş bulut sunucuları, yüksek performanslı işlemcilerden yararlanan işleme bağlı uygulamalar için idealdir. Bu ailedeki bulut sunucuları toplu işleme iş yükleri, medya dönüştürme, yüksek performanslı web sunucuları, yüksek performanslı bilişim (HPC), bilimsel modelleme, tahsis edilmiş oyun sunucuları ve reklam sunucusu altyapıları, makine öğrenimi çıkarımı ve diğer yoğun işlem içeren uygulamalar için oldukça uygundur. Yüksek performanslı bilişim (HPC), toplu işleme, reklam sunma, video kodlama, oyun, bilimsel modelleme, dağıtılmış analiz ve CPU temelli makine öğrenimi çıkarımı gibi kullanım örnekleri mevcuttur.
-- C tipi sunucular bu kategoride yer alır. 
-- C7g bulut sunucuları üzerindeki her vCPU, AWS Graviton3 işlemcisinin bir çekirdeğidir. 
-- C6g ve C6gn bulut sunucuları üzerindeki her vCPU, AWS Graviton2 işlemcinin bir çekirdeğidir. 
-- AVX, AVX2 ve gelişmiş ağ iletişimi yalnızca HVM AMI'ler ile başlatılan bulut sunucularında bulunur. 
-- Bu sayı, bu bulut sunucusu tipi için varsayılan ve en yüksek vCPU sayısıdır. Bu bulut sunucusu türünü başlatırken özel bir vCPU sayısı belirtebilirsiniz. Geçerli vCPU sayısı ve bu özelliği kullanmaya başlama hakkında daha ayrıntılı bilgi edinmek için CPU Optimizasyonu belgelerinin yer aldığı bu sayfayı ziyaret edin. 
-- Belirli bir ağ bant genişliğine "Varan" şeklinde işaretlenen bulut sunucuları, bir taban bant genişliğine sahiptir ve taban ağ genişliklerinin ötesine elden gelen en iyi şekilde artış için bir ağ G/Ç kredisi mekanizması kullanabilirler.

- ***Bellek İçin Optimize Edilmiş:*** Bellek için optimize edilmiş bulut sunucuları, bellekte büyük veri kümeleri işleyen iş yükleri için hızlı performans sunmak üzere tasarlanmıştır. Açık kaynaklı veri tabanları, bellek içi önbellekler, gerçek zamanlı büyük veri analizleri gibi yoğun bellek ihtiyacı olan uygulamalar gibi kullanım alanları mevcuttur.
-- R, X, Z ve U tipi sunucular bu kategoride yer alır. 
-- R6g ve X2gd bulut sunucuları üzerindeki her vCPU, AWS Graviton2 işlemcinin bir çekirdeğidir. 
-- Belirli bir ağ bant genişliğine "Varan" şeklinde işaretlenen bulut sunucuları, bir taban bant genişliğine sahiptir ve taban ağ genişliklerinin ötesine elden gelen en iyi şekilde artış için bir ağ G/Ç kredisi mekanizması kullanabilirler.

- Hızlandırılmış Bilişim: Hızlandırılmış bilişim bulut sunucuları; kayan nokta sayı hesaplamaları, grafik işleme veya veri deseni eşleme gibi işlevleri CPU'lar üzerinden çalışan yazılımların erişemeyeceği bir verimlilik düzeyinde gerçekleştirmek için donanım hızlandırıcıları veya ortak işlemcileri kullanır. Makine öğrenimi, yüksek performanslı bilişim, hesaplamalı akışkanlar dinamiği, hesaplamalı finans, sismik analiz, konuşma tanıma, sürücüsüz araçlar ve ilaç keşifleri gibi kullanım alanları mevcuttur.
-- F, P ve G tipi sunucular bu kategoride yer alır. 
-- Belirli bir ağ bant genişliğine varan şeklinde işaretlenen bulut sunucuları, bir taban bant genişliğine sahiptir ve taban ağ genişliklerinin ötesine elden gelen en iyi şekilde artış için bir ağ G/Ç kredisi mekanizması kullanabilirler.

- ***Depolama İçin Optimize Edilmiş:*** Depolama için optimize edilmiş bulut sunucuları; yerel depolama üzerindeki çok büyük veri kümelerine yüksek, sıralı okuma ve yazma erişimi gerektiren iş yükleri için tasarlanmıştır. Bu bulut sunucuları, uygulamalara saniye başına on binlerce düşük gecikmeli, rastgele G/Ç işlemi (IOPS) göndermek için optimize edilmiştir. Bu bulut sunucuları; ilişkisel veri tabanları (MySQL, MariaDB ve PostgreSQL) ve NoSQL veri tabanları (KeyDB, ScyllaDB ve Cassandra) gibi orta boyutlu veri kümelerine sahip olan ve yüksek işlem performansı ile yüksek ağ aktarım hızından yararlanabilecek G/Ç yoğun ve iş açısından kritik iş yükleri için saniye başına işlem sayısını (TPS) en üst düzeye çıkarır. Ayrıca arama altyapıları ve veri analizi iş yükleri gibi yerel depolama alanlarındaki orta boyutlu veri kümelerine çok hızlı erişim gerektiren iş yükleri için idealdirler.
-- R, X, Z ve U tipi sunucular bu kategoride yer alır. 
-- i3.metal, 36 fiziksel çekirdek üstünde 72 mantıksal işlemci sunar.

Sunucu tipleri modelleri belirli bir isimlendirme standarttı takip edilerek oluşturulmuştur. Örneğin; m4.large model bir sunucu genel amaçlı M tipi bir sunucun 4.jenarasyonudur. İlk yaratılan jenerasyon 1. olanlardır. Yıllar geçtikçe gelişen teknoloji ile yeni işlemciler, sunucu donanımları geliştirilir ve yeni sunucu makinelerinde barınacak sanal makineler için farklı model ismi kullanılır. AWS yeni jenerasyon servislerini teşvik amaçlı daha uygun fiyata sunmaktadır. Bununla birlikte “m4.large” da bulunan large kelimesi de sanal sunucunun özelliklerini temsilen kullanılır. Nano, micro ile başlayarak 24XLarge haline kadar farklı modeller bulunur. Bu artış sanal sunucunun RAM, bant genişliği, depolama, CPU performansı gibi değerlerini temsil etmektedir ve 24XLarge’a yaklaştıkça bu değerler daha yüksek olur. 

AWS, 2018 yılının sonuna doğru 2 yeni instance ortaya çıkarmıştır. ARM tabanlı işlemciler bulunduran sanal makinelerdir. M5a ve T3a modelleri ise AMD işlemci bulunduran sunuculardır.

# 6.3. Depolama Modelleri
Amazon EC2 iş yüklerinin depolama gereksinimi birbirinden çok farklı olabilir. Yerleşik bulut sunucusu geçici diskine ek olarak, diğer bulut depolama iş yükü gereksinimleri için uygun Amazon Elastic Block Store (Amazon EBS) ve Amazon Elastic File System (Amazon EFS) seçeneklerini de sunar. Amazon EBS, Amazon EC2 bulut sunucuları ile kullanılmak üzere kalıcı, yüksek oranda erişilebilir, tutarlı ve düşük gecikmeli blok depolama hacimleri sunarken Amazon EFS, paylaşılan erişime yönelik basit, ölçeklenebilir, kalıcı ve tam yönetilen bulut dosya depolaması sunar.

| Amazon Elastic File System (EFS) |Amazon Block Store (EBS) |
|--|--|
| Instance’e fiziksel olarak bağlıdır.| Kalıcı veri deposudur, instance’den bağımsız. |
| Kalıcı olmayan veri deposu. | Block tabanlı (base) depolama. |
| Veri başka bir makinede replika edilmez. | AZ içerisinde birden fazla cihazda replika edilir. |
| Snapshot desteği yok. | Snapshot desteği bulunur. |
| SSD veya HDD | SSD veya HDD |

Amazon Instance Store (Ephemeral); herhangi bir sanal makinenin üzerinde çalıştığı fiziksel sunucuya doğrudan bağlı disklerin kullanıldığı depolama yöntemine verilen isimdir. Direkt bağlı olduğu için yüksek erişimiz hızı ve düşük gecikme sunar. Disk giriş/çıkış hızının önemli olduğu depolama için optimize edilmiş D, H ve I ailelerinin bazıları bu modeldedir. Sanal makine kullanıcıdan bağımlı veya bağımsız kapanırsa veriler gider. 

EBS ise aktif olarak çok daha fazla kullanılan depolama modelidir. Amazon EBS, depolama performansınızı ve maliyetinizi uygulamalarınızın ihtiyaçlarına göre uyarlayabilmeniz için performans özellikleri ve fiyatları bakımından farklılık gösteren aşağıdaki birim türlerini sağlar. Hacim türleri şu kategorilere girer:

- ***Solid State Drives (SSD):*** Baskın performans özniteliğinin IOPS olduğu, küçük G/Ç boyutuna sahip sık okuma/yazma işlemlerini içeren işlemsel iş yükleri için optimize edilmiştir. 
- ***Hard Disk Drives (HDD):*** Baskın performans özniteliğinin aktarım hızı olduğu büyük akış iş yükleri için optimize edilmiştir. 
- ***Önceki Nesil:*** Verilere seyrek olarak erişilen ve performansın birincil öneme sahip olmadığı küçük veri kümelerine sahip iş yükleri için kullanılabilen sabit disk sürücüleri. Bunun yerine geçerli nesil bir birim türünü düşünmeniz AWS tarafından önerilir.

Örnek yapılandırması, Giriş/Çıkış özellikleri ve iş yükü talebi gibi EBS birimlerinin performansını etkileyebilecek çeşitli faktörler vardır. Bir EBS biriminde sağlanan IOPS'yi tam olarak kullanmak için EBS için optimize edilmiş örnekleri kullanmalısınız.

## 6.4. İşletim Sistemi Çeşitleri
Amazon Machine Image'lar (AMI'ler), Microsoft Windows'un yanı sıra Amazon Linux 2, Ubuntu, Red Hat Enterprise Linux, CentOS, SUSE ve Debian'ın da aralarında bulunduğu Linux dağıtımlarını içeren ve her geçen gün daha da genişleyen bir dizi işletim sistemi ile önceden yapılandırılmıştır. AWS bizlere olabildiğince fazla seçenek sunmak için çözüm ortaklarını ve topluluğuyla çalışır. AWS Marketplace, iyi bilinen satıcılar tarafından sağlanan ve EC2 bulut sunucularınızda çalışacak şekilde tasarlanmış geniş bir ticari ve ücretsiz yazılım seçenek yelpazesine sahiptir.

## 6.5. EC2 Servisi ile Sanal Makine Oluşturulması
![249](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e56b9360-a42e-4abb-81bb-1ccc0c2bcb96)

EC2 kontrol merkezine ilk girildiğinde sol bölümde temel-yan servisleri hakkında bilgiler ve ayarlamalara yer verilir. Orta bölümde sahip olunan kaynaklar, bölge ve AZ durumları bulunur. Instances (running) seçeneğinde çalışıyor olanlar görünür ancak şu an çalışan bir instance’a sahip değiliz. Turuncu launch instance butonuna tıklayarak ilk sanal makinemizi oluşturabiliriz. Adımlar sırasıyla şu şekildedir:

- ***Name and Tags:*** İlk olarak kurulacak sanal makineye bir isim verilmelidir. İsteğe bağlı olarak etiket ataması da yapılabilir. 
- ***Application and OS Images (Amazon Machine Image):*** AMI, bulut sunucunuzu başlatmak için gereken yazılım yapılandırmasını (işletim sistemi, uygulama sunucusu ve uygulamalar) içeren bir şablondur. Amazon Linux, Ubuntu, Microsoft, Red Hat, SUSE Linux gibi opsiyonlar sunulur. Sonrası mimarinin kaç bit olması gerektiğini belirleyebilirsiniz. 
- ***Instance Type:*** Başlık 4.6.2’de belirlenen şekilde micro, small gibi seçeneklerin bulunduğu bulut sunucusu tipi seçilir. 
- ***Key Pair (Login):*** Bulut sunucunuza güvenli bir şekilde bağlanmak için bir anahtar çifti kullanabilirsiniz. Örneğin başlatmadan önce seçilen anahtar çiftine erişiminiz olduğundan emin olun. Bu AWS tarafından önerilmektedir. Böylelikle bulut sunucunuz güvende olacaktır. 
- ***Network Setting:*** Bu alanda bağlantı ayarlarına yer verilmektedir. Güvenlik grubu şeklinde güvenlik duvarı belirlenebilir. Bununla beraber spesifik IP aralığından bağlanmaya izin verilmesi gibi ayarlar bulunur. 
- ***Configure Storage:*** Bu alanda depolama alnınızı konfigüre etmenize imkân sunulur. 
- ***Advaced Detail:*** Bu alan altında ise daha detaylı ayarlara yer verilmiştir. Bulut sunucu kapatıldığında ne olsun gibi seçenekler burada yer alır. Veya sunucu ilk başlatıldığı anda çalıştırılması istenen bir komut var ise bu belirtilebilir.

Bu kılavuzun bu aşamasında şu seçimler ile devam edelim.

- İsim olarak ‘seminer1’ seçiyoruz. 
- İşletim sistemi imajı olarak Amazon Linux seçip ilerliyoruz. 
- Instance type alanında ücretsiz deneme imkânı sunulan ‘t2.micro’ seçeneğini seçiyoruz.
- Key pair alanı için anahtar oluşturulması gerekmektedir. Bu yüzden Create new key pair diyoruz. Key’e isim olarak, “connection-ec2-from-windows” ismini verelim. Anahtar çifti tipini RSA ve gizli key formatını da ‘ppk’ seçiyoruz. Pem formatı OpenSSH için ``.ppk``formatı ise windows üzerinden sunucuya bağlanırken kullanılacak olan PuTTY aracı için kullanılır. Bu seçimlerden sonra dosya bilgisayara inecektir. 
- Gelişmiş ayarlarda bulunan ‘Tenancy’ seçeneğini ‘Shared’ yani paylaşımlı olarak belirliyoruz. 
- Yine gelişmiş ayarlarda bulunan ‘User data’ alanına şu kod satırı yazılır:
 ``#!/bin/bash``
 ``yum update -y ``, böylelikle bulut sunucu ilk açıldığında güncellemeleri otomatik olarak yapacaktır.
- Ağ ayarları alanında, Firewall için SSH, HTTP ve HTTPS seçeneklerinin üçünü de seçelim. Ve tüm bu seçimler için bağlantı kısıtlaması olmasın. Yani ``0.0.0.0/0`` şeklinde atanmış olur. Böylece IPv4 adresinden gelen tüm isteklere izin verilir. 
- Launch instance diyerek bulut sunucusu ayağa kaldırılacaktır.

PuTTY uygulamasını açtıktan sonra bağlanmak için ilk işlem olarak ``ec2- user@PUBLIC_IP_ADDRESS`` formatında PUBLIC_IP_ADDRESS kısmında kendi seminer1 adında oluşturduğumuz bulut sunucunun IP adresini ekleriz Sonrasında ise yine PuTTY üzerinden sol tarafta bulunan alanda, connection→SSH→Auth üzerinde doysa seçme kısmında indirilmiş olan gizli şifre dosyasını seçeriz. Sonrasında ‘open’ diyerek sunucuya bağlanılır. Bağlantıdan sonra Şekil: 30’daki gibi bir ekran bizi karşılar. ``sudo su``komutuyla root kullanıcı olduktan sonra işlevlere sonsuz yetki sahibi oluruz.

![250](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0785cb15-2bdb-4844-84dd-6762faaaf725)

Bu işlemden sonra daha önce S3 bucket üzerinde canlıya alınan siteyi sunucu üzerinden canlıya alalım. Bu işlem için ilk olarak nginx kullanılmalıdır. ``amazon-linux-extras install nginx1.12`` komutuyla indirmiş oluruz. ``service nginx start`` ile servis çalıştırılır. ``chkconfig nginx on`` komutuyla ise sunucu her açıldığında otomatik çalıştırılmasını sağlar. Daha önceden S3 başlığında, EC2 üzerinden S3’e tam erişim için oluşturulan IAM rolünü bu bulut sunucuya atamamız gerekir. Bulut sunucu seçiliyken, Actions→Secuirty→Modify IAM role seçeneklerini takip ederek oluşturulmuş olan role ataması yapılır.

![251](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ec2b0d8c-6ba8-4f68-aa09-5cbc8b425d98)

Tarayıcı üzerinden ``http://[PUBLIC_IP_ADDRESS]`` şekline girildiğinde nginx’in karşılama sayfası ortaya çıkacaktır. Atanan rolü kullanmak için ilk olarak ``aws s3 ls`` komutu ile S3 üzerinde oluşturulmuş bucket’lar listelenecektir. S3 üzerinde static bir web sayfası bulunuyordu. Onu nginx sunucu üzerinde yayınlamak için aşağıdaki adımları takip ederiz:

- ``cd /usr/share/nginx/html`` dizinine gideriz. 
- ``rm index.html`` diyerek var olan html dosyası silinir. 
- ``aws s3 ls [BUCKET_NAME] ``ile static web sayfasının bulunduğu bucket kontrol edilir. 
- ``aws s3 cp s3://[BUCKET_NAME]/index.html`` . komutu ile bulunulan dizine dosyalar kopyalanır. 
- Aynı şekilde ``aws s3 cp s3://[BUCKET_NAME]/clouds.jpg ``. komutu ile bulunan dizine görsel de alınır. 
- ``http://[PUBLIC_IP_ADDRESS]`` adresine gittiğimizde web sayfası görünecektir.

# 6.6. Elastic Load Balancing Service (ELB)
EC2 ve container’lar ile kullanılabilen bir servistir. AWS’in yönetilebilen yük dağıtım servisidir. Uygulamaların ölçeklenebilirliğini iyileştirmek için ağ trafiğini dağıtmanıza imkân tanır. Bütünleşmiş sertifika yönetimi, kullanıcı kimlik doğrulaması ve SSL/TLS şifre çözme ile uygulamalarınızın güvenliğini sağlarsınız. Uygulamaları yüksek erişilebilirlik ve otomatik ölçeklendirme ile sunabilirsiniz. Uygulamalarınızın durumunu ve performansını gerçek zamanlı olarak izleyebilir, sorunları ortaya çıkarabilir ve SLA uygunluğunu sürdürebilirsiniz. Elastic Load Balancing (ELB), gelen uygulama trafiğini bir veya daha fazla erişilebilirlik alanında (AZ) birden çok hedef ve sanal cihaz arasında otomatik olarak dağıtır.

![252](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b86b5546-aecd-43be-a69f-33133f19579b)

## 6.7. EC2 Auto Scaling
Amazon EC2 Auto Scaling uygulama erişilebilirliğini korumanıza yardımcı olur ve EC2 bulut sunucularını tanımladığınız koşullara göre otomatik olarak eklemenize veya kaldırmanıza olanak tanır. Filonuzun sağlığını ve erişilebilirliğini korumak için EC2 Auto Scaling'in filo yönetim özelliklerini kullanabilirsiniz. EC2 bulut sunucularını eklemek veya kaldırmak için EC2 Auto Scaling'in dinamik ve tahmini ölçeklendirme özelliklerini de kullanabilirsiniz. Dinamik ölçeklendirme, değişen talebe cevap verir ve tahmini ölçeklendirme, öngörülen talebe göre doğru sayıda EC2 bulut sunucusunu otomatik olarak zamanlar. Dinamik ölçeklendirme ve tahmini ölçeklendirme, daha hızlı ölçeklendirmek için birlikte kullanılabilir. 

İster bir isterse binlerce Amazon EC2 bulut sunucusu çalıştırıyor olun, Amazon EC2 Auto Scaling’i kullanarak hatalı Amazon EC2 bulut sunucularını ve kötü durumdaki uygulamaları tespit edebilir ve bulut sunucularını müdahale etmeden değiştirebilirsiniz. Bu durum, uygulamanızın beklediğiniz işlem kapasitesine sahip olduğundan emin olmanızı sağlar. Amazon EC2 Auto Scaling, EC2 bulut sunucuları için filo yönetimini otomatikleştirme amacıyla üç temel işleve sahiptir:

- ***Çalışan bulut sunucularının durumunu izleme:*** Amazon EC2 Auto Scaling, uygulamanızın trafik aldığından ve EC2 bulut sunucularının düzgün çalıştığından emin olmanızı sağlar. Amazon EC2 Auto Scaling düzenli olarak sistem durumu denetimleri gerçekleştirerek iyi durumda olmayan bulut sunucularını belirler.
- ***Kötü durumdaki bulut sunucularını otomatik olarak değiştirme:*** Kötü durumdaki bir bulut sunucusu denetimden geçemediğinde Amazon EC2 Auto Scaling bunu otomatik olarak sonlandırır ve yenisiyle değiştirir. Bu da bulut sunucusunun değiştirilmesi gerektiğinde manuel olarak müdahale etmenize gerek kalmadığı anlamına gelir.
- ***Erişilebilirlik alanlarındaki kapasiteyi dengeleme:*** Amazon EC2 Auto Scaling, bulut sunucularını alanlar arasında otomatik olarak dengeleyebilir ve yeni bulut sunucularını her zaman tüm filonuzdaki alanlar arasında mümkün olduğunca dengeli olacak şekilde başlatır.

EC2 Auto Scaling kullanıcılara esneklik sunmaktadır. Örneğin bir kullanıcı, sanal makineleri 5 dakika boyunca %90’dan fazla CPU kaynağı kullanırsa, yeni sanal makine oluştur ve bu sanal makine diğer sanal makinelerin CPU kaynağı kullanımı %30 değerinin altına düşene kadar çalısın şeklinde bir talimat oluşturabilir. Böylelikle kullanıcı tüm süreci otomatikleştirebilir.

## 6.8. EC2 Placment Group
Yeni bir EC2 bulut sunucusu başlattığınızda, EC2 hizmeti ilgili arızaları en aza indirmek için bulut sunucusunu tüm bulut sunucularınız temel donanıma yayılacak şekilde yerleştirmeye çalışır. İş yükünüzün gereksinimlerini karşılamak için birbirine bağlı bir grup örneğin yerleşimini etkilemek için yerleşim gruplarını kullanabilirsiniz. İş yükünün türüne bağlı olarak, aşağıdaki yerleştirme stratejilerinden birini kullanarak bir yerleşim grubu oluşturabilirsiniz:

- ***Küme –*** Bir erişilebilirlik alanı içinde birbirine yakın paketlerdir. Yani aynı makinede çalışır. Bu strateji, iş yüklerinin, HPC uygulamalarında tipik olan, sıkıca bağlanmış düğümler arası iletişim için gerekli olan düşük gecikmeli ağ performansını elde etmesini sağlar. AWS bu hizmeti kullanırken kullanıcılardan dikkat etmesi gereken uyarıları bulunur:
-- Aynı EC2 Instance tiplerini kullanılmasını önerir. m4.xlarge ile c4.xlarge gibi farklı tiplerde olmamasını önerir. 
-- Bu işlemin tek bir oluşturma isteği ile yapılmasını ister. İlk başta dört sunucu ile başlayarak sonradan 3 tane daha ekleme yapılmamasını bekler. Kurulumun iyi planlanması ve tek seferde gerçekleştirilmesi istenir. 
-- Bir sanal makineyi durdurup, tekrar başlatırken hepsinin aynı anda yapılmasını istemektedir
- ***Bölümleme –*** Örneklerinizi mantıksal bölümler arasında yayar, böylece bir bölümdeki örnek grupları, temel donanımı farklı bölümlerdeki örnek gruplarıyla paylaşmaz. Bu strateji genellikle Hadoop, Cassandra ve Kafka gibi büyük dağıtılmış ve çoğaltılmış iş yükleri tarafından kullanılır. Uygulamanın farklı fiziksel sunucularda olmasını, fiziksel sunucuya bir sorun olması durumunda tüm hizmetin durmasının istendiği durumlarda uygulanır.
- ***Yayılma –*** İlişkili arızaları azaltmak için küçük bir örnek grubunu farklı temel donanımlara yerleştirir.

EC2, temelde binlerce fiziksel sunucunun biri üzerinde çalışan sanal makinelerdir. EC2 üzerinde oluşturulmuş sanal makineleriniz birbirinden farklı fiziksel makinelerde çalışıyor olabilir. Her ne kadar sunucular arasında iletişim çok hızlı olabilse de bazı durumlarda bu hızın yetersiz olduğu durumlar oluşabilir. Yani çok düşük gecikmeye ihtiyaç duyulabilir. Diğer bir deyişle ise low latency (düşük gecikme) ve high throughput (yüksek verim) gerektiği durumlarda kullanıma uygundur.

## 6.9. EC2 Detaylı Kullanımı
### 6.9.1. Windows İşletim Sistemine Sahip Sanal Makine Kurulması
Windows işletim sistemine sahip bir sanal makine oluşturmadan önce bir güvenlik grubu (security group) oluşturulmalıdır. Bu güvenlik grubu üzerinden hangi bağlantılara izin verileceği gibi tanımlamalar yapılır. Bir güvenlik grubu oluşturmak için EC2 kontrol paneli üzerinde sol tarafta bulunan Netwrok & Security kategorisinden Security Groups seçilir. Kullanıcının karşısına çıkacak olan ekran Şekil: 33’te belirtilmiştir.

![253](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/2f5ad4d3-4463-4cc8-be0a-b930709d3a99)

Açılan sayfada sağ üstte bulunan buton ile yeni bir güvenlik grubu oluşturulabilir. İlk işlem olarak güvenlik grubuna bir isim ve açıklama girilmelidir. Bu aşamadan sonra “Inbound rules” altında kurallar tanımlanır. Bu kurallar oluşturulan sanal makineye bağlanmak için kullanılabilecek yöntemleri tanımlamaktadır. Sırasıyla SSH, HTTP ve HTTPS için destination yani hedef seçeneği “custom” yapılır ve hedef alanına ``0.0.0.0/0`` tanımlanır. Bu tanımlama sayesinde IPv4 ve IPv6 olmak üzere iki hedeften de gelecek tüm istekler ile sanal makinaya erişilmesi sağlanır. Bu varsayılan isteklerin yanında Windows üzerinden uzak masaüstü bağlantısı ile erişebilmek için ek bir tanımlama daha yapılmalıdır. Bu tanımlama şu şekilde oluşturulur:

Tip olarak “Custom TCP Protocol” seçilir. “Port range” değeri 3389 olarak tanımlanır ve yukarıda tanımlanan kurallarda olduğu gibi hedef için değer ``0.0.0.0/0`` olarak belirlenir. Böylelikle her cihazdan erişime açık bir uzak sunucu oluşturulmuş olur.

Güvenlik grubu tanımlandıktan sonra Windows işletim sistemine sahip sanal makine oluşturulmalıdır. EC2 kontrol paneli üzerinden “Launch instance” butonuyla bir sanal makine oluşturulur. Sanal makineyi oluşturmak için aşağıdaki adımlar izlenebilir:

- Application and OS Images ayarı olarak arama alanına Windows 2016 yazılır ve base “Microsoft Windows Server 2016 Base” AMI’ı seçilir. 
- Instance type olarak sunucunun gereksinimine göre bir tür seçilir. Bu kılavuz için ücretsiz kullanma imkânı sunulan t2.micro kullanılmıştır. 
- Key Pair seçeneğinde başlık 4.6.5. EC2 Servisi ile Sanal Makine Oluşturulması üzerinde oluşturulmuş olan key yani anahtar kullanılabilir. 
- Network settings altında bulunan Firewall için değeri bu başlık altında oluşturulan güvenlik grubu seçilmelidir. Bu işlem için “Select existing security group” seçeneği kullanılarak, oluşturulmuş olan güvenlik grubu seçilir. 
- Gelişmiş ayrıntılar seçeneğinin altında bulunan IAM instance profile kısmında daha önce oluşturulmuş olan EC2-S3-Full-access rolü seçilir. 
- Son işlem olarak turuncu “Launch instance” butonu ile sanal makine oluşturulur.

Bu işlemler sonucunda Windows işletim sistemine sahip sanal makine oluşturulmuş olur. Oluşturulan sanal makine seçili iken actions butonuna tıklanır ve alt sekmelerde görünen security sonrasında ise “Get Windows password” diyerek Windows işletim sistemine sahip sanal makineye bağlanırken kullanılacak olan şifre ve DNS bilgileri verilir. Şifreyi vermeden önce private key istemektedir. Bu adımda daha önce bilgisayara indirilen dosya kullanılır. Tüm işlemler sonunda uzak sunucudaki sanal bilgisayara bağlanmak için aşağıdaki bilgiler AWS tarafından sunulur:

- Public DNS bilgisi 
- Kullanıcı adı bilgisi 
- Parola bilgisi

Bu işlemlerden sonra yerel bilgisayar üzerinden Windows tuşu + R tuşuna basılır. Ekrana çıkan çalıştır dosyasına ``mstsc`` komutu girilir ve uzak masaüstü bağlantısı ekranı gelir. AWS tarafından sağlanan bilgiler ile bağlantı sağlanır. Böylelikle uzak sunucuda bulunan Windows sanal bilgisayara kullanıcı ara yüzü üzerinden erişilmiş olur.

### 6.9.2. Sanal Makineye Yeni Volume Eklenmesi
Windows sanal makineye uzak sunucu bağlantısı ile bağlanıldığında Şekil: 34’teki ekran kullanıcıyı karşılar.

![254](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c72cc495-2c2d-43fd-a227-2b3808aa3ee6)

Şimdi sırayla şu adımları izleyerek disk yönetim sistemine girelim:

- Sol altta bulunan Windows tuşuna tıklayalım. 
- Açılan menüde “Server Manager” seçeneğini seçelim. 
- Karşımıza çıkan Şekil: 35’teki ekranda ilk etapta sol tarafta bulunan “local server” seçeneğini sonrasında sağ üstte bulunan “tools” seçeneklerine sırasıyla tıklayalım.
![255](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/7dda0ad5-5b1d-4950-88e9-cc58b670da62)

- Tools seçeneğine tıklandığında açılır menüden “Computer Management” ve sonrasında ekrana gelen pencere de sol altta bulunan “Disk Management” seçeneklerini takip edelim. 
- Karşımıza instance kurulurken seçtiğimiz kök yani root volume gelecektir.

Bazı durumlarda sanal makinenin depolama alanına arttırmaya ihtiyaç duyulur. Fiziksel makinelerde bu işlem yeni bir depolama aygıtı alıp eklemek veya var olan ile yer değiştirmek şeklinde oluşturulur. Bulut bilişimin sunduğu bir diğer avantaj olan esneklik burada devreye girer. Var olan dosyaları kaybetmeden depolama alanı arttırılabilir. Şimdi yeni bir volume ekleyip bu volüme ile sanal makineyi birleştirelim. 

Bu işlemi yapmak için sırasıyla aşağıdaki adımlar izlenebilir:

- EC2 kontrol paneli açılır. 
- Sol menüde bulunan seçeneklerden “Elastic Block Store” altında bulunan “Volumes” seçeneğine tıklanır. 
- Sağ üstte bulunan turuncu “Create volume” seçeneği ile oluşturma işlemi başlatılır. 
- Volume türü ve alanı seçilir. Bu kılavuz için gp2 ve 20 GiB seçenekleri ile devam edelim. 
- Bir diski (volume) bir sanal makineye bağlamak için bu iki kaynağın aynı AZ yani erişilebilirlik alanında olması gerekir. Windows sanal makinemizin hangi AZ üzerinde barındığını bulmak için EC2 kontrol panelinde listelenen instance’ler içerisinde görebilir. Bu kılavuz hazırlanırken oluşturulmuş olan sanal makine “eu-west-1c” AZ’sinde bulunmaktadır. Bu yüzden volume oluşturulurken bu değer seçilir. 
- Oluşturulurken dikkat edilmesi gereken bir diğer durum, volume oluşturulma anında Encryption seçeneğinin aktif edilebilmesidir. Ancak, sanal makine oluşturulurken disk seçimi ekranında seçilen kök volume için bu seçenek aktif edilemiyordu. Bir sanal makinenin ilk oluşturulan root volume için bu seçenek açılamaz. Ancak EBS diskler oluşturulurken şifreleme seçeneği seçilerek oluşturulabilir. 
- İsteğe bağlı olarak oluşturulan volume’e bir tag değeri atanabilir.
- Son adım olarak turuncu “Create volume” seçeneğine tıklanır.

Volume oluşturulduktan sonra bu volume bir sanal makineye atanmalıdır ki kullanılabilsin. Bu işlem için atanacak volume seçili iken “Actions” butonu kullanılır ve “Attach volume” seçeneğine tıklanır. Açılan sayfada hangi instance için (sanal makine) atama yapılacağı seçilir ve “Attach volume” butonu ile atama yapılır. 

Bu işlemlerden sonra Windows sanal makineye döndüğümüzde aşağıdaki Şekil: 36 bizi karşılar.

![256](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c498a4f8-273e-4739-ad43-e0a242c884f2)

Görüldüğü gibi az önce oluşturulan disk başarıyla sanal makineye eklenmiştir. Ancak diskin aktifleştirilmesi gerekmektedir. Bunun için:

- Disk 1 yazısına sağ tıklanır ve “Online” seçeneğine tıklanır. 
- Disk 1 yazısına tekrardan sağ tıklanır ve bu sefer “Inıtilaze disk” seçeneğine tıklanır. Sunulan iki opsiyondan GPT olan seçilir. Disk makineye tanıtılmış olur. 
- Bu işlemden sonra artık diskin makineye bağlanması gereklidir. Bunun için ilk olarak sağ tık yaparak “New Volume” seçilir. 
- Diskin ne kadarını tanıtılması istendiği sorulur. Bu kılavuz çerçevesinde tamamı diyerek devam edebiliriz. 
- Windows işletim sisteminde disklere bir harf atanır. D harfi seçili iken devam edebiliriz. 
- Diski formatlamak istenilip/istenilmediği sorulur. “Perform a quick format” opsiyonu seçili iken devam edilir. En son adımda “Finish” diyerek işlemler tamamlanır.

Windows tuşuna basıp “This PC” diye aratarak bilgisayarım seçeneğine gidilir. Bu ekrana gidildiğinde sanal makine oluşturulurken belirtilen root volume ve az önce oluşturulmuş olan EBS volume aşağıdaki Şekil: 37’deki gibi görülür.

![257](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/147517ed-0eeb-4c86-969a-c44d0f1b26c7)

Gerektiği durumda volume’lerin listelendiği listeden, gerekli volume seçilerek Actions ve modify volume seçenekleri ile kapasite arttırmak mümkündür. Örneğin az önce oluşturulan EBS volume değerini 20 GB daha arttıralım. Windows sanal makineye girildiğinde yeni 20 GB boyuta sahip disk tanımlanmış olur. 

Bu volume istenirse yukarıdaki işlemlerde yapıldığı gibi yeni bir harf ataması ile bir disk olarak atanabilir. İstenirse de var olan, cihaz tarafından tanınan, volume’e sağ tıklayarak “Extend volume” seçeneği ile var olan volume genişletilebilir. Böylelikle dosyalar silinmeden var olan disk depolama kapasitesi arttırılmış olur.

### 6.9.3. RAID Konfigürasyonu
Amazon EBS ile, bulut sunucunuz için belirli RAID yapılandırması işletim sistemi tarafından desteklendiği sürece, geleneksel bir yalın donanım sunucuyla kullanabileceğiniz standart RAID yapılandırmalarından herhangi birini kullanabilirsiniz. Bunun nedeni, tüm RAID'in yazılım düzeyinde gerçekleştirilmesidir. 

Amazon EBS birim verileri, tek bir bileşenin arızalanmasından kaynaklanan veri kaybını önlemek için bir erişilebilirlik alanındaki birden çok sunucu arasında çoğaltılır. Bu çoğaltma, Amazon EBS birimlerini tipik ticari disk sürücülerinden on kat daha güvenilir hale getirir. 

Bir RAID 0 dizisi oluşturmak, bir dosya sistemi için tek bir Amazon EBS biriminde sağlayabileceğinizden daha yüksek bir performans düzeyi elde etmenize olanak tanır. 

Girdi/Çıktı performansı çok önemli olduğunda RAID 0 kullanılır. RAID 0 ile G/Ç, birimler arasında bir şerit halinde dağıtılır. Bir birim eklerseniz, doğrudan aktarım hızı ve IOPS eklemesini elde edersiniz. Ancak, şeridin performansının kümedeki en kötü performans gösteren birim ile sınırlı olduğunu ve kümedeki tek bir birimin kaybının dizi için tam bir veri kaybıyla sonuçlandığını unutmamak gerekir. 

Bir RAID 0 dizisinin elde edilen boyutu, içindeki birimlerin boyutlarının toplamıdır ve bant genişliği, içindeki birimlerin kullanılabilir bant genişliğinin toplamıdır. Örneğin, 4.000 sağlanan IOPS'ye sahip iki adet 500 GiB io1 biriminin her biri, kullanılabilir 8.000 IOPS bant genişliği ve 1.000 MiB/s aktarım hızı ile 1000 GiB RAID 0 dizisi oluşturur. 

RAID 5 ve RAID 6, Amazon EBS için önerilmez çünkü bu RAID modlarının eşlikli yazma işlemleri, birimleriniz için mevcut olan IOPS'nin bir kısmını tüketir. RAID dizinizin yapılandırmasına bağlı olarak bu RAID modları, RAID 0 yapılandırmasından %20-30 daha az kullanılabilir IOPS sağlar. Artan maliyet, bu RAID modlarında da bir etkendir; aynı birim boyutları ve hızları kullanıldığında, 2 hacimli RAID 0 dizisi, maliyeti iki katına çıkan 4 hacimli RAID 6 dizisinden daha iyi performans gösterebilir. 

RAID 1'in Amazon EBS ile kullanılması da önerilmez. Veriler aynı anda birden çok birime yazıldığından RAID 1, RAID olmayan yapılandırmalara göre Amazon EC2'den Amazon EBS'ye daha fazla bant genişliği gerektirir. Ek olarak, RAID 1 herhangi bir yazma performansı iyileştirmesi sağlamaz. 

Linux işletim sistemine sahip bir sanal bulut sunucuda RAID 0 dizisi kurmak önemlidir. Bu prosedürü gerçekleştirmeden önce RAID 0 dizinizin ne kadar büyük olması gerektiğine ve kaç IOPS sağlamak istediğinize karar vermeniz gerekir. Bu işlemi tamamlamak için şu adımlar izlenebilir:

- Diziniz için Amazon EBS birimlerini oluşturun. Diziniz için aynı boyuta ve IOPS performans değerlerine sahip birimler oluşturun. EC2 bulut sunucunuzun kullanılabilir bant genişliğini aşan bir dizi oluşturmadığınızdan emin olun. 
- Amazon EBS birimlerini diziyi barındırmak istediğiniz örneğe ekleyin. ‒ Yeni eklenen Amazon EBS birimlerinden mantıksal bir RAID cihazı oluşturmak için ``mdadm`` komutunu kullanın. ``number_of_volumes`` için dizinizdeki birim sayısını ve ``device_name`` yerine dizideki her birim için aygıt adlarını ``(/dev/xvdf gibi)`` değiştirin. Ayrıca dizi için MY_RAID değerini kendi benzersiz adınızla değiştirebilirsiniz. 
- Cihaz adlarını bulmak için lsblk komutu ile sanal makinenizdeki cihazları listeleyebilirsiniz. 
- Bir RAID 0 dizisi oluşturmak için aşağıdaki komutu çalıştırın (diziyi şeritlemek için ``--level=0`` seçeneğine dikkat edin): 
``sudo mdadm --create --verbose /dev/md0 --level=0 --name=MY_RAID --raiddevices=number_of_volumes device_name1 device_name2``
- RAID dizisinin başlatılması ve eşitlenmesi için zaman tanıyın. Bu işlemlerin ilerlemesini aşağıdaki komutla takip edebilirsiniz: 
``sudo cat /proc/mdstat``
 Aşağıdaki örnek çıktıdır: 
 ``Personalities : [raid0]`` 
 ``md0 : active raid0 xvdc[1] xvdb[0] 41910272 blocks super 1.2 512k chunks`` ``unused devices: <none> ``
Genel olarak, aşağıdaki komutla RAID diziniz hakkında ayrıntılı bilgileri görüntüleyebilirsiniz: ``sudo mdadm --detail /dev/md0`` 
Aşağıdaki örnek çıktıdır: 
``/dev/md0:``

``Version : 1.2 ``
``Creation Time : Wed May 19 11:12:56 2021 ``
``Raid Level : raid0 ``
``Array Size : 41910272 (39.97 GiB 42.92 GB) ``
``Raid Devices : 2 ``
``Total Devices : 2 ``
``Persistence : Superblock is persistent ``
``Update Time : Wed May 19 11:12:56 2021 ``
``State : clean``
`` Active Devices : 2 ``
``Working Devices : 2 ``
``Failed Devices : 0 ``
``Spare Devices : 0 ``
``Chunk Size : 512K ``
``Consistency Policy : none ``
``Name : MY_RAID``
``UUID : 646aa723:db31bbc7:13c43daf:d5c51e0c ``
``Events : 0 ``
| ``Number`` |``Major``  | ``Minor`` |  ``RaidDevice`` | ``State`` |
|--|--| -- |--  | -- |
| ``0`` | ``202`` | ``16`` | ``0`` |`` active sync 		/dev/sdb``	|
| ``1`` | ``202`` | ``32`` | ``1`` |`` active sync 		/dev/sdc``	|
- RAID dizinizde bir dosya sistemi oluşturun ve bu dosya sistemine daha sonra bağlandığınızda kullanmak üzere bir etiket verin. Örneğin, MY_RAID etiketli bir ext4 dosya sistemi oluşturmak için aşağıdaki komutu çalıştırın: 
``sudo mkfs.ext4 -L MY_RAID /dev/md0``
Uygulamanızın gereksinimlerine veya işletim sisteminizin sınırlamalarına bağlı olarak, ext3 veya XFS gibi farklı bir dosya sistemi türü kullanabilirsiniz (ilgili dosya sistemi oluşturma komutu için dosya sistemi belgelerinize bakın). 

- RAID dizisinin önyükleme sırasında otomatik olarak yeniden birleştirildiğinden emin olmak için RAID bilgilerini içerecek bir yapılandırma dosyası oluşturun: 
``sudo mdadm --detail --scan | sudo tee -a /etc/mdadm.conf`` 
Amazon Linux dışında bir Linux dağıtımı kullanıyorsanız bu komutu değiştirmeniz gerekebilir. Örneğin, dosyayı farklı bir konuma yerleştirmeniz veya ``--examine`` parametresini eklemeniz gerekebilir. Daha fazla bilgi için Linux bulut sunucunuzda ``man mdadm.conf`` dosyasını çalıştırın. 

- Yeni RAID yapılandırmanız için blok cihaz modüllerini düzgün şekilde önceden yüklemek üzere yeni bir ram disk görüntüsü oluşturun: 
``sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r) ``
- RAID diziniz için bir bağlama noktası oluşturun. ``sudo mkdir -p /mnt/raid ``
- Son olarak, oluşturduğunuz bağlama noktasına RAID aygıtını monte edin:
``sudo mount LABEL=MY_RAID /mnt/raid`` RAID aygıtınız artık kullanıma hazırdır.

Linux işletim tarafında durum böyledir. Daha önceki başlıklar altında oluşturduğumuz Windows işletim sistemine sahip sanal bilgisayara RAID 5 konfigürasyonun nasıl yapıldığını beraber görelim. Bu işlemler için sırasıyla aşağıdaki adımlar tanımlanır.

- Başlık 4.6.9.2. Sanal Makineye Yeni Volume Eklenmesi konusunu referans alarak 3 adet volume oluşturarak başlayalım. Her volume’e tür olarak gp2, erişilebilirlik alanı olarak Windows sanal makine ile aynı AZ’yi ve sırasıyla etiket değerlerini de name anahtarına karşılık ‘birinci’, ‘ikinci’ ve ‘ucuncu’ şeklinde değerler atayalım. 
- Oluşturulan volume’leri sırasıyla Windows işletim sistemine sahip sanal makineye ‘attach’ işlemini uygulayalım. Yani oluşan diskleri, bu sanal makineye bağlayalım. ‒ Windows sanal makinemize, uzak masaüstü bağlantısı ile bağlandığımızda tüm diskler disk yönetimi ekranında görünecektir. 
- Tüm diskleri sırasıyla sağ tıklama ile ‘online’ yapalım. Online olan her diski de sağ tık ile GTP olarak başlatalım (initilaze). 
- Disklerden birine sağ tıklarsak “New RAID-5 Volume” seçeneğini kullanabiliriz. Tüm diskleri sırasıyla ‘selected’ alanına çekelim. ‒ Üç tane 20 GB disk kullanmamıza rağmen, total alan 40 GB görünmektedir. Bunun sebebi RAID-5 dizisidir. RAID-5 dizisi diğer disklerde birer parity bloğu tutuğu için tüm depolama alanı kullanılmayacaktır. 
- İleri diyerek bir harf ve isim ataması yapıp kurulumu tamamlarız. Kurulum tamamlanırken diskleri dinamik diske çevirmek için işletim sistemi izin isteyebilir. Bu adımda izin verip devam edilmelidir.

Tüm bu işlemlerden sonra bilgisayarım üzerinden baktığımızda raid-5 diski görünür. Her dosya üç diske birden yazılacaktır. Disklerden biri kaybedilse bile dosyalara ve diğer raid-5 disklerine erişmeye devam edebiliriz. 

Bu işlemlerden sonra Windows işletim sistemine sahip sanal makineyi silmek için terminate edebiliriz. Terminate edilen sanal makinenin kök diski otomatik silinirken, EBS üzerinden sonradan oluşturulan diskler otomatik olarak silinmez. Başka bir sanal bilgisayara aktarılmak üzere bekletilir.

### 6.9.4. EC2 ile Snapshots Kullanımı
EBS birimleri, Amazon EC2 için birincil kalıcı depolama seçeneğidir. Bu blok depolamayı, veri tabanları gibi yapılandırılmış veriler veya bir birimdeki dosya sistemindeki dosyalar gibi yapılandırılmamış veriler için kullanabilirsiniz. 

EBS birimleri belirli bir Erişilebilirlik Alanına yerleştirilir. Birimler, herhangi bir tek bileşenin arızalanmasından kaynaklanan veri kaybını önlemek için birden çok sunucu arasında çoğaltılır. Başarısızlık, hacmin boyutuna ve performansına bağlı olarak hacmin tamamen veya kısmen kaybolması anlamına gelir. 

EBS hacimleri, yüzde 0,1-0,2'lik bir yıllık başarısızlık oranı (AFR) için tasarlanmıştır. Bu, EBS birimlerini, yaklaşık yüzde 4'lük bir AFR ile başarısız olan tipik ticari disk sürücülerinden 20 kat daha güvenilir hale getirir. Örneğin, 1 yıl boyunca çalışan 1.000 EBS biriminiz varsa, bir veya iki birimin başarısız olmasını beklemelisiniz. 

Amazon EBS, verilerinizin belirli bir zamanda yedeklerini almak için bir anlık görüntü özelliğini de destekler. Tüm EBS birim türleri, dayanıklı anlık görüntü yetenekleri sunar ve yüzde 99,999 kullanılabilirlik için tasarlanmıştır. 

Amazon EBS, herhangi bir EBS biriminin anlık görüntülerini (yedeklerini) oluşturma olanağı sağlar. Anlık görüntü, EBS birimlerinizin yedeklerini oluşturmaya yönelik temel bir özelliktir. Bir anlık görüntü, EBS biriminin bir kopyasını alır ve onu birden fazla Erişilebilirlik Alanında yedekli olarak depolandığı Amazon S3'e yerleştirir. İlk anlık görüntü, birimin tam bir kopyasıdır; devam eden anlık görüntüler yalnızca artımlı blok düzeyindeki değişiklikleri depolar. 

Anlık görüntüyü aldığınız aynı bölgedeki Amazon EC2 konsolundan bir geri yükleme işlemi gerçekleştirebilir, bir anlık görüntüyü silebilir veya etiketler gibi anlık görüntü meta verilerini güncelleyebilirsiniz. 

Bir anlık görüntünün geri yüklenmesi, tam birim verileriyle yeni bir Amazon EBS birimi oluşturur. Yalnızca kısmi bir geri yüklemeye ihtiyacınız varsa, birimi farklı bir cihaz adı altında çalışan örneğe ekleyebilirsiniz. Ardından onu bağlayın ve verileri yedekleme biriminden üretim birimine kopyalamak için işletim sistemi kopyalama komutlarını kullanın. 

AWS, AMI'ler ve anlık görüntüler oluşturmak ve yönetmek için çok sayıda seçenek sunar. İhtiyaçlarınızı karşılayan yaklaşımı kullanabilirsiniz. Birçok müşterinin karşılaştığı yaygın bir sorun, anlık görüntü yaşam döngüsünü yönetmek ve anlık görüntüleri amaca, saklama ilkesine vb. göre net bir şekilde hizalamaktır. Uygun etiketleme olmadan, anlık görüntülerin yanlışlıkla veya otomatik bir temizleme işleminin parçası olarak silinme riski vardır. Ayrıca, hala gerekli olup olmadıklarına dair net bir anlayış olmadığı için tutulan eski anlık görüntüler için ödeme yapabilirsiniz. 

Bir AMI, bir bulut sunucusu başlatmak için gereken bilgileri sağlar. AMI, görüntü oluşturulduğunda örneğe eklenen EBS birimlerinin kök birimini ve anlık görüntülerini içerir. Yalnızca EBS anlık görüntülerinden yeni örnekler başlatamazsınız; bir AMI'den yeni örnekler başlatmanız gerekir. Bir AMI oluşturduğunuzda, kullandığınız hesapta ve bölgede oluşturulur. AMI oluşturma süreci, örneğe eklenen her birim için Amazon EBS anlık görüntüleri oluşturur ve AMI, bu Amazon EBS anlık görüntülerine atıfta bulunur. Bu anlık görüntüler Amazon S3'te bulunur ve son derece dayanıklıdır. 

EC2 bulut sunucunuzun bir AMI'sini oluşturduktan sonra, bulut sunucusunu yeniden oluşturmak veya örneğin daha fazla kopyasını başlatmak için AMI'yi kullanabilirsiniz. Ayrıca, uygulama geçişi veya DR için AMI'leri bir bölgeden diğerine kopyalayabilirsiniz.

![258](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e3348c12-38ec-4963-b5bd-875b4c5addb1)

VMWARE sanal makinesi gibi bir sanal makineyi AWS'ye geçirmiyorsanız, bir EC2 bulut sunucusundan bir AMI oluşturulmalıdır. Amazon EC2 konsolundan bir AMI oluşturmak için örneği seçin, eylemleri seçin, görüntüyü seçin ve ardından görüntü (Image) oluştur opsiyonunu seçin. 

Bir AMI yaratmak tek bir bulut sunucu ayarı oluşturmak ve bu bulut sununun kök diskinin snapshot’ını alarak diğer bulut sunucuları bu snapshot ile oluşturmak adına önemlidir. Böylelikle birden fazla aynı özelliklere sahip makine oluşturulmak istenildiğinde işlem oldukça kolaylaşır. Örneğin; önceki başlıklar altında oluşturduğumuz Amazon Linux işletim sistemine sahip bulut sunucuya nginx ve S3 içerisinde bulunan static web sayfasını almıştık. Eğer bu işlem birden fazla sanal makine için yapılacak ise, EC2 instance’ının snaphot’u alınır ve diğer sanal makineler bu snapshot ile oluşturulan AMI’lardan oluşturulur. Bu işlemleri yapmak için aşağıdaki adımlar izlenebilir:

- İlk olarak snapshot’ı alınacak olan bulut sunucu makinesi kapatılmalıdır. Aktif olarak çalışan bir sanal makinenin snapshot’ını almak risklidir ve sorunlar çıkarabilir. 
- Sanal makineyi kapattıktan sonra EC2 kontrol panelinde sol tarafta bulunan elastic block store alt başlığına gidilir ve snapshots seçeneği tıklanır. 
- Az önce kapatılan sanal makinenin volume’ü seçilerek oluşturulma başlanır. 
- Bir açıklama ve isim tag’i belirlenir. 
- AWS de bulunan EBS üzerinden yaratılmış volüme’lerin o andaki kopyasını alma işlemine snapshots denir. Bu snapshot’lar S3 bucket’ında tutulur ancak gidip S3 bucket’ından erişilemez ve görüntülenmez. Tüm işlemler EC2 kontrol paneli üzerinden gerçekleştirilir. 
- Oluşturulmuş bir snapshot’tan yeni bir volume veya AMI yaratılabilir. Sonrasında bu AMI ile tüm değişiklikleri tutan yeni sanal makineler oluşturulabilir. Başka bir region veya bulunan region altında kopyalama yapılabilir. 
- Daha önceki başlıklarda bir root diskin şifrelenmeyeceğini belirtmiştik. Ancak root diskin snapshot’u alınır ve kopyalama yaparken şifreleme seçeneği açılabilir. Sonrasında bu disk oluşturulacak bir sanal makinenin kök diski olarak seçilir ise kök disk şifrelenmiş şekilde başlatılmış olur. 
- Snapshot seçili iken create volume ile tür, boyut, AZ gibi değerler ile sıfırdan bir volume oluşturulma işlemleri gibi oluşturma yapılabilir. 
- Bu başlık altında AMI oluşturmaya odaklanacağımız için; create image diyerek işlemlere başlayabiliriz.
- Bir isim verilmesi istenir, sonrasında mimari ve açıklama seçilir. İsim olarak BaseAMI ve mimari olarak x86-64 değerlerini seçerek devam edelim. 
- Sanallaştırma türü olarak “Hardware virtuilaziton” seçilir ve oluşturulur. 
- AMI oluşturduktan sonra yeni instance oluşturulurken işletim sistemi seçilen ekranda AMI üzerinden oluşturulma yapılmasını istediğimizi ve benim AMI’larım seçeneği altında oluşturulan BaseAMI seçilir. 
- Sonrasında önceki başlıklar altında anlatıldığı gibi bir instance oluşturulur. Güvenlik grubu, IAM rolü gibi değişkenler seçilir. Gizli şifreye hala sahip olduğumuz onayını verdikten sonra instance çalıştırılır. 
- Başarıyla tamamladığımızı görmek için ``http://[PUBLIC_IP_ADDRESS]`` adresine gittiğimizde, daha önce oluşturulmuş olan sanal makinede barınan web sayfası görünecektir.

Tüm bu işlemler özellikle sistem mimarlarına birden fazla aynı konfigürasyona sahip bulut sunucu oluştururken büyük oranda kolaylık sağlar ve zamandan tasarruf ettirir.

### 6.9.5. EC2 ile Elastic Loud Balancer Kullanımı
Elastic Load Balancing, gelen trafiğinizi bir veya daha fazla erişilebilirlik alanında EC2 bulut sunucuları, kapsayıcılar ve IP adresleri gibi birden çok hedefe otomatik olarak dağıtır. Kayıtlı hedeflerinin sağlığını izler ve trafiği yalnızca sağlıklı hedeflere yönlendirir. Elastic Load Balancing, gelen trafikteki değişikliklere yanıt olarak yük dengeleyici kapasitenizi otomatik olarak ölçeklendirir. 

Yük dengeleyici, iş yüklerini sanal sunucular gibi birden çok işlem kaynağına dağıtır. Yük dengeleyici kullanmak, uygulamalarınızın kullanılabilirliğini ve hata toleransını artırır. 

Uygulamalarınıza yönelik genel istek akışını kesintiye uğratmadan, ihtiyaçlarınız değiştikçe yük dengeleyicinize işlem kaynakları ekleyebilir ve bu kaynakları kaldırabilirsiniz. 

Yük dengeleyicinin istekleri yalnızca sağlıklı olanlara göndermesi için işlem kaynaklarının durumunu izleyen sistem durumu denetimlerini yapılandırabilirsiniz. Ayrıca, bilgi işlem kaynaklarınızın ana işlerine odaklanabilmesi için şifreleme ve şifre çözme işini yük dengeleyicinize devredebilirsiniz. 

Bir load balancer yani yük dengeleyici oluşturmak için ilk olarak EC2 kontrol panelinde solda bulunan menüden “Load Balancing” başlığı altında bulunan “Load Balancers” seçeneğine tıklanır. Sonrası “Create Load Balancer” butonu ile yük dengeleyici oluşturulmaya başlanır. 

Bu başlık altında izleyeceğimiz adımlar bir senaryoya göre ilerlemektedir. Bir web sitemizin olduğunu (şu an EC2 bulut sunucuların ikisinde de aynı web sayfası var.) düşünelim. Birden fazla sunucuda bu web sitesini barındırmak ve bir kesinti olması durumunda, hizmete devam etmek istiyoruz. Bu senaryo öznelinde aşağıdaki adımları izleyerek ilk yük dengeleyicimizi oluşturalım:

- Yük dengeleyici türü seçim ekranında Application Load Balancer seçeneğini seçelim. 
- Bir isim atamamız gerekiyor. “ilklb” (ilk load balancer) adını verelim. 
- Şema bilgisi olarak Internet-facing seçeneğini seçelim. Çünkü senaryo uyarınca bizim elde ettiğimiz trafik dış dünyadan gelecek ve içeride kaynaklar arasında paylaşılacaktır.
- IP adres türü olarak IPv4’ü seçelim. 
- Network mapping altında tüm erişilebilirlik alanlarını seçelim. Bu seçenekler trafiği hangi AZ’lerde bulunan kaynaklar arasında dağıtacağımızı sorar. 
- Güvenlik grubu olarak daha önceki başlıklarda oluşturduğumuz. “Ec2-secuirtygroup” seçeneği ile devam edelim.
- Listener olarak varsayılan olan HTTP – 80 port seçeneği ile devam edelim. Default action kısmında “Create target group” seçeneği ile bir hedef grubu oluşturalım. Hedef türü olarak “Instances” seçip bir grup ismi belirleyelim. Health cheks başlığı altında AWS’nin sunucuya belli aralıklarla istek atmasını ve cevap alması durumunda trafik akışına devam etmesi için gerekli ayarlar bulunur. Bu değerleri varsayılan olarak bırakabiliriz.
- Oluşturulan target grubu load balancer üzerinden seçelim ve create ile yük dengeleyicimizi oluşturalım. 
- EC2 kontrol paneli üzerinden “Load Balancing” başlığı altında bulunan, “Target Groups” seçeneğine tıklayalım. Target seçili iken açılan ekranda “targets” sekmesine sahip olunan iki instance’ı ekleyelim ve kaydedelim. 
- Tüm bu işlemler sonunda tanımlanan load balancer’in DNS değerinden siteye ulaşılabilir.

Farkı görmek zor olacaktır. Bu yüzden sanal makinelere sırayla bağlanarak index.html dosyasında bir değişiklik yapabiliriz. Böylelikle yük dengeleyici çalışma mantığı daha kalıcı olacaktır. Bu işlem için şu adımları izleyelim:

- İlk sunucuya PuTTY aracı ile bağlanalım. 
- ``sudo su`` komutu ile yönetici yetkisi elde edelim. 
- ``nano /usr/share/nginx/html/index.html`` komutu ile ``index.html`` dosyamızı nano editör ile açalım. Sayfa içerisinde etiketleri arasında bulunan bir yere “SUNUCU1” yazalım. ``Ctrl + X``, sonrasında y ve enter tuşları ile kaydı tamamlayalım. 
- Bu işlemleri diğer sunucu için de uygulayalım ve bu sefer “SUNUCU2” yazalım.

Yukarıdaki işlemler yapıldıktan sonra tanımlanan yük dengeleyici DNS adresine ulaşıp sayfayı birkaç kez yenilediğimizde “SUNUCU1” ve “SUNUCU2” yazılarını göreceğiz. Load balancer iki sunucuyu da eş zamanlı kullanmaktadır. 

Hedef grupların listelendiği ekrana gelirsek ve oluşturulmuş olan hedef gruba tıklarsak sunucuların durumu görünecektir.

![259](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/df2cdc19-b189-409d-aa2e-ce85e8bc8925)

EC2 kontrol paneli üzerinden sunuculardan birini kapatmamız durumunda o sunucu unhealthy yani sağlıksız olarak işaretlenecektir ve yük dengeleyici sadece diğer sunucu üzerinden hizmet vermeye devam edecektir. Bunu şu durumda sayfayı yenileyerek görebiliriz.

### 6.9.6. EC2 ile Auto Scaling Kullanımı
Amazon EC2 Auto Scaling, uygulamanızın yükünü işlemek için doğru sayıda Amazon EC2 bulut sunucusuna sahip olduğunuzdan emin olmanıza yardımcı olur. Otomatik ölçeklendirme grupları adı verilen EC2 örnekleri koleksiyonları oluşturursunuz. Her Auto Scaling grubunda minimum örnek sayısını belirtebilirsiniz ve Amazon EC2 Auto Scaling, grubunuzun asla bu 133 boyutun altına düşmemesini sağlar. Her Auto Scaling grubunda maksimum örnek sayısını belirtebilirsiniz ve Amazon EC2 Auto Scaling, grubunuzun asla bu boyutun üzerine çıkmamasını sağlar. Grubu oluştururken veya sonrasında herhangi bir zamanda istediğiniz kapasiteyi belirtirseniz Amazon EC2 Auto Scaling, grubunuzun bu kadar çok örneğe sahip olmasını sağlar. Ölçeklendirme ilkelerini belirtirseniz Amazon EC2 Auto Scaling, uygulamanızdaki talep arttıkça veya azaldıkça bulut sunucularını başlatabilir veya sonlandırabilir. 

Örneğin, aşağıdaki Şekil: 40’ta verilen otomatik ölçeklendirme grubunun minimum boyutu bir örnek, istenen kapasitesi iki örnek ve maksimum boyutu dört örnektir. Tanımladığınız ölçeklendirme ilkeleri, belirttiğiniz ölçütlere göre minimum ve maksimum örnek sayınız dahilinde örnek sayısını ayarlar.

![260](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ffeeaf83-9a10-4b10-8d99-e82a595e4e68)

Auto Scaling, iki temel bileşenden oluşur bunların ilki “Launch Configuration”dur. Bu bileşen sadece auto scaling servisinde bulunmaz. Bir sanal bulut sunucusu oluştururken AMI, rol, güvenlik grubu gibi birçok ayar yapılandırılır. Launch Configuration ise bu seçilen ayarların hepsinin bir kere belirlenip bir dosyada tutulmasıdır. Auto scaling servisi bir sunucu oluştururken bu ayarlamaları otomatik olarak oluşturduğunuz launch configuration üzerinden alacaktır. Oluşturmak için aşağıdaki adımlar izlenmelidir:

- EC2 kontrol paneli üzerinde sol tarafta bulunan menülerden “Auto Scaling” başlığı altında bulunan “Launch Configuration” seçeneğine tıklanır. 
- Create diyerek ilk başlatma yapılandırması (Launch Configuration) oluşturulur. 
- İlk olarak bir isim belirlenmelidir. Bu kılavuz kapsamında adını “ilk-launchconfig” olarak belirleyelim. 
- AMI olarak daha önceki başlıklarda oluşturulan “BaseAMI” ı seçelim. 
- Instance type olarak t2.micro seçeneği seçelim. 
- IAM rolü olarak yine daha önceki başlıklarda oluşturulan “EC2-S3-Full-Access” seçeneğini kullanalım. 
- Volume, varsayılan olarak gelen root volume’ü olarak kalsın. 
- Güvenlik grubu olarak daha önceki başlıklarda oluşturulmuş olan “Ec2-SecuirtyGroup” opsiyonu ile devam edelim. 
- Key pair için daha önce Windows işletim sistemine bağlanmak için sahip olduğumuz anahtarı kullanalım.

Launch Configuration yani başlatma yapılandırması başarıyla tamamlandıktan sonra yine sol menüde aynı başlık altında bu “Auto Scaling Group” seçeneğini kullanalım. Aşağıdaki adımları takip ederek auto scaling group oluşturabiliriz:

- Create butonu ile ayarlamalara başlayalım. 
- Bir isim verelim. Bu kılavuz kapsamında isim olarak “ilk-auto-scaling-group” adını kullanıyoruz. 
- Launch template bilgisi istenen alanda, sağ üstte bulunan “switch the launch configuration” seçeneğini kullanalım. 
- Bu ayarlamadan sonra az önce oluşturulan “ilk-launch-config”i seçelim. İleri diyerek sonraki adıma geçelim. 
- Network seçenekleri kısmında VPC değerini varsayılan olarak bırakalım ve tüm AZ değerlerini ekleyelim. İleri diyerek sonraki adıma geçelim.
- Auto scaling grup kapsamında oluşacak sanal bulut sunucuları bir load balancer arkasında çalıştırabiliriz. Load balancing kısmında var olan load balancer’ı seçmek istediğimi belirtip. Daha önceki başlıkta seçili olan load balancer’ı seçelim. 
- Health check kısmında ELB seçeneğini işaretleyelim. İleri diyerek sonraki adıma geçelim. 
- Aynı anda min. 2 sanal bulut sunucumuzun olmasını belirtmek için desired ve minimum kapasite değerlerini 2 olarak ayarlayalım. Maksimum kapasite değerini ise 4 olarak atayalım. 
- Scaling policies kısmında “Target tracking scaling policy” seçeneğini seçelim. Alta çıkan yeni seçeneklerde metrik türü olarak Avarage CPU Utilization seçeneğini kullanıp değer olarak 30 verelim. Böylelikle aynı anda çalışan iki sunucu %30 üzerinde CPU kullanmaya başlarsa yeni bir sunucu eklenecek ve %30 altına geri düşmesi durumunda tekrar sunucuları silecek yani terminate edecektir. 
- Notification kısmında olası bir yeni makine oluşturulmasında AWS SNS servis aracılığı ile e-posta almak isteyip-istemediğimizi sorar. Şimdilik eklemeden devam edelim. 
- Oluştur diyerek auto scaling grubumuzu oluşturalım.

EC2 kontrol panelini girdiğimizde oluşturulan yeni iki sanal makine listelenecektir. Targets grubuna bakıyoruz ve load balancers içerisinde DNS adresini açalım. Daha önceki ilk iki sunucudaki web sayfasının aynısı görünecektir. Ve bu sefer diğer ikisinin index.html dosyasında yaptığımız değişikliğin olmadığı web sayfası yani orijinal hali görünecektir. 

EC2 kontrol paneli üzerinden oluşturulan instance’lerden birini terminate edelim ve sonrasında auto scaling groups’ta bulunan “ilk-auto-scaling-group” seçili iken aşağıda açılan pencereden “Activity” sekmesi aşağıdaki gibi görünecektir.

![261](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/0f94f337-7f56-487c-90be-f454763ac5d0)

Şekli incelersek terminate edilen yani silinen instance yerine yenisinin oluşturulduğu bildirilmiştir. 

Daha önceden manuel olarak oluşturulan iki sunucu varken auto scale group neden yeni sunucu yaratır? Bu sorunun cevabı şu şekilde özetlenebilir: Auto Scaling grup, kullanıcıların mevcut instance ortamına bakmaz. Çünkü her ne kadar sanal makineler aynı işlemi yapsa da auto scaling grup var olan sunucuların ne iş yaptığını bilemez. Bu durumdan dolayı, auto scaling gruba var olan sunucuları tanıtmamız gerekir. Bu eylem için, sanal bulut sunucu seçili iken, Actions → Instance settings → Attach to Auto Scaling Group seçenekleri izlenir. Bu işlem iki sunucuya da uygulanır. 

Bu işlemler tamamlandıktan sonra, auto scale gruba dönünce desired kapasite değeri 2’den 4’e çıkmış olarak görünür. Manuel olarak eklenen sanal bulut sunucuları bu sayıyı (arzu edilen kapasite) arttırır. Bu işlemi düzenlemek için, oluşturulan grup seçili iken Actions→ Edit → Desired Capacity değeri tekrardan ikiye indirilir. Auto scaling grupta, activity history üzerinde bu güncelleme değerlerine yer verilir. 

Şimdi de %30 üzerinde CPU kullanımında yeni sunucu eklenmesi durumunu gözlemleyelim. Bunu gerçek zamanlı olarak binlerce kullanıcı bulamayacağımız için bir paket yardımıyla yapacağız. Aktif olarak çalışan iki sanal makineden birine bağlanalım PuTTY üzerinden bağlanalım. Sonra sırasıyla aşağıdaki adımları izleyelim:

- ``sudo su``, komutu ile root yetkisini alalım. 
- ``yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest7.noarch.rpm``, ile gerekli indirmeyi yapalım. 
- ``yum install stress``, ile kurulumu yapalım. 
- ``stress --cpu 80 --timeout 2000``, komutu ile CPU kullanımını başlatalım ve EC2 instance içerisinde monitoring yaparak izleyelim.

Auto scaling %30’u geçince tespit edecektir. İki sunucunun ortalaması %30 değerinden yüksek olduğu için iki tane yeni instance oluşturulmaya otomatik olarak başlanır. 

Auto scaling tüm bu işlemlerin verilen yörüngelerde otomatik olarak tanımlanmasını sağlamaktadır.


