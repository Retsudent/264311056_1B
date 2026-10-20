# SOAL 1: Data Definition & Relasi
**Bobot: 40% — SCPMK0720801 (DDL & Relasi)**

## Soal

Pembuatan struktur fisik dan ketepatan relasi.

1. Pilihlah **3 tabel** dari proyek kelompok Anda yang saling berelasi (contoh: 2 tabel induk/master dan 1 tabel transaksi/anak).
2. Tuliskan kode SQL `CREATE TABLE` untuk ketiga tabel tersebut.
3. **Syarat wajib:**
   - Tentukan tipe data yang rasional dan *Primary Key* yang valid.
   - Harus ada deklarasi *Foreign Key* yang menghubungkan tabel transaksi dengan kedua tabel induk.

## Jawaban

### 1. Pemilihan Tiga Tabel

Tiga tabel yang digunakan dalam proyek database SIAKAD adalah:

1. **Mahasiswa:** Tabel induk yang menyimpan data mahasiswa.
2. **Matkul:** Tabel induk yang menyimpan data mata kuliah.
3. **KRS:** Tabel transaksi yang menyimpan mata kuliah yang diambil mahasiswa.

### 2. Kode SQL

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

- **Primary Key (PK):** `nim` pada tabel mahasiswa, `kode_mk` pada tabel matkul, dan `id_krs` pada tabel KRS.
- **Foreign Key (FK):** Kolom `nim` dan `kode_mk` pada tabel KRS menghubungkan tabel transaksi dengan tabel mahasiswa dan matkul.
- **ON DELETE CASCADE:** Data KRS yang terkait akan ikut terhapus ketika data induknya dihapus.
- **ON UPDATE CASCADE:** Perubahan nilai kunci pada tabel induk akan diterapkan pada data terkait.

Dengan struktur tersebut, tabel KRS terhubung dengan kedua tabel induk sesuai persyaratan soal.

