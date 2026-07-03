# 📱 HASH-KASIR V3.3.5 - Serverless POS & Repair Tracking System

HASH-KASIR adalah aplikasi kasir (Point of Sale) sekaligus pelacakan servis gadget berbasis web *Single-Page Application* (SPA). Sistem ini mengusung konsep *Serverless* dengan memanfaatkan **Google Sheets** sebagai database cloud utama melalui perantara **Google Apps Script REST API**, sehingga memangkas seluruh biaya operasional sewa server menjadi **Rp0,- / bulan**[cite: 1].

---

## 🛠️ Tech Stack & Arsitektur
* **Frontend:** HTML5, CSS3 (Mobile-First Layout dioptimalkan untuk perangkat tablet seperti SPC L80S), JavaScript (ES6+, Fetch API)[cite: 1].
* **Advanced Frontend API:** HTML Canvas API (Modul perekaman grafis koordinat pola kunci layar secara *real-time*)[cite: 1].
* **Backend Engine:** Google Apps Script bertindak sebagai RESTful API Serverless (`doGet` & `doPost`)[cite: 1].
* **Database:** Google Sheets Cloud Database dengan enkripsi token keamanan[cite: 1].
* **Hardware Integration:** Web Printing API (Sinkronisasi layout otomatis ke mesin printer termal 80mm via USB/Bluetooth)[cite: 1].

---

## 🚀 Fitur Unggulan (Key Features)

### 1. Asynchronous Auto-Invoice Cloud
Sistem mengeliminasi celah duplikasi nomor nota. Setiap kali form dibuka, sistem secara asinkronus (`async/await`) memeriksa nomor urut terakhir langsung dari cloud database berdasarkan tanggal hari ini dan menghasilkan nomor invoice unik (Contoh: `INV-03072026-001`)[cite: 1].

### 2. Dynamic Canvas Authentication Form
Mengintegrasikan papan gambar 3x3 berbasis HTML Canvas[cite: 1]. Ketika pengguna menggambar pola kunci HP pelanggan, sistem menangkap jalur koordinat, mengubahnya menjadi kode teks urutan (Contoh: `1-5-9-8`), sekaligus mampu mereplikasi gambar pola tersebut langsung ke dalam struk cetak[cite: 1]. Form ini adaptif, mendukung mode Gambar Pola, teks PIN, maupun opsi Tanpa Kunci[cite: 1].

### 3. Legal Risk Protection Note (Fitur Perlindungan Hukum)
Menyediakan modul input catatan risiko fisik awal (seperti: *cat mengelupas, backdoor renggang, LCD shadow*). Data ini dikunci di baris database cloud dan dipaksa muncul dengan layout tebal (*solid border*) di Struk Tanda Terima maupun Struk Pelunasan Akhir sebagai bukti hukum yang kuat untuk menghindari perselisihan atau komplain sepihak dari konsumen[cite: 1].

### 4. Dual-Receipt Workflow (Arsitektur Dua Struk)
Sistem pintar yang memisahkan logika cetak[cite: 1]:
* **Struk Tanda Terima:** Mencetak data DP (Uang Muka), estimasi biaya, detail unit, catatan risiko, dan gambar pola kunci untuk dibawa pulang pelanggan[cite: 1].
* **Struk Pelunasan Akhir:** Mengambil data asli dari cloud berdasarkan nomor invoice, lalu otomatis mengalkulasi total biaya, akumulasi DP awal, dan sisa pembayaran hari itu hingga berstatus `LUNAS`[cite: 1].

---

## 📊 Skema Arsitektur Data
[Tablet POS App] --(Fetch API / JSON)--> [Google Apps Script API Engine] --(SpreadsheetApp)--> [Google Sheets Database]
|
(Web Printing API)
v
[Thermal Printer 80mm]

---

*Proyek ini dikembangkan secara mandiri untuk membuktikan bahwa teknologi cloud mumpuni dapat diimplementasikan secara maksimal untuk efisiensi modal pelaku usaha kecil (UMKM)[cite: 1].*
