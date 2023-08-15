# 26. AWS Lambda & Amazon API Gateway
## 26.1. AWS Lambda
AWS Lambda, olaylara yanıt olarak kodunuzu çalıştıran ve temel işlem kaynaklarını otomatik olarak yöneten bir sunucusuz işlem hizmetidir. Bu olaylar, bir e-ticaret sitesinde kullanıcının bir ürünü alışveriş sepetine koyması gibi durum değişikliklerini veya güncellemeleri içerebilir. AWS Lambda'yı kullanarak diğer AWS hizmetlerinizi özel mantıkla genişletebilir veya AWS'nin ölçek, performans ve güvenlik düzeyinde çalışan kendi arka uç hizmetlerinizi oluşturabilirsiniz. AWS Lambda, Amazon API Gateway aracılığıyla gönderilen HTTP istekleri, Amazon Simple Storage Service (Amazon S3) klasörlerindeki nesnelerde yapılan değişiklikler, Amazon DynamoDB'de gerçekleştirilen tablo güncellemeleri ve AWS Step Functions durum geçişleri gibi birden fazla olaya yanıt olarak otomatik olarak kod çalıştırır.

![293](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/00998e2d-0b7d-438e-9924-c0b52bbf0fce)

Lambda, kodunuzu yüksek erişilebilirliğe sahip bir işlem altyapısında çalıştırır ve işlem kaynaklarınıza ilişkin tüm yönetim görevlerini üstlenir. Bunlar, sunucu ve işletim sistemi bakımı, kapasite tedariki ve otomatik ölçeklendirme, kod ve güvenlik düzeltme eki dağıtımı, kod izleme ve günlük kaydını içerir. Sizin tek yapmanız gereken kodu sağlamaktır. 

Bu servisi somut şekilde açıklamak için bir senaryo üzerinden ilerleyelim. Tek başına olan bir geliştirici, bir python uygulaması ile bir sosyal medyadan belirli bir hashtag’e sahip görselleri çekiyor, sonrasında bu görsele bir watermark (görünmez imza) ekliyor. Sonrasında bu görseli de S3 bucket’a ve DynamoDB’ye yolluyor. 

Bu senaryoda, altyapı yönetimi zahmetli ve karmaşık bir iştir. Kodu yazıp uygulamayı oluşturmak işin sadece bir kısmını oluşturuyor. Bu uygulamanın (veya kodun) bir ortamda kesintisiz bir şekilde müşterilerin hizmetine sunulması ise ekstra emek isteyen bir süreçtir. Bunlara ek olarak kodun çalışması gereken bir sunucuda barınması gerekecektir. Bu duruma sektör Function as a Service (FaaS) konseptini ortaya çıkarmıştır. 

FaaS, kullanıcıların bir sunucu yönetmeden uygulama geliştirmelerine ve işlevleri dağıtmalarına olanak sağlayan ve işlem verimliliğini arttıran bir bulut bilişim modelidir. FaaS’ın temelindeki konsept, serverless (sunucusuz) olarak bilinen konsepttir. Bu konseptte tüm bilişim altyapısı bulut bilişim sağlayıcısı tarafından yönetilir ve bizler sadece kod ile 195 ilgileniriz. Kodun çalıştırılması ve sonucun gönderilmesi için gereken tüm altyapı servisi sağlayıcının görevidir. 

AWS’nin serverless hizmeti ise Lambda servisidir. Lambda Python, Node.js, Go ve C# kodu çalıştırıp bir işlem sunucusu verir.

## 26.2. Amazon API Gateway
Amazon API Gateway, geliştiriciler tarafından istenen ölçekte API'ler oluşturulup yayımlanmasını, bunların izlenmesini, bakımın yapılmasını ve güvenliğinin sağlanmasını mümkün kılan, tam olarak yönetilen bir hizmettir. API'ler; uygulamaların arka uç hizmetlerinizdeki verilere, iş mantığına veya işlevlere erişmesini sağlayan "giriş kapıları" görevini görür. API Gateway'i kullanarak gerçek zamanlı çift yönlü iletişim uygulamalarını mümkün kılan RESTful API'leri ve WebSocket API'leri oluşturabilirsiniz. API Gateway, container'lı ve sunucusuz iş yüklerine ek olarak web uygulamalarını da destekler.

![294](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/1eb912d7-5a0a-4846-8aad-8392e139944b)

API Gateway, yüz binlerce API çağrısının kabul edilip işlenmesi için gerekli olan trafik yönetimi, CORS desteği, yetkilendirme ve erişim denetimi, kısıtlama, izleme, API sürüm yönetimi dahil olmak üzere tüm görevleri üstlenir. API Gateway'de minimum ücret veya peşin maliyet yoktur. Aldığınız API çağrıları ve dışarı aktarılan veri miktarı karşılığında ücret ödersiniz ve API Gateway'in katmanlı fiyatlandırma modeli sayesinde API kullanımınızın ölçeği büyüdükçe maliyetinizi düşürebilirsiniz. İki adet API tipi sunar:

- ***RESTful API’ler:*** HTTP API’ler kullanarak sunucusuz iş yükleri için optimize edilmiş RESTful API’ler ve HTTP arka uçlar oluşturun. HTTP API’ler, sadece API proxy'si işlevselliği gerektiren API’ler oluşturmak için en iyi seçenektir. API'leriniz, tek bir çözümde API proxy'si işlevselliğine ve API yönetim özelliklerine ihtiyaç duyan API'lere yönelikse, API Gateway çözümü ayrıca REST API’ler de sunar.
- ***WEBSOCKET API’ler:*** WebSocket API'lerini kullanarak, sohbet uygulamaları ve akış panoları gibi gerçek zamanlı çift yönlü iletişim uygulamaları oluşturun. API Gateway, arka uç hizmetinizle istemcileriniz arasındaki ileti aktarımını işleyen kalıcı bir bağlantı oluşturur.

Bu iki servisin aynı başlık altında oluşturulma sebebi ise AWS Lambda ile de bir nevi mikro servisler yaratılabilir. Bu servislere, giriş noktasında ortak bir authentication (kimlik doğrulama) alt yapısı gerekir. Bu hizmeti API Gateway ile sağlarız.



