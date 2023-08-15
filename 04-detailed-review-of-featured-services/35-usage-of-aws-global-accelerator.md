# 36. AWS Global Accelerator
AWS Global Accelerator, yerel ve global kullanıcılar için uygulamalarınızın performansını iyileştirmek için hızlandırıcılar oluşturduğunuz bir hizmettir. Seçtiğiniz hızlandırıcı türüne bağlı olarak ek avantajlar elde edebilirsiniz: 

Standart bir hızlandırıcı ile, küresel bir izleyici kitlesi tarafından kullanılan internet uygulamalarınızın kullanılabilirliğini artırabilirsiniz. Standart bir hızlandırıcı ile Global Accelerator, trafiği AWS küresel ağı üzerinden istemciye en yakın bölgedeki uç noktalara yönlendirir. 

Özel bir yönlendirme hızlandırıcıyla, bir veya daha fazla kullanıcıyı birçok hedef arasından belirli bir hedefe eşleyebilirsiniz. Global Accelerator, birden çok AWS bölgesindeki uç noktaları destekleyen global bir hizmettir.

![301](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/deadbdcd-97c6-47b6-bf55-ab03ac192cf2)

Varsayılan olarak Global Accelerator, hızlandırıcınızla ilişkilendirdiğiniz statik IP adresleri sağlar. Statik IP adresleri, AWS uç ağından herhangi bir şekilde yayınlanır. IPv4 için Global Accelerator, iki statik IPv4 adresi sağlar. İkili yığın için Global Accelerator toplam dört adres sağlar: iki statik IPv4 adresi ve iki statik IPv6 adresi. IPv4 için Global Accelerator'ın sağladığı adresleri kullanmak yerine, bu giriş noktalarını Global Accelerator'a (BYOIP) getirdiğiniz kendi IP adres aralıklarınızdan IPv4 adresleri olacak şekilde yapılandırabilirsiniz. 

Statik IP adresleri, hızlandırıcıyı devre dışı bıraksanız ve artık trafiği kabul etmese veya yönlendirmese bile, hızlandırıcınız var olduğu sürece ona atanmış olarak kalır. Ancak, bir hızlandırıcıyı sildiğinizde, ona atanan statik IP adreslerini kaybedersiniz, dolayısıyla artık bunları kullanarak trafiği yönlendiremezsiniz. Bir hızlandırıcıyı silme izinleri olan kullanıcıları sınırlamak için Global Accelerator ile etiket tabanlı izinler gibi IAM politikalarını kullanabilirsiniz. Standart hızlandırıcılar için Global Accelerator, trafiği sistem durumuna, istemci konumuna ve yapılandırdığınız ilkelere göre optimum bölgesel uç noktaya yönlendirmek için AWS küresel ağını kullanır ve bu da uygulamalarınızın kullanılabilirliğini artırır. 

Standart hızlandırıcılar için uç noktalar, bir AWS bölgesinde veya birden çok bölgede bulunan Ağ Yük Dengeleyiciler, Uygulama Yük Dengeleyiciler, Amazon EC2 bulut sunucuları veya Elastic IP adresleri olabilir. Hizmet, istemcilerden gelen internet trafiğinin her zaman sağlıklı uç noktalara yönlendirilmesini sağlamak için sağlık veya yapılandırmadaki değişikliklere anında tepki verir.
