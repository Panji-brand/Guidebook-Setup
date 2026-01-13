# Setup Frontend (With Next.JS)

**Link Videos:**

## Setup Repository Frontend

Template Repository:  
👉 https://github.com/tapeds/next-template.git

### 1️⃣ Setup Awal

Pastikan tools berikut sudah terinstall di komputer:

- **Node.js (LTS)**  
  👉 https://nodejs.org
- **Git**  
  👉 https://git-scm.com
- **Code Editor** (Disarankan: VS Code)

Cek instalasi melalui terminal:

```bash
node -v
npm -v
git --version
```

### 2️⃣ Membuka Repository Template

1. Buka link repository:  
   👉 https://github.com/tapeds/next-template.git
2. Pastikan halaman repository terbuka
3. Klik tombol **Code**

### 3️⃣ Clone Repository ke Local

1. Buka terminal / command prompt
2. Jalankan perintah berikut:

```bash
git clone https://github.com/tapeds/next-template.git
```

3. Masuk ke folder project:

```bash
cd next-template
```

### 4️⃣ Install Dependencies

1. Install seluruh dependency yang dibutuhkan project:

```bash
npm install
```

2. Tunggu hingga proses selesai dan folder node_modules otomatis terbentuk.

### 5️⃣ Setup Environment (.env)

1. Cari file **.env.example**
2. Duplikat file tersebut
3. Rename menjadi **.env**
4. Isi konfigurasi berikut:

```text
NEXT_PUBLIC_API_BASE_URL=http://localhost:3000/api
```

> ⚠️ File .env tidak boleh di-commit ke repository

### 6️⃣ Menjalankan Project Frontend

Jalankan project dengan perintah:

```bash
npm run dev
```

Buka browser dan akses:  
👉 http://localhost:3000

Jika halaman tampil, berarti setup frontend berhasil ✅

### 7️⃣ Struktur Folder (Ringkas)

Struktur utama frontend:

```text
src/
├─ app/         # Routing & pages
├─ components/  # Reusable components
├─ services/    # API request
├─ styles/      # Styling
└─ utils/       # Helper functions
```

## Git Workflow Frontend

### 8️⃣ Membuat Branch Frontend

Sebelum mulai bekerja, buat branch baru:

```bash
git checkout -b feat/setup-frontend
```

### 9️⃣ Aturan Commit Message

Gunakan standar Conventional Commit:

- **feat:** fitur baru
- **fix:** perbaikan bug
- **chore:** setup / konfigurasi
- **docs:** dokumentasi
- **style:** styling / UI
- **refactor:** perbaikan struktur code

Contoh commit yang benar:

```bash
git commit -m "chore: initial frontend setup"
git commit -m "feat: create homepage layout"
git commit -m "fix: navbar responsive issue"
```

### 🔟 Push Code ke Repository

Setelah commit, lakukan push:

```bash
git push origin feat/setup-frontend
```

## Setup Bruno (API Management)

Bruno digunakan untuk testing API dan mengelola endpoint secara lokal.

### 1️⃣ Install Bruno

Download Bruno:  
👉 https://www.usebruno.com

Install sesuai sistem operasi masing-masing.

### 2️⃣ Membuat Bruno Collection

1. Buat folder di dalam project frontend:

```text
/bruno
```

2. Buka aplikasi **Bruno**
3. Klik **Open Collection**
4. Pilih folder **bruno**

### 3️⃣ Setup Environment Bruno

1. Klik menu **Environment**
2. Buat environment baru Nama: **Local**
3. Tambahkan variable:

```text
base_url = http://localhost:3000/api
```

### 4️⃣ Membuat Request API Pertama

1. Klik **New Request**
2. Method: **GET**
3. URL:

```text
{{base_url}}/health
```

4. Klik **Send**

Jika response berhasil, maka koneksi API siap digunakan.

### 5️⃣ Commit Setup Bruno

Simpan konfigurasi Bruno ke repository:

```bash
git add bruno
git commit -m "chore: setup bruno api collection"
git push origin feat/setup-frontend
```
