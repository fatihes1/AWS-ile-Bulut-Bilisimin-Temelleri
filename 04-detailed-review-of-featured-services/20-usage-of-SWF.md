# 21. SWF (Simple Workflow Service)
Amazon Simple Workflow Service (Amazon SWF), dağıtılmış bileşenler arasında çalışmayı koordine eden uygulamalar oluşturmayı kolaylaştırır. Amazon SWF'de görev, uygulamanızın bir bileşeni tarafından gerçekleştirilen mantıksal bir çalışma birimini temsil eder. Uygulama genelinde görevleri koordine etmek, uygulamanın mantıksal akışına göre görevler arası bağımlılıkları, zamanlamayı ve eş zamanlılığı yönetmeyi içerir. Amazon SWF, ilerlemelerini 
takip etme ve durumlarını koruma gibi temel karmaşıklıklar hakkında endişelenmeden görevleri uygulama ve koordine etme konusunda size tam kontrol sağlar.

![289](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/03154a4a-9187-40b9-8b26-64d1cd9d409b)

Amazon SWF'yi kullanırken görevleri gerçekleştirmek için çalışanları (workers) uygularsınız. Bu çalışanlar, Amazon Elastic Compute Cloud (Amazon EC2) gibi bulut altyapısında veya kendi tesislerinizde çalışabilir. Uzun süren veya başarısız olabilen, zaman aşımına uğrayabilen, yeniden başlatma gerektirebilecek ya da değişen aktarım hızı ve gecikme süresiyle tamamlanabilecek görevler oluşturabilirsiniz. Amazon SWF, görevleri depolar ve hazır olduklarında çalışanlara atar. İlerlemelerini izler ve tamamlanma ayrıntıları da dahil olmak üzere durumlarını korur. Görevleri koordine etmek için Amazon SWF'den her görevin en son durumunu alan ve sonraki görevleri başlatmak için kullanan bir program yazarsınız. Amazon SWF, uygulamanın bağımsız bileşenlerdeki arızalara karşı dayanıklı olması için uygulamanın yürütme durumunu dayanıklı bir şekilde korur. Amazon SWF ile bu uygulama bileşenlerini bağımsız olarak uygulayabilir, dağıtabilir, ölçeklendirebilir ve değiştirebilirsiniz. 

Amazon SWF, çeşitli uygulama gereksinimlerini destekleyecek özellikler sunar. Medya işleme, web uygulaması arka uçları, iş süreci iş akışları ve analitik işlem hatları dahil olmak üzere görevlerin koordinasyonunu gerektiren bir dizi kullanım durumu için uygundur. 

Kısaca özetlemek gerekirse; SWF servisi bir işlemin durumunu başından sonuna kadar takip etmek için kullanılır. Bu servis, alt görevlerin durumlarını ve işlem sonuçlarını tutar. SWF servisi temelde bir iş yapmıyor, yapılan işin düzgün sırayla yapılabilmesini ve gerekli aksiyonların tetikletilebilmesini sağlar. Üç bölümden oluşur:

- ***Workflow Starter:*** Uygulama başlatıcıdır. 
- ***Worflow Decider:*** Koordinasyon sağlar. Çıktılara göre başka durumları ve servisleri tetikleyebilir. Örneğin bir online alışveriş sitesindeki stok kontrolü işlemi gibi.
- ***Workflow Worker:*** Esas işi yapan ve sonuçları dönen bileşen olarak düşünülebilir.

Aslında workflow, SQS hizmetinde bir kuyruk yaratarak ve sonrasında bu kuyruğu programlayarak üretilebilir. Ancak; AWS bunu ayrı bir servis olarak sunmanın kullanıcılara kolaylık sağlayacağına inanmıştır. Bununla beraber kimi durumlarda SWF, SQS hizmeti yerine de kullanılabilir.
