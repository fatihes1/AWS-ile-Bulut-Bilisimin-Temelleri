# 9. AWS Direct Connect & VPN Servisi
4.9. AWS Direct Connect & VPN Servisi AWS Direct Connect, dahili ağınızı standart bir ethernet fiber optik kablo üzerinden bir AWS Direct Connect konumuna bağlar. Kablonun bir ucu yönlendiricinize, diğer ucu bir AWS Direct Connect yönlendiricisine bağlıdır. Bu bağlantıyla, ağ yolunuzdaki internet servis sağlayıcılarını atlayarak doğrudan genel AWS hizmetlerine (örneğin, Amazon S3'e) veya Amazon VPC'ye sanal arabirimler oluşturabilirsiniz. Bir AWS Direct Connect konumu, ilişkili olduğu bölgede AWS'ye erişim sağlar. Diğer tüm genel bölgelerdeki genel AWS hizmetlerine erişmek için genel bir bölgede veya AWS GovCloud'da (ABD) tek bir bağlantı kullanabilirsiniz.

![268](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/64f59a41-4ff6-457d-b6c6-eeef3206844b)

Önceki başlık altında VPC konusunu ele alırken, VPC’lerin izole birer ortam olduğunu ama VPC peering ile de bu VPC’leri birbirleriyle bağlayabildiğimizden bahsetmiştik. Peki, şöyle bir senaryo ile karşı karşıya kaldığımızda ne yapacağız: VPC’yi genişletmek istediğimiz ortam başka bir VPC değil de kendi veri merkezimiz ise nasıl bir yol izlemeliyiz? Bu konuda iki yönteme başvurulabilir: VPN ve AWS Direct Connect. 

VPN’in AWS tarafındaki sanal ucuna virtual private gateway denir. Firma da bulunan fiziksel uca da customer gateway adı verilmektedir. Trafik internet üzerinden şifreli olarak iletilecektir. Ancak hız hem firmanın alt yapı hızına hem de AWS hızına göre değişecektir. Bu durumlardan dolayı AWS Direct Connect servisini kullanmak kullanıcılara daha verimli bir hizmet sunar. 

Direct Connect, AWS’nin dünya genelinde birçok ağ bağlantısı partneri ile yaptığı anlaşmalar sonucu oluşturduğu bir bağlantı servisidir. Henüz Türkiye’de kullanıma açılmamış bir servistir. 

Türkiye’de olma durumunu senaryo üzerinden ele alalım. AWS, Turk Telekom gibi kendi yüksek bağlantı hızlı veri merkezi olan servis sağlayıcılar ile anlaşarak; onların bağlantı merkezi ile AWS arasına geniş bantlı, kapalı devre bir bağlantı kurar. Firma, bu bağlantı noktasına MPLS gibi tamamen kapalı, firmaya özel bir bağlantı çeker. Hızı ve özellikleri firmanın seçimine bırakılır. Varsayalım ki bu firma, 1GB per seconds ve 10 GB per seconds olmak üzere iki bağlantı seçeneği sunuyor. Direct connect hizmeti veren partner bu bağlantıyı sağlar. 

Firma, endüstri standardı olan 802.1Q WLAN’larla, birden fazla VPC’ye ya da AWS’nin S3 gibi public servislerine bu bağlantı üzerinden güvenli ve düşük gecikmeli olarak bağlantı sağlayabilir. Böylelikle müşterileri bu partner firmaları köprü olarak kullanarak, AWS üzerinde barınan VPC’ler ile kendi firmalarında bulunan veri merkezlerini bağlayarak ağ alt yapılarını genişletmiş olur.

