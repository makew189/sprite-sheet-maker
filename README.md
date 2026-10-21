# Sprite Sheet Maker – proyek Android (versi APK untuk dipakai sendiri)

ID aplikasi: `com.seismicsys.spritesheet` · minSdk 24 (Android 7.0) · targetSdk 34.
Pengaturan build (AGP 8.5.2, Gradle 8.7, compileSdk 34) sama dengan proyek Rocky Smash, jadi cocok dengan Android Studio yang sama.
Tidak butuh Node, npm, atau terminal.

## Membuat APK
1. Ekstrak zip ini. Android Studio → **Open** → pilih folder `spritesheet-android-apk` → tunggu Gradle sync selesai.
2. Menu **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
3. Klik **locate** pada notifikasi di pojok kanan bawah.
   Hasil: `app/build/outputs/apk/debug/app-debug.apk`. Salin ke HP dan pasang.

## Cara berkas disimpan
- **Android 10 ke atas:** langsung tersimpan di `Download/SpriteSheetMaker/` (muncul pesan di layar).
- **Android 7–9:** muncul pemilih berkas "Simpan sebagai".
- Tidak ada izin yang diminta. Di tab Ekspor, biarkan "Cara simpan" pada **Otomatis**.

## Perilaku khusus
- Tombol Back menutup jendela pratinjau atau mode "Pilih banyak"; selain itu tekan dua kali untuk keluar.
- Proyek tersimpan otomatis (juga saat aplikasi ke latar belakang). Gunakan "Simpan proyek" untuk cadangan.
- Ingin dikunci portrait? Ubah `fullSensor` → `portrait` di `AndroidManifest.xml`.

## Memperbarui aplikasi
Ganti `app/src/main/assets/www/index.html`, naikkan `versionCode` di `app/build.gradle`, build ulang.

## Debug
Sambungkan HP dan buka `chrome://inspect/#devices` di Chrome desktop (hanya untuk APK debug).

## Untuk Google Play nanti
Versi ini menargetkan API 34. Play Store untuk aplikasi baru mewajibkan API 36, jadi gunakan paket `spritesheet-android.zip`
(AGP 8.9.1, Gradle 8.11.1, butuh Android Studio Meerkat 2024.3.1 Patch 1 atau lebih baru).
