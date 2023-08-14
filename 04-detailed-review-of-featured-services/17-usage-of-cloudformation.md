# 18. CloudFormation
Önceki başlıkta en temelinde bir web uygulamasının front, back ve veri tabanı olmak üzere 3 temel bileşenden oluştuğundan bahsetmiştik. Bu bileşenler bir altyapı oluştururken instance’ler, gateway’ler, router tabloları gibi birçok alt bileşen kullanmanız gerekecektir. Bu işlem birden fazla sefer yapılıyor ise her seferinde bileşenler oluşturulup sonrasında da gerekli bağlantıları kurmak zahmetli bir hal alacaktır.

AWS CloudFormation, altyapıyı kod olarak ele alarak ilgili AWS ve üçüncü taraf kaynaklarından oluşan bir koleksiyonu modellemenin, bunları hızlı ve tutarlı bir şekilde sağlamanın ve yaşam döngüleri boyunca yönetmenin kolay bir yolunu sunar. Bir CloudFormation şablonu, istediğiniz kaynakları ve bağımlılıklarını açıklar, böylece bunları bir yığın olarak başlatabilir ve yapılandırabilirsiniz. Kaynakları tek tek yönetmek yerine, bir yığının tamamını tek bir birim olarak, ihtiyaç duyduğunuz sıklıkta oluşturmak, güncellemek ve silmek için bir şablon kullanabilirsiniz. Birden çok AWS hesabı ve AWS bölgesi genelinde yığınları yönetebilir ve sağlayabilirsiniz.

CloudFormation temelde iki bileşenden oluşur. Bunlardan biri **CloudFormation template** diğeri ise **CloudFormation Stack**’tir.

İstediğiniz hizmet veya uygulama mimarileri için JSON veya YAML formatında template’ler oluşturabiliriz. AWS CloudFormation’ın bu template üzerinde bulunan hizmetlerin veya uygulamaların hızlı/güvenilir bir şekilde kurulmasını sağlayabilirsiniz. (stack olarak da adlandırılır.) Ayrıca stack’leri gerektiğinde kolayca güncelleyebilir veya çoğaltabilirsiniz. 

Oluşturulan template dosyası yerel makinede veya S3 bucket’inde tutulabilir. Sonrasında ise CloudFormation aracılığıyla bu template dosyasını kullanarak bir stack yaratırsınız. AWS sizin belirlediğiniz kaynakları, belirlediğiniz şekilde oluşturacaktır. 

Bununla beraber stack oluşturulmuş olsa bile template üzerinde yapılan bir güncelleme hazırlanmış stack üzerine uygulanabilir. 

Bir template dosyası aşağıdaki bileşenleri içerebilir:

- ***Version:*** Template’e versiyon numarası atayarak gelişimini takip etmenize ve birden fazla versiyonunu yaratmanıza imkân sağlar.
- ***Description:*** Template ile ilgili açıklama girmek istenildiği zaman kullanılır. Örneğin bu template neden oluşturuldu, amacı nedir, sonucunda ne olacak tarzı yazılı bir açıklama girilebilir. 
- ***MetaData:*** Template’in temel özelliklerini ve template hakkında ek bilgiler tutabilirsiniz. Örneğin AWS::CloudFormation::Designer attribute’u ile bu template’i kim oluşturuldu bilgisi tutulabilir. 
- ***Parameters:*** Yaratılacak kaynaklarla ilgili seçilmesi gereken seçenekleri bu kısımda belirleyebilirsiniz. Örneğin EC2 sanal makine yaratılan bir template’e parameters kısmında “KeyPair seçimi” parametresini girerseniz daha sonra bu template’den 177 yaratılacak bir stack’in yaratılma aşamasında kullanıcıya hangi keypair’i kullanmak istediğini soracak ve kullanıcın girdiği değer o sanal makine yaratılırken kullanılacaktır. 
- ***Conditions:*** Şartlar bu kısımda belirlenir. Eğer şu seçildiyse bunu yap ama seçilmediyse şunu yap şeklinde koşula göre yön belirleyebilirsiniz. 
- ***Outputs:*** Stack yaratımı sonucunda kullanıcıya geri bildirmek istediğiniz bilgileri bu kısımda belirlersiniz. Örneğin, yaratılan EC2 sanal makinelerinin ip adres bilgilerini ekranda kullanıcıya göstermek isterseniz bunu Outputs kısmında seçmeniz gerekmektedir. 
- ***Resources:*** Her template’de mutlaka bulunması şart olan tek alandır. O template ile yaratılmasını istediğiniz kaynakları belirlersiniz.

## 18.1. CloudFormation Servisinin Kullanımı
“Create a stack” diyerek ilk stack’imizi oluşturalım. Bu aşamada template dosyasını AWS tarafından sunulan hazır bir template olarak devam edeceğiz. Normalde template dosyalarının JSON formatında olduğunu belirtmiştik. Ancak AWS tarafından sunulan “Template Designer” ile bir GUI üzerinden bu dosyalar oldukça kolay bir şekilde oluşturulabilir. “Create a stack” dedikten sonra aşağıdaki adımları izleyelim:

- “Prerequisite - Prepare template” başlığı altında “Template is ready” opsiyonu seçili iken Amazon S3 URL bilgisi ile devam edeceğimiz şekilde ayarlama yapalım. 
- “Amazon S3 URL” alanına “https://s3-us-west-2.amazonaws.com/cloudformationtemplates-us-west-2/VPC_AutoScaling_and_ElasticLoadBalancer.template” bilgisini girelim. Bu adresi tarayıcıdan açtığımızda JSON formatında bir template dosyası olduğunu görebiliriz. 
- View in Designer dediğimizde Şekil: 61’deki gibi görünüm oluşacaktır.
![282](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/b1a93f95-2c27-46ee-a6f1-3553161d26cd)

- Stack için bir isim girmemiz beklenmektedir. İsim alanına “ilkCFstack” girelim. 
- Instance sayısı olarak 1 ve türü olarak ise t2.micro’yu seçelim.
- “KeyName” değeri olarak daha önceki başlıklarda oluşturduğumuzu key’i (windows sanal makinesine bağlanmak için oluşturulan) seçelim. 
- VPC olarak “ilkVPC” ismini verdiğimiz VPC’yi subnet’ler altında da sadece public olan subnet’leri seçelim.
- Permission alanında eğer ki bir yetki gereksinimi varsa gerekli IAM role seçilir, bu template için bir yetki gereksinimi yoktur. 
- “Stack creation options” başlığı altında “Time-out” özelliği bulunmaktadır. Belirtilen süre içerisinde stack oluşumu tamamlanmaz ise o ana kadar oluşan tüm kaynakları siler ve oluşturma işlemini durdurur. Şimdilik bu özellikte kapalı olsun. 
- “Stack failure options” ise stack oluşturulurken bir hata oluşması durumunda oluşturma işlemini tamamıyla durdurup kaynakları silsin mi yoksa o hatalı adımı atlayıp devam mı etsin seçeneği sunulur.

Belirtilen URL ile oluşturulacak stack oluşumu biraz süre alabilir. 10-15 dk kadar geçen bir süreden sonra stack tamamıyla oluştuğunda “Outputs” ekranında bize bir URL verir. Bu URL’e tarayıcıdan gittiğimizde AWS tarafından bize dönen “Tebrikler” web sayfası görüntülenir. 

Stack silinmesi durumunda ise stack’i oluşturan tüm kaynaklar silinmeye başlar, böylelikle kullanıcının tüm kaynakları tek tek bulup kaldırmanıza gerek kalmamış olur.

