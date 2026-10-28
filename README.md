# Ev Hatırlatıcım — Android APK'yı bulutta oluşturma

Bu proje, Android Studio kurmadan bir **debug APK** üretmek için GitHub Actions iş akışı içerir.
Derleme GitHub'ın bulut runner'ında yapılır; Android Studio bilgisayarına gerek yoktur.

## APK üretme adımları

1. GitHub'da yeni bir repository oluştur (ör. `ev-hatirlaticim`).
2. Bu ZIP'i açıp içindeki dosyaları repository'ye yükle ve commit et.
   - `www/index.html`
   - `package.json`
   - `package-lock.json` yoksa sorun değil; workflow `npm install` çalıştırır.
   - `capacitor.config.ts`
   - `.github/workflows/android-apk.yml`
3. GitHub repository sayfanda **Actions** sekmesine gir.
4. Soldaki **Android APK oluştur** iş akışını seç.
5. **Run workflow** düğmesine bas ve çalışmasını bekle.
6. Başarılı çalışınca iş akışının sonuç sayfasında **Artifacts** bölümündeki
   `ev-hatirlaticim-debug-apk` dosyasını indir.
7. ZIP içindeki `app-debug.apk` dosyasını Android telefonuna aktar ve kur.
   Telefon, tarayıcıdan veya dosya yöneticisinden APK kurulumu için izin isteyebilir.

## Önemli bilgiler

- Bu bir **debug APK**'dır: kişisel test ve kurulum içindir. Google Play'e yayınlanmaya hazır, imzalı release paketi değildir.
- Uygulama verileri şu anda tarayıcı/WebView yerel depolamasında tutulur. Uygulamayı kaldırma/verileri temizleme kayıtları silebilir; Ayarlar içinden JSON yedeği al.
- Bu paket mevcut web prototipini Android uygulama kabuğuna koyar; Kotlin/Room'a taşınmış yerel veritabanı değildir.
- Namaz vakitleri örnek değerlerle gelir, otomatik servis ve Google Takvim entegrasyonu yoktur.
- Bu workflow Android projesini bulutta üretir; bu nedenle `android/` klasörünü ZIP içinde önceden bulundurmak gerekmez.
- Daha sonra Google Play için release APK/AAB, imza anahtarı ve güvenli GitHub Secrets yapılandırması ayrıca gerekir.

## Dosya yapısı

```text
www/index.html
package.json
capacitor.config.ts
.github/workflows/android-apk.yml
```
