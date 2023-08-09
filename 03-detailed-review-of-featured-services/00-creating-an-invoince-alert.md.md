# 1. Fatura Alarmı Oluşturma
Servisleri kullanmaya geçmeden önce fatura alarmı oluşturmak mantıklıdır. Böylelikle beklenti dışı bir fiyatlandırma ile karşı karşıya kalma olasılığınız düşecektir. Fatura alarmını oluşturmak aşağıdaki adımlar izlenmelidir.

- AWS Managment Console (Yönetim Konsolu) üzerinde sağ üstte bulunan kullanıcı adına tıklanmalıdır.
![232](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/1dede968-dc9f-47af-8582-5e4be2cf4e44)

- Açılan menü üzerinden “Biling Dashboard” yani faturalandırma kontrol paneli seçeneğine tıklanır.
- Açılan kontrol panelinde sol tarafta bulunan menülerden “Budgets” yani bütçeler seçeneğine tıklanır.
![233](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/4c8b66fc-95fd-4230-967c-88d5da01352c)

- Turuncu “Create budget” butonuyla birlikte bir bütçe oluşturulmaya başlanır.
- Bütçe oluşturma butonuna bastıktan sonra 5 adımdan oluşan bütçe oluşturma sayfası kullanıcıları karşılar.
![234](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/d6ff32a1-0ccc-4d7b-8bfa-b6a596db1370)

Bu adımlar sırayla şu şekildedir:

- **Adım 1:** Bütçe türünün seçilmesi : Seçilebilecek dört farklı bütçe türü bulunmaktadır:
-- ***Maliyet bütçesi (AWS tarafından önerilen):*** Maliyetlerinizi belirli bir dolar tutarına göre izler ve kullanıcı tanımlı eşiklere ulaşıldığında uyarılar alırsınız. Maliyet bütçelerini kullanarak, belirlediğiniz bütçe ödemek istediğiniz maksimum tutar olacaktır, beklenen bulut harcamanızı temsil eder. Örneğin, bir iş birimi için bir maliyet bütçesi ayarlayabilir ve ardından ilişkili üye hesapları gibi ek parametreler ekleyebilirsiniz.
-- ***Kullanım bütçesi:*** Bir veya daha fazla belirtilen kullanım türü / kullanım türü grubu kullanımınızı izler ve kullanıcı tanımlı eşiklerinize ulaşıldığında uyarılar alırsınız. Kullanım bütçelerini kullanarak, bütçelenen tutar, beklenen kullanımınızı temsil eder. Örneğin, Amazon EC2 ve Amazon S3 gibi belirli hizmetlerin kullanımını izlemek için bir kullanım bütçesi kullanabilirsiniz. Böylelikle bu servislerin her biri için ne kadar bütçe değerinde kullanım olacağını belirtebilirsiniz.
-- ***Tasarruf planları bütçesi:*** Tasarruf planlarınızla ilişkili kullanımı veya kapsamı takip eder ve yüzdeniz tanımladığınız eşiğin altına düştüğünde uyarılar alın. Bir kapsam hedefi belirlemek, örnek kullanımınızın ne kadarının tasarruf planları tarafından kapsandığını görmenizi sağlarken bir kullanım hedefi belirlemek, tasarruf planlarınızın kullanılmadığını veya yeterince kullanılmadığını görmenizi sağlar.
-- ***Rezervasyon bütçesi:*** Rezervasyonlarınızla ilişkili kullanımı veya kapsamı takip eder ve yüzdeniz tanımladığınız eşiğin altına düştüğünde uyarı alın. Kapsam hedefi belirlemek, bulut sunucusu kullanımınızın ne kadarının rezervasyonlar tarafından kapsandığını görmenizi sağlarken bir kullanım hedefi belirlemek, rezervasyonlarınızın kullanılmadığını veya yeterince kullanılmadığını görmenizi sağlar. Amazon EC2, Amazon RDS, Amazon Redshift, Amazon ElastiCache ve Amazon ElasticSearch servisleri için rezervasyon uyarıları desteklenir.

- **Adım 2:** Bütçenin belirlenmesi.
-- Bu adım altında yapılacak ilk işlem oluşturulacak bütçeye bir isim vermek olacaktır. 1-100 karakter arasında bir bütçe ismi belirlenir.
-- Bütçe tutarının ayarlanması alanında ilk olarak günlük, aylık, üç ayda bir veya yıllık olmak üzere hangi periyotlarla faturalandırılmak istediğiniz belirtilir. Sonrasında bütçe bu periyotlar arasında sürekli yenilensin mi yoksa sadece belirli bir aralıkta mı geçerli olacağına karar verilir. Bütçeleme yönetimi altında fixed (tek bir tutara göre planlanır), planned (her bütçeleme periyodu için ayrı bir bütçe belirlenir) ve aut-adjusting (önceki kullanımlara göre otomatik oluşturulur) olmak üzere üç seçenek vardır. Son aşama olarak bütçeniz miktarını dolar cinsinden belirtmeniz istenir.
-- Bütçe kapsamı alanı altında tüm AWS servisleri için mi yoksa belirli servisler için mi bütçenin tanımlandığı belirlenir.

- **Adım 3:** Uyarıların yapılandırılması.
-- Bu aşamada belirlenen bütçenin kullanıcı tarafından belirlenen bir yüzde değerine geldiğinde yine kullanıcı tarafından belirlenen e-posta adresine uyarı maili gönderilir.

- **Adım 4:** Opsiyonlu olan eylem eklenmesi.
-- Bir bütçe eylemi, maliyet bilincine sahip bir kültürü güçlendirmek için maliyet tasarrufu yanıtlarını tanımlamanıza ve tetiklemenize olanak tanır. EC2 bulut sunucusunun daha fazla maliyete maruz kalmasını durdurmak gibi uyarı eşiğiniz aşıldığında çalıştırılan eylemleri ekleme seçeneğiniz vardır. Eylem eklemek istediğiniz uyarıları seçebilir, ardından bu eylemleri tanımlayabilirsiniz.

- **Adım 5:** Gözden geçirilmesi.
-- Bu aşamada ise oluşturulacak olan bütçe ayarları gözden geçirilir ve bütçe oluşturulur.
