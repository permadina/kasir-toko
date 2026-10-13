Kasir & Stok Toko
Aplikasi kasir dan manajemen stok berbasis satu file HTML (`kasir-toko.html`). Tidak perlu instalasi, database, atau koneksi internet. Semua data disimpan di browser (localStorage).
Fitur
Data Barang – kelola kode, nama, stok, harga beli, harga jual, untung per unit, dan total nilai stok.
Kasir / Penjualan – buat nota penjualan dengan diskon, stok berkurang otomatis, nota bisa dicetak.
Laporan Penjualan – lihat riwayat transaksi, omzet, dan grafik tren harian dengan filter tanggal.
Cara Menjalankan
Opsi 1: Buka langsung
Klik dua kali `kasir-toko.html`, atau seret ke jendela browser (Chrome, Edge, Firefox, Safari).
Opsi 2: Localhost
Dari folder berisi file ini, jalankan salah satu:
```
python -m http.server 8000
```
atau
```
npx serve
```
Lalu buka `http://localhost:8000/kasir-toko.html`.
Opsi 3: Domain / hosting (public_html)
Unggah `kasir-toko.html` ke folder `public\_html` hosting Anda (via File Manager atau FTP), lalu buka `https://domainanda.com/kasir-toko.html`. Anda boleh mengganti nama file menjadi `index.html` agar terbuka langsung dari alamat domain.
Panduan Penggunaan
1. Data Barang
Buka tab Data Barang.
Isi Kode Barang (harus unik), Nama Barang, Kuantitas/Stok, Harga Beli, dan Harga Jual.
Klik Simpan Barang.
Tabel daftar barang menampilkan:
Untung/unit = Harga Jual − Harga Beli
Total Nilai Stok = Stok × Harga Jual
Stok ≤ 3 ditandai merah sebagai peringatan stok menipis.
Tombol Edit mengubah data barang (kode tidak bisa diubah), tombol Hapus menghapus barang. Gunakan kolom pencarian untuk mencari berdasarkan kode atau nama.
2. Kasir / Penjualan
Buka tab Kasir / Penjualan.
Ketik kode atau nama barang di kolom pencarian, lalu klik barang yang muncul untuk memasukkannya ke keranjang.
Atur jumlah dengan tombol + / – (tidak bisa melebihi stok). Tombol x menghapus barang dari keranjang.
Pada panel Nota Penjualan (kanan), lihat rincian barang, Total Belanja, dan isi Diskon (pilih `Rp` untuk nominal atau `%` untuk persen).
Total Bayar akan dihitung otomatis.
Klik Simpan & Cetak Nota. Sistem akan:
menyimpan transaksi,
mengurangi stok barang otomatis,
membuka dialog cetak nota (bisa dicetak atau disimpan sebagai PDF).
Tombol Kosongkan mengosongkan keranjang tanpa menyimpan transaksi.
3. Laporan Penjualan
Buka tab Laporan Penjualan.
Pilih Dari Tanggal dan Sampai Tanggal, lalu klik Terapkan Filter. Tombol Hari Ini mengembalikan filter ke hari ini.
Ringkasan menampilkan jumlah transaksi, total omzet, dan rata-rata per transaksi.
Grafik batang menunjukkan tren omzet per hari pada rentang yang dipilih.
Tabel Riwayat Transaksi menampilkan nomor nota, waktu, jumlah item, total belanja, diskon, dan bayar akhir.
Penyimpanan Data & Backup
Data tersimpan di localStorage browser pada perangkat yang dipakai.
Data tidak otomatis sinkron antar perangkat atau antar browser.
Data hilang jika Anda menghapus data/cache situs (clear browsing data) atau memakai mode incognito/private.
Membuka file dari `file://` dan dari `http://localhost` atau domain dianggap sumber berbeda, sehingga datanya terpisah. Pilih satu cara akses dan konsisten.
Untuk memindahkan data ke perangkat lain: buka halaman aplikasi, tekan `F12` → tab Console, lalu jalankan:
```js
  copy(JSON.stringify({b: localStorage.toko\_barang\_v1, t: localStorage.toko\_transaksi\_v1}))
  ```
Tempel hasilnya ke file teks sebagai backup. Untuk memulihkan, jalankan di perangkat tujuan:
```js
  const d = JSON.parse(`ISI\_BACKUP\_DI\_SINI`);
  localStorage.toko\_barang\_v1 = d.b; localStorage.toko\_transaksi\_v1 = d.t; location.reload();
  ```
Catatan Penting
Menghapus transaksi tidak mengembalikan stok barang. Jika perlu, koreksi stok manual lewat tab Data Barang.
Mengedit harga barang tidak mengubah transaksi lama (harga tersimpan pada saat transaksi terjadi).
Kode barang tidak boleh sama dengan barang lain.
Cetak nota memakai fitur print browser; untuk printer thermal, pilih printer tersebut di dialog cetak dan atur ukuran kertas sesuai.
Keterbatasan
Aplikasi ini cocok untuk satu kasir/satu perangkat. Untuk banyak kasir, data terpusat, login pengguna, atau backup otomatis, diperlukan backend dan database (misalnya PHP + MySQL).
Struktur File
```
kasir-toko.html   → seluruh aplikasi (HTML + CSS + JavaScript)
README.md         → dokumentasi ini
```
