# Membuat APK lewat GitHub (tanpa Android Studio)

GitHub membangun APK-nya di cloud. Kamu hanya mengunggah proyek ini lalu mengunduh hasilnya.

## 1. Buat repositori
1. Masuk ke github.com (daftar dulu jika belum punya akun).
2. Klik **+ → New repository**. Nama: `sprite-sheet-maker`. Pilih **Public** (build gratis tanpa batas) atau **Private** (ada kuota gratis bulanan). Jangan centang README. Klik **Create repository**.

## 2. Unggah proyek (pilih salah satu)
**A. Lewat browser (tanpa terminal)**
1. Ekstrak zip ini. Di halaman repositori yang masih kosong, klik **uploading an existing file**.
2. Seret **seluruh isi** folder hasil ekstrak (bukan folder luarnya) ke halaman itu, termasuk folder `.github`.
   - Folder `.github` bisa tersembunyi di Mac/Linux (Mac: tekan Cmd+Shift+titik di Finder).
3. Klik **Commit changes**.
4. Cek bahwa berkas `.github/workflows/build-apk.yml` ada di repositori. Jika tidak: **Add file → Create new file**, ketik nama `.github/workflows/build-apk.yml`, tempel isi berkas `build-apk.yml.salinan`, lalu Commit.

**B. Lewat terminal**
```bash
cd spritesheet-android-github
git init -b main
git add .
git commit -m "Sprite Sheet Maker"
git remote add origin https://github.com/NAMAMU/sprite-sheet-maker.git
git push -u origin main
```

## 3. Tunggu build
1. Buka tab **Actions**. Workflow **Build APK** berjalan otomatis (sekitar 5–10 menit untuk yang pertama). Jika tidak, pilih workflow itu lalu **Run workflow**.
2. Lingkaran hijau = berhasil. Merah = gagal (lihat bagian 6).

## 4. Ambil APK
- **Dari Actions:** buka run yang hijau, bagian **Artifacts**, unduh `SpriteSheetMaker-debug-apk` (berupa zip berisi `SpriteSheetMaker-debug.apk`).
- **Tautan langsung (paling enak di HP):** tab **Releases → Draft a new release**, pada *Choose a tag* ketik `v1.0.0` lalu **Create new tag**, klik **Publish release**. Workflow berjalan lagi dan APK terlampir di halaman release setelah beberapa menit.

## 5. Memperbarui aplikasi
Buka `app/src/main/assets/www/index.html` di GitHub, klik ikon pensil, tempel versi baru, lalu Commit. Build berjalan otomatis dan menghasilkan APK baru. Untuk pembaruan berikutnya, naikkan `versionCode` di `app/build.gradle`.

## 6. Jika build gagal
Buka run yang merah, klik langkah yang bertanda ✗, lalu salin pesan error-nya. Penyebab yang paling mungkin:
- Versi sebuah Action sudah berubah (GitHub sering memperbarui). Pesannya biasanya menyebut nama Action-nya.
- Lisensi atau platform Android SDK tidak ditemukan.
- Berkas tidak lengkap saat diunggah (misalnya `app/build.gradle` atau folder `res` hilang).

## Catatan
- APK ini ditandatangani dengan kunci debug: cukup untuk dipakai sendiri, **bukan** untuk Google Play. Untuk Play Store, gunakan paket API 36 dan simpan keystore sebagai GitHub Secrets (jangan pernah mengunggah keystore ke repositori).
- Pemasangan manual di perangkat Indonesia bisa meminta langkah tambahan karena verifikasi pengembang. Lihat panduan terpisah.
