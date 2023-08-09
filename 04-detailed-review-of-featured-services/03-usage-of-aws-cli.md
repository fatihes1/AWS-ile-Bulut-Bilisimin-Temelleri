# 4. AWS Command Line Interface (CLI)
AWS Komut Satırı Arabirimi (CLI), AWS hizmetlerinizi yönetmek için kullanabileceğiniz birleşik bir araçtır. Tek bir aracı indirip yapılandırarak birden çok AWS hizmetini komut satırından kontrol edebilir ve betikler aracılığıyla otomatikleştirebilirsiniz.
- ***Linux Shell:*** Linux veya macOS'ta komutları çalıştırmak için bash, zsh ve tcsh gibi yaygın kabuk programlarını kullanılabilir. 
- ***Windows Command Line:*** Windows'ta komutları Windows komut isteminde veya PowerShell'de çalıştırabilirsiniz. 
- ***Remotely:*** PuTTY veya SSH gibi bir uzak terminal programı veya AWS Systems Manager ile Amazon Elastic Compute Cloud (Amazon EC2) örneklerinde komut çalıştırabilirsiniz.

AWS Management Console'daki tüm IaaS (hizmet olarak altyapı) AWS yönetim, yönetim ve erişim işlevleri, AWS API ve AWS CLI'da mevcuttur. Yeni AWS IaaS özellikleri ve hizmetleri, başlatma sırasında veya başlatmadan sonraki 180 gün içinde API ve CLI aracılığıyla tam AWS Management Console işlevselliği sağlar. 

AWS CLI, AWS hizmetlerinin genel API'lerine doğrudan erişim sağlar. AWS CLI ile bir hizmetin yeteneklerini keşfedebilir ve kaynaklarınızı yönetmek için kabuk komut dosyaları geliştirebilirsiniz. Düşük seviyeli, API eşdeğeri komutlara ek olarak, birkaç AWS hizmeti, AWS CLI için özelleştirmeler sağlar. Özelleştirmeler, karmaşık bir API'ye sahip bir hizmetin kullanımını basitleştiren daha üst düzey komutlar içerebilir. 

Yönetim konsolu üzerinden yapılan her işlem komut satırlarıyla da yapılabilir. Belli aralıklarla tekrarlanan işlemler için bash script’ler oluşturularak otomatikleştirilebilir.

``aws configure`` komutu ile AWS komut satırına bağlanılma isteği oluşturulur. Sırasıyla tanımlanmış olan IAM hesabının erişim anahtarı ve gizli erişim anahtarı bilgileri girilir. Sonrasında bir bölge belirtilmedikçe varsayılan olarak hangi bölgenin seçilmesi istendiği sorulur. Son sorulan girdi ise varsayılan çıktıların hangi formatta istendiğidir. Buna yaygın olan JSON ile cevap verilebilir. AWS komut satırları ``aws SERVIS_ADI PARAMETRE`` formatında çalışır. Örneğin S3 içerisinde bulunan tüm bucket’ların listelenmesi için ``aws s3 ls`` komutu kullanılır. En temel komut ise yardım komutudur. Amazon S3 içerisindeki kullanılabilecek komutları görmek için ``aws s3 help`` komutu yeterli olacaktır.
