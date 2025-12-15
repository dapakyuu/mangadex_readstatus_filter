# MangaDex Read Status Filter for Advanced Search

Tampermonkey userscript untuk menambahkan **filter berdasarkan status baca** (Reading, Completed, Dropped, dll.) ke halaman **Advanced Search MangaDex**.  
Script ini memudahkan pengguna untuk menyaring manga sesuai status yang tersimpan di akun MangaDex mereka.

---

## ✨ Fitur
- Menambahkan dropdown **Read Status** di samping tombol Reset filter.
- Mendukung status:
  - All
  - Not Added
  - Reading
  - On Hold
  - Plan to Read
  - Dropped
  - Re‑Reading
  - Completed
- Tombol **Apply** untuk langsung menyembunyikan/menampilkan manga sesuai status.
- Tombol **Set Config** untuk menyimpan kredensial OAuth MangaDex (username, password, client_id, client_secret).
- Konfigurasi tersimpan secara **persistent** menggunakan Tampermonkey storage.
- Filter tetap aktif ketika:
  - Navigasi **Back/Forward** di browser.
  - Pindah halaman (page=1 → page=2, dst.).
- Auto‑apply status terakhir setelah reload/back/pindah page.
- Popup interaktif dengan animasi untuk konfigurasi dan notifikasi.

---

## 📦 Instalasi
1. Pastikan sudah menginstal [Tampermonkey](https://www.tampermonkey.net/) di browser.
2. Buat script baru.
3. Copy‑paste isi file `__ ==UserScript==.txt` ke editor Tampermonkey.
4. Save.

---

## ⚙️ Konfigurasi
1. Klik tombol **Set Config** di halaman MangaDex `/titles`.
2. Isi:
   - **Username**
   - **Password**
   - **Client ID**
   - **Client Secret**
3. Klik **Save** → konfigurasi tersimpan di Tampermonkey storage.
4. Refresh halaman untuk login ulang.

> ⚠️ Catatan: Client ID dan Secret bisa dibuat melalui [MangaDex API Personal Clients](https://api.mangadex.org/docs/02-authentication/personal-clients).

---

## 🚀 Penggunaan
1. Buka halaman [MangaDex Advanced Search](https://mangadex.org/titles).
2. Pilih status baca dari dropdown **Read Status**.
3. Klik **Apply** → manga akan difilter sesuai status.
4. Navigasi ke halaman lain (page=2, page=3, dst.) → filter otomatis diterapkan kembali.
5. Klik **Reset filters** untuk menghapus semua filter.

---

## 🛠️ Teknologi
- **Tampermonkey API**: `GM_xmlhttpRequest`, `GM_setValue`, `GM_getValue`
- **MangaDex API**:
  - `POST /token` untuk login
  - `GET /manga/status` untuk bulk status
  - `GET /manga/status?statuses[]=` untuk filter status
- **JavaScript ES6** dengan async/await
- **MutationObserver** untuk deteksi navigasi SPA MangaDex
- **History API** (`pushState`, `replaceState`, `popstate`) untuk deteksi pindah halaman

---

## 📖 Contoh Tampilan
- Dropdown **Read Status** muncul di samping tombol Reset.
- Tombol **Set Config** membuka popup konfigurasi.
- Tombol **Apply** menyaring manga sesuai status.
<img width="1048" height="235" alt="image" src="https://github.com/user-attachments/assets/db44ae21-a10c-4c1c-89dd-bd5dff9ada55" />
---

## 👤 Credit
- Author: **dapakyuu (Daffa Al‑Fathir Ismail)**
- GitHub: [https://github.com/username/repo-name](https://github.com/username/repo-name)

---

## 📜 License
MIT License – bebas digunakan, dimodifikasi, dan didistribusikan dengan tetap mencantumkan credit.

---

## 📝 Catatan Tambahan
- Script ini membutuhkan akun MangaDex dan kredensial OAuth untuk bisa mengambil status baca.
- Jika manga list belum muncul (loading), filter akan dicoba ulang otomatis setelah beberapa detik.
- Script ini masih bisa dikembangkan lebih lanjut, misalnya:
  - Menambahkan indikator loading saat Apply.
  - Menyimpan preferensi filter per user.
  - Integrasi dengan daftar manga favorit.

