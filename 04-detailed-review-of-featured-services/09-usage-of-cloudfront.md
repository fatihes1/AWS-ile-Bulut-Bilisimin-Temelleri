# 10. Amazon CloudFront
CloudFront servisinin daha iyi anlaşılması için öncelikle CDN (Content Delivery Network) yani içerik dağıtım ağının ne olduğunun bilinmesi gerekir.

## 10.1. CDN Nedir?
İçerik dağıtım ağı (CDN), internet içeriğinin hızlı teslimatını sağlamak için birlikte çalışan, coğrafi olarak dağıtılmış bir sunucu grubunu ifade eder. 

Bir CDN, HTML sayfaları, JavaScript dosyaları, stil sayfaları, resimler ve videolar dahil olmak üzere internet içeriğinin yüklenmesi için gereken varlıkların hızlı bir şekilde aktarılmasına izin verir. CDN hizmetlerinin popülaritesi artmaya devam ediyor ve bugün web trafiğinin çoğu, Facebook, Netflix ve Amazon gibi büyük sitelerden gelen trafik de dahil olmak üzere, CDN'ler aracılığıyla sunuluyor. 

Düzgün yapılandırılmış bir CDN, web sitelerinin dağıtılmış hizmet reddi (DDOS) saldırıları gibi bazı yaygın kötü niyetli saldırılara karşı korunmasına da yardımcı olabilir.

## 10.2. CDN Kullanmanın Avantajları Nedir?
Bir CDN kullanmanın faydaları, bir internet mülkünün boyutuna ve ihtiyaçlarına bağlı olarak değişse de çoğu kullanıcı için birincil faydalar 4 farklı bileşene ayrılabilir:

1. ***Web sitesi yükleme sürelerini iyileştirme -*** Yakındaki bir CDN sunucusunu kullanarak web sitesi ziyaretçilerine daha yakın içerik dağıtarak, ziyaretçiler daha hızlı sayfa yükleme süreleri yaşarlar. Ziyaretçiler yavaş yüklenen bir siteden uzakta tıklamaya daha meyilli olduklarından, bir CDN hemen çıkma oranlarını azaltabilir ve insanların sitede geçirdikleri süreyi artırabilir. Başka bir deyişle, daha hızlı bir web sitesi, daha fazla ziyaretçinin kalacağı ve daha uzun süre bağlı kalacağı anlamına gelir. 
2. ***Bant genişliği maliyetlerini azaltmak -*** web sitesi barındırma için bant genişliği tüketim maliyetleri, web siteleri için birincil giderdir. Önbelleğe alma ve diğer optimizasyonlar yoluyla CDN'ler, bir kaynak sunucunun sağlaması gereken veri miktarını azaltabilir ve böylece web sitesi sahipleri için barındırma maliyetlerini azaltabilir.
3. ***Artan içerik kullanılabilirliği ve yedeklilik -*** Büyük miktarda trafik veya donanım arızası, normal web sitesi işlevini kesintiye uğratabilir. Dağıtılmış yapıları sayesinde, bir CDN daha fazla trafiği işleyebilir ve donanım arızalarına birçok kaynak sunucudan daha iyi dayanabilir. 
4. ***Web sitesi güvenliğini iyileştirme -*** Bir CDN, DDoS azaltma, güvenlik sertifikalarında iyileştirmeler ve diğer optimizasyonlar sağlayarak güvenliği artırabilir.

## 10.3. CDN Nasıl Çalışır?
Özünde, bir CDN, içeriği mümkün olduğunca hızlı, ucuz, güvenilir ve güvenli bir şekilde teslim etme hedefiyle birbirine bağlı bir sunucu ağıdır. Hızı ve bağlantıyı iyileştirmek için bir CDN, sunucuları farklı ağlar arasındaki değişim noktalarına yerleştirir. 

Bu internet değişim noktaları (IXP'ler), farklı internet sağlayıcılarının farklı ağlarından kaynaklanan trafiğe birbirlerine erişim sağlamak için bağlandığı birincil konumlardır. Bir CDN sağlayıcısı, bu yüksek hızlı ve yüksek düzeyde bağlantılı konumlara bağlantı kurarak, yüksek hızlı veri dağıtımında maliyetleri ve geçiş sürelerini azaltabilir. 

Bir CDN, sunucuların IXP'lere yerleştirilmesinin ötesinde, standart istemci/sunucu veri aktarımlarında bir dizi optimizasyon yapar. CDN'ler, veri merkezlerini dünya çapında stratejik konumlara yerleştirir, güvenliği artırır ve çeşitli arıza türlerinden ve internet tıkanıklığından kurtulmak için tasarlanmıştır.

## 10.4. CloudFront Hizmeti
Amazon CloudFront en temelde AWS’nin CDN hizmetidir. Dünya çapında binlerce katman 1/2/3 telekomünikasyon operatörüyle uyumlu çalışan Amazon CloudFront, optimum performans için gerekli tüm başlıca erişim ağlarıyla bağlantılıdır ve yüzlerce terabit dağıtılmış kapasiteye sahiptir. CloudFront uç konumları; dünyanın dört bir yanını dolaşan tamamen yedekli, çok sayıda 100 GbE paralel fiberin oluşturduğu ve hem kaynak getirme işlemlerinin hem de dinamik içerik hızlandırmasının iyileştirilmesi için on binlerce ağ ile bağlantılı olan AWS ağ omurgası aracılığıyla AWS bölgelerine (AWS Region) bağlıdır. 

Amazon CloudFront, son kullanıcılara daha düşük gecikme süresiyle içerik teslim etmek için 47 ülkedeki 90’dan fazla şehirde, 410’dan fazla varlık noktasından (PoP) (400’den fazla uç konumu ve 13 adet bölgesel orta katman önbelleği) oluşan küresel bir ağ kullanır.

![269](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/137090ca-63aa-4281-9802-7a9c28a34855)

CDN hizmeti “Edge Location” adı verilen veri merkezlerinden bu hizmeti sağlar. Bu veri merkezleri, AWS’nin bölgelerinden (region) ayrıdır. Bu veri merkezlerinde sadece CloudFront hizmeti sunulur. CloudFront temelde aşağıda belirtilen hizmetleri sunar:

- Statik resim, css ve diğer medya dosyalarını önbellekler. 
- Web formları, yorum ve giriş kutuları, “sepete ekle” düğmeleri veya son kullanıcılardan veri yükleyen diğer özelliklere sahip dinamik içeriği de önbellekler. 
- Canlı video yayınları ve talebe bağlı video (Live Streaming ve On-Demand Video) isteklerini de ön belleklemenize imkân tanır. 
- HTTP GET, HEAD, POST, PUT, DELETE, OPTIONS ve PATCH isteklerini destekler. 
-  API isteklerini hızlandırır. 
- Lambda@Edge 
- AWS Shiled ile entegre Layer 3-4 Ddos Mitigation ve AWS WAF ile entegre Layer 7 koruması 
- SSL/TSL desteği

## 10.5. CloudFront Servisinin Kullanımı
CloudFront kontrol paneline gittikten sonra, “Create a CloudFront distribution” butonu ile hizmeti kullanmak için ilk adım atılabilir. Sonrasında aşağıdaki adımlar takip edilebilir:

- ‘Origin Domain’ alanına yayınlanmak istenen web sayfasını seçilir. Listelenenlerde bu kılavuz kapsamında AWS S3 bucket’ında yayınlanan web sayfası ve yine bu kılavuz kapsamında “Load Balancer” servisi ile yükü farklı sunuculara dağıtılan yayında bulunan web sayfası çıkar. Bununla beraber dış dünyadan da bir domain girilebilir. Bu kılavuz kapsamında load balancer kullanarak yayında olan web sayfasını seçelim. 
- Origin path kısmında spesifik olarak bir dizin (örneğin web sayfasındaki sadece görsellerin bulunduğu bir dizin gibi) seçilebilir. Bu aşamada boş bırakarak kök dizini seçmiş olalım. 
- Bir isim girilmesini beklemektedir. Bir isim belirterek sonraki aşamaya geçilir. 
- Opsiyonel olarak sunulan “Add custom header” alanı bu aşamada boş bırakılır. Bu alan kaynak sunucuya atılacak her istekte eklenmek istenen bir HTTP header bulunuyor ise o eklenebilir. Birden fazla CDN sunucusu kullanırken paketin nereden geldiğini HTTP loglarından görmek için önemlidir. 
- “Default cache behavior” seçeneği altında bulunan “Path pattern” başlığı varsayılan olan “*” olarak bırakılır. Böylelikle tüm static dosyalar önbelleklenir. 
- Sonraki aşamada “Compress objects automatically” seçeneği vardır. Burada eğer ki içerik sıkıştırılabilir ise CloudFront otomatik olarak sıkıştırsın mı diye kullanıcıya sorar. Bu aşamada bu soruya da hayır diyelim. ‒ Viewer protocol policy seçeneğinde, dağıtımın dışarıdan gelen isteklere nasıl yanıt vereceği belirtilir. Bu kısmı HTTP ve HTTPS olarak seçebiliriz.
- Sonrasında ise izin verilen HTTP metotlarının seçilmesini ister. GET, HEAD ve OPTION basit işlem istekleri içindir. Ancak POST, PATCH, DELETE gibi metotlar iletişim formu ve S3 hizmetinden dosyalarının eklenip/silinmesi gibi istekler için gerekli metotlardır. 
- Sonrasında ise “Restrict viewer access” seçeneği bulunur. İzleyici erişimini kısıtlarsanız, izleyicilerin içeriğinize erişmek için CloudFront imzalı URL'leri veya imzalı tanımlama bilgilerini kullanması gerekir. Bu kılavuz kapsamında hayır diyerek devam edelim.
- “Cache key and origin requests” seçeneği önerilen seçenek ile devam edelim. 
- “AWS WAF web ACL” seçeneğini de varsayılan değer olarak “None” bırakalım. 
- Alternate domain name (CNAME) alanı, CloudFront otomatik DNS atayacak ancak sizin web sayfanızın domain bilgilerinin girilmesini bekler. Bu aşamada boş bırakabiliriz.
- Custom SSL gibi diğer tüm seçenekleri bu aşamada varsayılan değeri olarak bırakıp oluşturalım.

Dağıtım durumu uygun olana kadar bekleyelim. Bu işlem yarım saat kadar sürebilmektedir. Dağıtım aktif olduğunda ayarlar üzerinden özelleştirmeler yapılabilir. Örneğin;

- Restrictions seçeneğinden “Geo Restrictions” ile dağıtıma çeşitli coğrafi bölgelerden erişimi engelleyebilirsiniz. 
- Bununla beraber “White-list” ile de dağıtıma sadece hangi coğrafi bölge veya ülkelerden bağlanmasını sağlayabilirsiniz.
- CloudFront’ta bulunan Invalidation özelliği sayesinde anında güncelleme yapılabilir. Somut bir örnek vermek gerekirse bir web sayfasını yayına aldınız ve bu sayfaya gelen istek sayesinde bir static görsel önbelleklendi. Sonradan fark ettiğinizde yanlış bir görsele yer verdiğinizi fark ettiniz. Ancak görsel çoktan önbelleklendi ve yaşama süresi (TTL) bitene kadar CDN hizmeti sunan sunucuda duruyor. Hemen silinebilmesi için “Create Invalidation” kullanılır. Böylelikle TTL süresine aldırış etmeden gerekli düzenleme uygulanır.

Domain bilgileri ile siteye bağlandığınızda bir GET isteği yapıldığı Chrome tarayıcının geliştirici kısmında görünür. Headers kısmına baktığımızda ise “X-Cache: Hit from cloudfront” gibi bir bilgi ile bu istek sonucunun, CloudFront sunucuları üzerinden geldiğini belirtir.
