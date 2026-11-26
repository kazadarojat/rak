# Rerana

**Reportase Asendatif Kontemplatif** adalah aplikasi jurnal harian berbasis web untuk mendokumentasikan aktivitas, pengalaman, kondisi diri, pemikiran, dan refleksi sehari-hari.

Rerana dirancang sebagai aplikasi statis yang dapat dijalankan melalui GitHub Pages tanpa akun, backend, atau database. Catatan disimpan di penyimpanan browser, sedangkan pemindahan dan pencadangan antarperangkat dilakukan secara manual menggunakan file JSON.

**Aplikasi:** https://kazadarojat.github.io/rak/  
**Repository:** https://github.com/kazadarojat/rak
<img width="2124" height="740" alt="image" src="https://github.com/user-attachments/assets/60d26c61-3727-4a40-bf5f-7ad9254d5405" />


---

## Fitur

### 1. Diary harian

Catatan harian dibagi menjadi tujuh bagian:

| Bagian | Informasi yang dicatat |
| --- | --- |
| **Waktu & Istirahat** | Tanggal, hari, waktu bangun, waktu tidur, kondisi fisik, dan mimpi |
| **Konsumsi & Asupan** | Menu sarapan, makan siang, dan makan malam |
| **Mobilitas, Relasi & Suasana Hati** | Tempat yang dikunjungi, orang yang ditemui, dan mood |
| **Produktivitas & Finansial** | Kegiatan kuliah, belajar, proyek, pembelian, dan pengeluaran |
| **Intisari, Pemikiran & Rencana** | Highlight, insight, ide, pertanyaan, dan rencana esok hari |
| **R.A.K.** | Narasi bebas tentang peristiwa dan perjalanan reflektif hari itu |
| **Gratitude** | Tiga hal yang disyukuri serta evaluasi keberhasilan dan kekurangan hari itu |

Kolom narasi R.A.K. dilengkapi penghitung jumlah kata dan karakter.

### 2. Penyimpanan otomatis

- Perubahan pada kolom diary disimpan otomatis ke `localStorage` browser.
- Tombol **Simpan** tersedia untuk menyimpan catatan secara manual.
- Catatan diorganisasi berdasarkan tanggal.
- Pengaturan tampilan disimpan secara terpisah dari data diary.

> **Penting:** `localStorage` hanya berlaku pada browser dan perangkat yang digunakan. Data tidak otomatis tersinkronisasi ke perangkat lain. Menghapus data situs atau profil browser dapat menghilangkan catatan yang belum dicadangkan.

### 3. Riwayat dan arsip

- Melihat daftar catatan berdasarkan tanggal.
- Membuka kembali catatan untuk dibaca atau diedit.
- Menghapus catatan tertentu.
- Mengunduh seluruh arsip diary dalam format JSON.
- Mengimpor arsip JSON untuk memulihkan atau memindahkan catatan.

### 4. Impor dan ekspor JSON

Fitur ini mendukung alur pencadangan manual antarperangkat.

**Ekspor**
1. Buka menu **Riwayat**.
2. Pilih **Unduh Cadangan (.json)**.
3. Simpan file hasil unduhan di tempat yang aman, misalnya Telegram Saved Messages atau penyimpanan pribadi lainnya.

**Impor**
1. Buka Rerana pada perangkat tujuan.
2. Buka menu **Riwayat**.
3. Pilih **Impor JSON**.
4. Pilih file cadangan Rerana.
5. Tunggu notifikasi hasil impor.

Importer mendukung:
- Format JSON lama yang menggunakan tanggal sebagai key utama.
- Format terbungkus yang menempatkan catatan di dalam properti `entries`.

**Jika terdapat tanggal yang sama:**
- Pilih **OK** untuk mengganti catatan yang sudah ada pada tanggal yang sama dengan catatan dari file.
- Pilih **Batal** untuk mempertahankan catatan lama pada tanggal yang sama. Catatan dari tanggal yang belum ada tetap akan diimpor.

Dengan demikian, tombol **Batal** pada konfirmasi konflik bukan membatalkan seluruh proses impor, melainkan melewati catatan yang tanggalnya sudah tersedia.

Sebelum memulihkan arsip ke perangkat yang berisi catatan penting, sebaiknya unduh cadangan terlebih dahulu.

### 5. Kustomisasi tampilan

Pengguna dapat menyesuaikan tampilan melalui menu **Tampilan**:

- **8 tema warna:** Kertas Hangat, Sepia Klasik, Malam Gelap, Biru Tengah Malam, Hutan Teduh, Angin Laut, Senja Lavender, dan Mawar Lembut.
- **10 pilihan font:** Inter, Plus Jakarta Sans, DM Sans, Nunito, Lora, Merriweather, Crimson Pro, Playfair Display, JetBrains Mono, dan Space Mono.
- **4 ukuran teks:** Kecil, Normal, Besar, dan Ekstra.
- Pengaturan tampilan dapat dikembalikan ke default.

### 6. Salin catatan

Catatan harian dapat disalin menjadi format teks yang rapi untuk disimpan, dibagikan, atau digunakan sebagai bahan dokumentasi dan analisis.

---

## Alur penggunaan yang disarankan

Rerana tidak menyediakan sinkronisasi cloud otomatis. Untuk menggunakan jurnal di beberapa perangkat, gunakan alur berikut:

1. Tulis dan lengkapi diary pada perangkat yang sedang digunakan.
2. Unduh cadangan JSON melalui menu **Riwayat**.
3. Simpan atau kirim file tersebut ke Telegram Saved Messages atau tempat penyimpanan pribadi.
4. Pada perangkat lain, buka aplikasi Rerana dan impor file JSON terbaru.
5. Setelah melanjutkan pencatatan, unduh kembali cadangan terbaru.

Untuk analisis mingguan atau bulanan, file JSON dapat diberikan secara manual kepada AI sebagai bahan penyusunan laporan reflektif. Rerana sendiri tidak mengirimkan data ke AI secara otomatis.

---

## Format data JSON

Ekspor saat ini menggunakan objek dengan tanggal sebagai key. Contoh struktur sederhananya:

```json
{
  "2026-11-26": {
    "tanggal": "2026-11-26",
    "hari": "Kamis",
    "bangun": "05:30",
    "kondisi_fisik": "Cukup fit",
    "breakfast": "Nasi dan telur",
    "mood": "Tenang",
    "highlight": "Menyelesaikan tugas",
    "rak": "Hari ini kisahku dimulai dari...",
    "gratitude_1": "Kesehatan",
    "gratitude_2": "Keluarga",
    "gratitude_3": "Kesempatan belajar"
  }
}
```

Contoh di atas hanya menampilkan sebagian kolom. File ekspor memuat seluruh kolom diary yang digunakan aplikasi.

Format terbungkus dengan properti `entries` juga dapat dibaca oleh fitur impor, selama key tanggal dan struktur setiap catatan valid.

---

## Teknologi

Rerana dibuat sebagai aplikasi web statis dengan:

- **HTML** untuk struktur halaman.
- **Tailwind CSS CDN** untuk styling antarmuka.
- **JavaScript** untuk interaksi, pencatatan, penyimpanan, serta impor dan ekspor data.
- **Google Fonts** untuk pilihan tipografi.
- **Browser localStorage** untuk menyimpan catatan dan preferensi tampilan.

Tidak diperlukan Node.js, database, API key, atau proses build untuk menjalankan versi statis aplikasi ini.

---

## Menjalankan secara lokal

1. Clone repository:

   ```bash
   git clone https://github.com/kazadarojat/rak.git
   ```

2. Masuk ke direktori:

   ```bash
   cd rak
   ```

3. Buka `index.html` melalui browser.

Aplikasi juga dapat dijalankan melalui server lokal statis. Koneksi internet diperlukan untuk memuat Tailwind CSS CDN dan Google Fonts.

## Deploy ke GitHub Pages

Repository ini menggunakan struktur sederhana dengan `index.html` di root.

1. Buka **Settings** pada repository GitHub.
2. Masuk ke menu **Pages**.
3. Pada bagian **Build and deployment**, pilih **Deploy from a branch**.
4. Pilih branch `main` dan folder `/ (root)`.
5. Simpan pengaturan dan tunggu proses deployment selesai.

Setelah aktif, aplikasi dapat diakses melalui:

https://kazadarojat.github.io/rak/

---

## Privasi dan pencadangan

- Catatan diary disimpan di browser pengguna melalui `localStorage`.
- Aplikasi tidak menggunakan akun pengguna, backend, atau database cloud.
- Aplikasi tidak menyediakan enkripsi untuk data yang tersimpan di browser maupun file JSON.
- File JSON berisi informasi pribadi yang ditulis pengguna. Simpan dan bagikan file tersebut dengan hati-hati.
- Pengaturan tema, font, dan ukuran teks disimpan terpisah dan tidak termasuk dalam cadangan JSON diary.
- Jangan mengandalkan satu salinan arsip saja. Simpan cadangan berkala di lokasi yang aman.

---

## Batasan saat ini

- Tidak ada sinkronisasi otomatis antarperangkat.
- Tidak ada akun atau autentikasi pengguna.
- Tidak ada penyimpanan cloud bawaan.
- Impor dan ekspor dilakukan secara manual melalui file JSON.
- Analisis AI dan pembuatan laporan dilakukan di luar aplikasi dengan memberikan file arsip secara manual.
- Cadangan JSON hanya mencakup data diary, bukan preferensi tampilan.

---

## Kontribusi dan pengembangan

Saran, laporan bug, dan ide pengembangan dapat disampaikan melalui [GitHub Issues](https://github.com/kazadarojat/rak/issues) atau Pull Request.

Saat mengembangkan fitur yang mengubah struktur data diary, pertahankan kompatibilitas dengan arsip JSON sebelumnya agar catatan lama tetap dapat dipulihkan.
