# 13. RedShift (Bulut Veri Ambarı)

Amazon Redshift, her ölçekte en iyi fiyat performansını sunmak için AWS tarafından tasarlanan donanım ve makine öğrenimi kullanarak veri ambarları, operasyonel veri tabanları ve data-lake'ler bünyesindeki yapılandırılmış ve yarı yapılandırılmış verileri analiz etmek üzere SQL kullanır.

![277](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/908d2ba7-a9fc-4c84-9922-851d60cec973)

Veri ambarınızın yönetimini düşünmek zorunda kalmadan saniyeler içinde veriden ön görülere ulaşmaya ve iş sonuçlarınızı elde etmeye odaklanmanızı sağlar. 

***Amazon Redshift Sunucusuz:***  Veri ambarı altyapısını ayarlayıp yönetmeye gerek kalmadan analizleri saniyeler içinde kolayca çalıştırmanızı ve ölçeklendirmenizi sağlayan, Amazon Redshift'in sunucusuz seçeneğidir. Redshift sunucusuz sayesinde veri analistleri, geliştiriciler, iş uzmanları ve veri bilimcileri dahil her kullanıcı, verileri veri ambarına yükleyip sorgulamak suretiyle kolayca öngörüler elde edebilir. 

***Sorgu Düzenleyicisi v2:*** Veri keşfi ve analizine yönelik web tabanlı bir analist workbench'i ile Amazon Redshift verilerinizi ve data-lake'inizi veri analistleri, veri mühendisleri ve diğer SQL kullanıcıları için daha erişilebilir kılmak üzere SQL'i kullanabilirsiniz. Sorgu düzenleyicisi v2, sorgu sonuçlarını tek bir tıklamayla görselleştirmenize, şemalar ve tablolar oluşturmanıza, verileri görsel olarak yüklemenize ve veri tabanı nesnelerine göz atmanıza olanak sağlar. Ayrıca SQL sorgularını, analizleri, görselleştirmeleri ve ek açıklamaları yazarak ekibinizle güvenli bir şekilde paylaşmanız için sezgisel bir düzenleyici sunar. 

***Otomatik Tablo Tasarımı:*** Amazon Redshift, kullanıcı iş yüklerini izler ve sorgu hızlarını optimize etmek üzere verilerin fiziksel yerleşimini iyileştirmek için sofistike algoritmalar kullanır. Otomatik tablo optimizasyonu, performansı kümenin iş yüküne göre optimize etmek için en iyi sıralama ve dağıtım anahtarlarını seçer. Amazon Redshift bir anahtarı uygulamanın küme performansını iyileştireceğini belirlerse yöneticinin müdahalesine gerek kalmadan tablolar otomatik olarak değiştirilir. Otomatik vakum silme, otomatik tablo sıralama ve otomatik analiz ek özellikleri de Redshift kümeleri için manuel bakım ve iyileştirme ihtiyacını ortadan kaldırarak hem yeni kümeler hem de üretim iş yükleri için en yüksek performansı sağlar.

Kendi araçlarınızı kullanarak sorgulama yapın: Amazon Redshift size konsoldan sorgu çalıştırma veya SQL istemci araçlarını, kitaplıklarını veya Amazon Quicksight, Tableau, PowerBI, QueryBook ve Jupyter Notebook dahil veri bilimi araçlarını bağlama esnekliğini sunar. 

Amazon Redshift ile etkileşim kuracak basit bir API: Amazon Redshift her türlü geleneksel, bulut temelli ve container'lı, sunucusuz web hizmetleri tabanlı uygulamalar ve olay odaklı uygulamalarla verilere sorunsuz şekilde erişmenize olanak tanır. Amazon Redshift Veri API'si, AWS SDK tarafından desteklenen Python, Go, Java, Node.js, PHP, Ruby ve C++ gibi programlama dilleri ve platformlarından veri erişimini, alımını ve çıkışını basitleştirir. Veri API'si, sürücüleri yapılandırma ve veri tabanı bağlantılarını yönetme ihtiyacını ortadan kaldırır. Bunun yerine, Veri API'si tarafından sağlanan güvenli bir API uç noktasını çağırarak bir Amazon Redshift kümesinde SQL sorguları çalıştırabilirsiniz. Veri tabanı bağlantılarını yönetme ve verileri arabelleğe alma işini Veri API'si üstlenir. Veri API'si zaman uyumsuz olduğundan, sonuçlarınızı daha sonra alabilirsiniz. Sorgu sonuçlarınız 24 saat boyunca depolanır. 

***Hata toleranslı:*** Veri ambarı kümenizin güvenilirliğini artıran çok sayıda özellik vardır. Örneğin Amazon Redshift, kümenin durumunu sürekli olarak izler. Arızalanan sürücülerden verileri otomatik olarak yeniden çoğaltır ve hata toleransı için düğümleri gerektikçe yeniler. Kümelerin herhangi bir veri kaybı veya uygulama değişikliği olmadan alternatif erişilebilirlik alanlarına (AZ) taşınması da mümkündür.

SQL tabanlı veri tabanları iki farklı sistem üzerine inşa edilmiştir:

- OLTP (On-line Transaction Processing)
-- Veri Tabanı (RDS) 
-- Veri girişi ve veri manipülasyonu 
-- Operasyonel günlük veri işlemleri için 
-- Veri analiz sorgularını çalıştırmak veri tabanının performansını düşürüyor ve mevcut iş akışının yavaşlamasına neden oluyor. 
-- Mevcut verileri saklamak için kullanılır. 
- OLAP (On-line Analytical Processing) 
-- Veri Ambarı (RedShift) 
-- Veri analizi 
-- Birleştirilmiş birden fazla kaynaktan gelen veri ile analiz için kullanılır. 
-- Oluşan veriyi analiz etmek için bu kullanılır.

Bu servisi bir senaryo üzerinden ele alalım. Diyelim ki Türkiye’nin 81 iline hizmet veren bir online web mağazası yönetiyoruz. Kullanıcıların, kullanıcı adı, adı, soyadı; mağaza ürünleri, ürünlerin bilgileri bir yapıda tutulmalıdır. Bununla beraber yapılan satın alma işlemleri, kredi kartı bilgileri ve fatura bilgileri de tutulmalıdır. 

Pazarlama bölümünün şöyle bir talepte bulunduğunu varsayalım: Yeni bir kampanya üzerinde çalışılıyor. Bu yüzden İç Anadolu bölgesinde en çok satılan on temizlik malzemesi ürününü ve satış rakamlarını listelememiz bekleniyor. Bununla beraber kadın-erkek, yaş aralıklarına göre satılma oranlarını da listelememiz ve bu sonuçları geçen senenin aynı verileri ile karşılaştırmanız istenir. 

Gerekli SQL sorgusu karmaşık da olsa hazırladık diyelim. Sorguyu çalıştırırsak web sitesi yavaşlayacak çünkü sorgu sistem kaynaklarını tüketecektir. Bu yüzden veri ambarları kullanılır. 

Bununla beraber senaryomuzu genişletirsek, diğer ülkelerde de mağazalar açtığımızı ve bu sorguyu tüm ülkeler için yapmamız istenirse. Bu iyice zor bir süreç haline gelir. Kullanıcının verilerin tek bir ortamda toplanıp sonrasında analiz etmesi gerekmektedir. Bu ihtiyaçtan dolayı veri ambarları ortaya çıkmıştır.


