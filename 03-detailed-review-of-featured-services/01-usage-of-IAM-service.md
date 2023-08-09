# 2. IAM (Identity and Access Management) Servisi Kullanımı
AWS Identity and Access Management (IAM), tüm AWS genelinde ayrıntılı erişim denetimi sağlar. IAM ile kimlerin hangi hizmet ve kaynaklara hangi koşullarda erişebileceğini belirleyebilirsiniz. IAM politikalarıyla, en az ayrıcalıklı izinleri sunmak için iş gücünüze ve sistemlerinize ilişkin izinleri yönetebilirsiniz. IAM ile kullanıcıların iş gücü ve iş yükleri için AWS izinlerini yönetebilirsiniz. 

Kullanıcıların iş gücü için, AWS hesaplarına erişimi ve bu hesaplardaki izinleri yönetmek amacıyla AWS Single Sign-On'u (AWS SSO) kullanmanız AWS tarafından tavsiye edilir. AWS SSO, AWS kuruluşunuz genelinde IAM rollerini ve politikalarını (policy) sağlamayı ve yönetmeyi kolaylaştırır. İş yükü izinleri için IAM rollerini ve politikalarını kullanabilirsiniz ve iş yükleriniz için yalnızca gerekli erişimi verirsiniz. 

IAM politikalarını kullanarak belirli AWS hizmet API'lerine ve kaynaklarına erişim izni verebilirsiniz. Ayrıca, belirli bir AWS kuruluşundaki kimliklere erişim izni vermek veya belirli bir AWS hizmeti aracılığıyla erişim vermek gibi erişimin verildiği belirli koşulları tanımlayabilirsiniz.

![235](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/2945d61e-7a2e-4e08-8008-2928db5290aa)

Bir AWS hesabınız var ise halihazırda bir “root” yani kök hesaba sahipsiniz. Ancak AWS işlemleri root hesabı ile yapmanızı tavsiye etmez. Root hesaplar sonsuz bir yetkiye sahiptir ve yapılan eylemler geri alınamaz.

![236](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/6c070f2d-1eb5-419f-a1cb-0e4fef99fc18)

IAM servisi altında dört temel konu vardır: Users (kullanıcılar), groups (gruplar), role (roller) ve policy (poliçeler/politikalar).

## 2.1. Kullanıcılar
IAM kullanıcısı, bir hesapta AWS ile etkileşim kurmak için kullanılan uzun vadeli kimlik bilgilerine sahip bir kimliktir.

![237](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/8ea4a6bd-4b3f-4fb2-b3a8-b14b16e16e68)

IAM kontrol paneli üzerinde sol tarafta bulunan “Users” seçeneğinden sonra mavi “Add user” butonunu kullanarak yeni bir IAM kullanıcısı oluşturulur.

- İlk aşamada bir IAM kullanıcısı için kullanıcı adı belirlenmesi beklenir. Sonrası ise AWS kaynaklarına erişim yöntemi seçilmelidir. İki seçenek bulunmaktadır. Bunlar “Erişim anahtarı - Programlı erişim” (AWS API, CLI, SDK ve diğer geliştirme araçları için bir erişim anahtarı kimliği ve gizli erişim anahtarı sağlar.) ve “Şifre - AWS Yönetim Konsolu erişimi” (Kullanıcıların AWS Management Console'da oturum açmasına olanak tanıyan bir parolayı etkinleştirir.) seçenekleridir. AWS yönetim konsolu erişim seçildiğinde kullanıcıya atanacak otomatik bir şifre olmasını isteyip istemediğimiz ve kullanıcın ilk girişinde şifresini değiştirme zorunluluğu olup olmamasını seçtiğimiz ekran gelir. 
- İzinler (permissions) kısmında ise kullanıcıya verilecek izinler tanımlanır. Bu izinler, daha önce oluşturulmuş bir kullanıcıya verilen yetkilendirmeler atanabilir, kullanıcı direkt bir grubun izinleri atanır veya yeni izinler tanımlanabilmektedir. Poliçeler JSON formatında dosyalardır ve oluşturulan kullanıcının hangi servislere izninin olduğunu ve hangi serviste hangi eylemlerine izin veriliyor gibi kısıtlamalar oluşturulmasını sağlar. 
- Sonraki aşamada bir etiket atanması beklenir. Etiketler anahtar-değerler çiftleri şeklindedir. Örneğin insan kaynakları bölümünde çalışan Ahmet adında bir çalışan için “department-hr:ahmet” şeklinde bir etiket root kullanıcının ilerleyen süreçlerde işini kolaylaştıracaktır.
- En son gözden geçirme aşamasından sonra eğer ki ilk aşamada “Erişim anahtarı - Programlı erişim” seçilmiş ise tek sefer görünecek olan erişim anahtarı ve gizli erişim anahtarı görünecektir. AWS tarafından bu bilgilerinin “.csv” formatında indirilmesi tavsiye edilir.

## 2.2. Gruplar
Kullanıcı grubu, IAM kullanıcılarının bir koleksiyonudur. Bir kullanıcı koleksiyonu için izinleri belirtmek için grupları kullanılır.

![238](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/740c8d51-9571-4bb7-8628-c941654570a8)

Bir grup tanımlamak için IAM kontrol paneli üzerinde sol tarafta bulunan “User Groups” seçeneğinden sonra mavi “Create group” butonunu kullanarak yeni bir kullanıcı grubu oluşturulur. Gruba bir isim ve sonrasında halihazırda var olan IAM kullanıcılarından hangilerini bu gruba eklemek istediğiniz sorulur. Son aşama olarak ise izinleri belirtecek poliçenin seçilmesi veya JSON formatında yazılması beklenir. 

Grubu oluştur dedikten sonra grup tanımlanmış olur. Bu gruba eklenecek her üye grubun sahip olduğu izinlere sahip olacaktır.

## 2.3. Roller
IAM rolü, kısa süreler için geçerli olan kimlik bilgileriyle belirli izinlere sahip oluşturabileceğiniz bir kimliktir. Roller, güvendiğiniz varlıklar tarafından üstlenilebilir.

![239](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/e9bae2ed-01f8-43dc-a9a4-d1f7ae00ce6a)

AWS kaynaklarının başka bir AWS kaynağına veya dışarıdan bir kullanıcının sahip olduğunuz AWS kaynaklarına erişebilmesi için oluşturulan yetki seviyeleridir. 

Bir rol tanımlamak için IAM kontrol paneli üzerinde sol tarafta bulunan “Roles” seçeneğinden sonra mavi “Create role” butonunu kullanarak yeni bir kullanıcı grubu oluşturulur. Role oluşturma üç adımdan oluşur:

- **Adım 1:** Güvenilir varlık seçilmesi.
-- Seçilebilecek 5 farklı varlık bulunur: AWS servisi, AWS hesabı, web kimliği, SAML 2.0 federasyonu (kendi aktif dizininizden bir kaynağa), özel olarak belirlenen varlık (kullanıcı tarafından tanımlanır) seçenekleri sunulur. Sonrasında ise hangi servise rol/kullanıcıya atanacağı seçilir.
- **Adım 2:** İzinlerin eklenmesi.
-- Servis, kullanıcı veya varlığa hangi izinler verileceği seçilir veya kullanıcı tarafından JSON formatında oluşturulur.
- **Adım 3:** Adlandırma, gözden geçirme ve oluşturma.
-- Son aşamada ise role bir isim, tanımlama atanır. Gözden geçirme işlemleri ile yapılan konfigürasyonlar kontrol edilir. En son aşamada opsiyonlu olarak etiket ekleme işlemi vardır.

Bu işlemler sonunda rol oluşturulmuş olur.

## 2.4. Poliçeler
Politika (poliçe), AWS'de izinleri tanımlayan bir nesnedir. Genel amaçları yetki dağıtmaktır. JSON ile kullanıcı tanımlı olabileceği gibi kontrol paneli üzerinden GUI ile de oluşturulabilir.

![240](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/f531d98e-07c1-4839-a589-6154a553fa2b)

Bir rol tanımlamak için IAM kontrol paneli üzerinde sol tarafta bulunan “Policies” seçeneğinden sonra mavi “Create Policy” butonunu kullanarak yeni bir kullanıcı grubu oluşturulur. 

Sırayla bir servis, hareket (eylem), kaynak ve talep koşulları seçilerek oluşturulabileceği gibi JSON formatı üzerinden kullanıcı tarafından elle de tanımlanabilir.

Örneğin, S3 servisi üzerinde listeleme ama aynı zamanda çok faktörlü doğrulama şartı koşan rol aşağıdaki JSON formatı ile tanımlanır.

![241](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b8e5dc4e-6e5d-4820-8655-28ca873fb453)

Poliçe tanımlandıktan sonra opsiyonlu olarak etiket bilgisi beklenir. En son aşamada ise poliçeye bir isim ve tanım atanır. Sonrasında poliçe tanımlanmış olur. Oluşturulan poliçe kullanıcı ve gruplara izin olarak atanırken kullanılabilir.


