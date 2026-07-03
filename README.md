# 📱 HASH-KASIR V3.3.5 - Serverless POS & Repair Tracking System

HASH-KASIR adalah aplikasi kasir (Point of Sale) sekaligus pelacakan servis gadget berbasis web *Single-Page Application* (SPA). Sistem ini mengusung konsep *Serverless* dengan memanfaatkan **Google Sheets** sebagai database cloud utama melalui perantara **Google Apps Script REST API**, sehingga memangkas seluruh biaya operasional sewa server menjadi **Rp0,- / bulan** .

---

## 🛠️ Tech Stack & Arsitektur
* **Frontend:** HTML5, CSS3 (Mobile-First Layout dioptimalkan untuk perangkat tablet seperti SPC L80S), JavaScript (ES6+, Fetch API) .
* **Advanced Frontend API:** HTML Canvas API (Modul perekaman grafis koordinat pola kunci layar secara *real-time*) .
* **Backend Engine:** Google Apps Script bertindak sebagai RESTful API Serverless (`doGet` & `doPost`) .
* **Database:** Google Sheets Cloud Database dengan enkripsi token keamanan .
* **Hardware Integration:** Web Printing API (Sinkronisasi layout otomatis ke mesin printer termal 80mm via USB/Bluetooth) .

---

## 🚀 Fitur Unggulan (Key Features)

### 1. Asynchronous Auto-Invoice Cloud
Sistem mengeliminasi celah duplikasi nomor nota. Setiap kali form dibuka, sistem secara asinkronus (`async/await`) memeriksa nomor urut terakhir langsung dari cloud database berdasarkan tanggal hari ini dan menghasilkan nomor invoice unik (Contoh: `INV-03072026-001`) .

### 2. Dynamic Canvas Authentication Form
Mengintegrasikan papan gambar 3x3 berbasis HTML Canvas . Ketika pengguna menggambar pola kunci HP pelanggan, sistem menangkap jalur koordinat, mengubahnya menjadi kode teks urutan (Contoh: `1-5-9-8`), sekaligus mampu mereplikasi gambar pola tersebut langsung ke dalam struk cetak . Form ini adaptif, mendukung mode Gambar Pola, teks PIN, maupun opsi Tanpa Kunci .

### 3. Legal Risk Protection Note (Fitur Perlindungan Hukum)
Menyediakan modul input catatan risiko fisik awal (seperti: *cat mengelupas, backdoor renggang, LCD shadow*). Data ini dikunci di baris database cloud dan dipaksa muncul dengan layout tebal (*solid border*) di Struk Tanda Terima maupun Struk Pelunasan Akhir sebagai bukti hukum yang kuat untuk menghindari perselisihan atau komplain sepihak dari konsumen .

### 4. Dual-Receipt Workflow (Arsitektur Dua Struk)
Sistem pintar yang memisahkan logika cetak :
* **Struk Tanda Terima:** Mencetak data DP (Uang Muka), estimasi biaya, detail unit, catatan risiko, dan gambar pola kunci untuk dibawa pulang pelanggan .
* **Struk Pelunasan Akhir:** Mengambil data asli dari cloud berdasarkan nomor invoice, lalu otomatis mengalkulasi total biaya, akumulasi DP awal, dan sisa pembayaran hari itu hingga berstatus `LUNAS`[cite: <img width="1364" height="640" alt="database" src="https://github.com/user-attachments/assets/fe010023-e7f4-4b9f-956a-e56fa0e4ab0b" />
1].

---

## 📊 Skema Arsitektur Data
[Tablet POS App] --(Fetch API / JSON)--> [Google Apps Script API Engine] --(SpreadsheetApp)--> [Google Sheets Database]
|
(Web Printing API)
v
[Thermal Printer 80mm]

---
## 📸 Bukti Implementasi & Visual (Screenshots)
*(Pajang foto-foto implementasi Anda di bawah ini setelah di-upload ke GitHub)*
1. **Tampilan Formulir Kasir di Tablet:**
   <img width="800" height="1280" alt="tampilan awal 1" src="https://github.com/user-attachments/assets/f01833c3-c0de-43dd-b2c1-1c92414c0bea" />
<img width="800" height="1280" alt="tampilan awal 2" src="https://github.com/user-attachments/assets/806339d9-2eb3-42ab-b4ea-3e5294d88bd3" />

2. **Hasil Cetakan Struk Termal Fisik:**
<img width="348" height="572" alt="struk dp" src="https://github.com/user-attachments/assets/5617ebe4-d49c-4495-a71a-2625e9234661" />
<img width="357" height="583" alt="struk ambil unit" src="https://github.com/user-attachments/assets/45a785d1-0e4f-40b2-af10-e3f9c0df1e42" />

   
3. **Penyimpanan Data di Google Sheets Cloud:**
<img width="1364" height="640" alt="database" src="https://github.com/user-attachments/assets/c0e655af-4e53-49a8-9a63-9bf6a5793a51" />


*Proyek ini dikembangkan secara mandiri untuk membuktikan bahwa teknologi cloud mumpuni dapat diimplementasikan secara maksimal untuk efisiensi modal pelaku usaha kecil (UMKM)
