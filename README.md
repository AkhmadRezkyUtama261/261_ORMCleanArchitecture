# Praktikum Web Service - ORM Clean Architecture

Implementasi REST API CRUD Komik menggunakan Node.js, Express, Sequelize ORM, dan PostgreSQL.

## Struktur Direktori

```text
+-- config/
¦   +-- config.js       # Konfigurasi database & environment
¦   +-- db.js           # Koneksi dan sinkronisasi Sequelize
+-- controller/
¦   +-- komikController.js  # Logic controller CRUD Komik
+-- migrations/         # Migration files dari Sequelize CLI
+-- models/
¦   +-- index.js        # Model loader Sequelize
¦   +-- komik.js        # Model entitas Komik
+-- routes/
¦   +-- api.js          # Routing endpoint API
+-- seeders/            # Seeder files Sequelize
+-- .env                # Variabel lingkungan database (git-ignored)
+-- .gitignore          # Daftar file/folder yang diabaikan git
+-- .sequelizerc        # Konfigurasi path Sequelize CLI
+-- index.js            # Entry point aplikasi Express
+-- package.json        # Dependensi dan script aplikasi
```

## Prasyarat & Instalasi

1. Pastikan PostgreSQL berjalan dan database `perpustakaan` telah dibuat.
2. Konfigurasi kredensial pada file `.env`:
   ```env
   DB_USER=postgres
   DB_PASS=your_password
   DB_DATABASE=perpustakaan
   DB_HOST=127.0.0.1
   DB_PORT=5432
   DB_DIALECT=postgres
   ```
3. Install dependensi (jika belum):
   ```bash
   npm install
   ```

## Menjalankan Aplikasi

Jalankan server dalam mode development menggunakan `nodemon`:

```bash
npm start
```

Server akan aktif pada: `http://localhost:3000`

---

## Endpoint API & Pengujian Postman

Base URL: `http://localhost:3000/api`

### 1. Tambah Komik Baru (Create)
- **Method:** `POST`
- **URL:** `http://localhost:3000/api/komik`
- **Headers:** `Content-Type: application/json`
- **Body (raw JSON):**
  ```json
  {
    "title": "Naruto Shippuden",
    "description": "Petualangan ninja Naruto Uzumaki",
    "author": "Masashi Kishimoto"
  }
  ```
- **Response:** `201 Created`

### 2. Dapatkan Semua Komik (Read All)
- **Method:** `GET`
- **URL:** `http://localhost:3000/api/komik`
- **Response:** `200 OK`

### 3. Dapatkan Komik Berdasarkan ID (Read by ID)
- **Method:** `GET`
- **URL:** `http://localhost:3000/api/komik/1`
- **Response:** `200 OK` (atau `404 Not Found` jika tidak ada)

### 4. Perbarui Komik (Update)
- **Method:** `PUT`
- **URL:** `http://localhost:3000/api/komik/1`
- **Headers:** `Content-Type: application/json`
- **Body (raw JSON):**
  ```json
  {
    "title": "Boruto: Two Blue Vortex",
    "description": "Kelanjutan petualangan ninja generasi baru",
    "author": "Masashi Kishimoto"
  }
  ```
- **Response:** `200 OK`

### 5. Hapus Komik (Delete)
- **Method:** `DELETE`
- **URL:** `http://localhost:3000/api/komik/1`
- **Response:** `200 OK`
  ```json
  {
    "message": "Komik deleted successfully"
  }
  ```
