# 📱 KaloriX — App Store Yayınlama Rehberi

Mac (veya MacInCloud) üzerinde adım adım uygulanacak komutlar.

## ÖN GEREKSINIMLER
- [ ] Mac veya MacInCloud (macincloud.com, saatlik ~3$)
- [ ] Apple Developer hesabı (developer.apple.com, 99$/yıl)
- [ ] Xcode kurulu (App Store'dan ücretsiz)
- [ ] Node.js kurulu (nodejs.org)

## ADIM 1 — Proje Klasörünü Hazırla
Mac'te Terminal aç:

```bash
mkdir kalorix && cd kalorix
# Bu paketteki package.json ve capacitor.config.json dosyalarını bu klasöre kopyala
npm install
```

## ADIM 2 — Web Dosyalarını Yerleştir
```bash
mkdir www
# index.html dosyasını www/ klasörüne kopyala
# icon.png ve manifest.json varsa onları da www/ içine koy
```

## ADIM 3 — iOS Projesini Oluştur
```bash
npx cap add ios
npx cap sync
```

## ADIM 4 — Xcode'da Aç
```bash
npx cap open ios
```

Xcode açılınca:
1. Sol panelde "App" projesine tıkla
2. "Signing & Capabilities" sekmesi
3. "Team" → Apple Developer hesabını seç
4. Bundle Identifier: com.kalorix.app (veya kendi seçtiğin)

## ADIM 5 — Uygulama İkonu
1. appicon.co adresine git
2. 1024×1024 px ikonunu yükle (icon.svg'den üretilen PNG)
3. iOS seçeneğiyle indir
4. Xcode'da Assets.xcassets → AppIcon'a sürükle

## ADIM 6 — Test Et
1. Xcode üst barda hedef olarak kendi iPhone'unu seç (USB ile bağlı)
2. ▶️ (Run) butonuna bas
3. iPhone'da Ayarlar → Genel → VPN ve Cihaz Yönetimi → geliştirici profilini onayla

## ADIM 7 — App Store'a Yükle
1. Xcode → Product → Archive
2. Archive penceresinde "Distribute App" → "App Store Connect"
3. appstoreconnect.apple.com'a git
4. "Yeni Uygulama" oluştur:
   - Ad: KaloriX
   - Bundle ID: com.kalorix.app
   - SKU: kalorix-001
5. appstore-metinleri.md içindeki metinleri ilgili alanlara yapıştır
6. Ekran görüntülerini yükle (iPhone'da çektiğin ekran görüntüleri)
7. Gizlilik politikası URL'si: gizlilik-politikasi.html dosyasını Netlify'a yükle, o adresi ver
8. "İncelemeye Gönder"

## İNCELEME SÜRECİ
- Apple incelemesi genelde 1-3 gün sürer
- Red gelirse sebebini bildirirler, düzeltip tekrar gönderirsin
- En yaygın red sebepleri ve çözümleri:
  - "API key gerektiriyor" → Demo notlarında açıkladık, sorun olmamalı
  - "Minimum işlevsellik" → 1500+ yemek veritabanı key'siz çalışıyor, yeterli

## MALIYET ÖZETI
| Kalem | Ücret |
|---|---|
| Apple Developer | 99$/yıl |
| MacInCloud (3 saat) | ~10$ |
| TOPLAM İLK YIL | ~109$ |
