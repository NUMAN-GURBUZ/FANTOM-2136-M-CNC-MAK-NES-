# FANTOM 2136 M CNC İşleme Merkezi

## Ayrıntılı SWOT Analizi: Fonksiyonel Emniyet, Endüstriyel Siber Güvenlik ve Dijitalleşme

**Rapor tarihi:** 23 Ekim 2026\
**İnceleme temeli:** Kullanıcının sağladığı *FANTOM 2136 M Laboratuvar
Föyleri* (8 sayfa), üreticinin yayımladığı ürün bilgileri ve aşağıda
listelenen standart/mevzuat kaynakları.

> **Önemli kapsam notu:** Bu çalışma, makinenin resmî uygunluk
> değerlendirmesi, penetrasyon testi, emniyet doğrulaması veya
> belgelendirme raporu değildir. PDF de bunun bir eğitim çıktısı
> olduğunu ve CE/mevzuat uygunluğu garantilemediğini açıkça
> belirtmektedir. Makineye özgü bir güvenlik açığı, uzaktan erişim
> bağlantısı, Safety PLC veya ışık perdesi kurulu olduğu doğrulanmış
> kabul edilmemiştir. Doğrulanmayan noktalar "saha doğrulaması gerekli"
> olarak işaretlenmiştir.

------------------------------------------------------------------------

## 1. Yönetici özeti

FANTOM 2136 M, üretici tarafından geniş çalışma alanı, PC tabanlı
kontrol, Alphacam 2D CAD/CAM yazılımı, Beckhoff servo eksenleri ve
24.000 dev/dk'ya kadar iş mili özellikleriyle tanımlanan bir CNC ahşap
işleme merkezidir. Üretici sayfasında çalışma alanı 2100 × 3660 mm, Z
ekseni hareketi 250 mm, iş mili 11 kW, kurulu güç 40 kW ve makine
ağırlığı 4500 kg olarak verilir. Güvenlik çiti ile ışık bariyeri
opsiyonel olarak listelenmiştir; bu nedenle belirli kurulumda bulunup
bulunmadıkları yerinde doğrulanmalıdır. [Üretici ürün
sayfası](https://krccnc.com/urunler/1004/fantom_serisi/1020/fantom_2136_m.aspx)

Bu makineye yönelik en önemli stratejik konu, yalnızca bilgisayarı veya
ağı korumak değildir. Program dosyası, hareket parametreleri, servo
sürücüler, bakım erişimi ve fiziksel emniyet fonksiyonları arasındaki
ilişkinin güvenli biçimde yönetilmesidir. Siber olay, üretimi
durdurmanın ötesinde takım yolu değişikliği, beklenmedik hareket veya
operatörün tehlikeye maruz kalması gibi fiziksel sonuçlara dönüşebilir.
Bu yüzden siber güvenlik ve fonksiyonel emniyet birlikte ele alınmalı;
ancak emniyet fonksiyonunun güvenilirliği yalnızca normal kontrol
PC'sinin güvenliğine dayandırılmamalıdır.

**Genel değerlendirme:** Çalışmanın en güçlü tarafı, teknik
riskleri insan güvenliğiyle ilişkilendirmesi ve doğrulanmamış açıkları
gerçek bulgu gibi sunmamasıdır. En büyük sınırlılığı ise mevcut
makinenin ağ topolojisi, kontrol PC'si yazılım/sürüm envanteri, emniyet
devresi, kullanıcı hesapları ve uzaktan erişim durumunun henüz
kanıtlarla doğrulanmamış olmasıdır. Dolayısıyla mevcut durum için
"güvenli" ya da "güvensiz" şeklinde kesin bir hüküm vermek mümkün
değildir.

------------------------------------------------------------------------

## 2. İncelenen sistem ve kanıt düzeyi

### 2.1 İncelemede ele alınan sistem başlıkları

Laboratuvar föyleri yedi çalışma alanından oluşur:

1.  **Safety Architecture:** Normal kontrol yolu ile emniyet yolunun
    ayrılması; E-stop, varsa Safety PLC/emniyet rölesi, STO/kontaktör ve
    güvenli duruma geçiş.
2.  **IEC 62443 Mini Workshop:** Ofis BT, mühendislik/CAD-CAM, CNC
    hücresi ve emniyet alanı gibi bölgelerin ayrılması; bölgeler arası
    geçişlerin kontrollü olması.
3.  **Threat & Risk:** Yetkisiz bakım hesabı, USB üzerinden
    yanlış/zararlı program ve kontrol PC'sinde zararlı yazılım gibi
    senaryoların puanlanması.
4.  **Secure Remote Access:** Jump server, VPN, MFA, kişisel hesap,
    oturum/değişiklik kaydı ve varsayılan kapalı erişim ilkeleri.
5.  **SBOM / CVE / Patch:** Bileşenin, sürümün ve erişilebilirlik
    koşulunun doğrulanması; yamanın önce test ortamında denenmesi.
6.  **CRA Incident Simulation:** Olayın güvenli biçimde yönetilmesi,
    kanıtların korunması, bildirim koşullarının kontrol edilmesi ve olay
    sonrası raporlama.
7.  **AI Safety Challenge:** Yanlış sınıflandırma, manipüle edilmiş
    görüntü ve düşük güven skorunda otomatik kabulü durdurma; insan
    incelemesi veya doğrulanmış alternatif kontrol.

Önerilen bölgeler mantıksal bir başlangıç modelidir; gerçek
bağlantıların ve kurulu bileşenlerin sahada doğrulanması gerektiği de
belirtilir.

### 2.2 Üretici tarafından yayımlanan teknik özellikler

  -----------------------------------------------------------------------
  Özellik                 Üretici sayfasında      SWOT açısından anlamı
                          belirtilen bilgi        
  ----------------------- ----------------------- -----------------------
  Çalışma alanı           2100 × 3660 mm          Büyük iş parçalarının
                                                  işlenmesini destekler;
                                                  çalışma alanına erişim
                                                  ve koruyucu düzeni
                                                  önemlidir.

  Z ekseni hareketi       250 mm                  Hareket alanı ve
                                                  takım/iş parçası
                                                  çarpışma senaryoları
                                                  risk analizine
                                                  katılmalıdır.

  Servo eksenleri         X: 2,3 kW; Y: 2 × 2,3   Hareket kontrolü ve
                          kW; Z: 2,3 kW Beckhoff  sürücü yapılandırmaları
                          servo                   kritik varlıklardır.

  İş mili                 11 kW Hiteco, 24.000    Dönen takım ve fırlayan
                          dev/dk                  parça tehlikeleri
                                                  yüksek şiddetli
                                                  fiziksel sonuçlar
                                                  doğurabilir.

  Kontrol                 PC tabanlı              PC, işletim sistemi,
                                                  yazılım, dosya aktarımı
                                                  ve bakım erişimi siber
                                                  risk değerlendirmesinde
                                                  önemlidir.

  CAD/CAM                 Alphacam 2D             Program üretimi, onay,
                                                  sürüm ve makineye
                                                  aktarım zinciri kontrol
                                                  edilmelidir.

  Güvenlik çiti / ışık    Opsiyonel               Belirli makinede mevcut
  bariyeri                                        oldukları varsayılamaz;
                                                  fiziksel kontrol ve
                                                  dokümantasyon gerekir.

  Kurulu güç / besleme    40 kW; 380 V, 50 Hz     Elektriksel tehlikeler,
                                                  enerji izolasyonu ve
                                                  bakım prosedürleri
                                                  önemlidir.
  -----------------------------------------------------------------------

Kaynak: [KRC CNC --- FANTOM 2136 M teknik
özellikleri](https://krccnc.com/urunler/1004/fantom_serisi/1020/fantom_2136_m.aspx).
Üretici sayfasındaki takım magazini ifadesinde sabit/döner magazin
seçenekleri farklı biçimde yazıldığından, kesin konfigürasyon sipariş ve
makine dokümanlarından doğrulanmalıdır.

### 2.3 Kanıt sınıfları

-   **Belgelendirilmiş kaynak bilgisi:** Üreticinin ürün sayfasında
    yayımlanan özellikler ve PDF'de yazılı eğitim senaryoları.
-   **Mühendislik çıkarımı:** PC tabanlı kontrol, yüksek hızlı iş mili
    ve servo eksenleri nedeniyle program bütünlüğü, yetkisiz değişiklik
    ve fiziksel emniyetin önemli olması.
-   **Sahada doğrulanması gereken bilgi:** Kontrol PC'sinin işletim
    sistemi ve sürümleri, ağ bağlantıları, servis hesapları, uzaktan
    erişim, USB politikası, gerçek emniyet devresi, STO'nun
    varlığı/bağlantısı, çit/ışık bariyeri ve üreticinin yama desteği.
-   **Doğrulanmamış iddia olarak kullanılmaması gerekenler:** Makinede
    belirli bir CVE bulunduğu, uzaktan erişimin açık olduğu, makinenin
    internete bağlı olduğu, belirli bir Safety PLC'nin kurulu olduğu
    veya üreticinin güvenlik açığı bulunduğu.

------------------------------------------------------------------------

## 3. SWOT analizi

SWOT'ta **Güçlü Yönler** ve **Zayıf Yönler** ağırlıklı olarak makinenin
yayımlanmış özellikleri ve PDF'de görülen mevcut bilgi düzeyiyle;
**Fırsatlar** ve **Tehditler** ise uygulanabilecek iyileştirmeler ve
makul risk senaryolarıyla değerlendirilmiştir. Risk senaryoları,
gerçekleşmiş olay veya doğrulanmış zafiyet anlamına gelmez.

### 3.1 Güçlü yönler (Strengths)

**G1 --- PC tabanlı kontrol ve tanımlı CAD/CAM akışı**

Üretici PC tabanlı kontrol ve Alphacam 2D kullanımını belirtir. Bu yapı,
programların kontrollü bir depoda tutulması, onaylı sürümlerin
belirlenmesi, dosya bütünlüğü kontrolü ve değişikliklerin kaydedilmesi
için yönetilebilir bir dijital iş akışı oluşturma fırsatı verir. Bu
kontrollerin hâlihazırda mevcut olduğu varsayılmamalıdır.

**G2 --- Servo ve iş mili bileşenlerinin tanımlı olması**

Üretici servo eksenleri ve iş mili bileşenlerini belirtir. Bu
varlıkların envanterlenebilmesi, bakım kayıtları ve konfigürasyon baz
çizgisi hazırlanabilmesi açısından başlangıç sağlar. Model, firmware ve
sürüm bilgileri ayrıca toplanmalıdır.

**G3 --- Emniyet ile siber güvenliği birlikte ele almaya elverişli bir
analiz çerçevesi**

PDF, normal kontrol yolu ile emniyet yolunu kavramsal olarak ayırır ve
"saldırgan içeri girse bile insanı koruyan emniyet fonksiyonu"
gereksinimini sorgular. Bu, yalnızca ağ güvenliği değil, fiziksel
sonuçları da kapsayan risk yaklaşımını destekler.

**G4 --- Risk senaryolarının fiziksel sonuca kadar izlenmesi**

Örnek senaryolar veri kaybıyla bitmez; yetkisiz bakım hesabının
parametre değiştirmesi, takım yolu değişikliği ve olası yaralanma gibi
sonuçlara kadar uzanır. Bu yaklaşım, risklerin önceliklendirilmesini ve
üretim/iş güvenliği ekiplerinin ortak değerlendirme yapmasını
kolaylaştırır.

**G5 --- Güvenlik çitinin ve ışık bariyerinin opsiyonel olduğunun açıkça
belirtilmesi**

Opsiyon bilgisi, kurulumlar arasında farklılık olabileceğini görünür
kılar. Doğru sonraki adım, özelliklerin varlığını varsaymak değil,
makine seri numarasına ve kurulu konfigürasyona ait belgelerle yerinde
doğrulamaktır.

### 3.2 Zayıf yönler (Weaknesses)

**Z1 --- Mevcut siber güvenlik durumu henüz kanıtlanmış değil**

PDF'de uzaktan erişimin kurulup kurulmadığı, hesap politikaları, ağ
bağlantıları ve kayıt mekanizmaları doğrulanmamış olarak belirtilir. Bu
nedenle gerçek güvenlik seviyesi hakkında kesin sonuç çıkarmak mümkün
değildir. Envanter ve saha doğrulaması olmadan kontrol önlemlerinin
etkinliği ölçülemez.

**Z2 --- PC tabanlı kontrol, yazılım ve dosya bütünlüğünü kritik hâle
getiriyor**

Kontrol PC'si ve CAD/CAM aktarım zinciri, programların yanlışlıkla veya
yetkisiz biçimde değiştirilmesi riskini gündeme getirir. Bu, PC tabanlı
kontrolün tek başına bir kusuru olduğu anlamına gelmez; uygun hesap
yönetimi, dosya onayı, yedekleme ve değişiklik kontrolü yoksa risk
büyür.

**Z3 --- Fiziksel koruyucuların kurulum durumu belirsiz**

Üretici çit ve ışık bariyerini opsiyonel olarak listeler. Bu nedenle
koruyucuların varlığı, konumu, kilitleme mantığı ve emniyet devresine
bağlantısı doğrulanmadan koruma yeterliliği söylenemez.

**Z4 --- SBOM, sürüm ve CVE eşlemesi için yeterli veri yok**

PDF'de kontrol PC'sindeki yazılım bileşeni, sürüm, makineye özgü CVE ve
CVSS puanı doğrulanmamış olarak gösterilir. Bu durum bir zafiyetin
varlığını kanıtlamaz; fakat etkilenme analizi, destek durumu ve yama
kararlarının veriye dayalı yapılmasını engeller.

**Z5 --- Emniyet performans seviyesi dokümanla doğrulanmalı**

PDF, PLr/SIL seviyesinin varsayılmaması ve risk değerlendirmesiyle
belirlenmesi gerektiğini doğru biçimde vurgular. Gerçek emniyet devresi,
bileşenler, devre şemaları, duruş performansı ve doğrulama kayıtları
olmadan belirli bir PLr/SIL seviyesi iddia edilemez.

**Z6 --- Olay müdahalesi ve kanıt yönetimi prosedürlerinin uygulamadaki
olgunluğu bilinmiyor**

PDF iyi bir olay zaman çizelgesi sunar; ancak gerçek kurumda
sorumluların atanıp atanmadığı, yedeklerin test edilip edilmediği,
logların saklanma süresi ve olay tatbikatı yapılıp yapılmadığı
bilinmiyor.

### 3.3 Fırsatlar (Opportunities)

**F1 --- IEC 62443 temelli varlık, zone/conduit ve risk
değerlendirmesi**

Makineyi ofis BT, mühendislik/CAD-CAM, CNC kontrol hücresi ve emniyet
alanı olarak mantıksal bölgelere ayıran bir taslak hazırlanabilir. Her
bölge arasındaki iletişim ihtiyacı gerekçelendirilip izin listesiyle
sınırlandırılabilir. IEC 62443-3-2; sistem kapsamını belirleme,
zone/conduit oluşturma, risk değerlendirme, hedef güvenlik seviyesini
belirleme ve gereksinimleri belgeleme konularını kapsar. [IEC
62443-3-2](https://webstore.iec.ch/en/publication/30727)

**F2 --- Güvenli uzaktan erişim standardı oluşturma**

Uzaktan bakım gerekiyorsa erişim; VPN, MFA, jump server, kişiye özel
hesap, en az ayrıcalık, süreli yetkilendirme, oturum kaydı ve varsayılan
kapalı yaklaşımıyla tasarlanabilir. Gerçekten gerekmiyorsa uzaktan
erişim kapalı tutulabilir. Bu karar, mevcut bağlantılar ve bakım
gereksinimleri doğrulandıktan sonra verilmelidir.

**F3 --- Makineye özgü SBOM ve varlık envanteri hazırlama**

Kontrol PC'si, işletim sistemi, CAD/CAM yazılımı, sürücüler, servis
araçları, ağ arayüzleri ve firmware sürümleri kaydedilebilir. CVE
değerlendirmesinde yalnızca ürün adı değil; bileşenin varlığı, etkilenen
sürüm ve erişilebilir saldırı yolu birlikte incelenmelidir. Üretici
desteği ve yama kullanılabilirliği kayıt altına alınmalıdır.

**F4 --- Onaylı CNC programı ve değişiklik yönetimi**

CAD/CAM'den makineye giden program akışı için şu kontroller
kurulabilir: - Programın yetkili kişi tarafından onaylanması. - Revizyon
numarası, tarih ve sorumlu bilgisinin tutulması. - Dosya hash'i veya
eşdeğer bütünlük kontrolü. - Üretimde kullanılan sürümün onaylı ana
kopyayla karşılaştırılması. - USB aktarımının sınırlandırılması ve
gerektiğinde kontrollü aktarım istasyonu kullanılması. - Değişiklik
sonrası güvenli test ve ilk parça kontrolü.

**F5 --- Emniyet doğrulama ve siber olay tatbikatını birlikte yürütme**

Yetkisiz hesapla giriş, program bütünlüğü şüphesi veya parametre
değişikliği senaryoları masa başı tatbikatla sınanabilir. Makinenin
durdurulması ve yeniden başlatılması yalnızca üretici prosedürleri ile
yetkili teknik personelin kontrolünde yapılmalıdır. Emniyet
fonksiyonlarının testleri, makineye özgü onaylı prosedürlerle
yürütülmelidir.

**F6 --- Yapay zekâ destekli kalite kontrolünü emniyet kontrolünden ayrı
tasarlama**

Yapay zekâ destekli kalite kontrolü senaryosu, kamera/YZ çıktısının tek başına
emniyet garantisi olmadığını belirtir. Haricî kalite kontrol eklentisi
geliştirilecekse düşük güven skoru, bozuk görüntü veya belirsiz
sınıflandırmada otomatik "OK" yerine durdurma, ikinci kontrol veya insan
onayı uygulanabilir. YZ'nin emniyet devresini yönetmesine izin
verilmemelidir.

**F7 --- İzlenebilir bir "Machine Security & Safety Starter Pack"
oluşturma**

Çalışma sonunda oluşturulacak çıktılar tek bir kanıt paketinde toplanabilir: makine
konfigürasyonu, ağ diyagramı, emniyet fonksiyonu haritası, risk
kayıtları, erişim politikası, SBOM/CVE kararları, yedekleme ve olay
müdahale prosedürleri, test kayıtları ve açık aksiyonlar. Bu paket,
bakım ve denetim hazırlığını kolaylaştırır; tek başına sertifikasyon
veya mevzuat uygunluğu kanıtı değildir.

### 3.4 Tehditler (Threats)

**T1 --- Yetkisiz bakım erişimiyle program veya hareket parametresi
değişikliği**

Bir servis hesabı ele geçirilir veya yetkisiz kullanılırsa program,
konfigürasyon ya da hareket parametrelerinde değişiklik riski
oluşabilir. Fiziksel sonuç, makinenin gerçek mimarisine ve korumalarına
bağlıdır. PDF bu senaryoyu yüksek öncelikli örnek olarak ele alır; bu,
olayın gerçekleştiğini göstermez.

**T2 --- USB veya dosya aktarımı üzerinden yanlış/zararlı program**

Yanlış revizyon, bozuk dosya ya da kötü amaçlı içerik makineye
aktarılabilir. Program onayı, kontrollü aktarım ve bütünlük kontrolü
yoksa takım yolunda istenmeyen değişiklikler, iş parçası hasarı, takım
hasarı veya duruş yaşanabilir.

**T3 --- Kontrol PC'sinde zararlı yazılım veya sistem arızası**

Kontrol PC'sindeki bir yazılım olayı üretimi durdurabilir, dosyalara
erişimi bozabilir veya konfigürasyonun güvenilirliğini belirsiz hâle
getirebilir. Fiziksel güvenlik etkisi varsayılmamalı; gerçek kontrol
mimarisi ve bağımsız emniyet önlemleriyle değerlendirilmelidir.

**T4 --- Emniyet ve normal kontrol arasındaki bağımlılıkların yanlış
anlaşılması**

Emniyet fonksiyonunun normal kontrol yazılımından bağımsız olduğu
yalnızca diyagramla kanıtlanamaz. Ortak güç, haberleşme, yapılandırma
veya donanım bağımlılıkları bulunup bulunmadığı şema ve testlerle
doğrulanmalıdır. Yanlış güven varsayımı ciddi bir organizasyonel
risktir.

**T5 --- Yama uygulanmaması veya kontrolsüz yama uygulanması**

Yamanın uygulanmaması bilinen riskleri sürdürebilir; üretim ortamında
test edilmeden yapılan güncelleme ise uyumluluk, program çalışması veya
emniyet doğrulaması sorunlarına yol açabilir. Önce etkilenen
bileşen/sürüm doğrulanmalı, test ortamında denenmeli, geri dönüş planı
hazırlanmalı ve gerekli emniyet kontrolleri tekrarlanmalıdır.

**T6 --- Tedarikçi desteği, yedek parça veya eski yazılım bağımlılığı**

Makine ya da bileşenlerin destek süresi, güncelleme yöntemi ve eski
sürümlerin kullanılabilirliği doğrulanmalıdır. Destek dışı bileşen varsa
risk; ağdan ayırma, erişimi kısıtlama, yedekleme ve izleme gibi telafi
edici kontrollerle azaltılabilir. Bu tür bir destek sorununun mevcut
olduğu henüz kanıtlanmış değildir.

**T7 --- Olay sırasında aceleyle resetleme veya kanıt kaybı**

Şüpheli durumda makineyi düşünmeden yeniden başlatmak logları, geçici
verileri veya olayın zaman çizgisini kaybettirebilir. Öncelik insan
güvenliği ve onaylı güvenli duruş prosedürüdür; ardından kanıtlar
korunmalı ve müdahale kaydedilmelidir.

**T8 --- Mevzuat ve müşteri beklentilerinin değişmesi**

AB pazarına sunulan makineler ve dijital bileşen içeren ürünler için
ilgili mevzuat kapsamı; üretici, entegratör, ithalatçı ve işletmecinin
rolüne göre ayrı değerlendirilmelidir. Mevzuata ilişkin genel bilgiler,
tek başına bu makinenin belirli bir yükümlülüğe tabi olduğunu veya uygun
olduğunu kanıtlamaz.

------------------------------------------------------------------------

## 4. SWOT'tan türetilen öncelikli eylem planı

Aşağıdaki sıra, önerilen bir uygulama planıdır; makinede mevcut güvenlik
açığı bulunduğu anlamına gelmez.

### Aşama 1 --- Önce doğrula (0--2 hafta)

1.  Makinenin seri numarası, üretim yılı, satın alma/kurulum
    konfigürasyonu ve üretici dokümanlarını topla.
2.  Gerçekte kurulu olan çit, kapı kilidi, ışık bariyeri, E-stop,
    emniyet rölesi/Safety PLC ve sürücü STO özelliklerini yetkili teknik
    personelle doğrula.
3.  Kontrol PC'si, işletim sistemi, Alphacam sürümü, sürücüler, servis
    yazılımları ve firmware sürümlerinin envanterini çıkar.
4.  Ethernet bağlantıları, USB kullanımı, bakım portları, uzaktan erişim
    ve hesapları dokümante et. Yetkisiz tarama veya üretimi
    etkileyebilecek test yapma.
5.  Mevcut yedeklerin tarihini, bütünlüğünü ve geri yükleme prosedürünü
    doğrula.

**Çıktı:** Makine konfigürasyon kaydı, varlık envanteri, doğrulanmış
ağ/emniyet şeması ve bilinmeyenler listesi.

### Aşama 2 --- Temel korumaları kur (2--6 hafta)

1.  Ofis ağı, CAD/CAM ve CNC hücresi arasındaki trafiği iş gereksinimine
    göre sınırlandır.
2.  Gerekli değilse uzaktan erişimi kapat; gerekliyse VPN + MFA + jump
    server + süreli onay + kayıt yaklaşımını uygula.
3.  Kişisel hesaplar, en az ayrıcalık ve servis hesabı yönetimi
    kurallarını yazılı hâle getir.
4.  Onaylı program deposu, revizyon yönetimi, dosya bütünlüğü kontrolü
    ve kontrollü USB aktarım süreci oluştur.
5.  Program, parametre ve konfigürasyon yedeklerini üretimden bağımsız
    bir konumda sakla; geri yükleme testini yetkili prosedürle
    gerçekleştir.

**Çıktı:** Zone/conduit taslağı, erişim standardı, program yönetim
prosedürü ve yedekleme kanıtı.

### Aşama 3 --- Risk ve yazılım yaşam döngüsü (6--10 hafta)

1.  Tehdit senaryolarını işletme, bakım, makine emniyeti ve BT/OT
    ekipleriyle gözden geçir.
2.  Risk skorlamasında olasılık, şiddet ve maruziyet ölçütlerinin açık
    tanımlarını belirle. PDF'deki 1--3 puanlı L × S × E yöntemi eğitim
    amaçlıdır; kurumsal risk metodolojisi yerine otomatik olarak
    geçirilmemelidir.
3.  SBOM ve CVE değerlendirmesini gerçek bileşen/sürüm bilgisi üzerinden
    yürüt.
4.  Yama yönetiminde test, onay, bakım penceresi, geri dönüş ve emniyet
    doğrulama adımlarını tanımla.
5.  Olay müdahale sorumlularını ve kanıt saklama yöntemini belirle; masa
    başı olay tatbikatı yap.

**Çıktı:** Risk kayıt defteri, yama karar kaydı, olay müdahale akışı ve
sorumluluk matrisi.

### Aşama 4 --- Doğrulama ve sürekli iyileştirme (10. hafta ve sonrası)

1.  Emniyet fonksiyonlarını üretici ve yetkili mühendislik
    prosedürleriyle doğrula.
2.  Ağ ve erişim kurallarını üretim güvenliğini etkilemeyen kontrollü
    yöntemlerle gözden geçir.
3.  Program geri yükleme, olay bildirimi ve bakım erişimi senaryolarını
    periyodik olarak tatbik et.
4.  Her değişiklikte makine konfigürasyon kaydını, SBOM'u, risk
    kayıtlarını ve test kanıtlarını güncelle.
5.  Açık kalan riskler için sorumlu, hedef tarih, telafi edici kontrol
    ve kabul kararını kaydet.

------------------------------------------------------------------------

## 5. Önceliklendirme tablosu

  ---------------------------------------------------------------------------
  Öncelik           Konu              Gerekçe             İlk somut adım
  ----------------- ----------------- ------------------- -------------------
  P1 --- Kritik     Emniyet zinciri   İnsan güvenliği     Gerçek devre şeması
  doğrulama         ve fiziksel       doğrudan            ve sahada yetkili
                    koruyucular       etkilenebilir;      doğrulama
                                      kurulu durum        
                                      belirsiz            

  P1 --- Yüksek     Bakım hesabı ve   Yetkisiz değişiklik Hesap/bağlantı
                    uzaktan erişim    olasılığı, erişim   envanteri ve erişim
                                      kanıtlanmadan       gözden geçirmesi
                                      değerlendirilemez   

  P1 --- Yüksek     CNC program       Yanlış veya         Onaylı program
                    bütünlüğü         yetkisiz program    deposu ve
                                      fiziksel işleme     revizyon/bütünlük
                                      sonucunu            kontrolü
                                      etkileyebilir       

  P2 --- Yüksek     PC/yazılım        CVE etkilenmesi     Sürüm envanteri ve
                    envanteri ve SBOM bileşen ve sürüm    üretici desteği
                                      bilgisi olmadan     doğrulaması
                                      belirlenemez        

  P2 ---            Yedekleme ve geri Olay veya arızadan  Yedeklerin geri
  Orta-yüksek       dönüş             sonra güvenilir     yükleme testi
                                      duruma dönüşü       
                                      destekler           

  P2 ---            Olay müdahale ve  Hızlı ve kontrollü  Rol ataması ve masa
  Orta-yüksek       kanıt yönetimi    müdahaleyi          başı tatbikat
                                      kolaylaştırır       

  P3 --- Gelişim    AI destekli       Üretim kalitesini   İnsan
  fırsatı           kalite kontrolü   artırabilir; yanlış onayı/fallback ve
                                      kabul riski         güven eşiği
                                      yönetilmelidir      doğrulaması
  ---------------------------------------------------------------------------

**Not:** Öncelikler, eldeki belgelere göre önerilen çalışma sırasıdır;
tamamlanmış saha risk değerlendirmesi veya sertifikalı risk puanı
değildir.

------------------------------------------------------------------------

## 6. Standartlar ve mevzuat bağlamı

### IEC 62443

IEC 62443 ailesi, endüstriyel otomasyon ve kontrol sistemlerinin siber
güvenliğini yaşam döngüsü boyunca ele alan standartlar ailesidir. IEC
62443-3-2 özellikle sistem kapsamı, zone/conduit ayrımı, risk
değerlendirmesi, hedef güvenlik seviyeleri ve güvenlik gereksinimlerinin
belgelenmesiyle ilgilidir. [IEC resmî yayın
kaydı](https://webstore.iec.ch/en/publication/30727) ve [ISA/IEC 62443
serisi genel
bakış](https://www.isa.org/standards-and-publications/isa-standards/isa-iec-62443-series).

Bu analizde IEC 62443'e atıf, makinenin standarda uygun veya sertifikalı
olduğu anlamına gelmez. Uygunluk iddiası için ilgili standartların tam
metni, uygulanabilir kapsam ve doğrulama kanıtları gerekir.

### AB Cyber Resilience Act (CRA)

PDF'nin 24 saat / 72 saat / 14 gün zaman çizelgesi, olay müdahalesini
öğretmek için kullanılmıştır. Ancak CRA'nın bildirim süreleri olayın
türüne ve düzeltici önlemin kullanılabilir olduğu zamana göre ayrışır.
Avrupa Komisyonunun güncel açıklamasına göre, **11 Eylül 2026
itibarıyla** kapsam dahilindeki üreticiler için aktif olarak istismar
edilen zafiyetler ve dijital unsurlu ürünlerin güvenliğini etkileyen
ciddi olaylara ilişkin bildirim yükümlülükleri uygulanmaktadır: erken
uyarı 24 saat içinde, bildirim 72 saat içinde; son rapor ise aktif
olarak istismar edilen zafiyetlerde düzeltici önlem kullanılabilir
olduktan sonra en geç 14 gün içinde, ciddi olaylarda 72 saatlik
bildirimi izleyen bir ay içinde sunulur. Uygulanabilirlik ve sorumlu
taraf, ürünün kapsamı ve olayın koşulları üzerinden hukuken
doğrulanmalıdır. [Avrupa Komisyonu --- CRA bildirim
yükümlülükleri](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting).

Bu nedenle föydeki "14 gün" ifadesi, her tür olay için tek ve evrensel
son rapor süresi olarak kullanılmamalıdır.

### AB Makine Mevzuatı

AB Makine Tüzüğü (EU) 2023/1230, AB pazarına sunulan makinelere yönelik
sağlık ve güvenlik gerekliliklerini düzenler ve genel uygulama tarihi 20
Ocak 2027 olarak belirtilmiştir. Uygulanabilirlik; ürünün pazara sunulma
zamanı, rol ve özel hükümler dikkate alınarak değerlendirilmelidir.
[EUR-Lex --- Makine güvenliği
gereklilikleri](https://eur-lex.europa.eu/EN/legal-content/summary/machinery-safety-requirements.html).

Bu rapor, FANTOM 2136 M'nin CE durumu veya belirli mevzuat maddelerine
uygunluğu hakkında hüküm vermez.

------------------------------------------------------------------------

## 7. Sonuç

FANTOM 2136 M için en yararlı yaklaşım, "makinede açık var mı?" sorusuna
erken ve kanıtsız cevap vermek yerine, önce gerçek konfigürasyonu
doğrulamak ve ardından fiziksel emniyet ile siber güvenlik arasında
izlenebilir bir kontrol zinciri kurmaktır.

SWOT'un ana sonucu şöyledir:

-   **Güçlü yön:** Makinenin ana teknik bileşenleri tanımlıdır ve PDF,
    fiziksel sonuçları merkeze alan disiplinli bir analiz çerçevesi
    sunar.
-   **Zayıf yön:** Mevcut kurulumun ağ, yazılım, hesap, emniyet ve yama
    durumu hakkında yeterli saha kanıtı yoktur.
-   **Fırsat:** IEC 62443 yaklaşımıyla varlık envanteri, zone/conduit
    mimarisi, güvenli bakım erişimi, program bütünlüğü ve kanıt paketi
    oluşturulabilir.
-   **Tehdit:** Yetkisiz bakım erişimi, yanlış program aktarımı, yazılım
    olayı veya yetersiz olay müdahalesi üretim ve insan güvenliğini
    etkileyebilir; bunların makinede gerçekleştiği şu an doğrulanmış
    değildir.

**Önerilen ilk karar:** Emniyet devresi ve fiziksel koruyucuların gerçek
kurulumunu yetkili teknik personelle doğrulayın; aynı anda kontrol
PC'si, yazılım sürümleri, ağ bağlantıları, servis hesapları ve program
aktarım zinciri için kanıtlı bir envanter çıkarın. Bu iki çalışma
tamamlanmadan makineye özgü güvenlik açığı, PLr/SIL seviyesi veya
mevzuat uygunluğu iddiasında bulunmayın.

------------------------------------------------------------------------

## 8. Kaynakça

1.  **KRC CNC**, *FANTOM 2136 M --- Teknik Özellikler*.
    https://krccnc.com/urunler/1004/fantom_serisi/1020/fantom_2136_m.aspx\
    Makinenin yayımlanmış teknik özellikleri için birincil üretici
    kaynağı.

2.  **International Electrotechnical Commission (IEC)**, *IEC
    62443-3-2:2020 --- Security for industrial automation and control
    systems, Part 3-2: Security risk assessment for system design*.
    https://webstore.iec.ch/en/publication/30727\
    Endüstriyel sistem kapsamı, zone/conduit ve risk değerlendirme
    yaklaşımı.

3.  **International Society of Automation (ISA)**, *ISA/IEC 62443 Series
    of Standards*.
    https://www.isa.org/standards-and-publications/isa-standards/isa-iec-62443-series\
    IEC 62443 ailesinin kapsamı ve yaşam döngüsü yaklaşımı.

4.  **European Commission**, *Cyber Resilience Act --- Reporting
    obligations*.
    https://digital-strategy.ec.europa.eu/en/policies/cra-reporting\
    CRA bildirim süreleri ve kapsam açıklaması. Güncel hukuki yorum için
    ilgili mevzuat metni ve ürün kapsamı ayrıca kontrol edilmelidir.

5.  **EUR-Lex / European Union**, *Machinery safety requirements ---
    Regulation (EU) 2023/1230*.
    https://eur-lex.europa.eu/EN/legal-content/summary/machinery-safety-requirements.html\
    AB Makine Tüzüğü ve genel uygulama tarihi hakkında resmî özet.

6.  **Kullanıcı tarafından sağlanan belge**, *FANTOM 2136 M Laboratuvar
    Föyleri --- Safety 4.0 Bootcamp*, 8 sayfa.\
    Emniyet mimarisi, IEC 62443 atölyesi, tehdit/risk, uzaktan erişim,
    SBOM/CVE/yama, CRA olay simülasyonu ve AI Safety Challenge
    bölümlerinin temel kaynağı.

------------------------------------------------------------------------

*Hazırlama ilkesi: Üretici verileri kaynakla desteklenmiş; laboratuvar
senaryoları gerçek olay veya doğrulanmış açık gibi sunulmamış; sahada
doğrulanması gereken noktalar açıkça belirtilmiştir.*
