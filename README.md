# ASM FARM MONITORING — EDAMAME

Aplikasi web responsif berbahasa Indonesia untuk mencatat operasional budidaya edamame. Versi ini berjalan di browser tanpa server atau proses build.

## Menjalankan aplikasi

1. Buka `index.html` menggunakan Chrome atau Edge.
2. Tinjau data contoh di **Data Lahan**; ubah atau hapus sebelum memakai aplikasi untuk catatan nyata.
3. Tambahkan lokasi lahan dan buat satu siklus untuk setiap blok dari **Siklus Tanam**.
4. Gunakan **Kalender** dan **Tugas Hari Ini** untuk mengelola agenda, lalu isi realisasi saat pekerjaan selesai.
5. Unduh backup JSON dari **Pengaturan** secara berkala.

Untuk mencoba pemasangan PWA, sajikan folder ini melalui localhost atau HTTPS. Contoh dengan Python, jalankan dari folder aplikasi:

```powershell
python -m http.server 8000
```

Kemudian buka `http://localhost:8000`. Service worker menyimpan aset aplikasi untuk pembukaan berikutnya. `index.html` juga dapat dibuka langsung, tetapi service worker dan pemasangan PWA memerlukan localhost atau HTTPS.

## Fitur yang berfungsi

- Mengelola lokasi lahan dan banyak blok, termasuk luas, pemilik/mitra, varietas, tanggal tanam, target HST, dan status.
- Membuat 16 agenda awal per blok dari template aktif. HST 0 memakai tanggal tanam aktual; perkiraan panen memakai tanggal tanam + target HST.
- Menggeser agenda setelah perubahan tanggal tanam dengan ringkasan perubahan sebelum disimpan. Kegiatan yang dikunci tetap pada tanggalnya.
- Kalender bulanan, mingguan, harian, dan agenda; filter lahan/status; tambah dan edit kegiatan dari tanggal kalender.
- Checklist, prioritas, penugasan petugas, duplikasi kegiatan, mulai, tunda dengan alasan, dan penyelesaian dengan formulir realisasi.
- Mencatat rencana benih per blok dan pemakaian aktual dari stok benih (kg) saat realisasi tanam. Saldo stok dikurangi, koreksi jumlah menyesuaikan stok, dan hasil panen layak jual diringkas sebagai kg hasil per kg benih. Mutasi stok lain juga dapat dicatat langsung.
- Formulir inspeksi dengan pengukuran, gejala, kesimpulan, tindak lanjut, indikator kondisi, dan foto.
- Pencatatan beberapa hasil panen per blok, sortir layak jual/afkir, harga, tujuan, foto, dan biaya panen.
- Pencatatan biaya; ringkasan biaya per kilogram, produktivitas, nilai jual, dan estimasi setelah biaya yang tercatat.
- Data tenaga kerja dan penanggung jawab; laporan operasional; ekspor CSV; tampilan cetak yang dapat disimpan sebagai PDF.
- Template kegiatan dapat ditambah, diedit, dinonaktifkan, dan disalin tanpa mengubah jadwal blok yang sudah berjalan.
- Backup dan pemulihan seluruh data dalam JSON.
- Tata letak responsif untuk ponsel, tablet, dan desktop.

## Akses dari HP

Tampilan aplikasi responsif untuk layar ponsel. Untuk akses dan pemasangan yang stabil, unggah folder aplikasi ke hosting statis yang menyediakan HTTPS, lalu buka alamat tersebut pada HP:

- Android: buka di Chrome, pilih menu ⋮, lalu **Install app** atau **Tambahkan ke layar utama**.
- iPhone: buka di Safari, pilih **Bagikan**, lalu **Tambahkan ke Layar Utama**.

Aplikasi ini PWA yang dapat dibuka seperti aplikasi dari layar utama, bukan berkas APK Android. Data tetap tersimpan di browser/perangkat masing-masing dan tidak tersinkron otomatis. Pindahkan data dengan backup JSON dari menu Pengaturan.

## Data contoh

Lahan, blok, jadwal, petugas, dan stok awal bertanda contoh. Beberapa realisasi contoh ditandai **DATA CONTOH** untuk memperagakan riwayat tugas selesai. Hapus atau ganti data ini sebelum menggunakannya sebagai catatan operasional ASM.

## Penyimpanan dan batasan

- Data disimpan di `localStorage` browser pada perangkat/profil browser ini. Data tidak tersimpan di cloud dan tidak tersinkron antarperangkat. Ekspor backup JSON sebelum berpindah browser atau menghapus data browser.
- Peran pada Pengaturan hanya label tampilan. Login dan pembatasan akses per pengguna belum aktif.
- Tidak ada integrasi push, WhatsApp, email, layanan cuaca, peta/koordinat, sinkronisasi offline, atau penyelesaian konflik multi-pengguna.
- Ketersediaan dan beban petugas dapat dicatat secara dasar, tetapi absensi, jam kerja terperinci, perhitungan upah borongan, dan peringatan kapasitas otomatis belum tersedia.
- Ambang kondisi inspeksi dipilih oleh pengamat. Aplikasi tidak mendiagnosis penyakit dan tidak memberi dosis pupuk/pestisida.
- Hari panen yang dilarang dapat diatur dan konflik tanggal estimasi ditandai di Siklus Tanam. Sistem tidak menggeser tanggal otomatis.
- PDF menggunakan dialog cetak browser. Foto disimpan di browser tanpa kompresi; foto besar dapat memenuhi kuota penyimpanan. Jika penyimpanan gagal, unduh backup dan kurangi ukuran foto.
- Template jadwal tidak memiliki riwayat versi. Perubahan template hanya dipakai saat membuat siklus baru.

## Pemeriksaan yang dilakukan

Pemeriksaan browser mencakup pembuatan lahan dan blok, pembuatan agenda, perhitungan HST, penggeseran dan penguncian jadwal, realisasi serta penundaan kegiatan, inspeksi, panen, biaya, mutasi stok, ekspor dan pemulihan backup, CSV, pemuatan ulang data, navigasi halaman, dan lebar tampilan ponsel.
