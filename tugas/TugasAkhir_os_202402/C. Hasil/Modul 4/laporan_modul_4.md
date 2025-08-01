# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Cinta Alghumaidatul A>`
**NIM**: `<240202855>`
**Modul yang Dikerjakan**:
`(Subsistem Kernel Alternatif – chmod() & /dev/random)`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 4 – Subsistem Kernel Alternatif**:
* Menambahkan system call baru chmod(path, mode) untuk mengatur mode file (read-only / read-write).
* Menambahkan device /dev/random yang menghasilkan byte acak ketika dibaca.
---

## 🛠️ Rincian Implementasi

### Modul 4:

* Menambahkan field mode ke struct inode di fs.h (read-write: 0, read-only: 1)
* Implementasi syscall chmod() di sysfile.c
* Registrasi syscall di syscall.h, syscall.c, user.h, usys.S
* Penambahan validasi di filewrite() agar gagal jika inode read-only
* Membuat file random.c untuk device /dev/random
* Registrasi device ke devsw[] di file.c, index 3
* Tambahan node device /dev/random via mknod() di init.c
* Program uji: chmodtest.c dan randomtest.c

---

## ✅ Uji Fungsionalitas

* chmodtest: Menguji sistem proteksi tulis terhadap file yang diubah ke mode read-only

* randomtest: Menguji pembacaan byte acak dari pseudo-device /dev/random
* 
---

## 📷 Hasil Uji

hasil uji tidak ada karena outputnya tidak ada sperti di screenshoot

---
<img width="988" height="427" alt="Screenshot 2025-07-30 192138" src="https://github.com/user-attachments/assets/98c817e4-e3ab-4081-b2fb-6ee25fd34059" />

---

## ⚠️ Kendala yang Dihadapi

* (1) Lupa menambahkan field mode di struct inode, menyebabkan nilai default selalu 0
* (2) Salah urutan iupdate() dan iunlock() menyebabkan inode tidak tersimpan
* (3) Device /dev/random awalnya gagal dibuka karena lupa mknod() di init.c
* (4) randomread() mengakses memory invalid karena tidak memperhatikan batas array dst[n]

---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

