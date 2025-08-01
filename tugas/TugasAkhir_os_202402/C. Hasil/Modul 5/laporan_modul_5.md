# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Nama Lengkap>`
**NIM**: `<Nomor Induk Mahasiswa>`
**Modul yang Dikerjakan**:
`(Contoh: Modul 1 – System Call dan Instrumentasi Kernel)`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 5 – Audit dan Keamanan Sistem**:
 Menambahkan fitur audit pada kernel xv6 yang mencatat setiap pemanggilan system call, serta menyediakan syscall get_audit_log() yang hanya dapat diakses oleh proses dengan PID 1. Audit ini mencatat PID pemanggil, nomor system call, dan waktu (tick) saat dipanggil.
---

## 🛠️ Rincian Implementasi

### Contoh untuk Modul 1:

* Menambahkan struktur audit_entry dan buffer audit_log[] di syscall.c
* Mengimplementasikan pencatatan log dalam fungsi syscall()
* Menambahkan system call get_audit_log():
* Nomor syscall ditambahkan di syscall.h
* Deklarasi di user.h
* Entri syscall ditambahkan ke usys.S
* Registrasi syscall dilakukan di syscall.c
* Implementasi syscall ditulis di sysproc.c dan dibatasi hanya untuk proses dengan PID 1
* Membuat program penguji audit.c untuk mencetak log
* Menambahkan _audit ke dalam Makefile

---

## ✅ Uji Fungsionalitas

audit: program untuk mengambil dan mencetak isi log system call. Diuji dalam dua kondisi:

* Sebagai proses biasa → Akses ditolak
* Sebagai proses PID 1 (init) → Berhasil menampilkan log audit

---

## 📷 Hasil Uji

### 📍Output `jika dijalankan oleh PID 1`:

```
=== Audit Log ===
[0] PID=1 SYSCALL=7 TICK=4
[1] PID=1 SYSCALL=15 TICK=7
[2] PID=1 SYSCALL=17 TICK=7
...

```

Jika ada screenshot:

```
<img width="1579" height="1057" alt="Screenshot 2025-07-31 143803" src="https://github.com/user-attachments/assets/bd51a4b6-e46c-4b75-965c-6ca03a1eea4d" />

```
<img width="958" height="1066" alt="Screenshot 2025-07-31 143819" src="https://github.com/user-attachments/assets/533d5ef7-07a0-4dbd-9ece-0a2dc9569a16" />

---

## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* Awalnya lupa menambahkan validasi PID dalam sys_get_audit_log(), sehingga semua proses bisa membaca log
* Salah dalam penggunaan argptr() menyebabkan kernel panic ketika audit.c mencoba mengakses buffer log
* audit_index tidak dijaga dengan batas maksimal, menyebabkan potensi overflow
* Program audit.c sempat gagal kompilasi karena deklarasi struct audit_entry tidak sama dengan versi kernel → disamakan di file user-level
* Lupa mendaftarkan audit.c di Makefile, menyebabkan program tidak muncul di shell xv6
---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

