# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Cinta Alghumaidatul Affaf>`
**NIM**: `<240202855>`
**Modul yang Dikerjakan**:
`(Manajemen Memori Tingkat Lanjut)`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 3 – Manajemen Memori Tingkat Lanjut**:
  Mengimplementasikan Copy-on-Write Fork agar proses fork() efisien dalam penggunaan memori, dan Shared Memory ala System V menggunakan syscall shmget() dan shmrelease().
---

## 🛠️ Rincian Implementasi

### modul 3:

* Menambahkan array ref_count[] di vm.c sebagai reference counter untuk halaman fisik
* Menambahkan flag PTE_COW di mmu.h untuk menandai halaman copy-on-write
* Membuat fungsi cowuvm() sebagai pengganti copyuvm() saat fork
* Menangani page fault di trap.c untuk membuat salinan halaman saat proses menulis ke memori COW
* Memodifikasi fork() di proc.c agar menggunakan cowuvm()
* Menambahkan struktur shmtab[] di vm.c untuk manajemen shared memory
* Membuat syscall baru shmget(int key) dan shmrelease(int key)
* Mendaftarkan syscall di syscall.c, usys.S, syscall.h, user.h, dan sysproc.c
---

## ✅ Uji Fungsionalitas

* cowtest: untuk menguji mekanisme Copy-on-Write pada fork

* shmtest: untuk menguji alokasi dan akses memori bersama

---

## 📷 Hasil Uji

### 📍 Contoh Output `cowtest`:

```
Child sees: Y  
Parent sees: X
```
### 📍 Contoh Output `shmtest`:

```
Child reads: A
Parent reads: B
```

```
![mod 3](https://github.com/user-attachments/assets/ac9a77f1-345f-4d09-80d2-ad954cd569e8)
---


---

## ⚠️ Kendala yang Dihadapi
---

* Error field read dan write di file.h karena salah deklarasi pointer function
✅ Fix: ubah jadi int (*read)(...)
* Fork gagal setelah CoW karena lupa mapping ulang dengan mappages() saat page fault
* Panic saat shmtest jalan karena lupa nambah incref() di shmget()
* shmrelease() tidak melepas halaman karena refcount tidak berkurang (double mapping)
---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

