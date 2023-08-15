# 27. ECS, EKS, ECR & Fargate
## 27.1. Amazon ECS (Elastic Container Service)
Amazon Elastic Container Service (Amazon ECS), kapsayıcı olan iş yüklerini AWS'de kolayca dağıtmanıza olanak tanır. Amazon ECS'nin güçlü basitliği, tek bir Docker kapsayıcısından tüm kurumsal uygulama portföyünüzü yönetmeye kadar büyümenize olanak tanır. Konteyner iş yüklerinizi, bir kontrol düzlemi veya düğümleri yönetmenin karmaşıklığı olmadan bulutta ve şirket içinde kullanılabilirlik alanları genelinde çalıştırabilir ve ölçeklendirme yapabilirsiniz.

## 27.2. Amazon EKS (Elastic Kubernetes Service)
Amazon Esnek Kubernetes Hizmeti (Amazon EKS), AWS'de ve yerinde Kubernetes çalıştırmanızı kolaylaştıran bir yönetilen Kubernetes hizmetidir. Kubernetes; container'lı uygulamaların dağıtım, ölçeklendirme ve yönetim süreçlerini otomatikleştirmeye yönelik bir açık kaynak sistemdir. Amazon EKS, sertifikalı bir şekilde Kubernetes uyumludur, yani yukarı akış Kubernetes'te çalışan mevcut uygulamalar Amazon EKS ile uyumludur. 

Amazon EKS, container'ları planlama, uygulama erişilebilirliğini yönetme, küme verilerini depolama ve diğer temel görevlerden sorumlu Kubernetes denetim düzlemi düğümlerinin erişilebilirliği ve ölçeklenebilirliğini otomatik olarak yönetir. 

Amazon EKS, Kubernetes uygulamalarınızı hem Amazon Elastic Compute Cloud (Amazon EC2) hem de AWS Fargate'te çalıştırmanıza olanak sağlar. Amazon EKS ile AWS altyapısının performansı, ölçeği, güvenirliği ve erişilebilirliğinden tamamen faydalanmanın yanı sıra yük dağıtımı için Application Load Balancer'lar (ALB'ler), rol tabanlı erişim denetimi (RBAC) ile AWS Identity and Access Management (IAM) entegrasyonu ve pod ağı için AWS Virtual Private Cloud (VPC) desteği gibi AWS ağ iletişimi ve güvenlik hizmetleri ile olan entegrasyonlardan faydalanabilirsiniz.

## 27.3. Amazon ECR (Elastic Container Registry)
Amazon Elastic Container Registry (Amazon ECR); Amazon Elastic Container Service (Amazon ECS) ve Amazon Elastic Kubernetes Service (Amazon EKS) ile entegre edilmiştir; bu, her iki düzenleyici ile uygulamalar için container görüntülerini kolayca depolayıp çalıştırabileceğiniz anlamına gelir. Yapmanız gereken tek şey, uygulamalarınız için uygun görüntüleri almak üzere Amazon ECS veya Amazon EKS için görev veya pod tanımınızda Amazon ECR deposunu belirtmektir. 

Amazon ECR, Open Container Initiative (OCI) standartlarını ve Docker Registry HTTP API V2'yi destekler. Bu, mevcut geliştirme iş akışınızı sürdürerek Amazon ECR ile etkileşim kurmak için Docker CLI komutlarını (ör. itme, çekme, listeleme, etiketleme) veya tercih ettiğiniz Docker araçlarını kullanmanıza olanak tanır. Bulutta, şirket içinde veya yerel bilgisayarınızda herhangi bir Docker ortamından Amazon ECR'ye kolayca erişebilirsiniz. Amazon ECR, depolarınızda Docker container görüntülerini ve ilgili OCI yapıtlarını depolamanıza olanak tanır.

## 27.4. AWS Fargate
AWS Fargate, kapsayıcılarınızı AWS'de dağıtmanın kolay bir yoludur. Basitçe söylemek gerekirse, Fargate EC2 gibidir ancak size sanal bir makine vermek yerine bir kapsayıcı alırsınız. Temeldeki örnekleri yönetmek zorunda kalmadan kapsayıcıları temel bir bilgi işlem ilkesi olarak kullanmanıza olanak tanıyan bir işlem motorudur. Tek yapmanız gereken kapsayıcı imajınızı oluşturmak, CPU ve bellek gereksinimlerini belirlemek, ağ ve IAM politikalarınızı tanımlamak ve başlatmak. Fargate ile uygulama ihtiyaçlarınızı yakından karşılayacak esnek yapılandırma seçeneklerine sahip olursunuz ve saniye başına ayrıntı düzeyiyle faturalandırılırsınız.

![295](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/38e67517-0b7d-4e60-b262-e225f7caedf7)

En iyi kısım ise, aynı ECS temel öğelerinin, API'lerinin ve AWS entegrasyonlarının tümünü kullanmaya devam edebilirsiniz. Fargate, Amazon Virtual Private Cloud (Amazon VPC), AWS Identity and Access Management (IAM), Amazon CloudWatch ve yük dengeleyicilerle yerel entegrasyonlar sağlar. Fargate görevleri, AWSVPC ağ modunu kullanır ve kaynaklarınızla güvenli bir şekilde iletişim kurmak için VPC'nizde bir Elastik Ağ Arayüzü (ENI) sağlar. AWS Komut Satırı Arabirimi (CLI) ile bir Fargate görevini başlatmak basittir.
