# 28. AWS KMS (Key Management Service)
Bu konunun öneminin anlaşılması açısından şifreleme yani encryption’un neden kullanıldığı ve önemi bilinmelidir.

## 28.1. Encryption Nedir?
Şifreleme (encryption), yalnızca yetkili tarafların bilgileri anlayabilmesi için verileri karıştırmanın bir yoludur. Teknik anlamda, insan tarafından okunabilen düz metinlerin, şifreli metin olarak da bilinen anlaşılmaz metne dönüştürülmesi işlemidir. Daha basit bir ifadeyle, şifreleme, okunabilir verileri alır ve rastgele görünecek şekilde değiştirir. Şifreleme, bir şifreleme anahtarının kullanılmasını gerektirir. Şifreleme anahtarı ise; şifreli bir mesajın hem göndericisinin hem de alıcısının üzerinde anlaşmaya vardığı bir dizi matematiksel değer.

![296](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/5f35d253-1310-44f8-bea8-2100563009d6)

Şifrelenmiş veriler rastgele görünse de şifreleme mantıklı ve öngörülebilir bir şekilde ilerler ve şifrelenmiş verileri alan ve doğru anahtara sahip olan bir tarafın verilerin şifresini çözerek onu düz metne dönüştürmesine izin verir. Gerçekten güvenli şifreleme, üçüncü bir tarafın kaba kuvvetle, başka bir deyişle anahtarı tahmin ederek şifreli metnin şifresini çözmesi veya kırması pek olası olmadığı kadar karmaşık anahtarlar kullanır. 

Şifreleme anahtarı, verileri rastgele görünecek şekilde değiştirmek için bir şifreleme algoritması içinde kullanılan bir karakter dizisidir. Fiziksel bir anahtar gibi, verileri kilitler (şifreler), böylece yalnızca doğru anahtara sahip birinin kilidini açabilmesi (şifresini çözebilmesi).

## 28.2. AWS KMS
AWS Key Management Service (AWS KMS), birçok AWS hizmetinde ve uygulamalarınızda şifreleme anahtarları oluşturup yönetmenizi ve bunların kullanımını denetlemenizi kolaylaştırır. AWS KMS, anahtarlarınızı korumak için FIPS 140-2 kapsamında doğrulanmış veya doğrulanma sürecinde olan donanım güvenlik modüllerini kullanan güvenli ve dayanıklı bir hizmettir. AWS KMS, düzenleme ve mevzuat uyumluluğu gereksinimlerinizi karşılamanıza yardımcı olmak amacıyla tüm anahtar kullanımlarının günlüklerini sağlamak için AWS CloudTrail ile entegredir

AWS Key Management Service (KMS), verilerinizi korumak için kullanılan şifreleme anahtarları üzerinde size merkezi kontrol sağlar. Hizmet, diğer AWS hizmetleriyle entegre olduğundan, bu hizmetlerde depoladığınız verileri şifrelemeyi ve bunların şifresini çözen anahtarlara erişimi kontrol etmeyi kolaylaştırır. AWS KMS ayrıca AWS CloudTrail ile entegredir. Böylelikle size kimin hangi anahtarları, hangi kaynaklarda ve ne zaman kullandığını denetleme olanağı sağlar. AWS KMS, geliştiricilerin doğrudan veya AWS SDK'yı kullanarak uygulama kodlarına kolayca şifreleme veya dijital imza işlevi eklemesine olanak tanır. AWS Encryption SDK, uygulamalarında yerel olarak verileri şifrelemesi/şifresini çözmesi gereken geliştiriciler için bir kök anahtar sağlayıcısı olarak AWS KMS'yi destekler.

AWS KMS, anahtarlarınızın yaşam döngüsü ve izinleri üzerinde size merkezi denetim sağlar. Dilediğiniz zaman yeni anahtarlar oluşturabilir ve anahtarları kimlerin kullanabileceğinden ayrı olarak kimlerin yönetebileceğini kontrol edebilirsiniz. AWS KMS tarafından oluşturulan anahtarları kullanmaya alternatif olarak, anahtarları kendi anahtar yönetimi altyapınızdan içe aktarabilir veya AWS CloudHSM kümenizde depolanan anahtarları kullanabilirsiniz. AWS KMS'de oluşturulan kök anahtarların, önceden şifrelenmiş verileri yeniden şifrelemeye gerek kalmadan yılda bir kez otomatik olarak döndürülmesini seçebilirsiniz. Hizmet, önceden şifrelenmiş verilerin şifresini çözmek için kök anahtarın eski sürümlerini otomatik olarak hazır tutar. Kök anahtarlarınızı yönetebilir ve kullanımlarını AWS Management Console'dan veya AWS SDK veya AWS Komut Satırı Arabirimi'ni (CLI) kullanarak denetleyebilirsiniz.

## 28.3. KMS Servisinin Kullanımı
KMS servisinin kontrol paneline ulaştığımızda sol tarafta 3 farklı alt başlık bulunmaktadır. Bu alt başlıklara yakından bakmak gerekirse:

- ***AWS Managed Keys:*** AWS tarafından oluşturulan ve yönetilen anahtarlardır. SNS, EBS ve RDS konu başlıklarında otomatik yaratılan anahtarlar bu kategori altında bulunur ve Amazon’un Key Store’unda depolanır. 
- ***Customer Managed Keys:*** AWS üzerinden kullanıcıların oluşturduğu ve yönettiği ancak yine de Amazon Key Store içerisinde depolanan anahtarlar bu alt başlık altında listelenir ve oluşturulur. 
- ***Customer Key Stores:*** AWS CloudHSM (Hardware Security Module) ile Amazon kullanıcılarına özel atanmış bir alan ayırır ve bu alanı kullanıcıya atar. Kullanıcıya ait anahtarlar artık bu alanda depolanır.

Customer managed key alt başlığına giderek bir anahtar (key) oluşturalım ve sonrasında bu anahtarın bir servisteki verileri şifrelemesini sağlayalım. Bunun için şu adımları izleyebiliriz:

- “Create key” diyerek ilk manuel anahtar oluşturma işlemine başlayabiliriz.
- Anahtar tipi olarak simetrik (Symmetric) türünü seçelim. 
- Key usage olarak da varsayılan olan “Encrypt and decrypt” seçeneği ile devam edebiliriz.
- Key material origin olarak KMS’i seçelim böylelikle tüm özellikleri ile KMS üzerinde duracaktır. 
- Tek bölgeye ait bir anahtar olsun bu yüzden “Single-Region key” diyelim. 
- Alias olarak “ilkKey” diyelim. Diğer alanları boş bırakarak sonraki aşamaya geçelim.
- Key administrators alanında bu anahtarı hangi kullanıcıların yönetilmesi izin verileceği sorulur. Bir rol veya kullanıcı seçilebilir. Aktif olduğumuz kullanıcıyı seçelim ve devam edelim.
- Define key usage permissions alanında ise bu anahtarı kimler kullanabilir ayarlaması yapılır. Bu kısımda da yine aktif olduğumuz kullanıcıyı seçelim. 
- Son sayfa da bir policy gösterilir ve onayla diyerek bu adım geçilir. Artık bir anahtara sahip oluruz. 
- Anahtar seçili iken Key Actions → Schedule key deletion seçeneği oluşturulan anahtarın bir süre sonra silinmesini sağlar. Ancak unutulmamalıdır ki anahtar silinirse bu anahtarla oluşturulan verileri daha sonra tekrar okuyamayız. 
- Hemen EC2 kontrol paneline ulaşalım ve EBS altında bir volume oluşturalım. gp2 general purpose ssd ve alan olarak da 10 Gb akab seçilim. Encryption alanında ise “Encrypt this volume” dedikten sonra aşağıda çıkan seçim alanından az önce oluşturulan “ilkKey” seçilebilir. 
- Bu aşamadan sonra volume’e yazılacak tüm veriler bu anahtarla şifrelenerek yazılacaktır.

Böylelikle KMS servisi sayesinde farklı servisler için oluşturulan anahtarları tek bir yerden yönetme imkanına sahip oluruz.
