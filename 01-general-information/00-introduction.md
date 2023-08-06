# 1. Giriş

Bulut bilişim, BT kaynaklarının internet üzerinden, istek üzerine ve kullandıkça ödeme fiyatlandırmasıyla sunulmasıdır. Fiziksel veri merkezleri ve sunucuları satın almak, bunlara sahip olmak ve sürekliliklerini sağlamak yerine, Amazon Web Services (AWS) gibi bir bulut sağlayıcının sunduğu işlem gücü, depolama ve veri tabanları gibi teknoloji hizmetlerine ihtiyaç duyduğunuzda erişebilirsiniz.

# 2. Sanallaştırma
## 2.1. Sunucu-İstemci Modeli
Sunucu (Server), hizmet sunan, güçlü ve yüksek kapasiteli işlem gücüne sahip makinelerdir. Uzun süreli, kesintisiz ve çoklu isteklere cevap vermek üzere tasarlanmıştır. İstemci (Client), sunucu tarafından sunulan hizmeti kullanan, görece daha düşük kapasite ve işlem gücüne sahip makinelerdir. Tek bir kullanıcıya hizmet vermek için tasarlanmıştır. Uzun süreli ve kesintisiz çalışma önceliği bulunmamaktadır. 

İstemci-sunucu modeli veya istemci-sunucu mimarisi, aynı sistemde bulunan veya bir bilgisayar ağı veya İnternet üzerinden iletişim kuran sunucular ve istemciler arasında görevleri bölen dağıtılmış bir uygulama çerçevesidir. İstemci, bir sunucu tarafından sağlanan bir hizmete erişmek için başka bir programa istek göndermeye güvenir. Sunucu, kaynakları müşterilerle paylaşan ve işleri istemciler arasında dağıtan bir veya daha fazla program çalıştırır. İstemci ile sunucu arasındaki ilişki Şekil: 1’de şematize edilmiştir.

![1](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/bc54158c-311c-4d20-b938-757e314df8d8)


İstemci sunucu ilişkisi, bir istek-yanıt mesajlaşma modelinde iletişim kurar ve kullanılacak kuralları, dili ve diyalog modellerini resmi olarak tanımlayan ortak bir iletişim protokolüne bağlı kalmalıdır. İstemci-sunucu iletişimi tipik olarak TCP/IP protokol paketine bağlıdır. 

Eski yıllarda bir uygulamanın ayağa kaldırılması için sunucuların sipariş edilip firma bünyesinde barındırılması gerekiyordu. Bu süreç Şekil: 2’de gösterilmiştir.

![2](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/db5aa832-8136-46be-b971-0ee0cf588882)

Siparişin temin edilmesinden, kurulmasına; işletim sisteminin makineye kurulmasından, uygulamaların çalıştırılmasına kadar geçen süre yaklaşık olarak üç ayı bulmaktadır.

## 2.2. Atıl Kapasite Sorunu
Pratikte iki farklı yazılım (mail sunucu yazılımı ve muhasebe yazılımı) aynı makinede kullanılabilir ancak izolasyon ve güvenlik riski gibi sebeplerden dolayı farklı sunucularda barındırılması gerekir. Bu durum canlıya alınacak her proje için yukarıda Şekil: 2’de gösterilen üç aylık sürecin tekrarlanmasına neden olur. Her yeni uygulama için yeni bir makine kurulması firmaların kaynak israfı ile karşı karşıya gelmesine neden olmuştur. 

Firmalar yazılımlarını sunucuda barındırırken sunucunun sunduğu çoğu özelliğin tamamını kullanmamaktadır. Örneğin 4 Core Thread CPU, 16 GB RAM, 1 TB depolama alanına sahip bir e-posta sunucusu yazılımı 2 Core, 4-8 GB RAM ve maksimum 200 GB depolama kullanabilir. Yazılım sunucu tarafından sağlanan sistemin sadece %30’luk bir kısmını kullanmış olur. Bu firmaya %70’lik bir atıl kapasite sorunu çıkaracaktır.

## 2.3. Sanallaştırma Temelleri
Atıl kapasite sorunu ve bir sunucuda birden fazla uygulama çalıştırılamaması sorununa çözüm olarak 2000’li yılların başında sanallaştırma teknolojisi ortaya çıkmıştır. Sanallaştırma teknolojisinin ortaya çıkışıyla birlikte bulut bilişimin temelleri atılmıştır. 

Sanallaştırma, fiziksel bir bilgi işlem ortamı yerine simülasyon uygulanmış (veya sanal) bir ortam oluşturur. Sanallaştırma çoğu zaman donanımlar, işletim sistemleri, depolama cihazları ve daha fazlasının bilgisayar tarafından oluşturulan sürümlerini içerir. Bu sayede kuruluşlar, tek bir fiziksel bilgisayarı veya sunucuyu birçok sanal makineye bölümleyebilir. Her sanal makine, tek bir konak makinenin kaynaklarını paylaşmasına rağmen bağımsız olarak etkileşimlerde bulunabilir ve farklı işletim sistemleri veya uygulamalar çalıştırabilir.

![3](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/13a11cee-91fa-45d0-9c87-91c2104c4e89)

Sanallaştırma sayesinde, aynı fiziksel makine üzerinde birden fazla işletim sistemi çalıştırarak aynı sistemin kullanılması sağlandı. Ana makine kaynaklarını alt sistemlere ortak olarak kullandırarak ana fiziksel sistemin tüm kaynaklarının optimum kullanılmasını sağlamıştır. 

Sanallaştırma teknolojisi ile imaj olarak yerleşen sunucular ortak bir alana veri depolar ve sistemlerden birinin hasar görmesi durumunda diğer sunucu hasarlı sunucunun yerini alarak hizmete devam edebilir.

## 2.4. Bilişim Altyapısı Oluşturma
Teknoloji, tek bir çalışanın işinden operasyonlara, ürün ve hizmetlere kadar günümüz işletmelerinin neredeyse her yönünü güçlendirir. Teknoloji, ağa doğru bir şekilde bağlandığında, iletişimi iyileştirmek, verimlilik oluşturmak ve üretkenliği artırmak için optimize edilebilir.

Bir BT altyapısı esnek, güvenilir ve güvenli ise, bir kuruluşun hedeflerine ulaşmasına ve pazarda rekabet avantajı sağlamasına yardımcı olabilir. Bundan farklı olarak, bir BT altyapısının düzgün şekilde uygulanmaması halinde, işletmeler, sistem kesintileri ve ihlaller gibi güvenlik ve verimlilik sorunlarıyla karşı karşıya kalabilirler. Genel olarak, düzgün bir şekilde uygulanmış bir altyapıya sahip olmak, bir işletmenin kârlı olup olmamasına ilişkin bir faktör olabilir. 

Geleneksel bir BT altyapısı, şu olağan donanım ve yazılım bileşenlerinden oluşur: tesisler, veri merkezleri, sunucular, ağ donanımı masaüstü bilgisayarları ve kurumsal uygulama yazılım çözümleri. Genellikle, bu altyapı kurulumu, diğer altyapı türlerinden daha fazla güç, fiziksel alan ve para gerektirir. Geleneksel bir altyapı, genellikle şirket içinde yalnızca şirket için veya özel kullanım için kurulur. 

Bir tekstil firmasının başlıca ihtiyaçları şu şekildedir: e-posta sunucusu, dosya sunucusu, muhasebe sunucusu, anında mesajlaşma sunucusu, web sunucusu ve veri tabanı sunucusu. 

Başlık 2.1. altında Şekil: 2’de değinilen üç aylık süreçte bu gereklilikler temin edilir. Tüm gereklilikler sağlandıktan sonra şirket içerisinde veri merkezi kurulması gerekmektedir. Adımlar basitçe şu şekildedir:

1. Sadece yetkili kişilerin girebilmesi için kartlı geçiş sistemi kurulur. 
2. Kurulacak olan fiziksel cihazların ısınma sorununu çözmek için soğutma sistemi oluşturulur. 
3. Kısa elektrik kesintileri için UDP cihazları, uzun elektrik kesintileri için jeneratörler temin edilir. 
4. Makinelerin yerleştirilmesi için gerekli olan rack kabinleri (sunucu rafları) alınır. 
5. Şirketteki diğer cihazlar dahil tüm cihazların haberleşmesi için gerekli alt yapı kurulur. Oda kablolar ile donatılır. 
6. Odaya internet hattı çekilir. 
7. Cihazları korumak adına gerekli güvenlik donanımları ayarlanır. 
8. Makinelere sanallaştırma yazılımı kurulur. 
9. Her bir uygulama için işletim sistemi ve yazılımların kurulumu tamamlanır.

Tüm bu adımlar sonrasında optimizasyonu olan bir sistem tamamlanmış olacaktır.

Bu sistem sorunları tamamıyla çözmeyecektir. Firma altında çalışan yazılım ekibinin bir geliştirmeyi canlıya almadan önce test etmesi için sunucu ihtiyacı oluşabilir. Bu ihtiyaç acil ise üç aylık süre beklemek için yeterli zaman bulunmayacaktır. Bundan dolayı piyasa bedelinin üstünde bir sunucu alınır ve yazılım ekibi testlerini yapar. Yazılım ekibinin işi bittikten sonra 19 elimizde fazladan makine kalacaktır. Elde bulunan bu fazla makine satılsa bile yazılım ekibinin bu senaryo ile tekrar problem başlatmayacağının bir garantisi yoktur.

Sanallaştırma atıl kapasite sorununa çözüm olsa da aşağıdaki konularda yetersiz kalmıştır:

 - İlk yatırım maliyeti yüksektir. 
 - Bakım maliyeti yüksektir.
 - Genişletilebilir değildir. 
 - Esnek değildir. 
 - Planlaması güçtür.

Sanallaştırma teknolojisinin bu sorunlara çözüm bulamaması sebebiyle ‘Neden herkes kendi veri merkezini kuruyor?’ mottosu ile bilişim alt yapısı farklı bir iş kolu olarak ayrılmıştır. Büyük veri merkezleri kurularak müşterilere sunucularını yerleştireceği sunucu rafları kiralanmaya başlamıştır. Böylelikle firmalar artık bakım, ağ gereksinimleri gibi konularla ilgilenmeyecektir. 

Büyük veri merkezlerinde bulunan paylaşımlı sistem fiyatı düşürmüştür ancak kapasite sorununa bir çözüm bulamamıştır. Bunun üzerine sunucu rafı kiralamaktan çıkarak direkt olarak sunucu kiralama sistemine evirilmiştir. Büyük veri merkezlerinin kendi bünyesindeki sunucuları müşterilere kiralayarak hizmet vermesi, bulut bilişimin alt yapının servis olarak sunulması (Infrastructure as a Service - IaaS) hizmetini oluşturmuştur.

# 3. IaaS, PaaS, Saas
Bulut bilişim (cloud computing), bilgisayar ve diğer cihazlar için, istenildiği zaman kullanılabilen ve kullanıcılar arasında paylaşılan bilgisayar kaynakları olarak tanımlanabilir. Bulut bilişim bir ürün değil internet tabanlı bir hizmettir. Temel kaynaktaki yazılım ve bilgilerin paylaşımı sağlanarak, mevcut bilişim hizmetinin; bilgisayarlar ve diğer aygıtlardan bilişim ağı (tipik olarak internet) üzerinden kullanılmasıdır. 

Bulut bilişim, BT alanında aslında yıllardır kullanılan hizmetler bütünüdür. Bulut aslında konsept ve bir iş yapış şeklidir. Bu iş yapış şekli değişik yöntemler içermektedir. Bu yöntemlerin tamamı bulut çatısı altında toplanmıştır.

## 3.1. Alt Yapının Servis Olarak Sunulması (Infrastructure as a ServiceIaaS)
IaaS, bulut BT için temel yapı taşlarını içerir. Genellikle ağ iletişimi, bilgisayarlar (sanal veya tahsis edilmiş donanım üzerinde) ve veri depolama alanına erişim sağlar. IaaS, BT kaynaklarınız üzerinde en yüksek esneklik ve yönetim denetimi seviyesini sunar. Bu, birçok BT departmanının ve geliştiricinin aşina olduğu mevcut BT kaynaklarına benzer.

## 3.2. Platformun Servis Olarak Sunulması (Platform as a Service-PaaS)
PaaS, altyapı (genelde donanım ve işletim sistemleri) yönetimi ihtiyacınızı ortadan kaldırarak uygulama dağıtma ve yönetim alanlarına odaklanmanızı sağlar. Bu da kaynak tedariki, kapasite planlaması, yazılım bakımı, düzeltme ekleri veya uygulamanızın çalıştırılmasıyla ilgili diğer benzer zorlu görevler konusunda endişelenmemenize ve bu sayede daha verimli bir şekilde çalışmanıza yardımcı olur.

## 3.3. Yazılımın Servis Olarak Sunulması (Software as a Service-SaaS)
SaaS, hizmet sağlayıcısı tarafından çalıştırılan ve yönetilen tamamlanmış bir ürün sunar. SaaS, çoğu zaman son kullanıcı uygulamalarını (web tabanlı e-posta gibi) ifade etmek için kullanılır. 20 SaaS teklifiyle, hizmetin bakımı veya altyapının yönetimi konusunda endişelenmeniz gerekmez. Düşünmeniz gereken tek şey bu yazılımı nasıl kullanacağınızdır.

## 3.4. Bulut Bilişim Konseptlerinin Farkları
Aşağıdaki Şekil: 4 üzerinde göründüğü gibi firma içi kaynakların yönetimi ile bulut konseptleri üzerinden kaynakların yönetilmesi arasında farklar bulunmaktadır. Şirket içerisinde kurulacak bir veri merkezi ile depolamadan işletim sistemine kadar tüm adımlar bilişim departmanı tarafından fiziksel olarak yapılmalıdır. Bulut konseptlerinden olan IaaS yani alt yapının servis olarak sunulması konseptinde sunucu, ağ, sanallaştırma gibi adımları bulut bilişim kullanıcı yerine yapılandırıyor. Aslında bulut bilişimin bu konseptinde kullanıcılara bir adet sanal bilgisayar tanımlanmış oluyor ve kullanıcılar işletim sistemi kurmaktan uygulama yayınlamaya kadar tüm adımları kendileri tamamlamış oluyor. PaaS yani platformun servis olarak sunulması konseptinde ise bulut bilişimin faydalarından yararlanan müşteriler sadece gerekli verilerden ve uygulamanın çalıştırılmasından sorumlu oluyor. Bulut bilişimin son konsepti olan SaaS yani yazılımın servis olarak sunulması konseptinde ise günümüzde kullanılan bulut depolama alanları, e-posta servisleri gibi ürünlerdir. Yani müşteriler sadece sunulan bulut tabanlı ürünü kullanmaktadır.

![4](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/87db101c-1ad4-428f-abc3-504e56fcf25c)

# 4. Yazılım Geliştirme Döngüsü
Yazılım Geliştirme Yaşam Döngüsü (Software Development Life Cycle, SDLC), yazılımları tasarlamak, geliştirmek ve test etmek amaçlı kullanılan bir süreç olarak ifade edebiliriz. Yazılımın nasıl geliştirileceği, sürdürüleceği ve daha iyi hale nasıl getirileceğinin açıklayan bir plandan oluşmaktadır. Buradan da yazılımın aslında bir ürün olduğu ve o ürününde bir yaşam süreci olduğunu gözlemlemiş oluyoruz. SDLC, müşteri isteklerini karşılayacak şekilde süre ve maliyet tahminleri dahilinde tamamlanması sağlanan kaliteli yazılım üretmeyi hedefler. Aynı zamanda SDLC, ISO/IEC 12207 dahilinde uluslararası bir standart olmayı amaçlar.

![5](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/8a6b9381-bcf3-4a01-8b6e-e7e95f1bb0f9)

Yazılımın ilk sürüm geliştirmesi bitmeye yakın bir beta sürümü yayınlanır. Beta sürümü test aşamasında kullanıcıların da dahil olduğu bir süreçtir. Yazılım firması ürünün ilk sürümünü (versiyon 1.0) müşteriye teslim eder. Müşteri kendi kaynaklarında ürünü çalıştırır. Bu süreçten sonra ilk sorunlarla ortaya çıkacaktır. Müşteri bunu yazılım firmasına bildirir. Yazılım firması ilk düzenlemesini yani “hotfix” hazırlar ve bu geliştirmeyi de müşteriye gönderir. 

Bu süreç her iki taraflı da sorun içermektedir. Yazılım firması açısından geri bildirimlerin toplanması zaman alacaktır, yazılımın kurulu olduğu sistem müşteriye ait olduğu için anında müdahale edememektedir, yüzlerce değişik sistem konfigürasyonu için uyumluluk oluşturmak zorlaşacaktır. Müşteri açısından bakıldığında ise; problem çözümü oldukça zahmetlidir, yeni özelliklerin bulunduğu sürümlere erişmek aylar sürebilir, alt yapı oluşturma ve yönetme işlemleri zahmetli ve pahalıdır.

Bulut bilişimin SaaS yani yazılım servis olarak sunulması modeli arkasındaki temel mantık ise yazılım firmasının uygulamayı kendi makinesinde çalıştırıp kullanıcıya bir kullanıcı adı ve parola ile sisteme giriş sağlamasını ve sonrasında kullanmasını hedeflemektedir. Müşteri büyük bütçeler ile bir yazılım almak yerine bir nevi kiralamış olur. 

Müşteri dönütlerinin hızlı olması, yazılım firmasını hızlı geliştirme ve test etme döngüsüne sokmuştur. Bu süreç sonrasında yazılım geliştirme ekibi ile operasyon ekibi arasında etkileşim ve iletişimin hızlı olması açısından DevOps fikri ortaya çıkmıştır.

# 5. DevOps
Geliştirme (Dev) ve işlemlerin (Ops) bir bileşeni olan DevOps; müşterilere sürekli olarak değer sunmak için bir araya gelen kişiler, süreçler ve teknolojiler bütünüdür. 

DevOps’un ekipler için anlamı nedir? DevOps, daha iyi ve daha güvenilir ürünler üretmek amacıyla koordinasyon ve iş birliği gerçekleştirmek için, eskiden birbirinden ayrı düşünülen geliştirme, BT operasyonu, kalite mühendisliği ve güvenlik rollerine olanak tanır. DevOps yöntemlerinin ve araçlarının yanı sıra bir DevOps kültürünü benimseyen ekipler müşteri gereksinimlerine daha iyi yanıt verme becerisi kazanıyor, oluşturdukları uygulamalara olan güvenlerini artırabiliyor ve iş hedeflerine daha hızlı bir şekilde ulaşabiliyor.

![6](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/ba1629c3-b113-4024-8d7d-987ea487d0f6)

DevOps sayesinde önceden senede iki büyük sürüm yayınlayabilen yazılım firmaları artık günde birkaç küçük yeni versiyonlara erişebilir hale geldi. DevOps fikrinin popüler bir hale gelmesi ile yazılan kodu otomatik olarak bulunduğu depodan alıp test ortamına alan, otomatik test edip stage production’a yollayan uygulamalar geliştirildi. Bu uygulamalara Docker ve Chef en büyük örneklerdir.

# 6. Mikroservis Mimarisi

![7](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e26393ef-4008-4e19-9ec3-43d875bc9277)

Monolitik mimari kendi kendine yetebilecek bir uygulamadaki bütün fonksiyonalitelerin tek bir çatı altında geliştirilmesidir. Ancak monolitik mimarinin bazı dezavantajları vardır:

- Uygulama büyüdükçe yeni özellik geliştirilmesi ve mevcut kodun bakımı zorlaşır. 
- Projede çalışan ekip sayısının ve çalışan sayısının artması ile geliştirme ve bakım daha güç hale gelir. 
- Birbirlerine olan bağımlılıklarından dolayı, bir fonksiyonalitede yapılan değişiklik diğer yerleri etkileyebilir. 
- Spesifik bir fonksiyonaliteyi ölçeklendirme imkânı yoktur. (Örneğin geliştirdiğiniz uygulamada sürekli fatura oluşturuluyor ve burası uygulamanın dar boğazı. Siz bu fonksiyonaliteyi birden fazla sanal makine da çalıştırmak isteseniz bile uygulamanız monolitik mimaride olduğu için sadece ilgili servis yerine bütün uygulamayı ölçeklendirmek zorunda kalırsınız.) 
- Versiyon yönetimi zorlaşır. 
- Uygulamada aynı programlama dili ve aynı framework’lerin kullanılması gerekir. 
- Uygulamada yapılan küçük bir değişiklikte bile bütün uygulamanın deploy olması (yayınlanması) gerekir.

Bu sorunların üstesinden gelmek için mikro servis mimarisi ortaya çıkmıştır. 

Mikro servis (micro service) mimarisi, tek bir uygulama geliştirirken modüler bir yapıda her biri küçük servis olarak düşünülmesi gereken ve her bir servisinde kendi işini ve iletişimini yürütebilen, çok karmaşık olmayan ve başka servislere bağımlılığı az olan mekanizmalara sahip bir yaklaşımdır. Bu servisler kendilerinin sorumlu olduğu tek bir işe odaklı ve bağımsız çalışabilen, otomatize bir deployment mekanizmasına sahip bir yapıdadır. Merkezi yönetim mekanizmalarından oldukça arındırılmış olmalıdır. Farklı programlama dillerinde geliştirilebilir ve farklı veri tabanı teknolojileri kullanılabilir.

Mikro servis mimarisi, monolitik mimarinin birçok soruna çözüm olabilse de çok daha karmaşık bir sistem ortaya çıkmıştır. Bu durum da DevOps fikrinin günbegün öneminin artmasına neden olmuştur. Mikro servis mimarisi servisleri ayrı ayrı geliştirme konusunda büyük oranda kolaylık sağlasa da ortaya çıkan kaynak israfı sorununu adresleyememiştir. Mikro servis mimarisinin temelinde uygulama programlama ara yüzü yani API bulunmaktadır.

# 7. API (Application Programming Interface)
Uygulama programlama arayüzleri yani API'ler, uygulamaların veri ve işlevsellik alışverişini kolay ve güvenli bir şekilde yapmasını sağlayarak yazılım geliştirmeyi ve yeniliği basitleştirir. 

Bir uygulama programlama arayüzü veya API, şirketlerin uygulamalarının verilerini ve işlevlerini harici üçüncü taraf geliştiricilere, iş ortaklarına ve şirketlerindeki dahili departmanlara açmasına olanak tanır. Bu, hizmetlerin ve ürünlerin birbirleriyle iletişim kurmasına ve belgelenmiş bir arayüz aracılığıyla birbirlerinin verilerinden ve işlevlerinden yararlanmasına olanak tanır. Geliştiricilerin bir API'nin nasıl uygulandığını bilmesine gerek yoktur; sadece diğer ürün ve hizmetlerle iletişim kurmak için arayüzü kullanırlar. API kullanımı son on yılda o kadar artmıştır ki, günümüzde en popüler web uygulamalarının çoğu API'ler olmadan mümkün olmayacaktı. 

API Gateway ise, istemcilerle back-end sunucuları / mikro servisler arasında duran bir API yönetim aracıdır.

API Gateway API isteklerini alarak çeşitli kurallara göre uygun servislere yönlendiren bir ters vekil sunucusu (reverse proxy) olarak çalışır. API Gateway istek sınırlandırma, istatistik, kimlik doğrulama vs. gibi çeşitli sık kullanılan işlevleri üzerine alarak asıl API sunucularınızın önünde bir üst katman oluşturur. İstemci tüm servislerden bilgiyi alır. 

İstemci dolaylı yoldan (API Gateway ile) da olsa tüm mikro servisler ile haberleşmiş olur. Aynı zamanda istemci, mikro servisler ile doğrudan bir iletişim kurmamış olur. 

Temelde API Gateway de bir servistir. Temel görevi ise diğer tüm servislere ortak erişilmesini sağlamaktır. Ana görevleri yönlendirme, birleştirme, yetkilendirme, yük dağıtımı, ön bellekleme ve izlemedir.

# 8. Container (Konteyner)
Mikro servisler öncesinde uygulamalar tek bir parça olarak kurgulanıyor ve hayata geçiriliyordu. Mikro servis mimarisi ile ana servisler, alt servislere ayrılmış oldu. Bu servislerin her biri için ayrı bir makine tahsis edilip, kuruldu. Yüksek erişilebilirlik olması yani yoğun istek altında kaldığında sistemin yavaşlamaması için tüm bu servisler çiftelenir. Tüm bu durumlar göz önüne alındığında, ana servisler alt servislere parçaladığında fazla sayıda makineye ihtiyaç duyulur hale gelindi.

Mikro servis mimarisinde bir servis için sadece işletim sisteminin bulunması gerekli kaynakların temini açısından yeterlidir. Bu durumda her bir servis için bir işletim sistemi kurulduğundan dolayı kaynak kullanımı büyük oranda artmıştır. Tüm mikro servisleri ayrı ayrı makinelerde barındırılmasının iki temel sebebi vardır.

- Uygulama izolasyonunu korumak, bundan dolayı da güvenliği sağlamak.
- Servisleri aynı makinede çalıştırılması durumunda makine bağımlılığının ortaya çıkacak olması.

Tüm bu sorunların önünce geçmek amacıyla ‘container (konteyner)’ teknolojisi ortaya çıkmıştır.

Konteynerler ister masa üstünde ister geleneksel BT'de veya bulutta olsun, uygulama kodunun istenen herhangi bir yerde çalıştırılabilmesi için, kitaplıkları ve bağımlılıkları ile birlikte ortak yöntemlerle paketlendiği, yürütülebilir yazılım birimleridir. 

Bunun için konteynerler bir çeşit işletim sistemi sanallaştırmasından yararlanır. Burada hem süreçlerin yalıtılması hem de bu süreçlerin erişimi olan disk, bellek ve CPU miktarının kontrolü için işletim sisteminin özelliklerinden (Linux kernel senaryosunda ad alanları ve cgroups primitifleri gibi) yararlanılır. 

Konteynerler küçük, hızlı ve taşınabilirdir. Bunun nedeni, sanal bir makinenin aksine, konteynerlerin her eş görünümde bir konuk işletim sistemi içermesinin gerekli olmaması, bunun yerine, ana sistem işletim sisteminin özelliklerinden ve kaynaklarından yararlanmasının yeterli olmasıdır. 

Konteynerler, ilk olarak, on yıllar önce FreeBSD Jails ve AIX Workload Partitions gibi sürümlerle ortaya çıktı. Ancak çoğu modern geliştirici, 2013 yılını, Docker'ın tanıtılmasıyla birlikte modern konteyner çağının başlangıcı olarak hatırlıyor.

![8](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/c04948a3-8081-4025-8c7a-e5a712fc769b)

Kısaca konteynerler birer sanal bilgisayar (Virtual Machine- VM) gibi çalışan ancak sanal bilgisayarlar kadar kaynak tüketmeyen bir yapı olarak tanımlanabilir.
