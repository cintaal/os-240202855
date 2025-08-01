# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Cinta Alghumaidatul Affaf>`
**NIM**: `<240202855>`
**Modul yang Dikerjakan**:
`( Modul 2 – Penjadwalan CPU Lanjutan (Priority Scheduling Non-Preemptive)
)`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 2 – Penjadwalan CPU Lanjutan (Priority Scheduling Non-Preemptive)**:
  Mengubah algoritma penjadwalan default Round-Robin pada xv6 menjadi Non-Preemptive Priority Scheduling. Penjadwalan ini memastikan bahwa proses RUNNABLE dengan prioritas tertinggi (angka prioritas paling kecil) akan dieksekusi terlebih dahulu, dan tidak akan digantikan oleh proses lain hingga selesai atau menunggu.
---

## 🛠️ Rincian Implementasi

### Modul 2:

* Menambahkan field priority ke dalam struct proc di file proc.h
* Inisialisasi nilai default priority di fungsi allocproc() pada proc.c
* Membuat syscall set_priority(int):
* Menambahkan nomor syscall di syscall.h
* Menambahkan deklarasi syscall di user.h dan entri di usys.S
* Registrasi syscall di syscall.c
* Implementasi fungsi syscall di sysproc.c
* Memodifikasi fungsi scheduler() di proc.c agar memilih proses RUNNABLE dengan prioritas tertinggi
* Membuat program uji ptest.c untuk menguji urutan eksekusi proses berdasarkan prioritas
* Menambahkan ptest ke daftar program pada Makefile

---

## ✅ Uji Fungsionalitas

* ptest: Menguji urutan eksekusi proses berdasarkan nilai prioritas (semakin kecil angka → prioritas lebih tinggi)

---

## 📷 Hasil Uji

### 📍Output `ptest`:

```
Child 1 selesai
Child 2 selesai
Parent selesai

```
<img width="1055" height="495" alt="Screenshot 2025-07-30 121839" src="https://github.com/user-attachments/assets/99a6f849-7ffe-4131-b755-28c0ec7acaa6" />

---

## ⚠️ Kendala yang Dihadapi

* Mengalami error saat menambahkan field baru di struct seperti priority, karena salah penulisan atau lupa menyertakan pointer (*) dalam deklarasi fungsi
* Pernah salah menambahkan entri syscall atau lupa registrasi, menyebabkan undefined reference saat build
* Kesulitan memahami relasi antara syscall dan devsw[] saat mencoba menautkan fungsi read
* Sempat bingung menentukan lokasi yang tepat untuk meletakkan fungsi extern agar dikenali oleh kernel
* Error linker muncul walaupun file .c sudah ditulis, karena belum ditautkan dengan benar di Makefile atau header file belum lengkap
---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum


---

