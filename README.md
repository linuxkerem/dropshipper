## Automate Dropshipping 
### Eldorado Guncellemesi Geldi !!
-------------------------------------
Gamermarkt web sitesi uzeirnde satisa cikarilmis olan Valorant ve Leauge of Legends hesaplarinin verilerini ve fotograflarini scrape edip global hesap satis siteleri olan G2G ve Eldorado'ya ilanlari yuklemenize olanak saglayan Python programi.

### Guvenlik
Python gibi acik kaynakli bir yazilim dilinde lisans anahtarli ve musteriye hizmet eden boyle bir proje yapmak ne kadar etik dusunmek size kalmis, ancak boyle buyuk bir projenin kaynak kodunu paylasmak istemedigim, riske atmak istemedigim icin satin alimlar disinda herhangi bir paylasimda bulunmama karari aldim. Eger herhangi bir sekilde kaynak kodunu koruma yolunu bildigini dusunen, aklinda bir fikir olan var ise memnuniyet ile benimle iletisime gecebilir. O zamana kadar yalnizca satin alimlarda kurulum sonrasinda kaynak kodlari obfuscate edilerek iletilmektedir.  ( Cython, pyinstaller, py2exe gibi turlu yollar test edildi, aradigim yol daha cok kaynak kodunu bir cloud'dan getirebilmek. )

------------
### Video
!! Not : Asagida bulunan videonun tarihi gecmis olup, programa birden fazla guncelleme gelmesiyle birlikte cok daha efektif bir sekilde calismaktadir.!! <br>
Asagida bulunan Youtube videosunda programin tamaminin detayli aciklamasini ve anlatimini bulabilirsiniz, yine de vakti olmayanlar icin burada da ustun koru bir anlatim yapacagim

<a href="http://www.youtube.com/watch?feature=player_embedded&v=Y_zK45wOoUIhq
" target="_blank"><img src="https://i.hizliresim.com/b2unlzn.jpg" 
alt="YouTube Link" width="450" height="281" /></a>


------------
#### Ozellikler
Projenin arayuzunun bir kopyasini asagida gorebilirsiniz. Arayuzde bulunan ayarlari kaydet ve yukle butonlari adi ustunde arayuzde yazilan tercihlerin hatirlanmasi icin eklenmistir.

<img src = 'https://github.com/linuxkerem/dropshipper/blob/main/images/dropshipperImageOne.png' width='350'/> <img src = 'https://github.com/linuxkerem/dropshipper/blob/main/images/dropshipperImageTwo.png' width='350'/> <img src = 'https://github.com/linuxkerem/dropshipper/blob/main/images/dropshipperImageThree.png' width='300'/>

Kisaca islevlerinden bahsetmek gerekirse;
- Veritabani icin MySQL Veritabani kullanilmistir. ( Veritabani dizayni pek ic acici degil. )
- Cryptolens kutuphanesi kullanilarak lisans sistemi eklenmistir.
- TL bazinda ki fiyati kullanicinin girdigi parametreye gore bolup EU bazina cevirerek satis ilanini yayinlar.
- Istege bagli olarak ilanlarin Leauge of Legends icin sampiyonlarin ve kostumlerin, Valorant icin yalnizca kostumlerin screenshotlarin alinip alinmadigi tercihi yapilir.
- TL bazinda maksimum fiyat ve minimum fiyat kullanici tarafindan belirtilebilir, istenilen fiyattan daha yuksek sayida ki bir ilan veri tabanina kayit edilmeyecek, dolayisi ile G2G'ye asla yuklenmeyecektir.
- Arayuzde bulunan Special Skins bolumunde deger algoritmasiyla bir siralama yapildigi takdirde ( Virgul ile ayrilmis, en degerli kostumden en degersiz kostume siralama ) herhangi bir ilanda bulunan Special Skin filtrelenecek ve G2G'ye yuklenecegi zaman baslikta yer alacaktir.
- Herhangi bir ilanda ki kostum sayisi minimum skin sayisi degerinden dusuk oldugu takdirde ilan cekilmeyecek ve veri tabanina kayit edilmeyecektir.
- Leauge of Legends ve Valorant icin ayri ayri kac tane Special Skins konulacagi ve minimum skin sayisi da yine kullanicinin tercihine birakilmistir.

------------
#### Icerik
- Gamermarktan veri cek fonksiyonu kisaca ilanlar sayfasina giris yapar, belirlenen filtrelemelere gore belirli ilanlari bulur ve tek tek ilanlari scrape etmeye baslar. Resimleri cek secenegi aktif ise skinlerin ( Leauge Of Legends'da Sampiyonlarin screenshot'u da aliniyor) screenshotunu cekip hizliresim.com'a yukledikten sonra url'i kopyalayip diger ilan ile devam eder ( Eger herhangi bir resim 20 MB'dan daha yuksek boyuta sahipse iki tane sikistirma fonksiyonu resimin boyutunu kucultmektedir ), yalniz deginilmesi gereken nokta sudur ki bu islem yapilirken cv2, pillow ve en onemlisi pyautogui kullanilmistir. Bundan dolayi chrome calisirken ana ekranda olmasi, maximized window'da bulunmasi ve bilgisayarda herhangi bir baska islem yapilmamasi sarttir. Bu yuzden dolayi videoda da belirttigim gibi sanal bir makine de bu projeyi kullanmayi oneriyorum.
- G2G'ye yukle fonksiyonu cagrildiginda yuklenmemis ilanlar tek tek G2G'ye yuklenir. Yuklenen ilanlarin ilk columnlarina G2G'nin her ilana essiz bir deger olarak atadigi offerNumber'lar ilanlarin veri tabani satirlarina atanir. Boylece ilan silinecegi veya satilacagi zaman ilani bulmak cok daha kolay olur.
- Yukarida belirtildigi gibi, Valorant ilanlari ayni sekilde Eldorado web sitesine de yuklenebilecektir.
- Ilanlar satilmis mi kontrol et fonksiyonu yalnizca satilmis ilanlar icin degil, degistirilmis yada bozulmus, kaldirilmis ilanlar icinde mevcuttur. Kisaca mevcut olmayan her ilani kaldirmaniza olanak saglar. MySQL Veri tabanindan tum urunlerin url'leri ve ayni url'e bagli urun ID'leri cagrilir. Eger Gamermarkt url'i error sayfasiyla bizi karsilarsa,  yada ana sayfaya yonlendirilirsek yeni bir sekmede G2G acilir, urunun ID'si aranir. ID Arama algoritmasina bagli olarak basliklarda ID belirtmek ve ID'lerden once ayirici bir emoji belirtmek zorunludur. Eger birden fazla sonuc bulunursa ( ki cokca yasanan bir durumdur cunku 80 ID'li bir ilan G2G'de aratildigi zaman 800'ler 8000'ler hatta 80.000 ID'li ilanlarda gelmektedir.) otomatik olarak son sayfanin en son asagisina iner, ki bu bizim tam olarak istedigimiz ilan olarak nitelendirilebilir. Ilan G2G'de deactive konumuna getirilir ve MySQL veri tabanindan kaldirilir.  Eger herhangi bir sonuc gelmezse ilan MySQL Veri tabanindan kaldirilir ve konsolda bu durum belirtilir.

------------
#### Iletisim

Discord : kmdev#3277

------------
#### Fiyatlandirma
Leauge of Legends G2G Haftalik 400 - Aylik 1250 <br>
Valorant G2G Haftalik 400 - Aylik 1250 <br>
( Ilk Ay'a Ozel Valorant G2G + Leauge of Legends G2G = 2200 )<br> 
Valorant Eldorado Haftalik 200 - Aylik 700 <br>
Valorant PlayerAuctions Haftalik 200 - Aylik 700
