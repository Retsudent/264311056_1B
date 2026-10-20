# SOAL 2: Operasi CRUD Dasar
**Bobot: 50% — SCPMK0720802 (CRUD Dasar)**

## Jawaban dan Hasil

### 1. CREATE — Menambahkan Data

Melakukan operasi `INSERT` untuk menambahkan minimal 3 baris data dummy ke masing-masing tabel, yaitu mahasiswa, matkul, dan KRS.

![Hasil INSERT data ke tiga tabel](assets/soal2no1.png)

### 2. READ — Menampilkan Data

Menampilkan seluruh isi tabel induk mahasiswa menggunakan perintah `SELECT *`.

![Hasil SELECT seluruh data mahasiswa](assets/soal2no2.png)

### 3. UPDATE — Mengubah Data

Mengubah nilai semester pada tabel KRS dengan menggunakan klausa `WHERE` berdasarkan Primary Key `id_krs` agar hanya satu baris data yang diperbarui.

![Perintah UPDATE data KRS](assets/soal2no3.png)

**3.1. Data sebelum diperbarui**

![Data KRS sebelum UPDATE](assets/beforeno3.png)

**3.2. Data setelah diperbarui**

![Data KRS setelah UPDATE](assets/afterno3.png)

### 4. DELETE — Menghapus Data

Menghapus salah satu baris data dummy pada tabel KRS menggunakan klausa `WHERE` berdasarkan Primary Key `id_krs` agar hanya data yang ditentukan yang dihapus.

![Perintah DELETE data KRS](assets/soal2no4.png)

**4.1. Data sebelum dihapus**

![Data KRS sebelum DELETE](assets/afterno3.png)

**4.2. Data setelah dihapus**

![Data KRS setelah DELETE](assets/soal2no4after.png)

