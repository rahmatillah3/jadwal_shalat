# Dashboard Monitoring Jadwal Sholat Seluruh Indonesia (38 Provinsi)

Aplikasi web dashboard terintegrasi untuk pemantauan jadwal sholat 38 ibukota provinsi di seluruh Indonesia (Sabang sampai Merauke), berbasis hisab resmi Kementerian Agama Republik Indonesia (standar MABIMS).

Aplikasi ini sudah dioptimalkan dan siap di-deploy langsung ke **Vercel** menggunakan Serverless PHP Runtime (`vercel-php`).

---

## 🚀 Struktur Proyek untuk Vercel

```text
jadwal-sholat/
├── api/
│   ├── index.php          # Entry point serverless function Vercel (Front Controller)
│   └── sholat.php         # Dedicated REST API JSON endpoint (/api/sholat)
├── index.php              # Berkas utama aplikasi web (PHP + Tailwind CSS + JS)
├── vercel.json            # Konfigurasi runtime PHP dan routing/rewrites Vercel
├── .gitignore             # File yang diabaikan oleh Git
├── .vercelignore         # File yang diabaikan saat upload ke Vercel
└── README.md              # Dokumentasi & panduan deployment
```

---

## 🌐 Cara Deploy ke Vercel

### Metode 1: Lewat GitHub (Paling Direkomendasikan & Otomatis)

1. **Inisialisasi Git dan Commit:**
   Buka terminal di folder project ini, lalu jalankan:
   ```bash
   git init
   git add .
   git commit -m "Siap deploy ke Vercel: jadwal sholat 38 provinsi"
   ```

2. **Buat Repository Baru di GitHub:**
   - Masuk ke akun [GitHub](https://github.com/new).
   - Buat repository baru (misal: `jadwal-sholat-indonesia`).
   - Salin URL remote repository Anda, lalu hubungkan:
   ```bash
   git branch -M main
   git remote add origin https://github.com/USERNAME_ANDA/jadwal-sholat-indonesia.git
   git push -u origin main
   ```

3. **Import Project ke Vercel:**
   - Buka dashboard [Vercel](https://vercel.com/dashboard).
   - Klik tombol **"Add New..."** -> **"Project"**.
   - Pilih repository GitHub yang baru saja Anda push.
   - Pada kolom *Framework Preset*, biarkan **Other**.
   - Klik tombol **"Deploy"**.
   - Tunggu 1–2 menit, web jadwal sholat Anda sudah live di URL `https://nama-project-anda.vercel.app`! 🎉

---

### Metode 2: Lewat Vercel CLI (Langsung dari Terminal)

1. Pastikan Node.js terpasang, lalu pasang Vercel CLI secara global:
   ```bash
   npm install -g vercel
   ```

2. Jalankan perintah login:
   ```bash
   vercel login
   ```

3. Jalankan deployment langsung dari folder project:
   ```bash
   vercel
   ```
   *(Pilih opsi default `Y` saat diminta konfirmasi setup project).*

4. Untuk deploy ke production domain:
   ```bash
   vercel --prod
   ```

---

## 💻 Cara Menjalankan di XAMPP (Lokal)

Aplikasi tetap dapat dijalankan secara normal di localhost XAMPP tanpa ada konfigurasi yang rusak:
1. Pastikan folder berada di: `C:\xampp\htdocs\jadwal-sholat`
2. Jalankan Apache di XAMPP Control Panel.
3. Buka browser dan akses:
   ```text
   http://localhost/jadwal-sholat/
   ```

---

## 📡 Endpoint REST API JSON

Selain tampilan visual dashboard, aplikasi ini menyediakan response data berformat JSON:

| Endpoint / URL | Keterangan |
| :--- | :--- |
| `GET /api/sholat` | Mengambil seluruh data jadwal sholat 38 provinsi (JSON) |
| `GET /api/jadwal` | Alias untuk endpoint data jadwal sholat (JSON) |
| `GET /?format=json` | Mengambil data dalam format JSON dari halaman utama |

**Contoh Response JSON:**
```json
{
  "status": "success",
  "code": 200,
  "pesan": "Jadwal Sholat 38 Ibukota Provinsi Republik Indonesia",
  "standar_hisab": "Kemenag RI (MABIMS)",
  "tanggal_masehi": "Senin, 26 Oktober 2026",
  "tanggal_hijriah": "14 Jumadil Ula 1448 H",
  "total_wilayah": 38,
  "statistik": {
    "total_wib": 18,
    "total_wita": 12,
    "total_wit": 8
  },
  "data": [
    {
      "id": 1,
      "kota": "Banda Aceh",
      "provinsi": "Aceh",
      "zona": "WIB",
      "subuh": "05:08",
      "dzuhur": "12:28",
      "ashar": "15:47",
      "maghrib": "18:29",
      "isya": "19:39",
      "hijriah": "14 Jumadil Ula 1448 H",
      "status": "Terverifikasi"
    }
  ]
}
```

---

## ✨ Fitur Unggulan

- **38 Ibukota Provinsi Resmi:** Mencakup seluruh provinsi baru di Papua (Papua Selatan, Pegunungan, Tengah, Barat Daya).
- **Penyesuaian 3 Zona Waktu:** WIB (UTC+7), WITA (UTC+8), dan WIT (UTC+9).
- **Jam Digital Real-Time Dinamis:** Sinkronisasi jam waktu nyata untuk ketiga zona waktu Indonesia.
- **Konversi Otomatis Kalender Hijriah:** Berdasarkan hisab Ummul Qura & kalender standar Indonesia.
- **Pencarian Cepat & Filter Zona:** Pencarian instan nama kota/provinsi tanpa reload halaman.
- **Modal Popup Rincian:** Menampilkan detail waktu sholat lengkap dan estimasi arah kiblat.
- **Salin ke Clipboard & Ekspor CSV:** Kemudahan menduplikasi jadwal ke teks pesan atau file spreadsheet.
- **Desain Modern & Responsif:** Menggunakan Tailwind CSS bernuansa Islami modern yang nyaman di perangkat mobile maupun desktop.
