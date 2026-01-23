# Panduan Lengkap DevOps & Setup Developer

Dokumen ini mencakup dua bagian utama:
1.  **setup Developer**: Persiapan komputer lokal untuk kontributor.
2.  **Setup Infrastruktur**: Konfigurasi server, Docker, Nginx, DNS, dan CI/CD untuk DevOps.

---

# BAGIAN 1: Persiapan Lingkungan Developer
*Wajib dilakukan oleh setiap developer baru.*

## 1. Persiapan Sistem (Windows)
Disarankan menggunakan **WSL2** untuk kesetaraan lingkungan dengan server.

### Langkah 1: Install WSL2
1.  Buka PowerShell (Admin).
2.  Jalankan: `wsl --install`
3.  Restart PC. Buat akun Ubuntu saat terminal muncul.

### Langkah 2: Tools Wajib
1.  **Windows Terminal**: Download dari Microsoft Store.
2.  **Git**: Download dari [git-scm.com](https://git-scm.com/).
    - Config:
      ```bash
      git config --global user.name "Nama"
      git config --global user.email "email@anda.com"
      ```
3.  **Visual Studio Code**: Download dari [code.visualstudio.com](https://code.visualstudio.com/).
    - Extensions: *WSL*, *Docker*, *Remote - SSH*.
4.  **Docker Desktop**: Download dari [docker.com](https://www.docker.com/).
    - Aktifkan fitur "Use WSL 2 based engine".

## 2. Registrasi Akun
- **GitHub/GitLab**: Untuk akses kode. Setup SSH Key (`ssh-keygen`) dan tambahkan ke pengaturan akun.
- **Docker Hub**: Daftar di [hub.docker.com](https://hub.docker.com/) untuk menyimpan image container. Login di terminal dengan `docker login`.

## 3. Menjalankan Proyek Lokal
1.  Clone repo: `git clone <URL_REPO>`
2.  Setup env: `cp .env.example .env`
3.  Jalankan: `docker-compose up -d --build`
4.  Akses: `localhost:3000` (Frontend), `localhost:5000` (Backend).

---

# BAGIAN 2: Konfigurasi Infrastruktur & DevOps
*Panduan untuk setup Server, Deployment, dan Pipeline.*

## 1. Docker & Containerization
Kita menggunakan Docker untuk membungkus aplikasi.

### Struktur File
- **Dockerfile Backend** (`Backend/Dockerfile`):
  ```dockerfile
  FROM node:18-alpine
  WORKDIR /app
  COPY package*.json ./
  RUN npm ci --only=production
  COPY . .
  EXPOSE 5000
  CMD ["npm", "start"]
  ```

- **Dockerfile Frontend** (`Frontend/Dockerfile`):
  ```dockerfile
  FROM node:18-alpine
  WORKDIR /app
  COPY package*.json ./
  RUN npm install
  COPY . .
  RUN npm run build
  EXPOSE 3000
  CMD ["npm", "start"]
  ```

- **docker-compose.yml** (Orkestrasi):
  Digunakan untuk menjalankan Frontend dan Backend secara bersamaan dalam satu network bridge.

## 2. Setup Nginx (Reverse Proxy)
Nginx digunakan sebagai gerbang utama (gateway) di server.

### Konfigurasi (`nginx.conf`)
```nginx
server {
    listen 80;
    server_name thoriq.com www.thoriq.com; # Ganti dengan domain Anda

    # Frontend
    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
    }

    # Backend API
    location /api/ {
        proxy_pass http://localhost:5000;
        proxy_set_header Host $host;
    }
}
```

### SSL (HTTPS)
Gunakan Certbot untuk SSL gratis:
```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d domainanda.com
```

## 3. Konfigurasi DNS
Atur DNS record di penyedia domain Anda (Cloudflare/Namecheap):

| Tipe | Nama | Value | Keterangan |
| :--- | :--- | :--- | :--- |
| **A** | `@` | `IP_PUBLIC_SERVER` | Point root domain ke IP VPS |
| **CNAME** | `www` | `domainanda.com` | Alias untuk www |

*Gunakan `dig domainanda.com` untuk cek propagasi.*

## 4. Setup CI/CD Pipeline
Otomatisasi deploy menggunakan GitHub Actions.

### File Workflow (`.github/workflows/deploy.yml`)
```yaml
name: Deploy App
on:
  push:
    branches: ["main"]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build & Push Docker
        # ... steps login docker hub & push image ...
      - name: Deploy to VPS
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.SERVER_IP }}
          username: ${{ secrets.USER }}
          key: ${{ secrets.SSH_KEY }}
          script: |
            cd Flexoo-Academy
            git pull
            docker-compose up -d --build
```
**Secrets Wajib di GitHub:** `DOCKER_USER`, `DOCKER_TOKEN`, `SERVER_IP`, `SSH_KEY`.
