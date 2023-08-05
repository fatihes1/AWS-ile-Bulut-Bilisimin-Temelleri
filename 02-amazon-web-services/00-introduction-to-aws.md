# 1. Amazon Web Servislerinin Tarihçesi

Fikir, Amazon tarafında verimlilik geliştirme ihtiyacından ve iş büyüdükçe hızla ölçeklendirme ihtiyacından kaynaklandı. 

2003 yılında Amazon, rakiplerine kıyasla önemli bir avantaja sahip olduklarını fark etti. Bu avantaj, Amazon altyapı hizmetleri ve altyapılarını güvenilir ve verimli bir şekilde yönetme ve ölçeklendirme yetenekleriydi. Amazon Web Servisleri fikri ilk olarak burada doğdu. 

Fikir, farklı donanım kaynaklarının (yani bilgi işlem, depolama, bellek vb.) bu işletim sisteminin bileşenleri olarak yalıtıldığı ve tüm “farklılaştırılmamış ağır yükleri” alan yönetilen hizmetler olarak sunulduğu bir 'İnternet İşletim Sistemi' olarak başladı. Bu, donanım ve fiziksel altyapıyı yönetme ihtiyacını ortadan kaldıran ve işletmelerin kendi iş durumlarına odaklanmalarını sağlayan devrim niteliğinde bir fikirdi. 

Amazon, bu fikri gerçeğe dönüştürmek için harekete geçmeye karar verdi. Amazon, (zorunluluktan dolayı) güvenilir ve uygun maliyetli veri merkezleri inşa etmede zaten harikaydı ve bu fikri giderek daha fazla keşfetmeye devam ettikçe, bu bilgi işlem alanının sadece dokunulmamış olmadığını, aynı zamanda Amazon için büyük bir potansiyele sahip olduğunu fark ettiler. İşletme ve kendi başına Amazon'un bir kolu olarak AWS hayata geçmiş oldu. 

AWS'nin başlangıcı, Amazon Simple Queue Service'in (Amazon SQS) başlatıldığı 2006 yılındaydı. Bunu kısa bir süre sonra S3, EC2 izledi ve AWS tarafından yapılan bu ilk tekliflerle, AWS'yi bulut bilişimde küresel bir oyuncu olmaya itmek için temeller inşa ediliyordu. 

O zamandan beri, AWS büyük adımlarla ilerleyerek Re:invent, Storage Day, Re:inforce gibi birçok konferansa ev sahipliği yaptı. Depolama, bilgi işlem, makine öğrenimi, IoT, vb. tabanlı geniş bir hizmet yelpazesiyle toplam hizmet miktarı 200'ün üzerine çıktı. Bu hem yeni başlayanların hem de kuruluşların, ölçeklenebilir, yönetilebilir çözümler oluşturabileceklerinden çok daha hızlı bir şekilde oluşturabilmesini sağladı.

# 2. AWS Küresel Alt Yapısı

Ağ bağlantılarının hızlanmasına paralel olarak talep edilen veri miktarı da arttı. Bu nedenle bulut bilişime karşı olan en büyük çekince; kendi bünyesinde barındırıp çok hızlı erişilebilecek hizmetlere başka bir lokasyon üzerinden ulaşarak yavaş erişim problemidir. Bir lokasyona fiziksel olarak ne kadar uzak olunursa hizmet o kadar yavaş olacaktır. AWS bu sorunu küresel alt yapısı sayesinde çözmeye çalışmaktadır. 

Dünya çapındaki veri merkezlerinden 200’ün üzerinde tam özellikli hizmet sunan AWS Küresel Bulut Altyapısı, en güvenli, en kapsamlı ve en güvenilir bulut platformudur. Uygulama iş yüklerinizi tek tıklamayla tüm dünyaya dağıtmanız gerektiğinde veya son kullanıcılarınıza daha yakın konumdan milisaniye cinsinden tek basamaklı gecikme sürelerine sahip özel uygulamalar oluşturmak ve dağıtmak istediğinizde, AWS size ihtiyaç duyduğunuz yerde ve zamanda bulut altyapısı sağlar.

## 2.1. Bölgeler
AWS'de, veri merkezlerini bir araya topladığımız dünya çapındaki fiziksel konumları ifade eden “Bölge” (region) kavramı bulunmaktadır. Her bir mantıksal veri merkezi grubunu Erişilebilirlik Alanı olarak adlandırırız. Her bir AWS bölgesi, bir coğrafi bölge içinde yalıtılmış ve fiziksel olarak ayrı şekilde konumlandırılmış birden fazla AZ'den (Availability Zone - Erişilebilirlik Alanı) oluşur. Bir bölgeyi genellikle tek bir veri merkezi olarak tanımlayan diğer bulut sağlayıcılarından farklı olarak, her AWS bölgesinde birden fazla AZ bulunması 26 müşterilere avantajlar sunar. Tüm AZ'ler, bağımsız güç, soğutma ve fiziksel güvenlik sistemlerine sahiptir ve son derece düşük gecikmeye sahip yedekli ağlar üzerinden birbirine bağlıdır. Yüksek erişilebilirliğe odaklanan AWS müşterileri, daha fazla hata toleransı elde etmek için uygulamalarını birden fazla AZ'de çalışacak şekilde tasarlayabilir. AWS altyapı bölgeleri (region) en yüksek güvenlik, uygunluk ve veri koruma düzeylerini karşılar. 

AWS, diğer bulut sağlayıcılarının tümünden daha geniş bir küresel ayak izi sunmakta ve hem bu küresel ayak izini desteklemek hem de müşterilerin dünya genelinde hizmet aldığından emin olmak için hızla yeni bölgeler açmaktadır. AWS; Kuzey Amerika, Güney Amerika, Avrupa, Çin, Asya Pasifik, Güney Afrika ve Orta Doğu dahil olmak üzere birden fazla coğrafyada bölgeye sahiptir.

## 2.2. Erişilebilirlik Alanları
Bir Erişilebilirlik Alanı (AZ), bir AWS bölgesindeki yedekli güç, ağ iletişimi ve bağlantıya sahip bir veya daha fazla ayrık veri merkezidir. AZ'ler, müşterilerin tek bir veri merkezinin sunabileceğinden daha yüksek oranda erişilebilir, hata toleranslı, ölçeklenebilir üretim uygulamaları ve veri tabanları kullanabilmesini sağlar. Bir AWS bölgesindeki tüm AZ'ler; AZ’ler arasında yüksek aktarım hızına ve düşük gecikmeye sahip ağ iletişimi sunmanın yanı sıra tam yedeklilik sağlayan, tahsis edilmiş metro fiber ağı üzerinden yüksek bant genişliği ve düşük gecikmeli ağ iletişimi ile birbirine bağlıdır. AZ'ler arasındaki tüm trafik şifrelenir. Ağ performansı, AZ’ler arasında zaman uyumlu çoğaltma yapmak için yeterlidir. AZ'ler, yüksek erişilebilirlik için uygulamaları bölümlere ayırmayı kolaylaştırır. Bir uygulama AZ'ler arasında bölümlere ayrıldığında, şirketler güç kesintileri, yıldırım, kasırga ve deprem gibi sorunlardan daha iyi korunur ve yalıtılır. Tüm AZ'ler, diğer AZ'lerden mantıklı bir mesafede bulunmaları için fiziksel olarak kilometrelerce uzağa konumlandırılmakla birlikte hepsi birbirine 100 km (60 mil) mesafe içinde yer alır.

## 2.3. AWS Yerel Alanları
AWS Yerel Alanları işlem, depolama, veri tabanı ve diğer seçili AWS hizmetlerini son kullanıcılara daha yakın konuma getirir. AWS Yerel Alanları sayesinde medya ve eğlence içeriği üretimi, gerçek zamanlı oyun, rezervuar simülasyonları, elektronik tasarım otomasyonu ve makine öğrenimi gibi, son kullanıcılarınıza on milisaniyeden kısa gecikme süreleri sunmanızı gerektiren zorlu gereksinimlere sahip uygulamaları kolayca çalıştırabilirsiniz. 

Her AWS yerel alanı; Amazon Elastic Compute Cloud, Amazon Virtual Private Cloud, Amazon Elastic Block Store, Amazon File Storage ve Amazon Elastic Load Balancing gibi AWS hizmetlerini son kullanıcılara coğrafi olarak yakın konumda kullanarak gecikme açısından hassas uygulamalarınızı çalıştırabileceğiniz bir AWS bölgesinin uzantısıdır. Yerel iş yükleri ile AWS bölgesinde çalışan iş yükleri arasında yüksek bant genişliğine sahip güvenli bağlantı sunan AWS yerel alanları, bölgedeki tüm hizmetlere aynı API'ler ve araç kitleri aracılığıyla sorunsuz bir şekilde bağlanmanızı mümkün kılar.

## 2.4. AWS Wavelength
WS Wavelength, geliştiricilerin mobil cihazlara ve son kullanıcılara on milisaniyeden kısa gecikme süreleri sunan uygulamalar oluşturmasına imkân tanır. AWS geliştiricileri, uygulamalarını wavelength alanlarına dağıtarak bölgedeki AWS hizmetlerinin tümüne sorunsuz bir şekilde erişebilir. Wavelength alanları, AWS işlem ve depolama hizmetlerini 5G ağların uç noktasına getirerek telekomünikasyon sağlayıcılarına ait veri merkezlerine ekleyen AWS altyapı dağıtımlarıdır. Bu, geliştiricilerin oyun ve canlı video akışı, uçta makine öğrenimi çıkarımı, artırılmış ve sanal gerçeklik (AR/VR) gibi, on milisaniyeden kısa gecikme süreleri gerektiren uygulamalar sunmasını sağlar. AWS Wavelength, AWS hizmetlerini 5G ağ uç 27 noktasına getirerek, mobil cihazdan bir uygulamaya bağlanmaya ilişkin gecikme süresini en aza indirir. Uygulama trafiği, mobil sağlayıcının ağından çıkmadan, dalga boyu bölgelerinde çalışan uygulama sunucularına ulaşabilir. Bu, internete yönelik ekstra ağ atlamalarını azaltır. Bu atlamalar, 100 milisaniyeden fazla gecikme sürelerine yol açarak müşterilerin 5G'deki ağ genişliği ve gecikme süresi iyileştirmelerinden tam olarak faydalanmasını engelleyebilir.

## 2.5. AWS Küresel Alt Yapı Haritası
AWS 2022 mayıs ayı itibariyle bünyesinde;
- Kullanıma sunulmuş 26 bölge ve her bölgede birden fazla erişilebilirlik alanı, 
- 84 erişilebilirlik alanı, 
- 17 yerel bölge (Local Zones) ve 25 dalga boyu bölgesi (Wavelength Zones), 
- Duyurulan 8 bölge ve 32 yerel bölge, 
- İkinci en büyük bulut sağlayıcısına oranla 2 kat daha fazla bölge, 
- Hizmet sunulan 245 ülke ve bölge, 
- 108 direkt bağlantı konumu, 
- 310’dan fazla varlık noktası (PoP), barındırmaktadır.
 
 Küresel çaptaki etkin milyonlarca müşterisi ve on binlerce çözüm ortağıyla AWS, en geniş ve en dinamik ekosisteme sahiptir. Start-up'lar, kuruluşlar ve kamu sektörü kurumları dahil olmak üzere neredeyse her sektörden ve her boyuttaki müşteriler, akla gelebilecek tüm kullanım örneklerini AWS'de çalıştırmaktadır.
 
XX Şekil

Müşteriler, bulut tabanlı altyapılarını barındırmak ve gittikleri her yerde daha iyi performans, güvenlik, güvenilirlik ve ölçek sağlamak için giderek artan oranda AWS'yi tercih ediyor. AWS, raporda adı geçen en iyi 7 satıcı arasından iş gerçekleştirme becerisi ve vizyon bütünlüğü ölçümlerinde ilk sırayı alarak üst üste 11. kez 2021 Gartner Magic Quadrant for Cloud Infrastructure and Platform Services listesinde “Lider” unvanına layık görüldü. 

AWS Cloud, dünya çapındaki 26 coğrafi bölgede 84 erişilebilirlik alanını kapsar. Ayrıca, 24 erişilebilirlik alanının yanı sıra Avustralya, Kanada, Hindistan, İsrail, Yeni Zelanda, İspanya, İsviçre ve Birleşik Arap Emirlikleri'nde (BAE) 8 AWS bölgesinin daha planlandığı açıklanmıştır. Aşağıdaki resimde aktif ve duyurulan bölgeler noktalar ile gösterilmiştir.

XX Şekil

# 3. AWS Yönetim Konsolu
AWS Management Console, AWS kaynaklarını yönetmek için geniş bir hizmet konsolları koleksiyonunu içeren ve bunlara atıfta bulunan bir web uygulamasıdır. İlk oturum açtığınızda konsol ana sayfasını görürsünüz. Ana sayfa, her bir hizmet konsoluna erişim sağlar ve AWS ile ilgili görevlerinizi gerçekleştirmek için ihtiyaç duyduğunuz bilgilere erişmek için tek bir yer sunar. Ayrıca son ziyaret edilenler, AWS Health, Trusted Advisor ve daha fazlası gibi widget'lar ekleyerek, kaldırarak ve yeniden düzenleyerek konsol ana sayfası deneyimini özelleştirmenize olanak tanır. 

Bireysel hizmet konsolları ise, bulut bilişim için çok çeşitli araçların yanı sıra hesabınız ve faturalandırmanız hakkında bilgiler sunar.

XX Şekil

Sağ üstte kullanıcı adının sol tarafında (Şekil: 11’de N.Virginia olarak görünen alan) “region” yani bölge seçilebilmektedir. Kaynaklar hangi bölge üzerinden oluşturulmak istenirse o bölge seçilip servis oluşturma işlemi sonrasında yapılmalıdır. 

Sol üste bulunan ‘Services’ sekmesinde tüm servisler alt kategoriler halinde listelenmiştir. Hangi uygulamanın hangi servis üzerinde çalıştığını izlemek için ise arama alanına ‘Resorces Groups’ yani ‘kaynak grupları’ yazılabilir. Oluşturulan tüm kaynaklara bir “tag” yeni etiket ataması yapılabilir. Böylelikle kaynakları birbirinden ayırmak daha kolay olacaktır ve karışıklığın önüne geçilecektir. Etiketleme işlemi bir anahtar-değer şeklinde tanımlanmaktadır. Örneğin satış departmanı için oluşturulan sanal makine servisini ‘departman:satis’ şeklinde etiketlemek mümkündür. Bu etiketlemeden sonra bu tag diğer kaynaklara verildiğinde hepsi aynı sekme altında görünecektir. Oluşturulan kaynakları bu şekilde sınıflandırmak ve etiketlere göre kaynakların durumlarını izleyebilmek kullanıcıların işini oldukça kolaylaştırmaktadır.
