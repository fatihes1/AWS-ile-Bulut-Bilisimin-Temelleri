# 5. Bulut Finansal Yönetim Servisleri
## 5.1. AWS Budgets
![41](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/9c00b439-68ba-42cd-a420-3471d3f841de)

İşletmeler ve kuruluşlar, bulut maliyetlerine ilişkin planlar oluşturmaya ve beklentileri belirlemeye ihtiyaç duyar. Bununla beraber bulut çevikliği, kullanımınızın dinamik doğasına ayak uydurmak için, tahmini hesaplama süreçlerinizi ve araçlarınızı uyarlamanızı gerektirir. Özel bütçeler oluşturabilir, maliyetinizin ve kullanımınızın nasıl ilerlediğini takip eder ve maliyet ya da kullanım eşik değeri aşıldığında hızlıca müdahale edebilirsiniz. 

AWS Budgets, maliyetinizi ve kullanımınızı en basitten en karmaşık kullanım örneklerine kadar izleyebilmeniz için özel bütçeler ayarlamanıza olanak tanır. AWS Budgets'ta, gerçek veya tahmini maliyetiniz ve kullanımız, bütçe eşiğinizi aştığında ya da gerçek rezerve edilmiş bulut sunucusu ve “Savings Plans” kullanımınız veya kapsamınız, istediğiniz eşiğin altına düştüğünde e-posta veya SNS bildirimi ile uyarı almayı seçebilirsiniz. AWS Budget Actions'ta, hesaplarınızdaki maliyet ve kullanım durumuna müdahale etmek için belirli eylemler de yapılandırabilirsiniz. Böylece, maliyetiniz veya kullanımınız eşiği aşarsa ya da aşacağı öngörülürse istenmeyen aşırı harcamanın azaltılması için otomatik olarak ya da onayınızla eylemler gerçekleştirilebilir.

## 5.2. AWS Cost and Usage Report (CUR)
![42](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/038eaec3-78ae-49eb-8953-e2c9ee2d68c6)

AWS Cost & Usage Report; AWS hizmetleri, fiyatlandırma, kredi, ücretler, vergiler, indirimler, maliyet kategorileri, rezerve edilmiş bulut sunucuları ve “Savings Plans” hakkındaki ek meta veriler dahil olmak üzere mevcut en kapsamlı AWS maliyet ve kullanım veri kümesini içerir. 

AWS Cost & Usage Report (CUR); ürün koduna, kullanım türüne ve işleme göre kullanımın hesap veya kuruluş düzeyinde kalem dökümünü sağlar. Bu maliyetler ayrıca maliyet tahsisi etiketlerine ve Cost Categories'e göre düzenlenebilir. AWS Cost & Usage Report; saatlik, günlük veya aylık ayrıntı düzeyinin yanı sıra yönetim ya da üye hesabı düzeyinde oluşturulabilir. Doğru erişim yetkilerine sahip olmak kaydıyla, kullanıcılar yönetim ve üye hesabı düzeyinde Cost & Usage Report'a erişebilir. Bu sayede yönetim hesabı sahipleri, üye hesapları için Cost & Usage Report oluşturmak zorunda kalmaz.

## 5.3. AWS Cost Explorer
![43](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f0b8f685-14eb-4c22-9590-0ffe2b3f41b4)

AWS Cost Explorer, zaman içindeki AWS maliyetlerinizi ve kullanımınızı görselleştirmenize, anlamanıza ve yönetmenize olanak tanıyan, kullanımı kolay bir arabirime sahiptir. 

Maliyet ve kullanım verilerini analiz eden özel raporlar oluşturarak hızlıca kullanmaya başlayabilirsiniz. Verilerinizi yüksek bir düzeyde (örneğin tüm hesaplarda toplam maliyet ve kullanım) analiz edebilir veya trendleri belirlemek, maliyetleri artıran unsurları tespit etmek ve anormallikleri saptamak için maliyet ve kullanım verilerinizi daha derinlemesine inceleme imkânı sunar.

## 5.4. Rezerve Edilmiş Bulut Sunucusu (RI) Raporlama
![44](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/51f7a782-9652-4dd6-88c0-12a12968b154)

“Rezerve Edilmiş Bulut Sunucusu” kullanım ve kapsam raporları, AWS Cost Explorer'da hazır olarak bulunur. Bu raporları kullanarak rezerve edilmiş bulut sunucuları için özel kullanım ve kapsam hedefleri belirleyebilir, hedefiniz doğrultusunda kaydettiğiniz ilerlemeyi görselleştirebilir ve istek üzerine fiyatlara kıyasla ne kadar tasarruf ettiğinize ilişkin bilgilere erişebilirsiniz. Buradan, size sunulan filtreleme boyutlarını (hesap, bulut sunucusu tipi, kapsam vb.) kullanarak temeldeki verileri daraltabilir ve bu sayede rezervasyonlarınız hakkında daha fazla bilgiye ulaşabilirsiniz.

## 5.5. Savings Plans
![45](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/204fc4d0-a2e1-47a3-b0b4-1245e95a5586)


Savings Plans, bir veya üç yıllık bir süreliğine belirli bir kullanım taahhüdü (USD/saat şeklinde hesaplanan) karşılığında istek üzerine fiyatlandırmaya kıyasla daha düşük fiyatlar sunan esnek bir fiyatlandırma modelidir. AWS üç tür Savings Plans sunar; Compute Savings Plans, EC2 Instance Savings Plans, ve Amazon SageMaker Savings Plans. Compute Savings Plans, Amazon EC2, AWS Lambda ve AWS Fargate üzerindeki kullanımlar için geçerlidir. EC2 Instance Savings Plans, EC2 kullanımı ve Amazon SageMaker Savings Plans ise Amazon SageMaker kullanımı için geçerlidir. AWS Cost Explorer'da kolayca 1 veya 3 yıllık dönem için Savings Plans'e kaydolabilir ve önerilerden, performans raporlama olanaklarından ve bütçe uyarılarından faydalanarak planlarınızı kolayca yönetebilirsiniz.


