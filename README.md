# Project Inventaris Sarana dan Prasarana Laboratorium RPL

## 👥 Nama Kelompok

1. Muhamad Satria Nabil
2. Kemala Putri Oktaviani
3. Alya Nur Azizah

---

# 📌 Deskripsi Proyek

Project ini merupakan aplikasi inventaris sarana dan prasarana Laboratorium RPL berbasis desktop menggunakan C# dan SQL Server. Sistem ini digunakan untuk membantu pengelolaan data barang laboratorium, pelaporan kerusakan barang, proses persetujuan perbaikan, serta maintenance barang secara terstruktur dan terintegrasi.

---

# 🧩 Entity Relationship Diagram (ERD)

<img width="459" height="319" alt="image" src="https://github.com/user-attachments/assets/241b1114-f33e-4163-b38c-ba1475c5f17b" />


# 🔥 Trigger Database

## 🟠 Trigger 1 — `trg_laporan_kerusakan`

### 📌 Tabel Trigger

`laporan_kerusakan`

### 📌 Event Trigger

`AFTER INSERT`

### 📌 Fungsi Trigger

Trigger digunakan untuk:

* mengurangi jumlah barang baik
* menambah jumlah barang rusak

ketika petugas membuat laporan kerusakan.

---

### 📌 Skenario Trigger

#### Sebelum

| Barang | Total | Jumlah Baik | Jumlah Rusak |
| ------ | ----- | ----------- | ------------ |
| Laptop | 5     | 5           | 0            |

---

#### Petugas Input

```text
jumlah_rusak = 1
```

---

#### Setelah Trigger Berjalan

| Barang | Total | Jumlah Baik | Jumlah Rusak |
| ------ | ----- | ----------- | ------------ |
| Laptop | 5     | 4           | 1            |

---

### 📌 Trigger Bekerja Ketika

* petugas membuat laporan kerusakan
* data berhasil masuk ke tabel `laporan_kerusakan`

---

# 🟣 Trigger 2 — `trg_maintenance_selesai`

### 📌 Tabel Trigger

`maintenance`

### 📌 Event Trigger

`AFTER UPDATE`

### 📌 Fungsi Trigger

Trigger digunakan untuk:

* menambah jumlah barang baik
* mengurangi jumlah barang rusak

ketika maintenance selesai.

---

### 📌 Skenario Trigger

#### Sebelum

| Barang | Total | Jumlah Baik | Jumlah Rusak |
| ------ | ----- | ----------- | ------------ |
| Laptop | 5     | 4           | 1            |

---

#### Maintenance Selesai

```text
status = selesai
```

---

#### Setelah Trigger Berjalan

| Barang | Total | Jumlah Baik | Jumlah Rusak |
| ------ | ----- | ----------- | ------------ |
| Laptop | 5     | 5           | 0            |

---

### 📌 Trigger Bekerja Ketika

* status maintenance diubah menjadi `selesai`
* data maintenance berhasil diupdate

---

# ⚙️ Fitur Sistem

## 👤 Super Admin

* Mengelola user
* Melakukan persetujuan
* Melihat laporan

## 🧑‍💼 Admin

* Mengelola laboratorium
* Mengelola barang
* Melakukan persetujuan
* Melihat laporan

## 👷 Petugas

* Melihat data barang
* Melakukan pengecekan barang
* Membuat laporan kerusakan
* Melakukan maintenance

---

# 🔄 Alur Sistem

1. Admin menginput data laboratorium
2. Admin menginput data barang berdasarkan laboratorium
3. Petugas melakukan pengecekan barang
4. Jika terdapat kerusakan:

   * petugas membuat laporan kerusakan
5. Trigger otomatis:

   * mengurangi jumlah barang baik
   * menambah jumlah barang rusak
6. Admin dan Super Admin melakukan persetujuan
7. Jika status_final = disetujui:

   * maintenance dapat dilakukan
8. Petugas melakukan maintenance
9. Saat maintenance selesai:

   * trigger otomatis mengembalikan jumlah barang baik
   * mengurangi jumlah barang rusak

---

# 🛠️ Teknologi yang Digunakan

* C#
* SQL Server
* Windows Forms
* Draw.io

---

# ✅ Kesimpulan

Sistem inventaris ini dibuat untuk membantu pengelolaan sarana dan prasarana laboratorium secara lebih terstruktur, efektif, dan terintegrasi mulai dari pendataan barang, pelaporan kerusakan, proses persetujuan, hingga maintenance barang.
