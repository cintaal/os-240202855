# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `Cinta Alghumaidatul Affaf`
**NIM**: `240202855`
**Modul yang Dikerjakan**:
`Modul 1 – System Call dan Instrumentasi Kernel`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 1 – System Call dan Instrumentasi Kernel**:
  Menambahkan dua system call baru pada kernel xv6, yaitu getpinfo() untuk melihat informasi proses yang sedang aktif (PID, ukuran memori, dan nama proses), serta getReadCount() untuk menghitung berapa kali fungsi read() dipanggil sejak sistem di-boot.
---

## 🛠️ Rincian Implementasi

### Contoh untuk Modul 1:

* Menambahkan struktur struct pinfo di file proc.h untuk menyimpan data proses
* Menambahkan variabel global readcount di sysproc.c untuk menghitung jumlah pemanggilan read()
* Mengedit syscall.h untuk menambahkan nomor system call baru
* Mendaftarkan syscall baru di syscall.c
* Menambahkan deklarasi syscall di user.h dan usys.S
* Mengimplementasikan fungsi sys_getpinfo dan sys_getreadcount di sysproc.c
* Menambahkan counter pada fungsi sys_read di sysfile.c
* Membuat dua program uji: ptest.c untuk getpinfo() dan rtest.c untuk getReadCount()
* Menambahkan program uji ke dalam Makefile
---

## ✅ Uji Fungsionalitas

* ptest: menguji apakah getpinfo() menampilkan proses yang aktif
* rtest: menguji apakah getreadcount() mencatat jumlah pemanggilan read()

---

## 📷 Hasil Uji

### 📍Output `ptest`:

```
PID	MEM	NAME
1	4096	init
2	2048	sh
3	2048	ptest

```

### 📍 Contoh Output `shmtest`:

```
Child reads: A
Parent reads: B
```

### 📍 Contoh Output `chmodtest`:

```
Write blocked as expected
```

Jika ada screenshot:

<img width="628" height="679" alt="Screenshot 2025-07-30 111725" src="https://github.com/user-attachments/assets/b3007a28-d171-4746-a64b-8d3a8ea3ae11" />



## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* Salah implementasi `page fault` menyebabkan panic
* Salah memetakan alamat shared memory ke USERTOP
* Proses biasa bisa akses audit log (belum ada validasi PID)

---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

