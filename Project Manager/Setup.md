# Setup Project Manager

**Link Videos:**

## Setup Github Project

### 1️⃣ Login/Register Akun GitHub

1. Buka website GitHub:
   👉 https://github.com
2. **Login** Github, jika belum punya silahkan **Register**
3. Masuk ke GitHub Dashboard

### 2️⃣ Membuat GitHub Organization

1. Klik foto profil (kanan atas)
2. Pilih **Your organizations**
3. Klik **New organization**
4. Pilih **Free**
5. Isi Organization name (contoh: `Project-Flexoo-Academy`) dan Email
6. Klik **Create organization**
7. Invite anggota tim (opsional)

### 3️⃣ Membuat Repository di Organization

1. Masuk ke halaman **Organization**
2. Klik tab **Repositories**
3. Klik **New**
4. Isi Repository name, Visibility (**Set Private**)
5. Klik **Create repository**

### 4️⃣ Memulai GitHub Project

#### A. Membuat Project

1. Masuk ke halaman **Organization**
2. Klik tab **Projects**
3. Klik **New project**
4. Pilih **Board**
5. Isi nama project
6. Klik **Create project**

#### B. Setup Kolom Status

```text
Backlog → To Do → In Progress → Review → Done
```

- **Backlog**  
  Berisi daftar task atau ide yang **belum diprioritaskan**.  
  Biasanya masih berupa gambaran umum dan belum siap dikerjakan.

- **To Do**  
  Task yang **sudah jelas dan siap dikerjakan**, namun belum dimulai.  
  Biasanya sudah memiliki deskripsi dan tujuan yang jelas.

- **In Progress**  
  Task yang **sedang dikerjakan** oleh developer.  
  Setiap task di kolom ini sebaiknya sudah memiliki assignee.

- **Review**  
  Task yang **sudah selesai dikerjakan**, namun masih menunggu:

  - Code review
  - Testing
  - Approval dari mentor / lead

- **Done**  
  Task yang **sudah selesai sepenuhnya**, telah di-review, dan tidak memerlukan perubahan tambahan.

### 5️⃣ Membuat GitHub Project

1. Masuk ke repository
2. Klik tab **Issues**
3. Klik **New issue**
4. Isi Title dengan **Setup initial project**, Description opsional boleh Penjelasan singkat
5. Klik **Submit new issue**

### 6️⃣ Menambahkan Issue ke Project Board

1. Buka issue
2. Di sidebar kanan → **Projects**
3. Pilih project yang dibuat
4. Issue masuk ke board

### 7️⃣Setup Sprint (Iteration)

#### A. Membuat Sprint

1. Masuk ke **GitHub Project**
2. Klik **+** → **New field**
3. Pilih **Iteration**
4. Nama: **Sprint**
5. Atur durasi (1–2 minggu)

#### B. Assign Task ke Sprint

1. Klik issue di board
2. Pada field **Sprint**
3. Pilih sprint aktif

## Setup Figma Team Project

Figma digunakan sebagai tools untuk **perancangan flow aplikasi**.  
FigJam dipakai untuk membuat **flowchart, user flow, dan alur sistem** sebelum masuk ke tahap desain UI dan coding.

### 1️⃣ Login/Register Akun Figma

1. Buka website Figma:
   👉 https://www.figma.com
2. **Login** Figma, jika belum punya akun silahkan **Register**
3. Setelah login, kamu akan masuk ke **Figma Dashboard**

### 2️⃣ Membuat Team (Grup Project)

1. Pada sidebar kiri Figma Dashboard
2. Klik **New team**
3. Isi **Team name** (contoh: `Flexoo Academy Project`)
4. Klik **Create team**
5. Invite anggota tim (opsional)

### 3️⃣ Membuat Project di Dalam Team

1. Masuk ke **Team** yang sudah dibuat
2. Klik **New project**
3. Isi **Project name** (contoh: `Application Flow`)
4. Klik **Create project**

### 4️⃣ Membuat File FigJam

1. Masuk ke **Project**
2. Klik **New**
3. Pilih **FigJam**
4. Beri nama file (contoh: `App Flow Diagram`)

### 5️⃣ Setup Area Kerja FigJam

Saat FigJam terbuka, lakukan setup awal:

- Tambahkan **judul flow aplikasi** di bagian atas
- Gunakan **sticky notes** untuk coretan awal (brainstroming)
- Gunakan **shape** untuk flowchart
- Gunakan **arrow/connector** untuk arah alur

### 6️⃣ Elemen Dasar Flowchart di FigJam

Gunakan elemen berikut agar flow mudah dipahami oleh seluruh tim:

- **Oval** → Start / End
- **Rectangle** → Proses sistem
- **Diamond** → Decision (Ya / Tidak)
- **Arrow** → Arah alur

> Gunakan warna berbeda untuk membedakan **aksi user** dan **proses sistem**.

### Contoh Simple Flowchart Aplikasi

Contoh Flowchart Figjam:

```text
Start
  ↓
User Action
  ↓
System Process
  ↓
Decision?
 ↓      ↓
Yes     No
 ↓      ↓
Next    Error Handling
 ↓
End
```
