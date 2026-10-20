# SOAL 1: Data Definition & Relasi
**Bobot: 40% — SCPMK0720801 (DDL & Relasi)**

### 1. Pemilihan Tiga Tabel

Tiga tabel yang digunakan dalam proyek database SIAKAD adalah:

1. **Mahasiswa** sebagai tabel induk yang menyimpan data mahasiswa.
2. **Matkul** sebagai tabel induk yang menyimpan data mata kuliah.
3. **KRS** sebagai tabel transaksi yang menyimpan mata kuliah yang diambil oleh mahasiswa.

### 2. Kode SQL CREATE TABLE

```sql
USE siakad_database;

-- Tabel Mahasiswa
CREATE TABLE mahasiswa (
    nim VARCHAR(100) NOT NULL,
    nama VARCHAR(100) NOT NULL,
    semester INT NOT NULL,
    PRIMARY KEY (nim)
) ENGINE=InnoDB;

-- Tabel Mata Kuliah
CREATE TABLE matkul (
    kode_mk VARCHAR(100) NOT NULL,
    nama_mk VARCHAR(100) NOT NULL,
    sks INT NOT NULL,
    PRIMARY KEY (kode_mk)
) ENGINE=InnoDB;

-- Tabel KRS
CREATE TABLE krs (
    id_krs VARCHAR(20) NOT NULL,
    nim VARCHAR(100) NOT NULL,
    kode_mk VARCHAR(100) NOT NULL,
    semester VARCHAR(20) NOT NULL,
    tahun_akademik VARCHAR(20) NOT NULL,
    PRIMARY KEY (id_krs),

    CONSTRAINT fk_krs_mahasiswa
        FOREIGN KEY (nim)
        REFERENCES mahasiswa(nim)
        ON DELETE CASCADE
        ON UPDATE CASCADE,

    CONSTRAINT fk_krs_matkul
        FOREIGN KEY (kode_mk)
        REFERENCES matkul(kode_mk)
        ON DELETE CASCADE
        ON UPDATE CASCADE
) ENGINE=InnoDB;
```

### 3. Penjelasan Relasi

- **Primary Key (PK):** `nim` pada tabel mahasiswa, `kode_mk` pada tabel matkul, dan `id_krs` pada tabel KRS digunakan sebagai identitas unik setiap data.
- **Foreign Key (FK):** Kolom `nim` pada tabel KRS menghubungkan data KRS dengan tabel mahasiswa, sedangkan kolom `kode_mk` menghubungkan tabel KRS dengan tabel matkul.
- **ON DELETE CASCADE:** Data KRS yang terkait akan terhapus ketika data induknya dihapus.
- **ON UPDATE CASCADE:** Perubahan nilai Primary Key pada tabel induk akan diterapkan pada Foreign Key yang terkait.

Dengan struktur tersebut, tabel KRS memiliki relasi dengan kedua tabel induk, yaitu mahasiswa dan mata kuliah, sesuai dengan persyaratan soal.