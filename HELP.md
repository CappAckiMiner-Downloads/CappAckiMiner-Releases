# CappAckiMiner PRO — Kullanım ve Yardım

Bu kılavuz Windows PRO ve PRO B sürümlerinin güvenli kurulumu, temel kullanımı, ekrandaki durumlar ve sık karşılaşılan sorunlar içindir. Uygulamanın özel mining algoritması, iç zamanlayıcıları, retry politikası, SDK çağrı sırası ve teslim stratejisi bu açık dokümana dahil değildir.

## İçindekiler

- [Sürüm seçimi](#sürüm-seçimi)
- [Kurulumdan önce](#kurulumdan-önce)
- [Windows kurulumu](#windows-kurulumu)
- [İlk açılış ve cüzdanlar](#ilk-açılış-ve-cüzdanlar)
- [Mining başlatma ve durdurma](#mining-başlatma-ve-durdurma)
- [Ekrandaki sayaçlar](#ekrandaki-sayaçlar)
- [Kart durumları](#kart-durumları)
- [Accept çerçeveleri](#accept-çerçeveleri)
- [Ayarlar](#ayarlar)
- [Cüzdan yedeği](#cüzdan-yedeği)
- [Güncelleme ve iki sürümü birlikte kullanma](#güncelleme-ve-iki-sürümü-birlikte-kullanma)
- [Sorun giderme](#sorun-giderme)
- [Log paylaşırken güvenlik](#log-paylaşırken-güvenlik)
- [Dosya doğrulama](#dosya-doğrulama)

## Sürüm seçimi

| Sürüm | Amaç | İç sürüm |
| --- | --- | --- |
| **PRO** | TEST4.3 PRO tabanlı, daha muhafazakâr karşılaştırma hattı | `1.3.20-test.4.3pro.9` |
| **PRO B** | Yeni yaşam döngüsü düzeltmelerinin bulunduğu alternatif karşılaştırma hattı | `1.3.20-test.20` |

İki sürüm Single Engine mimarisidir. Ayrı uygulama kimliği, kurulum klasörü, EXE adı ve yerel veri alanı kullanırlar; bu nedenle aynı bilgisayarda yan yana kurulup ayrı ayrı açılabilirler.

> **Önemli:** Aynı cüzdanı PRO ve PRO B üzerinde aynı anda mining'e başlatmayın. Bu, sağlıklı bir A/B karşılaştırması değildir ve aynı cüzdan için çakışan oturumlar oluşturabilir.

## Kurulumdan önce

1. Mevcut cüzdanlarınızın güncel bir yedeğini oluşturun.
2. Yedek dosyasının açılabildiğini ve güvenli bir konumda bulunduğunu kontrol edin.
3. İndirdiğiniz setup dosyasının SHA-256 değerini bu deponun README dosyasındaki değerle karşılaştırın.
4. Çalışan mining varsa güncelleme için uygun bir zamanda kontrollü biçimde durdurun.
5. Setup'ı yalnız bu GitHub deposundaki resmi release bağlantısından indirin.

Windows kurulumları şu anda Authenticode ile imzalı değildir. Bu yüzden Windows SmartScreen “tanınmayan uygulama” uyarısı gösterebilir. Dosya adını, indirme adresini ve SHA-256 değerini doğrulamadan devam etmeyin.

## Windows kurulumu

1. İstediğiniz sürümün setup dosyasını indirin.
2. SHA-256 değerini doğrulayın.
3. Setup'ı çalıştırın ve ekrandaki kurulum adımlarını tamamlayın.
4. Uygulamayı Başlat menüsünden veya oluşturulan kısayoldan açın.
5. İlk açılış tamamlanmadan uygulamayı zorla kapatmayın.

PRO ile PRO B artık birbirinin üzerine kurulmaz. İki uygulamanın adı ve veri alanı ayrıdır.

## İlk açılış ve cüzdanlar

Uyumlu eski bir CappAckiMiner profili bulunursa uygulama ilk çalıştırmada bu profili bir kez kendi veri alanına kopyalayabilir. Bundan sonra PRO ve PRO B değişikliklerini ayrı saklar; bir sürümde eklenen veya silinen cüzdanın diğer sürümde otomatik değişmesi beklenmemelidir.

İlk kontrolde:

- Cüzdan sayısının doğru olduğunu kontrol edin.
- Cüzdan adlarının ve adreslerinin beklediğiniz hesaplarla eşleştiğini doğrulayın.
- Eksik cüzdan varsa güvenli yedeğinizden içe aktarın.
- Bir cüzdanı silmeden önce yedeğinin bulunduğundan emin olun.
- Aynı cüzdanı iki sürümde eşzamanlı çalıştırmayın.

## Mining başlatma ve durdurma

### Start All

Start All, hazır cüzdanları toplu başlatır. Henüz hazır olmayan cüzdanlar gerekli kontroller tamamlandıkça sıraya katılabilir. Menüde seçilen toplu başlangıç gecikmesi, Start All ile yönetilen cüzdanların doğrulanmış yeni epoch başlangıçlarında da uygulanır.

### Kart üzerindeki Start

Bir cüzdan kartındaki Start düğmesi yalnız o cüzdanı hedefler. Toplu başlangıç için seçilmiş ek gecikmeyi beklemeden başlatma isteği verir; ancak ağ, epoch ve güvenlik kontrolleri yine geçerlidir.

### Stop ve Stop All

- Karttaki Stop yalnız ilgili cüzdan için durdurma niyeti oluşturur.
- Stop All, çalışan ve toplu başlamayı bekleyen cüzdanları durdurur/iptal eder.
- Stop işleminden sonra eski oturuma ait gerçek bir SDK sonucu geç gelebilir. Bu sonuç mining'i yeniden başlatmaz.

Bir düğmeye arka arkaya çok kez basmak süreci hızlandırmaz. Ekrandaki durum değişimini bekleyin.

## Ekrandaki sayaçlar

### Total NACKL

Uygulamanın cüzdanlardan okuduğu toplam görünür bakiyeyi gösterir. Ağ yanıtı gecikirse kısa süre eski değer görünebilir.

### Daily NACKL

Doğrulanmış ağ günlük epochu içinde gözlenen pozitif bakiye artışlarının toplamıdır. Saat 00:00'a veya son 24 saate bağlı bir sayaç değildir; doğrulanmış yeni günlük epoch ile sıfırlanır.

### Epoch NACKL

Geçerli kısa mining epochu boyunca gözlenen ödül artışlarını toplar ve yeni doğrulanmış kısa epoch ile sıfırlanır. Üç nokta menüsü mevcutsa yakın epoch geçmişi burada görülebilir.

### CPU ve TPS

CPU, uygulamanın çalışma yükünü; TPS ise ağın gözlenen işlem hızını temsil eden bilgi alanlarıdır. Tek başına yüksek TPS veya düşük CPU accept garantisi değildir.

### Network Health

Ağ sağlığı, harici ağ gözlemlerinden oluşturulan yardımcı bir göstergedir. Kırmızı–sarı–yeşil zemin genel durumu hızlı okumayı sağlar.

- **No data / Veri yok:** Henüz geçerli örnek alınmamıştır.
- **Stale data / Eski veri:** Son örnek güncelliğini kaybetmiştir.
- Sağlık yüzdesi mining sonucunun garantisi değildir.

## Kart durumları

Durum adları kısa tutulur. Bir kartın birkaç durumdan sırayla geçmesi normaldir.

| Durum | Genel anlamı |
| --- | --- |
| `READY` | Cüzdan başlatma isteği için hazırdır. |
| `QUEUE` | Yerel başlatma veya ağ işlemi sırasındadır. |
| `MINING` | Aktif mining oturumu yürütülmektedir. |
| `WAIT` | Mevcut oturumun ağ/SDK aşamasının tamamlanması beklenmektedir. |
| `RESULT` | Sonuç işleniyor veya doğrulanıyordur. |
| `CHECK` | Sonuç/epoch durumu yeniden kontrol ediliyordur. |
| `CLOSE` | Eski oturumun güvenli kapanış aşamasıdır. |
| `EPOCH` | Yeni doğrulanmış epoch beklenmektedir. |
| `REC` / `RESTORE` | Uygulama cüzdanın çalışma durumunu güvenli biçimde kurtarmayı deniyordur. |
| `Insufficient time` / `Yetersiz süre` | Geçerli epochta yeni ve güvenli bir oturum başlatmak için yeterli süre kalmamıştır. |

`BC 70` görünmesi, yerel oturumun tek başına başarıyla sonuçlandığını kanıtlamaz. Sonuç ve kapanış durumu SDK/ağ yanıtlarıyla birlikte değerlendirilir.

### “Yetersiz süre” neden görülür?

Yeni bir mining oturumunun güvenli biçimde tamamlanamayacağı kadar az süre kaldığında yeni başlangıç yapılmaz. Bu koruma devam eden bir oturumu zorla kesmez. Tamamlanmış bir oturumun sonuç/kapanış durumu da yalnız süre azaldı diye kaybolmamalıdır.

## Accept çerçeveleri

Cüzdan kartlarının çerçeve rengi gerçek SDK sonuçlarının hangi oturum bağlamında gözlendiğini anlatır:

- **Yeşil:** Geçerli oturum ve doğrulanmış geçerli epoch için accept gözlenmiştir.
- **Mavi:** Önceki oturuma ait gerçek accept sonucu geç ulaşmıştır.
- **Mavi/yeşil dönüşümlü:** Aynı kartta hem geç gelen eski oturum accept izi hem geçerli oturum accept izi vardır.

Yeni doğrulanmış kısa epochta görsel izler sıfırlanır. Çerçeve yalnız görsel bilgidir; mining'i başlatmaz, durdurmaz ve ödül hesabı yerine geçmez.

Karttaki yeşil sayı accept, kırmızı sayı reject sayacıdır. Fareyi sayının üzerinde tuttuğunuzda açıklaması görünür.

## Ayarlar

### Cüzdan başlatma aralığı

Çok sayıda cüzdanın aynı anda yük bindirmemesi için toplu başlatma istekleri arasında boşluk bırakır. Daha düşük değer her zaman daha iyi sonuç anlamına gelmez.

### Start All başlangıç gecikmesi

Toplu başlatılan cüzdanların doğrulanmış epoch başlangıcından sonra ne kadar bekleyeceğini seçer. Karttan tekil Start bu ek toplu gecikmeyi kullanmaz.

### Root/proof retry

Geçici ağ veya SDK koşullarında ilgili kontrolün ne sıklıkta yeniden denenebileceğini yönetir. Çok sık deneme ağ ve sistem yükünü artırabilir; çok seyrek deneme ise hazır hale gelmeyi geciktirebilir. Kararlı çalışan bir sistemde yalnız sorun gözlendiğinde ve kontrollü karşılaştırmayla değiştirin.

Bu ayar mining tap zamanlamasından ayrıdır. Üretim tap zamanlaması kullanıcı menüsünde değiştirilmez.

### Main ve Lite görünümü

Main görünümü geniş kartlar ve daha ayrıntılı düzen, Lite görünümü daha fazla cüzdanı aynı ekranda izlemek için yoğun düzen sunar. Görünüm değişikliği mining motorunu değiştirmez.

### Dil ve animasyonlar

Dil seçimi arayüz metinlerini değiştirir. Genel animasyon seçimi yalnız desteklenen görsel efektleri etkiler; mining sonucunu değiştirmez.

## Cüzdan yedeği

Yedek, güncelleme ve test işlemlerinden önceki en önemli güvenlik adımıdır.

- Yedeği yalnız güvendiğiniz çevrimdışı veya şifreli konumda saklayın.
- Bulut paylaşım bağlantısını herkese açık hale getirmeyin.
- Yedek dosyasını GitHub'a, Telegram grubuna veya destek mesajına eklemeyin.
- İçe aktardıktan sonra cüzdan sayısını ve adlarını kontrol edin.
- İçe aktarma tamamlanmadan uygulamayı kapatmayın.
- Eski yedeğinizi silmeden önce yeni yedeği test edin.

Uygulama içindeki Wallet Backup seçeneği desteklenen yedekleme ve içe aktarma akışını açar. Ayrı bir yedekleme aracı kullanıyorsanız dosyanın bu sürümle uyumlu olduğundan emin olun.

## Güncelleme ve iki sürümü birlikte kullanma

1. Mining'i uygun anda durdurun.
2. Güncel yedeği alın ve kontrol edin.
3. Yeni setup'ın hash değerini doğrulayın.
4. İlgili sürümün setup'ını çalıştırın.
5. Açılıştan sonra cüzdanları ve ayarları kontrol edin.
6. Önce az sayıda cüzdanla gözlem yapın; ardından toplu başlatın.

PRO ve PRO B aynı anda açık olabilir. Ancak aynı cüzdan yalnız bir sürümde çalıştırılmalıdır. Karşılaştırma yaparken farklı cüzdan grupları kullanın veya aynı cüzdanı sırayla, aynı ağ koşullarında deneyin.

Bir sürümü kaldırmak diğer sürümün kurulumunu kaldırmaz. Yine de kaldırma seçeneği yerel uygulama verisini silmeyi teklif ederse yedeğiniz olmadan onay vermeyin.

## Sorun giderme

### Start All pasif veya cüzdan başlamıyor

- En az bir cüzdanın hazır olup olmadığını kontrol edin.
- Epochta “Yetersiz süre” görülüp görülmediğine bakın.
- Cüzdanın AUTO durumunu ve bekleyen Stop niyetini kontrol edin.
- Network Health alanında veri yok/eski veri uyarısı olup olmadığına bakın.
- Önce karttan tekil Start ile bir cüzdanı deneyin.
- Uygulamayı art arda açıp kapatmak yerine mevcut kontrolün tamamlanmasını bekleyin.

### Kart WAIT, RESULT, CHECK veya CLOSE durumunda uzun kalıyor

Bu durumlar her zaman donma anlamına gelmez; geç ağ/SDK sonucu veya eski oturumun güvenli kapanışı bekleniyor olabilir.

- Ağ sağlığını ve internet bağlantısını kontrol edin.
- Aynı cüzdanın diğer sürümde çalışmadığından emin olun.
- Önce bir epoch geçişini gözlemleyin.
- Sorun tekrarlanırsa Log düğmesinden kayıt alın; cüzdan sırlarını paylaşmadan yalnız ilgili zaman aralığını gönderin.

Yeni sürümlerde doğrulanmış yeni epoch, aktif işi kalmamış eski yerel sahipliğin sonraki başlangıcı gereksiz yere engellemesini önlemek üzere ele alınır. Geç gelen gerçek sonuç eski oturuma yazılabilir ama yeni oturumun kontrolünü alamaz.

### Accept düşük veya reject yüksek

Accept oranı yalnız uygulama arayüzüne bağlı değildir. Ağ yoğunluğu, endpoint yanıtları, SDK sonucu, cüzdan yetkilendirmesi ve epoch zamanlaması etkili olabilir.

- Aynı cüzdanı iki uygulamada aynı anda çalıştırmayın.
- Ağ sağlığı kötü veya veri eskiyse sonucu tek epoch üzerinden değerlendirmeyin.
- Ayarları sürekli değiştirmek yerine birkaç tam epoch boyunca kontrollü gözlem yapın.
- Çok agresif retry ayarlarının daha iyi accept anlamına gelmediğini unutmayın.
- Reject ve accept sayılarını ödül bakiyesiyle karıştırmayın.

### Network Health “No data” veya “Stale data” gösteriyor

- İnternet bağlantısını kontrol edin.
- Güvenlik duvarı veya DNS'in ağ gözlem servisine erişimi engelleyip engellemediğini kontrol edin.
- Bir süre bekleyin; gösterge cüzdan başına değil, uygulama genelinde güncellenir.
- Veri yokluğu otomatik olarak ağın sağlıklı veya sağlıksız olduğu anlamına gelmez.

### Bakiye veya Daily/Epoch NACKL geç güncelleniyor

Ağ okumaları gecikebilir veya sırası değişebilir. Sayaçlar yalnız doğrulanmış ve uygun sıradaki gözlemleri hesaba katmak üzere tasarlanmıştır. Uygulamayı sürekli yeniden başlatmak güncellemeyi hızlandırmaz.

### Windows uygulamayı engelliyor

- Dosyanın resmi release sayfasından geldiğini doğrulayın.
- SHA-256 değerini kontrol edin.
- Dosya hash'i eşleşmiyorsa çalıştırmayın ve yeniden indirin.
- Kurumsal cihazlarda sistem yöneticinizin politikasına uyun.

### Uygulamalar ayrı açılmıyor

Güncel setup'larda PRO ile PRO B'nin uygulama kimliği, EXE adı ve veri alanı ayrıdır. Eski bir build çalışıyorsa onu kapatın, güncel iki setup'ı yeniden kurun ve Başlat menüsündeki tam adları kullanın.

## Log paylaşırken güvenlik

Tanı logları sorunu bulmada yararlıdır fakat paylaşmadan önce mutlaka kontrol edilmelidir.

Paylaşmayın:

- özel anahtar veya recovery phrase,
- cüzdan yedek dosyası,
- bağlantı/deep-link içindeki gizli yetkilendirme verisi,
- kişisel klasör adları ve gereksiz sistem bilgileri,
- erişim token'ları, çerezler veya API anahtarları.

Mümkünse yalnız sorunun başladığı dakikadan birkaç dakika öncesini ve sonrasını paylaşın. Orijinal logu güvenli yerde tutup paylaşılacak kopyadaki hassas alanları maskeleyin.

## Dosya doğrulama

Güncel Windows setup hash'leri:

```text
BFBB03A27100243604FA84D075E8453F0B86513275EE8EF4282A6FC9B4A3A4C1  CappAckiMiner-PRO.exe
6824257881D08B8E8ACFC49139C5E3CCCCB9A185DC05F4620524C5AF104D058C  CappAckiMiner-PRO_B.exe
```

PowerShell:

```powershell
Get-FileHash .\CappAckiMiner-PRO.exe -Algorithm SHA256
Get-FileHash .\CappAckiMiner-PRO_B.exe -Algorithm SHA256
```

Çıktıdaki hash ile bu sayfadaki hash birebir aynı olmalıdır. Bir karakter bile farklıysa dosyayı çalıştırmayın.

## Destek için gerekli bilgiler

Sorun bildirirken şu bilgileri eklemek teşhisi hızlandırır:

- PRO mu PRO B mi kullandığınız,
- About/Log alanındaki tam iç sürüm,
- Windows sürümü,
- sorunun görüldüğü yerel saat ve epoch,
- etkilenen cüzdan sayısı ve seviye aralığı,
- ekrandaki durum adı,
- hassas verileri temizlenmiş ilgili log bölümü,
- mümkünse kişisel veri içermeyen ekran görüntüsü.

Özel anahtar, recovery phrase veya cüzdan yedeği hiçbir destek talebi için gerekli değildir.

## Sınırlamalar

CappAckiMiner bir ağ istemcisidir. Ağın kullanılabilirliğini, SDK'nın verdiği sonucu, accept oranını veya ödül miktarını garanti edemez. Arayüzdeki sağlık, sayaç ve durum alanları tanı ve izleme içindir; zincir üzerindeki nihai sonucu değiştirmez.

Bu açık yardım belgesi kullanıcıya gerekli çalışma bilgisini verir. Uygulamanın özel scheduling, retry, proof/root, teslim ve sonuç eşleştirme uygulama ayrıntıları güvenlik ve ürün bütünlüğü nedeniyle yayımlanmaz.
