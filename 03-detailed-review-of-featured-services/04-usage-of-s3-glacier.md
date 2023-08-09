# 5. Amazon S3 Glacier
![248](https://github.com/fatihes1/AWS-ile-Bulut-Bilisimin-Temelleri/assets/54971670/4ec783dc-ac8d-45eb-ae51-03a396e58f8c)

Veri arşivleme için en düşük maliyetli ve milisaniye düzeyinde erişim sunan uzun vadeli, güvenli ve dayanıklı depolama sınıflarıdır. Amazon S3 Glacier depolama sınıfları, performans ihtiyaçlarınızı karşılamak için milisaniye ile saat düzeyinde farklı alım süreleri içeren seçenekler sağlar. S3 Glacier Instant Retrieval depolama sınıfı, tıbbi görüntüler veya haber medya varlıkları gibi anında erişim gerektiren arşivler için milisaniyeler içinde erişim olanağı sunar. S3 Glacier Flexible Retrieval, üç erişim seçeneği sunmaktadır: genellikle 1-5 dakika içinde tamamlanan hızlandırılmış alımlar, genellikle 3-5 saat içinde tamamlanan standart alımlar ve büyük hacimli veriler için genellikle 5-12 saat içinde tamamlanan ücretsiz toplu alımlar. Amazon S3 Glacier Deep Archive depolama sınıfı, 12-48 saat arasında değişen iki alma seçeneği sunar. 

Amazon S3 Glacier servisi neredeyse tüm işlevlerini komut ekranı üzerinden yapmaya izin verir. Mahzen, kısaca mantıksal depolar olarak düşünülebilir. Mahzenlerin içerisine arşivler oluşturulur. Arşivler S3 bucket’ları gibi veri depolarıdır. Yönetim konsolu üzerine sadece vault (mahzen) açılmasına izin verir. Arşiv oluşturma, dosya yükleme, dosya çekme gibi işlemler sadece komut ekranından yapılabilir. 

S3’teki glacier storage tier (katman) bu servis üzerinden yönetilemez. Glacier servisinde depolansa da sadece ve sadece S3 üzerinden yönetilir/erişilir.

## 5.1. Glacier Kullanımı

```
# KAYNAK: https://docs.aws.amazon.com/cli/latest/userguide/cli-servicesglacier.html / Özgür ÖZTÜRK - Bulut Bilişimin Temelleri ve AWS Çözüm Mimarlığına Giriş Eğitimi (Udemy) 

# 0: Komut satırından “egitimvault” diye bir vault (mahzen) yaratılır 
aws glacier create-vault --account-id - --vault-name egitimvault 

# 1: 3 mb boyutunda largefile isimli bir dosya yaratılır 
dd if=/dev/urandom of=largefile bs=3145728 count=1 

# 2: Dosya split ile bölünür 
split --bytes=1048576 --verbose largefile chunk 

# 3: Multipart upload için bir alan açılır 
aws glacier initiate-multipart-upload --account-id - --archive-description "multipart upload test" --part-size 1048576 --vault-name egitimvault 

# Komutu sonucu şu şekildedir: { "location": "/097479760550/vaults/egitimvault/multipartuploads/ssW0KxfMgdJ4LTRposuVTpPgrGsTAPze_GQUwtFWrJwIKEkNOdX_F0zyNAA_pQIptvpZueGWWUszGZ446HBIE9aWWVr", "uploadId": "ssW0KxfMgdJ4LTRposuVTpPgrGsTAPze_GQUwtFWrJwIKEkNOdX_F0zyNAA_pQIptvpZueGWWUszGZ446HBIE9aWWVr" } 

# 4: Sonra bu uploadID değerini bir değişkene atıyoruz ve multipart upload'a başlıyoruz
$UPLOADID="ssW0KxfMgdJ4LTRposuVTpPgrGsTAPze_GQUwtFWrJwIKEkNOdX_F0zyNAA_pQIptvpZueGWWUszGZ446HBIE9aWWVr" 112 aws glacier upload-multipart-part --upload-id $UPLOADID --body chunkaa --range 'bytes 0-1048575/*' --account-id - --vault-name egitimvault aws glacier upload-multipart-part --upload-id $UPLOADID --body chunkab --range 'bytes 1048576-2097151/*' --account-id - --vault-name egitimvault aws glacier upload-multipart-part --upload-id $UPLOADID --body chunkac --range 'bytes 2097152-3145727/*' --account-id - --vault-name egitimvault 

# 5: Openssl ile dosyanın hashını çıkarıyoruz ki buradaki dosya ile giden dosya aynı mı kontrol edebilelim 
$ openssl dgst -sha256 -binary chunkaa > hash1 
$ openssl dgst -sha256 -binary chunkab > hash2 
$ openssl dgst -sha256 -binary chunkac > hash3 

# 6: İlk 2 hashi yeni bir dosya yapıyoruz sonra onun da da hashini alıyoruz 
$ cat hash1 hash2 > hash12 $ openssl dgst -sha256 -binary hash12 > hash12hash 

# 7: Sonra bunu üçüncü dosyayla birleştiriyoruz ve en sonunda o hash değerini değişkene atıyoruz 
$ cat hash12hash hash3 > hash123 
$ openssl dgst -sha256 hash123 SHA256(hash123)= 9628195fcdbcbbe76cdde932d4646fa7de5f219fb39823836d81f0cc0e18aa67 
$ TREEHASH=9628195fcdbcbbe76cdde932d4646fa7de5f219fb39823836d81f0cc0e18aa67 

# 8: Son olarak da upload’u tamamlıyoruz 
aws glacier complete-multipart-upload --checksum $TREEHASH --archive-size 3145728 --upload-id $UPLOADID --account-id - --vault-name egitimvault
```


