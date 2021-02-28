# HorizenTestSidechain
Hedef:Sphere By Horizen ile cüzdan oluşturup bir yan zincir oluşturmak sonrasında ana zincir ve yan zincir arasında işlem yapmak.
*Bu rehber bu işlemlerin nasıl yapıldığını içermektedir.*
 
Sphere by Horizen Kurulumu ve Ayarlanması

https://github.com/HorizenOfficial/Sphere_by_Horizen_Sidechain_Testnet/releases/tag/desktop-v2.0.0-beta-sidechain-testnet
Bu adresten cüzdanın testnet versiyonu için indirme işlemimizi yapıyoruz.
(Windows için .exe  / Linux için .deb)
Ben bu rehberi Windows için oluşturdum.
Uygulamayı indirme işlemini bitirip kurulumu yaptıktan sonra sizleri çok hoş bir arayüz karşılayacak.Bu ekrandan kayıt işlemlerimizi yapıyoruz.


Kayıt işlemlerinden sonra bir cüzdan ekleyin.










Cüzdanımızı oluşturduktan sonra Sphere by Horizen’in Blockchain ile senkronize olmasını bekliyoruz.






Senkronizasyon işleminin bittiğinden emin olmalıyız.


tZEN’leri Elde Etme
Sıra geldi test işlemi için gerekli olan ZEN’lerimize.Bu ZEN’leri https://heap.horizen.io adresinden alabiliriz.
Buraya cüzdan adresi olarak Sphere Horizen içinde oluşturduğumuz cüzdanımızın adresini giriyoruz.





Bir sonraki aşamaya geçmeden önce bilgisayarımızda bazı yazılımların yüklü olduğundan emin olmamız gerekiyor.
Bu yazılımlar 
Java 8.0 versiyonu ya da daha yenisi                    : https://java.com/tr/download/
Maven                                                                        : https://maven.apache.org/download.cgi
Scala                                                                          : https://www.scala-lang.org/download/


Şimdi geldik yan zincirin bileşenlerini bilgisayarımıza çekmeye.Bu işlem için komut satırımıza şu kodu girelim:
$   git clone https://github.com/ZencashOfficial/Sidechains-SDK.git

Şimdi ana dizinimizi bu dizin yapalım.
$   cd Sidechains-SDK
Dizinimize geçtikten sonra maven ile derleme yapalım.
$   mvn  package
Bu işlemleri doğru ve eksiksiz bir biçimde yapıp maven derlemesinden sonra komut satırında “BUILD SUCCESS” yazısını gördüğünüzden emin olun.

Önyükleme(Boostrapping)
Sıra geldi önyüklemeye.(Boostrapping)
Bu işlem için; https://github.com/HorizenOfficial/Sidechains-SDK/blob/master/examples/simpleapp/README.md buradaki adımları rehber alıcaz.
Öncelikle Sidechain-SDK dizini içinde olduğumuzdan emin olalım.
Önyükleme işlemi için;
$ java -jar tools/sctool/target/sidechains-sdk-scbootstrappingtools-0.2.5.jar 
Bu işlemin devamında
$ generatekey {"seed":"my seed"} 
yazarak bize özel anahtarımızı oluşturuyoruz.
$ generateVrfKey {"seed":"my seed"}
son olarak 
$ generateProofInfo {"seed":"my seed", "keyCount":7, "threshold":5}
Burada aldığımız anahtarlar transfer işlemimiz için gerekli olan anahtarlardı.


*Bir sonraki adıma geçmeden önce kesinlikle komut satırını kapatmayın.Buradaki anahtarlara ihtiyacımız olacak.* 
Yeni bir yan zincir oluşturma
Bu işlemden önce cüzdanımızda mutlaka ZEN olmalı.Çünkü bir yan zincir oluşturmak için bu ZEN’lerin bir miktarını yan zincirimize aktarmamız gerekiyor.
Yan zincirimize bir isim verelim. Örn:Yeni yan zincir
Artık komut satırında elde ettiğimiz anahtarları kullanma vakti.
Sidechain creation adress: $ generatekey {"seed":"my seed"} çağrımızla gelen halka açık anahtarımız. 
wCertVk: $ generateProofInfo {"seed":"my seed", "keyCount":7, "threshold":5} çağrımızla gelen doğrulama anahtarı
Constant data: $ generateProofInfo {"seed":"my seed", "keyCount":7, "threshold":5} çağrımızla gelen {"threshold":5,"genSysConstant": ……. kısmında  yazan anahtarımız
Custom data: $ generateVrfKey {"seed":"my seed"} çağrımızla gelen vrf halka açık anahtar 


Bu işlemlerden sonra bir yan zincir oluşturma isteği göndermiş olduk.Bir süre bekliyoruz ve sonra onaylanıyor.




Ana zincirden yan zincire doğru işlem yapma

 https://heap.horizen.io ‘dan elde ettiğimiz tZEN’leri yan zincire aktarma vakti.
Cüzdanımıza girip sağ yukarıdaki “SEND” butonuna tıklıyoruz.



Ekranda sağ üstte yer alan “Sidechain transaction” düğmesini aktifleştiriyoruz.
Sidechain kısmından oluşturduğumuz yan zinciri seçiyoruz.
Adress kısmına $ generatekey {"seed":"my seed"} çağrımızla gelen halka açık anahtarımızı giriyoruz.
Continue tuşuna basarak yan zincirimize gönderim işlemini gerçekleştiriyoruz.



Bir süre sonra işlemimiz gerçekleşecek.

Cüzdanımıza tıklayarak işlem geçmişimizi görebiliriz.















