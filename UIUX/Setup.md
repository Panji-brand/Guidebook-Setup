## Setup Figma Design System & Website Design

Kita membuat **2 file utama** (Design System & Website Design)

### 1️⃣ Login/Register Akun Figma

1. Buka website Figma:
   👉 https://www.figma.com
2. **Login** Figma, jika belum punya akun silahkan **Register**
3. Masuk ke **Figma Dashboard**

### 2️⃣ Masuk ke Team & Project

1. Pilih **Team** yang sudah dibuat
2. Masuk ke **Project** tempat file akan disimpan

### 3️⃣ Membuat File Design System (Menggunakan Template)

1. Buka link template Design System:
   👉 https://www.figma.com/community/file/1203061493325953101
2. Klik tombol **Duplicate**
3. Pilih **Team & Project** tujuan
4. Tunggu hingga file berhasil dibuat
5. Rename file menjadi **Design System**

### 4️⃣ Menyiapkan File Design System

File ini berfungsi sebagai **sumber utama komponen UI**.

Pastikan di dalam file terdapat:

- Colors
- Typography
- Components
- Spacing / Layout
- Icons

> File **Design System** tidak digunakan untuk desain halaman website.

### 5️⃣ Membuat File Website Design

1. Masuk ke **Project**
2. Klik **New**
3. Pilih **Design file**
4. Rename file menjadi **Website Design**

### 6️⃣ Publish Library Design System

1. Buka file **Design System**
2. Klik tab **Assets**
3. Klik ikon **Library**
4. Aktifkan Components, Color Styles dan Text Styles
5. Klik **Publish**

### 7️⃣ Import Library ke Website Design

1. Buka file **Website Design**
2. Klik tab **Assets**
3. Klik ikon **Library**
4. Aktifkan Library **Design System**
5. Tutup menu Library

### 8️⃣ Menggunakan Komponen dari Design System

1. Masuk ke tab **Assets**
2. Cari komponen dari **Design System**
3. Drag & drop ke canvas
4. Gunakan **Instance**, bukan Main Component
5. Lakukan perubahan hanya pada instance

### 9️⃣ Struktur Halaman Website (Opsional Senyamannya)

Gunakan page terpisah untuk setiap halaman:

- Home
- About
- Features
- Contact
- Auth (Login / Register)

Semua halaman wajib menggunakan komponen dari **Design System** supaya ketika melakukan perubahan akan lebih mudah.

### 🔟 Best Practice Penggunaan Design System

- ❌ Jangan copy-paste komponen manual
- ❌ Jangan edit Main Component di Website Design
- ✅ Selalu gunakan Library
- ✅ Update komponen hanya di Design System
- ✅ Publish ulang Library jika ada perubahan
