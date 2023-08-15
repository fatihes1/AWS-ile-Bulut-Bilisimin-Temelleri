# 35. Amazon Aurora Serverless
Amazon Aurora Serverless, Amazon Aurora için isteğe bağlı bir otomatik ölçeklendirme yapılandırmasıdır. Otomatik olarak başlar, kapanır ve uygulamanızın ihtiyaçlarına göre kapasite ölçeğini büyütür veya küçültür. Herhangi bir veri tabanı kapasitesini yönetmeden veri tabanınızı bulutta çalıştırmanıza imkân tanır.

![300](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/1df8b8f4-59c6-4cf5-9a6d-5bc616f14181)

Veri tabanı kapasitesini manuel olarak yönetmek değerli zamanınızı alabilir ve veri tabanı kaynaklarının verimsiz kullanılmasına yol açabilir. Aurora Serverless ile, basitçe bir veri tabanı uç noktası oluşturur, isteğe bağlı olarak dilediğiniz veri tabanı kapasitesi aralığını belirtir ve uygulamalarınızı bağlarsınız. Veri tabanı etkin durumdayken kullandığınız veri tabanı kapasitesi için saniye bazında ödeme yaparsınız ve Amazon RDS Management Console’da birkaç tıklamayla standart ile sunucusuz yapılandırmalar arasında geçiş yapabilirsiniz.

Veri tabanı sağlama ve kapasitesini yönetme karmaşasını ortadan kaldırır. Veri tabanı, uygulamalarınızın ihtiyaçlarına uygun şekilde otomatik olarak başlatılır, kapatılır ve ölçeklendirilir. 

İşlem ve bellek kapasitesini istemci bağlantılarını kesintiye uğratmadan rahatça, gerektiği gibi ölçeklendirir. 

Yalnızca kullandığınız veri tabanı kaynakları için saniye bazında ödeme yapın. Gerçekten çalışmayan veri tabanı bulut sunucuları için ödeme yapmazsınız. 

Dağıtılmış, hata toleranslı, kendi kendine onarılan Aurora depolaması üzerine yapılandırılmıştır ve veri kaybına karşı koruma için 6 yoldan replikasyon sağlar. 

Şu anda (Ağustos 2022) ön izleme aşamasında olan Amazon Aurora Serverless v2, bir saniyeden kısa bir süre içinde anında yüzlerce işlemden yüz binlerce işleme kadar ölçeklenebilir. Ölçeklendirildikçe, uygulamanın ihtiyaç duyduğu doğru miktarda veri tabanı kaynağını sağlamak için kapasiteyi küçük artışlarla ayarlar. Herhangi bir veri tabanı kapasitesini yönetmeniz gerekmemektedir, yalnızca uygulamanızın kullandığı kapasite için ödeme yaparsınız ve en yüksek yük için tedarik kapasitesi maliyetine kıyasla veri tabanı maliyetinizin %90'ına kadar tasarruf edebilirsiniz. 

Aurora Serverless v2 (Ön izleme), geliştirme ve test ortamları, web siteleri ve seyrek, aralıklı veya öngörülemeyen iş yüklerine sahip uygulamalardan yüksek ölçek ve yüksek kullanılabilirlik gerektiren en zorlu, iş açısından kritik uygulamalara kadar her tür veri tabanı iş yükünü destekler. Global Veri tabanı, Multi-AZ dağıtımları ve okuma kopyaları dahil tüm Aurora özelliklerini destekler. Aurora Serverless v2 (Ön izleme) şu anda yalnızca MySQL uyumluluğuna sahip Aurora için ön izleme modunda mevcuttur.
