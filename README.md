# 🚀 PostgreSQL with Docker Compose

Repository ini menyediakan konfigurasi **Docker Compose** untuk menjalankan PostgreSQL secara cepat, mudah, dan terisolasi menggunakan container.  
Cocok untuk kebutuhan **development**, **testing**, maupun **production** ringan.

---

## 📦 Fitur

- Menjalankan PostgreSQL dalam container.
- Konfigurasi fleksibel melalui file `.env`.
- Data persisten menggunakan **Docker Volume**.
- Restart policy dapat disesuaikan (`no`, `always`, `on-failure`, `unless-stopped`).

---

## ⚙️ Konfigurasi

Semua variabel environment disimpan dalam file `.env`.  
Berikut contoh `.env`:

```bash
# Versi image PostgreSQL
POSTGRESQL_IMAGE_VERSION=15

# Nama container
POSTGRESQL_CONTAINER_NAME=postgres_server

# User dan password default
POSTGRESQL_USERNAME=myuser
POSTGRESQL_PASSWORD=mypassword

# Port host (akan map ke 5432 di dalam container)
POSTGRES_PORT=5432

# Lokasi data (gunakan absolute path di production)
POSTGRES_DATA_PATH=./

# Restart policy (pilihan: no, always, on-failure, unless-stopped)
POSTGRES_RESTART=unless-stopped
```

---

## ▶️ Menjalankan Container

1. Pastikan sudah membuat file `.env` di root project.
2. Jalankan perintah berikut:

```bash
docker compose up -d
```

3. Untuk menghentikan container:

```bash
docker compose down
```

---

## 🔗 Koneksi ke Database

Setelah container berjalan, PostgreSQL dapat diakses melalui:

- **Host:** `localhost`
- **Port:** `5432` (atau sesuai `POSTGRES_PORT` di `.env`)
- **Username:** sesuai `POSTGRESQL_USERNAME`
- **Password:** sesuai `POSTGRESQL_PASSWORD`
- **Database default:** `postgres`

Contoh koneksi dengan `psql`:

```bash
psql -h localhost -U myuser -d postgres
```

---

## 💾 Penyimpanan Data

Data PostgreSQL disimpan pada folder lokal sesuai konfigurasi di `.env`:

```bash
${POSTGRES_DATA_PATH}.postgres # contoh: ./.postgres
```

Sehingga data tetap aman meskipun container dihentikan atau dihapus.

---

## 🛠️ Tips

- Gunakan `restart: unless-stopped` agar container tetap berjalan otomatis setelah reboot.
- Jangan lupa **ganti password default** untuk keamanan.

---

## 📜 Lisensi

Proyek ini menggunakan lisensi bebas. Silakan digunakan untuk kebutuhan pribadi maupun proyek Anda.
