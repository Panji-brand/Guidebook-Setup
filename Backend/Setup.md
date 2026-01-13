# Setup Backend (With Golang)

**Link Videos:**

## Setup Repository Backend

Template Repository:  
👉 https://github.com/Flexoo-Academy/Backend-Template.git

### 1️⃣ Setup Awal

Pastikan tools berikut sudah terinstall di komputer:

- **Go (Latest Version)**  
  👉 https://go.dev/dl/  
  Download versi terbaru sesuai sistem operasi
- **Git**  
  👉 https://git-scm.com
- **PostgreSQL**  
  👉 https://www.postgresql.org/download/  
  Atau gunakan Docker (opsional)
- **Code Editor** (Disarankan: VS Code)  
  👉 https://code.visualstudio.com

Cek instalasi melalui terminal:

```bash
go version
git --version
psql --version
```

### 2️⃣ Membuka Repository Template

1. Buka link repository:  
   👉 https://github.com/Flexoo-Academy/Backend-Template.git
2. Pastikan halaman repository terbuka
3. Klik tombol **Code**

### 3️⃣ Clone Repository ke Local

1. Buka terminal / command prompt
2. Jalankan perintah berikut:

```bash
git clone https://github.com/Flexoo-Academy/Backend-Template.git
```

3. Masuk ke folder project:

```bash
cd Backend-Template
```

### 4️⃣ Install Dependencies Golang

1. Install seluruh dependency yang dibutuhkan project:

```bash
go mod download
```

2. Verifikasi dependencies sudah terinstall:

```bash
go mod verify
```

3. Tunggu hingga proses selesai dan semua package otomatis terdownload.

### 5️⃣ Setup PostgreSQL Database

#### A. Cara 1: Install PostgreSQL Langsung

1. Install PostgreSQL dari link di atas
2. Buka **pgAdmin** atau **psql** terminal
3. Buat database baru:

```sql
CREATE DATABASE flexoo_academy;
```

4. Buat user baru (opsional):

```sql
CREATE USER flexoo_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE flexoo_academy TO flexoo_user;
```

#### B. Cara 2: Menggunakan Docker (Lebih Mudah)

1. Pastikan **Docker Desktop** sudah terinstall:  
   👉 https://www.docker.com/products/docker-desktop

2. Jalankan PostgreSQL dengan Docker:

```bash
docker run --name postgres-flexoo -e POSTGRES_USER=flexoo_user -e POSTGRES_PASSWORD=your_password -e POSTGRES_DB=flexoo_academy -p 5432:5432 -d postgres:15
```

3. Cek container berjalan:

```bash
docker ps
```

4. Untuk stop container:

```bash
docker stop postgres-flexoo
```

5. Untuk start container kembali:

```bash
docker start postgres-flexoo
```

### 6️⃣ Setup Environment (.env)

1. Cari file **.env.example** di root project
2. Duplikat file tersebut
3. Rename menjadi **.env**
4. Isi konfigurasi berikut:

```text
# Server Configuration
PORT=8080
ENV=development

# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_USER=flexoo_user
DB_PASSWORD=your_password
DB_NAME=flexoo_academy
DB_SSL_MODE=disable

# JWT Configuration
JWT_SECRET=your_super_secret_key_change_this_in_production
JWT_EXPIRES_IN=24h

# CORS Configuration
ALLOWED_ORIGINS=http://localhost:3000
```

> ⚠️ File .env tidak boleh di-commit ke repository  
> ⚠️ Pastikan .env sudah ada di .gitignore

**Penjelasan Environment Variables:**

- `PORT`: Port untuk menjalankan server backend
- `ENV`: Environment (development/production)
- `DB_HOST`: Host database (localhost jika lokal)
- `DB_PORT`: Port PostgreSQL (default: 5432)
- `DB_USER`: Username database
- `DB_PASSWORD`: Password database
- `DB_NAME`: Nama database
- `DB_SSL_MODE`: SSL mode (disable untuk development)
- `JWT_SECRET`: Secret key untuk JWT authentication
- `JWT_EXPIRES_IN`: Durasi expire token
- `ALLOWED_ORIGINS`: URL frontend yang diizinkan akses API

### 7️⃣ Migrasi Database

1. Jalankan migrasi untuk membuat tabel di database:

```bash
go run cmd/migrate/main.go
```

Atau jika project menggunakan script lain:

```bash
make migrate-up
```

2. Cek tabel sudah terbuat di database:

```sql
\dt
```

Atau menggunakan pgAdmin untuk melihat struktur tabel.

### 8️⃣ Menjalankan Project Backend

Jalankan server backend dengan perintah:

```bash
go run cmd/main.go
```

Atau gunakan **hot reload** dengan Air (jika tersedia):

```bash
air
```

Server akan berjalan di:  
👉 http://localhost:8080

Cek API health check:  
👉 http://localhost:8080/api/health

Jika response berhasil, berarti setup backend berhasil ✅

### 9️⃣ Struktur Folder Backend

Struktur utama backend:

```text
Backend-Template/
├─ cmd/
│  ├─ main.go           # Entry point aplikasi
│  └─ migrate/          # Database migration
├─ internal/
│  ├─ config/           # Konfigurasi aplikasi
│  ├─ database/         # Database connection
│  ├─ handlers/         # HTTP handlers
│  ├─ middleware/       # Middleware (auth, cors, etc)
│  ├─ models/           # Database models
│  ├─ repositories/     # Data access layer
│  ├─ routes/           # API routes
│  └─ services/         # Business logic
├─ migrations/          # SQL migration files
├─ .env.example         # Template environment
├─ .gitignore           # Git ignore file
├─ go.mod               # Go dependencies
└─ go.sum               # Go dependencies checksum
```

## Git Workflow Backend

### 🔟 Membuat Branch Backend

Sebelum mulai bekerja, buat branch baru:

```bash
git checkout -b feat/setup-backend
```

### 1️⃣1️⃣ Aturan Commit Message

Gunakan standar Conventional Commit:

- **feat:** fitur baru
- **fix:** perbaikan bug
- **chore:** setup / konfigurasi
- **docs:** dokumentasi
- **refactor:** perbaikan struktur code
- **perf:** peningkatan performa

Contoh commit yang benar:

```bash
git commit -m "chore: initial backend setup"
git commit -m "feat: create user registration endpoint"
git commit -m "fix: database connection error"
```

### 1️⃣2️⃣ Push Code ke Repository

Setelah commit, lakukan push:

```bash
git push origin feat/setup-backend
```

## Setup Bruno (API Testing)

Bruno digunakan untuk testing API backend dan dokumentasi endpoint.

### 1️⃣ Install Bruno

Download Bruno:  
👉 https://www.usebruno.com

Install sesuai sistem operasi masing-masing.

### 2️⃣ Membuat Bruno Collection

1. Buat folder di dalam project backend:

```text
/bruno
```

2. Buka aplikasi **Bruno**
3. Klik **Open Collection**
4. Pilih folder **bruno**

### 3️⃣ Setup Environment Bruno

1. Klik menu **Environment**
2. Buat environment baru:
   - Nama: **Local**
3. Tambahkan variable:

```text
base_url = http://localhost:8080/api
token =
```

4. Buat environment **Production** (opsional):

```text
base_url = https://api.production.com/api
token =
```

### 4️⃣ Membuat Request API Pertama

#### A. Health Check

1. Klik **New Request**
2. Nama: **Health Check**
3. Method: **GET**
4. URL:

```text
{{base_url}}/health
```

5. Klik **Send**

Response yang diharapkan:

```json
{
  "status": "ok",
  "message": "Server is running"
}
```

#### B. Test Register User

1. Klik **New Request**
2. Nama: **Register User**
3. Method: **POST**
4. URL:

```text
{{base_url}}/auth/register
```

5. Pilih tab **Body** → **JSON**
6. Masukkan body:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

7. Klik **Send**

#### C. Test Login User

1. Klik **New Request**
2. Nama: **Login User**
3. Method: **POST**
4. URL:

```text
{{base_url}}/auth/login
```

5. Pilih tab **Body** → **JSON**
6. Masukkan body:

```json
{
  "email": "john@example.com",
  "password": "password123"
}
```

7. Klik **Send**
8. Copy **token** dari response
9. Paste ke environment variable **token**

#### D. Test Protected Endpoint

1. Klik **New Request**
2. Nama: **Get Profile**
3. Method: **GET**
4. URL:

```text
{{base_url}}/users/profile
```

5. Pilih tab **Headers**
6. Tambahkan header:

```text
Authorization: Bearer {{token}}
```

7. Klik **Send**

### 5️⃣ Struktur Folder Bruno (Rekomendasi)

Organisir endpoint berdasarkan module:

```text
bruno/
├─ Auth/
│  ├─ Register.bru
│  ├─ Login.bru
│  └─ Logout.bru
├─ Users/
│  ├─ Get Profile.bru
│  ├─ Update Profile.bru
│  └─ Delete User.bru
└─ environments/
   ├─ Local.bru
   └─ Production.bru
```

### 6️⃣ Commit Setup Bruno

Simpan konfigurasi Bruno ke repository:

```bash
git add bruno
git commit -m "chore: setup bruno api collection"
git push origin feat/setup-backend
```

## Tips & Best Practices

### ✅ Development Workflow

1. **Selalu jalankan migrasi** sebelum coding
2. **Test endpoint** menggunakan Bruno setelah membuat API baru
3. **Commit berkala** dengan pesan yang jelas
4. **Gunakan hot reload** (Air) untuk development lebih cepat
5. **Validasi input** setiap endpoint untuk keamanan

### ✅ Database Management

1. **Backup database** secara berkala
2. **Gunakan migration** untuk perubahan schema
3. **Jangan hardcode** connection string
4. **Gunakan prepared statements** untuk mencegah SQL injection

### ✅ Security Best Practices

1. **Jangan commit** file .env ke repository
2. **Gunakan strong password** untuk database
3. **Rotate JWT secret** secara berkala di production
4. **Enable CORS** hanya untuk domain yang dipercaya
5. **Validasi semua input** dari user
6. **Gunakan HTTPS** di production
