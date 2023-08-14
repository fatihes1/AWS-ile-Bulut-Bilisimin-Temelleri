# 22. SES (Simple Email Service)
Amazon Simple Email Service (SES), geliştiricilerin herhangi bir uygulamadan posta göndermesine olanak tanıyan uygun maliyetli, esnek ve ölçeklenebilir bir e-posta hizmetidir. Amazon SES'yi işlemsel, pazarlama veya toplu e-posta iletimi gibi birkaç farklı e-posta kullanım senaryosunu destekleyecek şekilde hızlıca yapılandırabilirsiniz. Amazon SES'nin esnek IP dağıtımı ve e-posta kimlik doğrulaması seçenekleri, teslim edilebilirliği artırır ve gönderenin itibarını korur. Analiz verilerinin gönderilmesi sayesinde de her bir e-postanın etkisi ölçülür. Amazon SES sayesinde e-postaları güvenli biçimde, global olarak ve uygun ölçekte gönderebilirsiniz. 

Amazon SES, Amazon SES konsolu, basit posta aktarma protokolü (SMTP) arayüzü ve Amazon SES API’sı dahil olmak üzere e-posta gönderimi için çeşitli yöntemler sunar. AWS komut satırı arabirimi (AWS CLI) veya bir AWS yazılım geliştirme kiti (SDK) kullanarak API’ya erişebilirsiniz.

## 22.1. SES Esnek Dağıtım Seçenekleri

### 22.1.1. Paylaşımlı IP Adresleri
Varsayılan olarak Amazon SES, diğer Amazon SES müşterileriyle paylaşılan IP adreslerinden e-posta gönderir. Paylaşılan adresler, kurulu IP’lerle hemen gönderime başlamak isteyen birçok müşteri için mükemmel bir seçenektir. Temel Amazon SES fiyatlandırmasına dahildir ve yüksek teslim edilebilirlik sağlamak için itibarları dikkatle izlenir.

### 22.1.2. Özel IP Adresleri
Kendi IP itibarını yönetmek isteyen müşteriler için Amazon SES hesabınızla kullanmak amacıyla özel IP adresleri kiralayabilirsiniz. Bu IP adresi havuzlarını oluşturmak için özel IP havuzları özelliğini de kullanabilirsiniz. Müşteriler bu özel IP’lerden gelen tüm trafiği gönderebilir veya belirli kullanım örneklerini belirli IP’lerle uyumlu hale getirmek için yapılandırma kümelerini kullanabilir.

### 22.1.3. Sahip Olunan IP Adresleri
Amazon SES ayrıca Bring Your Own IP (BYOIP) özelliğini de destekler. Bu özellik, Amazon SES aracılığıyla e-posta göndermek için sahip olduğunuz bir IP adresi aralığını kullanmanızı sağlar. Bu, mevcut yatırımlardan yararlanmayı ve diğer e-posta servis sağlayıcılarından geçişi kolaylaştırır. 

Kısaca özetlemek gerekirse; AWS tarafından sunulan e-posta gönderim servisidir. Uygulamalar aracılığıyla e-posta iletimi yapar. Teslim edilemeyen iletileri kopyalamak yani depolamak için bir e-posta sunucusu lazımdır. 

Gmail, hotmail gibi bir servis değildir. Yani günlük kullanım için tasarlanmamıştır. Binlerce farklı e-posta adresine, tek bir API çağrısı üzerinden kampanya maili gönderme gibi senaryolarda kullanılır. Bununla birlikte iletilme oranları gibi istatiksel değerleri de döndürür. 

SMTP server olarak, AWS SDK ile yarattığınız uygulamanın içinden ya da AWS CLI kullanarak komut satırından e-posta gönderilmesini sağlar.

## 22.2. SES Servisinin Kullanımı
AWS yönetim konsolu üzerinden SES kontrol paneline ulaştıktan sonra “create identity” seçeneğine tıklayalım ve sonrasında aşağıdaki adımları takip edelim:

- Identity details başlığı altında “domain” ve “Email address” olmak üzere iki seçenek bulunur. Domain alanı seçilmesi durumunda bir domain tanıtılır ve sonrasında o domain’e bağlı olan tüm e-posta adresleri otomatik eklenmiş olur. Biz “Email address” seçeneği ile ilerleyelim ve bir e-posta adresi girelim. 
- E-posta adresine gelen doğrulama mailini onaylayalım.
- Domain tanıtımı yapılması durumunda ise onay işlemi bir TXT bir CNAME ve bir tane de MX kaydı oluşturularak yapılır. 
- Eğer ki domain AWS üzerinden temin edilmiş ise “useRoute53” seçeneği de kullanılabilir. Bu alan kayıtlarını otomatik yapacaktır. 
- E-posta gönderirken başlangıç aşamasında spam olma durumuna karşın sadece onaylanan e-postalar ve domainlere e-posta gönderilebilir. Sonrasında belirli bir süre geçtikten sonra “Request a sending limit increase” diyerek onaylanmamış e-postalara da ileti gönderebilir hale gelirsiniz. 
- Solda bulunan “Dedicated IPs” alt başlığı sayesinde hizmete sabit bir IP atayabilirsiniz. Bazı durumlarda mailin sabit bir IP adresinden gitmesi gerekmektedir. 
- Solda bulunan “Configuration sets” alt başlığı sayesinde ise gönderilen mailin açılıpaçılmadığı gibi e-posta ait durum raporlarının CloudWatch, SNS veya Kinesis hizmetlerinde tutulmasını sağlayabilirsiniz. “Create set” diyerek bir set oluşturalım ve adını “ConfigSet” olarak belirleyelim. Sonrasında başka bir işlem yapmamıza gerek yok. 
- Solda bulunan “Cross-account notifications” alt başlığı sayesinde başka bir hesap adına gönderilen e-postalar ile ilgili bildirim almanızı sağlar. 
- Solda bulunan “Email templates” alt başlığı sayesinde bazı kalıp e-postalar atabilirsiniz. E-posta template’i sabittir. Sadece kullanıcı adı gibi değerler değişir. Bunun için bir JSON dosyası oluşturalım ve adını “myTemplate.json” olarak belirleyelim. Dosya örneğin şu şekilde olabilir:
![290](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/57bb8e74-f357-4832-8ed7-d66454d16d22)

- Bu dosyaya “SES” adını verdiğimiz bir klasör/dizinde tutalım. 
- Terminal üzerinden bu “SES” klasörünün olduğu dizine ulaşalım. 
-  ``aws ses create-template --cli-input-json file://myTemplate.json`` komutunu girelim ve template’i ses servisine tanımlayalım. ‒ 
- Sonrasında ``myemail.json``adında bir JSON dosyası da mail için oluşturalım. Bu JSON dosyası şu şekilde görünecektir:
![291](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/651f2f70-72ae-4b50-8f66-a8f0d834a373)

Bu JSON dosyasında “Template” değeri az önce yüklediğim template iken “ConfigurationSetName” değeri ise oluşturduğumuz “ConfigSet” bileşeninden gelir. Son adım olarak aşağıdaki komutu girelim:
``aws ses send-templated-email --cli-input-json file://myemail.json``

Bu komut sayesinde verilen kullanıcı ve ürün adi değişken değerlerine göre “ToAddresses” içerisinde bulunan e-posta adresine e-posta iletilmiş olur.


