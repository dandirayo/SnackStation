# Snack Station — Ngemil On Duty

Website aplikasi web mandiri (*self-contained*) untuk **Kantin Kejujuran / Self-Service Snacks** Snack Station.

Dibangun dengan desain **Neo-Brutalist / Retro Paper**, responsif untuk perangkat mobile (termasuk optimasi khusus iOS/Android) dan desktop.

---

## Fitur Utama

- **Katalog Snack Interaktif Berbasis Foto**:
  - Foto kemasan produk nyata yang dioptimalkan untuk seluruh 36 item jajanan.
  - Filter kategori (*SEMUA*, *MANIES MANIES*, *MICIN KRIUK*, *PENGGANJAL LAPAR*).
  - Kontrol jumlah pesanan `+` dan `-` per produk.
- **Kalkulator Keranjang Otomatis**:
  - Penghitungan total harga (format Rupiah) secara *real-time*.
  - Tombol **RESET** untuk mengosongkan keranjang dalam satu klik.
- **Struk Pesanan & Checkout**:
  - Modal struk belanja dengan rincian per item dan total pembayaran.
  - Gambar QRIS pembayaran statis/mandiri.
- **Integrasi WhatsApp**:
  - Pembuatan format teks pesanan otomatis ke WhatsApp admin (*Mas Gugun* / nomor tujuan).
- **Tipografi & Ikon Bersih**:
  - Desain monokromatik bersih tanpa ikon berwarna yang mencolok.
  - Font: *Archivo Black* & *Space Mono* (Google Fonts).

---

## Cara Menjalankan

Karena dibuat murni dengan HTML5, CSS3, dan Vanilla JavaScript tanpa dependensi build tools yang rumit:
1. Cukup klik ganda (*double click*) file `index.html` untuk langsung membukanya di browser favorit Anda (Google Chrome, Microsoft Edge, Safari, dll.).
2. Atau jika ingin menjalankan lokal web server:
   ```bash
   # Menggunakan Python
   python -m http.server 3000
   ```
   Lalu buka `http://localhost:3000` di browser.

---

## Konfigurasi & Kustomisasi

### 1. Mengubah Nomor WhatsApp Admin
Buka file `index.html` dan cari variabel `GUGUN_PHONE` pada bagian `<script>`:
```javascript
const GUGUN_PHONE = '6282127875202'; // Ganti dengan nomor WhatsApp Anda (format internasional tanpa tanda +)
```

### 2. Mengedit / Menambah Daftar Menu & Harga
Cari objek `menuData` pada `<script>` di `index.html`:
```javascript
const menuData = {
  "MANIES MANIES": [
    { id: "m1", name: "Astorr", price: 1500 },
    // Tambah atau sesuaikan item di sini
  ],
  "MICIN KRIUK": [
    { id: "k1", name: "Chitato & Lite", price: 3000 },
  ],
  "PENGGANJAL LAPAR": [
    { id: "p1", name: "Pop Mie Goreng", price: 6500 },
  ]
};
```

### 3. Menambahkan Gambar pada Menu Snack
Simpan foto produk snack ke dalam folder `images/` (format PNG atau JPG disarankan berlatar transparan atau bersih).
Lalu tambahkan elemen `.item-thumb-box` pada item di `index.html`:
```html
<div class="item">
  <div class="item-thumb-box">
    <img class="item-thumb" src="images/nama-snack.png" alt="Nama Snack" loading="lazy" width="56" height="56">
  </div>
  <div class="item-info">...</div>
  ...
</div>
```
Dan tambahkan properti `image` pada item di objek `menuData`:
```javascript
{ id: "m2", name: "Beng - Beng Maxx", price: 5000, image: "images/beng-beng-maxx.png" },
```

### 4. Mengganti Gambar QRIS
Cari elemen `<img>` dengan `class="qris-img"` di `index.html`:
```html
<img class="qris-img" src="data:image/jpeg;base64,..." alt="QRIS Snack Station">
```
Anda dapat mengganti `src` dengan Data URI Base64 baru atau menggunakan path gambar lokal (misalnya `src="assets/qris.jpg"`).
