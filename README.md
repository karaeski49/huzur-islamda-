# Huzur: Android APK

Bu klasör, Huzur uygulamasını Android APK'ya çevirmek için hazır bir projedir.

## Yol A: Bilgisayarsız, GitHub ile (önerilen)

GitHub ücretsiz hesapla APK'yı senin yerine derler. Bilgisayara bir şey kurmak gerekmez.

1. github.com'da hesap aç, "New repository" ile boş bir depo oluştur (Private olabilir).
2. Bu klasörün içindekileri depoya yükle: "Add file" > "Upload files". `.github` klasörü dahil her şeyi yüklediğinden emin ol. Klasör yüklemek için masaüstü tarayıcı gerekir.
3. Depoda "Actions" sekmesini aç. "APK derle" çalışmaya başlar, yaklaşık 5-10 dakika sürer.
4. Bittiğinde çalıştırmaya tıkla, sayfanın altındaki "huzur-apk" dosyasını indir. İçinden `app-debug.apk` çıkar.
5. APK'yı telefonuna gönder, aç ve "bilinmeyen kaynaklardan yüklemeye" izin ver.

Derleme hata verirse Actions sayfasındaki kırmızı adımın günlüğünü kopyalayıp bana gönder.

## Yol B: Bilgisayarda Android Studio ile

Node.js ve Android Studio kurulu olmalı. Bu klasörde:

```
npm install
npx cap add android
npx cap sync android
npx cap open android
```

Android Studio açılınca Build > Build APK(s) ile APK üret. Bildirimlerin çalışması için `android/app/src/main/AndroidManifest.xml` dosyasında `</manifest>` satırından önce şu iki satırı ekle:

```
<uses-permission android:name="android.permission.POST_NOTIFICATIONS" />
<uses-permission android:name="android.permission.SCHEDULE_EXACT_ALARM" />
```

## Notlar

- Ezan bildirimi: Vakitler ekranında "Ezan bildirimi" anahtarını aç. Uygulama, sonraki 7 gün için bildirim kurar. Uygulamayı en az haftada bir açarsan bildirimler sürekli yenilenir.
- Android 12 ve üzerinde "tam zamanlı alarm" izni kapalı olabilir. Bildirimler birkaç dakika gecikirse Ayarlar > Uygulamalar > Huzur > Alarmlar ve hatırlatıcılar iznini aç.
- Pil tasarrufu bildirimleri geciktirebilir. Gerekirse Huzur için pil kısıtlamasını kapat.
- Yazı tipleri internet varken yüklenir. İnternet yoksa telefonun kendi yazı tipi kullanılır.
- Bu APK test imzalıdır ve Play Store'a yüklenemez. Play Store için imzalı paket (AAB) ve geliştirici hesabı gerekir.
