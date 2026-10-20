# MangaTranslate AI — prototipe 0.1

Proyek awal penerjemah teks dari gambar manhwa/komik ke Bahasa Indonesia. Antarmuka responsif, dapat dipasang sebagai aplikasi web (PWA) di Android, dan bisa dikembangkan menjadi APK.

## Fitur yang sudah ada
- Tampilan mobile-first bertema gelap modern.
- Upload gambar JPG/PNG/WEBP (maks. 15 MB).
- Memakai Tesseract.js untuk OCR di browser.
- Pilihan bahasa sumber atau deteksi aksara sederhana.
- Memakai MyMemory Translation API untuk menerjemahkan teks ke Indonesia.
- Bisa mencoba memuat URL gambar langsung jika server mengizinkan CORS.
- Menampilkan gambar asli dan hasil teks terjemahan, serta menyalin teks.

## Batasan penting versi 0.1
- Ini prototipe yang dapat dijalankan, belum penerjemah komik profesional.
- OCR di browser memakai paket bahasa yang dimuat dari internet. Paket `kor`/`jpn`/`chi_sim` pada kode dipakai untuk pengenalan; jika OCR gagal atau paket bahasa tak termuat, ubah bahasa sumber atau tingkatkan konfigurasi OCR.
- Deteksi bahasa awal berbasis aksara, bukan AI vision penuh. Teks Latin diasumsikan Inggris kecuali dipilih manual.
- MyMemory merupakan layanan pihak ketiga dengan batas penggunaan/ketergantungan jaringan; hasil dan ketersediaannya bisa berubah. Jangan memasukkan teks privat.
- Link halaman situs komik umumnya tidak bisa dibaca langsung karena CORS, login, anti-bot, atau hak akses. Untuk saat ini simpan gambar/screenshot yang memang boleh Anda gunakan lalu upload.
- Hasil terjemahan belum dihapus/ditempel otomatis ke dalam balon dialog gambar. Fitur itu perlu tahap lanjutan (deteksi kotak teks, inpainting, tata letak teks, dan backend).
- Gunakan hanya gambar yang Anda punya izin untuk diproses; jangan melewati login atau proteksi situs.

## Menjalankan hanya dari HP Android (gratis)
Cara termudah:
1. Unduh ZIP proyek dan ekstrak.
2. Buka `index.html` di editor kode Android seperti Acode. Pratinjau lokal mungkin membatasi modul atau service worker, tetapi fungsi dasar dapat dicoba dengan internet aktif.
3. Untuk instalasi PWA yang lebih stabil, unggah isi folder ke repositori GitHub:
   - Buat repo baru, misalnya `mangatranslate-ai`.
   - Upload semua file/folder dari ZIP (bukan ZIP-nya saja).
   - Buka **Settings → Pages**, pilih branch `main` dan folder `/(root)`, lalu Save.
   - Tunggu sampai URL GitHub Pages muncul.
   - Buka URL itu di Chrome Android → menu ⋮ → **Tambahkan ke layar utama** / **Install app**.
4. Pastikan koneksi internet aktif saat OCR/terjemahan pertama kali karena pustaka dan layanan eksternal dimuat dari internet.

## Rencana agar menjadi APK Android sungguhan
Setelah prototipe web stabil, bungkus dengan Capacitor dari lingkungan Node.js (misalnya GitHub Codespaces jika tersedia untuk akun Anda) lalu build APK. Build Android native penuh biasanya membutuhkan Android SDK; ini kurang praktis jika hanya menggunakan HP. PWA di atas adalah jalur gratis termudah untuk uji awal.

## Struktur
- `index.html` — antarmuka dan logika awal.
- `manifest.json` — metadata aplikasi web.
- `sw.js` — cache dasar untuk PWA.
- `icon.svg` — ikon aplikasi.
