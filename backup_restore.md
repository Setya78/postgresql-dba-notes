# Backup & Restore PostgreSQL Database

## 📌 **1. Backup Database**
### 🔹 **Backup Full Database**
Gunakan perintah berikut untuk membuat cadangan database PostgreSQL secara lengkap:

```bash
pg_dump -U postgres -d dijaga_db -F c -f dijaga_db_backup.sql
```

**Penjelasan:**
- `-U postgres` → Login sebagai pengguna `postgres`
- `-d dijaga_db` → Nama database yang akan di-backup
- `-F c` → Format custom untuk backup
- `-f dijaga_db_backup.sql` → Nama file hasil backup

### 🔹 **Backup Hanya Data (Tanpa Struktur)**

```bash
pg_dump -U postgres -d dijaga_db --data-only -f dijaga_db_data_only.sql
```

## 🔄 **2. Restore Database**
### 🔹 **Restore Full Database**

```bash
pg_restore -U postgres -d dijaga_db -F c -c -f dijaga_db_backup.sql
```

**Penjelasan:**
- `pg_restore` digunakan untuk mengembalikan backup
- `-d dijaga_db` → Target database untuk restore
- `-F c` → Format custom backup
- `-c` → Membersihkan database sebelum restore

### 🔹 **Restore Hanya Data (Tanpa Struktur)**
Jika hanya ingin mengembalikan data tanpa merubah struktur:

```bash
pg_restore -U postgres -d dijaga_db --data-only -f dijaga_db_data_only.sql
```

## ✅ **3. Verifikasi Data Setelah Restore**
Setelah proses restore selesai, pastikan data benar-benar sudah dikembalikan dengan perintah berikut:

```sql
SELECT * FROM logs;
SELECT * FROM backups;
```

Jika data sudah ada, berarti restore berhasil. Jika tidak, ulangi proses restore dengan memperhatikan error yang muncul.

---

Dokumentasi ini dibuat untuk memastikan proses backup & restore berjalan dengan baik. Jika ada perubahan dalam skema database, pastikan untuk memperbarui prosedur ini.**
