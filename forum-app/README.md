# FoeumSitem Forum

App Crypto 24 içine WebView, iframe veya doğrudan bağlantı olarak eklenebilecek topluluk forumu arayüzü.

## Mevcut özellikler

- Karanlık, neon-vurgulu responsive forum arayüzü
- Kanal filtreleri, konu arama ve popülerlik sıralaması
- Yeni konu oluşturma modalı
- Konu detay modalı, beğeni ve kaydetme etkileşimleri
- Profil ve rozet koleksiyonu ekranı
- Moderasyon kuyruğu, topluluk istatistikleri ve hızlı admin işlemleri görünümü
- Recharts tabanlı aktivite trendi, kanal etkileşimi, kullanıcı dağılımı ve en aktif üyeler grafik/dashboards
- Dönem, grafik metriği, kanal, kullanıcı durumu ve üye araması için gelişmiş admin filtreleri
- Filtrelenmiş kullanıcı listesini UTF-8 CSV olarak indirme ve özet, kullanıcılar, aktivite, kanallar, segmentler sayfalarından oluşan Excel raporu
- Mobil alt navigasyon ve Vercel SPA rewrite ayarı

## Vercel yayınlama

Vercel projesi oluştururken **Root Directory** olarak `forum-app` klasörünü seçin. Framework otomatik olarak Vite algılanır; build komutu `npm run build`, çıktı klasörü `dist` olarak kalabilir.

## Üretim için sonraki adım

Bu sürüm etkileşimli frontend prototipidir ve hızlı tasarım/UX doğrulaması için örnek veriler kullanır. Gerçek kullanıcı hesabı, kalıcı konu/yanıt verisi, canlı bildirimler, dosya yükleme ve rol bazlı admin yetkisi için `web-db-user` backend'ini veya Vercel uyumlu bir API + Postgres/Neon/Supabase katmanını bağlayın. İstemci tarafına gizli anahtar koymayın.

## GitHub Pages

Bu repo, `.github/workflows/deploy-pages.yml` ile `main` push'unda otomatik olarak GitHub Pages'e yayınlanır. Vite `base` ayarı `/FoeumSitem/` olarak yapılandırılmıştır.

## Dosya paylaşımı

Forum arayüzünde IPTV listeleri, M3U/M3U8, APK, ZIP, MP4 ve TXT dosyaları seçilebilir ve konu taslağına eklenebilir. GitHub Pages statik olduğu için dosyalar şu an tarayıcı oturumunda hazırlanır; kalıcı, kullanıcılar arası dosya paylaşımı için Supabase Storage, S3 veya benzeri bir backend ve kimlik doğrulama bağlanmalıdır.

## GitHub Discussions çalışma modeli

FoeumSitem, sunucu kullanmadan GitHub Discussions üzerine çalışan özel bir arayüzdür.

- Forum ve konu listesi herkese açıktır.
- Konu açmak ve yanıt yazmak için kullanıcı GitHub hesabıyla açılan GitHub Discussion sayfasında oturum açar.
- Yeni paylaşım ekranı başlık ve metin taslağını panoya kopyalar; ardından seçilen kategori için GitHub Discussion oluşturma ekranını açar.
- TXT, M3U, M3U8 ve görseller GitHub Discussion editörüne eklenebilir. Büyük APK/ZIP dosyaları için GitHub Releases kullanılması önerilir.
- Konu içindeki “GitHub'da yanıtla” bağlantısı ilgili Discussion kategorisini açar; yanıtlar GitHub'da kalıcı tutulur.
- Rozet görünümü ve analitik ekranı statik arayüzde yer alır. Gerçek kullanıcı kimliği ve moderasyon GitHub hesabı, Discussions ve repository ayarları üzerinden yönetilir.
- Admin panelindeki “GitHub moderasyonu” düğmesi repository Discussions alanına yönlendirir; token statik siteye gömülmediği için güvenli yazma/silme işlemleri GitHub üzerinde yapılır.

### Moderasyon önerisi

Repository sahibi veya maintainer; Discussion kilitleme, yorum silme, spam bildirimi ve kullanıcı engelleme işlemlerini GitHub Discussions arayüzünden yapmalıdır. GitHub Pages tarafında gizli erişim anahtarı tutulmaz.
