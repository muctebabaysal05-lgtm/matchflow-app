# MatchFlow — Ana Ürün Tanımı ve Uygulama Gereksinimleri

Bu belge MatchFlow'un tek ana gereksinim kaynağıdır. Mevcut çalışan özellikler korunur; yeni sürümlerde çalışan davranışlar kullanıcı açıkça istemeden kaldırılmaz veya yeniden yorumlanmaz. Uygulama Türkçe, mobil öncelikli ve koyu temalıdır.

## 1. Ürün ve platform
- Ürün adı tam olarak **MatchFlow**; sürüm başlığı `MatchFlow N.` biçiminde, yalnızca M ve F büyük.
- Android telefon/tablet, iPhone/iPad ve masaüstü tarayıcılarında aynı uygulama ve aynı veri modeli.
- PWA manifesti ve ikon ile ana ekrana eklenebilir. iOS Safari ve Android tarayıcıları için duyarlı arayüz.
- Koyu lacivert/siyah zemin, mor gradient/ana aksiyonlar, ölçülü turkuaz vurgular; altın gol aktifken altın tema. Yeşil ana buton teması kullanılmaz.
- Kullanıcıdan kod düzenlemesi, terminal işlemi veya dosyaları elle birleştirmesi istenmez.
- Çevrimdışı yerel kullanım desteklenir. Floot projesi kapsamında service worker eklenmez.

## 2. Ana gezinme
Üç ana bölüm ve isimleri:
1. **1 · MAÇ ÖNCESİ**
2. **2 · MAÇ**
3. **3 · SİSTEM**

Her sayfada sağ üstte **TÜMÜNÜ SİL** bulunur. Tam sıfırlama öncesinde açık bir onay/iptal penceresi gösterilir; iptal hiçbir veriyi değiştirmez.

## 3. Oyuncular ve takım oluşturma
- Oyuncu sayısı: 4–56; takım sayısı: 2–10. Takım başına hedef oyuncu sayısı 2–7.
- Oyuncu adları düzenlenebilir. Mobil klavye açıldığında giriş alanı kullanılabilir kalır.
- Seviye 1–5: **1 Hiç oynamıyor, 2 Az oynamış, 3 Orta, 4 İyi, 5 Çok iyi**.
- Oyuncular **ABI** olarak işaretlenebilir. ABI'nin kendi 1–5 seviyesi takım gücü hesabına aynen girer; ABI etiketi yıldız puanını artırmaz.
- Yeterli ABI varsa her takıma en az bir ABI dağıtılması hedeflenir; fazlalar olabildiğince dengeli paylaştırılır.
- Dağıtımda önce takım oyuncu sayıları olabildiğince eşitlenir (fark en fazla 1 hedefi), sonra yıldız toplamı/ortalaması ve ABI dengesi birlikte optimize edilir.
- Takım adları değiştirilebilir ve kilitlenebilir. Kilit takım adının yanlışlıkla değiştirilmesini önler; oyuncu dağılımını veya seviyeleri kilitlemez.
- Yeniden dağıtım, kilitli takım adlarını koruma ve geri alma davranışları korunur. Takım kimlikleri adlardan bağımsız tutulur.

## 4. Oyun modları ve puanlama
Mod adları aynen:
- 🏆 **KLASİK LİG**
- ⚔️ **ELEME**
- 🔥 **MERDİVEN**
- 🇨🇭 **İSVİÇRE KAOSU**

**Klasik Lig:** Galibiyet 2 puan, beraberlik 1 puan, mağlubiyet 0 puan. Sıralamada puan ve eşitlik bozma ölçütleri tutarlı uygulanır. Tablo oynanan maç, galibiyet (G), beraberlik (B), mağlubiyet (M) ve puan gösterir.

**Eleme:** Kaybeden elenir, kazanan ilerler; takım sayısı tek olduğunda uygun bay geçişi kullanılır. Şampiyon, elenenler ve devam edenler doğru gösterilir. Beraberlik/uzatma çözümü uygulama içindeki seçili maç kuralına göre tutarlı olmalıdır.

**Merdiven:** Kazanan sahada kalır; kaybeden sıradaki takıma yer verir. Galibiyet serisi ve sıra/karşılaşma akışı görünür. Gereksiz tekrar rakipleri azaltılır.

**İsviçre Kaosu:** Puan/performans yakınlığına göre eşleşme; önceki rakip tekrarları azaltılır; tek sayıda takım varsa bay geçişi uygulanır. Takımların oynadığı maç sayıları olabildiğince eşit tutulur.

Genel fikstür ilkesi: önce adil/eşit maç sayısı (mümkünse tam eşit, değilse fark en fazla 1), ardından kullanılabilir süre içinde mümkün olan en fazla uygun maç; aynı rakibin tekrarını ve arka arkaya aynı takımın sahaya çıkmasını azalt. Gerçekleşen maç sayısı ve takım başına maç sayısı ayrı ve doğru gösterilir.

## 5. İkinci maç / saha ekranı
- Üstte belirgin, okunaklı, geriye sayan maç süresi.
- İki takım karşılıklı görünür: sol tarafta bir takımın profil/kartı ve hemen altında takım adı; sağda diğer takımın profil/kartı ve adı.
- Takımların sol/sağ yerleri değiştirilebilir. Yer değiştirme yalnızca sunum tarafını değiştirir; takım kimliği, oyuncuları, fikstür bağlantısı ve sonuçlar karışmaz.
- Maç başlatma, duraklatma ve sıfırlama kontrolleri mevcut mor MatchFlow stilinde kalır.
- Sonuç seçimi: **Kazandı**, **Kaybetti**, **Berabere**. Seçim doğru takım kimliğine bağlanır; sonuç sonradan düzenlenebilir/geri alınabilir ve kilitlenebilir.
- Bu aşamada gol sayacı/saha üzerinde gol kaydı eklenmez. Gol sistemi daha sonraki ayrı geliştirmedir.
- Referans saha ekranından yalnızca iki taraflı maç sunumu ve karşılaşma mantığı alınır; yeşil butonlar veya başka uygulamanın renk dili kopyalanmaz.

## 6. Süre ve değişim sayacı
- Maç süresi ayarlanabilir; güncel proje aralığı 5–120 dakikadır. Değişim süresi de ayarlanabilir.
- Başlat/durdur/sıfırla. Süre, interval/timer tick sayısına güvenmek yerine gerçek zaman damgası ile hesaplanır; ekran kapalıyken veya uygulama arka plandayken geçen süre doğru bulunur.
- Maç süresi bitince maç biter ve değişim sayacı otomatik başlar.
- Değişim süresi bitince uyarı/ses verilir ve yeni maç süresi hazır durumda gösterilir; yeni maç kendi kendine başlamaz.
- Maç bitişi, değişim bitişi ve Altın Gol için birbirinden ayırt edilebilir sesli uyarılar.
- Paylaşım kodu aktarımında devam eden timer'ın o anki saniyesi taşınmaz; diğer maç ve ayar verileri korunur.

## 7. Altın Gol
- Altın Gol ana turnuva modlarından ayrı bir ek kuraldır.
- Aktif olduğunda ikinci maç ekranının tamamı altın/sarı tona geçer; büyük ve belirgin Altın Gol göstergesi, dış ışıma/parıltı ve kontrollü parçacık efekti bulunur.
- Altın Gol aktifken sekme/sekme göstergesi de altın durumunu açıkça yansıtır; Altın Gol'e geçişte ilgili sekmenin yukarı taşınması/hareket etmesi davranışı korunur. Mevcut gezinme düzeni bozulmaz.
- Altın Gol'de beraberlik sonucu verilmez; ilk gol maçı bitirir ve kazanan kaydedilir. (Gol sayacı arayüzü bu fazda ayrıca istenene kadar eklenmez.)
- Altın Gol mesajları kısa, okunabilir süreyle ve düşük performans yüküyle gösterilir; sarı/altın emojiler kullanılır. Mesajlar gereksiz tekrar etmez.

## 8. Sayaçlar ve dokunma davranışı
- Tek dokunuş +1.
- Yaklaşık 1–2 saniye basılı tutunca hızlı artış başlar; parmak/işaretçi bırakılınca durur.
- Uzun basma sonrası tarayıcının click olayı ikinci kez sayı eklememelidir.
- iOS ve Android dokunma, pointer, klavye ve erişilebilirlik davranışları test edilir.

## 9. Kayıt, geri yükleme ve aktarım kodu
- Oyuncu adları/seviyeleri/ABI, takım sayısı ve adları/kilitleri, seçili mod, fikstür, maç sonuçları, sıralama verileri ve süre ayarları otomatik olarak yerel kalıcı kayda yazılır.
- Sayfa yenileme, tarayıcıyı kapatıp açma ve uygulamaya geri dönme verileri kaybettirmez (tarayıcı verileri kullanıcı tarafından silinirse bunun dışında).
- **PAYLAŞIM KODU** dışa/içe aktarma: KOPYALA ve YAPIŞTIR. Kod tüm organizasyon verisini taşır; başka cihazda aynı organizasyon devam ettirilebilir.
- Kod doğrulanmadan mevcut verinin üzerine yazılmaz. Bozuk/geçersiz kod mevcut veriyi kesinlikle bozmaz. Pano izni yoksa metin alanına elle yapıştırma desteklenir.
- Paylaşım kodu canlı bulut eşitlemesi değildir; iki cihaz değişiklikleri kendiliğinden eşitlemez. Güncel kod tekrar aktarılmalıdır.
- Eski sürüm kodları için uyumlu alanlar mümkün olduğunca korunur; bilinmeyen alanlar sessizce kayıp yaratmamalıdır.

## 10. Sonuçlar, sistem bilgisi ve güvenilirlik
- Sonuç düzenleme, geri alma ve kilitleme; puan tablosu/fikstür/takım istatistikleriyle tutarlı güncellenir.
- Aynı veri tek bir ortak durum modelinden yönetilir; sayfalar arasında kopya ve çelişkili takım verisi üretilmez.
- Sayı, puan, galibiyet/beraberlik/mağlubiyet ve maç sayıları otomatik hesaplanır.
- Sistem sayfası paylaşım kodunu ve kayıt/aktarım, takım dengeleme, mod ve süre mantığını anlaşılır biçimde açıklar.
- Veri geçerliliği kontrol edilir; geçersiz içe aktarma mevcut durumu değiştirmez.
- Testler: takım sayısı/oyuncu sınırları, ABI dağıtımı, kilitli takım adı, her modda fikstür/sonuç, 2–0–1 puanlama, yer değiştirme, timer arka plan doğruluğu, otomatik değişim, Altın Gol geçişi, uzun basma, kayıt/geri yükleme, hatalı paylaşım kodu ve küçük/büyük mobil ekran.

## 11. Sürüm ve değişiklik ilkesi
- Var olan çalışan sürüm korunur; önemli değişiklik öncesi yeni commit/geri dönüş noktası oluşturulur.
- Değişiklikler küçük ve izlenebilir commit'lerle yapılır. Kullanıcı istemeden çalışan özellikler silinmez.
- Her geliştirme sonrası gerçek uygulama üzerinde işlev ve mobil davranış test edilir. Yalnızca gerçekten test edilen şey tamamlandı diye bildirilir.
- Kaynak olarak GitHub'daki mevcut `index.html` ve önceki MatchFlow 69 HTML kaynak dosyası karşılaştırmalı referanstır. Birinin diğerinin yerine körlemesine yazılması yasaktır.
