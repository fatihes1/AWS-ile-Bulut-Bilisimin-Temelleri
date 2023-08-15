# 29. AWS Directory Service
AWS Managed Microsoft Active Directory (AD) olarak da bilinen Microsoft Active Directory için AWS Directory Service, dizin bilgilerini kullanan iş yüklerinizin ve AWS kaynaklarınızın AWS’de yönetilen Active Directory'i (AD) kullanmasına imkân tanır. AWS Managed Microsoft AD, Microsoft AD'nin kendisi temel alınarak oluşturulmuştur ve mevcut Active Directory'nizdeki verileri bulutla eşitlemenizi ya da buluta çoğaltmanızı gerektirmez. Standart AD yönetim araçlarını kullanabilir, grup ilkesi ve tek oturum açma gibi yerleşik AD özelliklerinden yararlanabilirsiniz. AWS Managed Microsoft AD ile Amazon EC2 ve Amazon RDS for SQL Server bulut sunucularını kolayca etki alanınıza katabilir ve AWS En User Computing (EUC) hizmetlerini (Amazon WorkSpaces gibi) AD kullanıcıları ve gruplarıyla kullanabilirsiniz.

Bu servisi bir örnek üzerinden ele alalım. Bir firmada çalıştığımızı varsayalım. 5 çalışanımızın ve her birinin de kendisine ait bir iş bilgisayarı olduğunu düşünelim. Bununla beraber bu beş çalışan için veri saklama ve dosya paylaşma için bir adet sunucu ayırdığımızı varsayalım. Her kullanıcı kendi iş bilgisayarına bir parola ve kullanıcı adı ikilisi ile giriş sağlayabiliyor. Çalışanların sunucu üzerinde hesabı olmamasından dolayı kullanıcılar sunucu üzerinden dosya paylaşamıyor. Her kullanıcıya iş bilgisayarında bulunan kullanıcı adı parola ikilisi ile sunucuda bir hesap açalım. Olası bir durumda kullanıcı kendi iş bilgisayarının şifresini değiştirse de sunucuda bulunan şifre değişmeyecektir. Çünkü bu iki hesap sadece aynı kullanıcı adı ve parolaya sahip tamamıyla farklı hesaplar. 

Bu sorun dizin servisleri ile çözülmüştür. Kullanıcı adı, parola ve diğer ek bilgileri kendi üzerinde tutmak yerine bu bilgiler bir dizin servisinin yüklü olduğu sunucuda tutulur. Her ihtiyaç olduğunda bu sunucudan bilgiler çekilerek kullanılır. Dizin servisleri böylelikle kullanıcı yönetimi, kimlik doğrulama ve kullanıcı yetkilendirme işlemlerine yardım etmiş olur. 

Bu alanda dünyada en popüler olan uygulamalardan biri Microsoft Active Directory diğeri ise aynı hizmeti veren açık kaynaklı SAMBA4’tür. AWS Managed Microsoft AD, AWS ortamında Microsoft Active Directory oluşturmanızı sağlar.

- Standart ve Enterprise sürümleri mevcuttur. 
- Std 30000 objeye kadar, Ent 500000 objeye teorik limitleri bulunur. 
- Trust oluşturma dahil tüm Active Directory özellikleri mevcuttur.
- Kurulu bulunan bölge (region) içerisindeki 2 ayrı AZ’de birer domain controller ile gelir ve ek domain controller eklenebilir.

Bununla beraber Ad Connector;

- Active Directory Proxy hizmetidir. 
- Small ve large olmak üzere iki seçenek sunar. Small seçenek 500 kullanıcıya kadar uygunken, large sürümü 5000 kullanıcıya kadar uyumluluk sağlar.
- Mevcut on-premise active directory (AD) kurulumunu VPC içerisinde genişletmeye imkân tanır.

SAMBA4 için ise Simple AD bulunur, Simple AD;

- Yönetilen Linux Samba4 dizin hizmetidir. 
- Small ve large olmak üzere iki seçenek sunar. Small seçenek 2000 kullanıcıya kadar uygunken, large sürümü 20000 kullanıcıya kadar uyumluluk sağlar. 
- Trust vb. gelişmiş active directory (AD) özellikleri desteklenmez.

Amazon Cognito Your User Pools ise;

- Amazon Cognite Your User Pools, Amazon Cognito’daki bir kullanıcı dizinidir. Bir kullanıcı havuzuyla, kullanıcılarınız web veya mobil uygulamanızda Amazon Cognito aracılığıyla oturum açabilirler. 
- Uygulamalarınıza kullanıcı kaydı ve oturum açma özellikleri eklemenize imkân tanır. 
- Kullanıcı havuzundan SAML kimlik sağlayıcıları ile birlikte Facebook, Google ve Amazon ile giriş yapma imkânı sağlar.

Bununla beraber AWS’nin en yeni servislerinden olan AWS Cloud Directory hiyerarşik veri tutmak için özelleştirilmiş bir dizin hizmetidir. Geliştiriciler için kolay kullanım imkânı sunar.
