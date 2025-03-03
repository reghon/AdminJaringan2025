## ADMINISTRASI JARINGAN

### PERTEMUAN 2 (REVIEW OS)

**Dosen Pengampu:**  
Dr. Ferry Astika Saputra St, M.Sc

**Dibuat oleh:**  
Muhammad Raihan Ghani  
3123600027  
Teknik Informatika D4 A  

---
# Sistem Berkas (Filesystem)

Sistem berkas adalah cara untuk merepresentasikan dan mengorganisasi sumber daya penyimpanan dalam sistem. Sistem berkas terdiri dari empat komponen utama:

1. **Namespace** – Cara menamai dan mengorganisasi objek dalam hierarki.
2. **API** – Sekumpulan sistem panggilan (system calls) untuk menavigasi dan memanipulasi objek.
3. **Model Keamanan** – Skema untuk melindungi, menyembunyikan, dan membagikan objek dalam sistem.
4. **Implementasi** – Perangkat lunak yang menghubungkan model logis dengan perangkat keras.

## Jenis Sistem Berkas
Sistem berkas berbasis disk yang umum digunakan meliputi:
- **ext4**, **XFS**, dan **UFS** (digunakan di Unix/Linux)
- **ZFS** (Oracle) dan **Btrfs**
- **VxFS** (Veritas) dan **JFS** (IBM)

Selain itu, terdapat sistem berkas asing seperti **FAT** dan **NTFS** (digunakan di Windows) serta **ISO 9660** (digunakan oleh CD/DVD).

## Pathname (Jalur Berkas)
Pathname adalah string yang menggambarkan lokasi berkas dalam hierarki sistem berkas. Terdapat dua jenis pathname:
- **Jalur Absolut**: Menunjukkan lokasi lengkap, misalnya `/home/username/file.txt`
- **Jalur Relatif**: Menunjukkan lokasi relatif terhadap direktori saat ini, misalnya `./file.txt`

## Mounting dan Unmounting Sistem Berkas
Sistem berkas dapat dipasang (**mount**) ke dalam pohon sistem berkas utama dengan perintah:
```bash
mount /dev/sdb1 /mnt
```
Untuk melepas (**unmount**), gunakan:
```bash
umount /mnt
```

## Organisasi Pohon Berkas Unix/Linux
Beberapa direktori utama dalam sistem berkas UNIX/Linux:
- `/boot` → Menyimpan kernel OS.
- `/etc` → Berisi berkas konfigurasi sistem.
- `/bin` dan `/sbin` → Menyimpan utilitas penting.
- `/dev` → Direktori virtual untuk perangkat sistem.
- `/usr` → Menyimpan program standar, pustaka, dan dokumentasi.
- `/var` → Berisi log, spool, dan data yang terus berubah.

## Jenis Berkas dalam UNIX/Linux
1. **Regular files** → Berkas teks, data, atau program.
2. **Directories** → Berisi referensi ke berkas lain.
3. **Character device files** → Komunikasi berbasis karakter dengan perangkat keras.
4. **Block device files** → Komunikasi berbasis blok dengan perangkat penyimpanan.
5. **Local domain sockets** → Komunikasi antarproses dalam satu sistem.
6. **Named pipes (FIFOs)** → Komunikasi antarproses dalam host yang sama.
7. **Symbolic links** → Tautan fleksibel ke berkas atau direktori lain.

# Bit Izin Akses (Permission Bits)
Setiap berkas memiliki izin akses yang dibagi menjadi tiga kelompok:
- **Pemilik (user - u)**
- **Grup (group - g)**
- **Orang lain (others - o)**

Setiap kelompok terdiri dari tiga bit:
- **r** (read) → Membaca isi berkas atau melihat daftar isi direktori.
- **w** (write) → Memodifikasi berkas atau menambah/menghapus berkas dalam direktori.
- **x** (execute) → Menjalankan berkas atau mengakses direktori.

## Representasi Oktal
Setiap tiga bit izin akses dapat direpresentasikan dalam angka oktal:
- **Pemilik**: `400` (r--), `200` (-w-), `100` (--x)
- **Grup**: `040` (r--), `020` (-w-), `010` (--x)
- **Orang lain**: `004` (r--), `002` (-w-), `001` (--x)

Contoh:
```bash
chmod 644 file.txt  # Memberikan izin rw-r--r--
```

## Perintah Pengelolaan Izin Akses
- **Melihat izin akses:**
  ```bash
  ls -l
  ```
- **Mengubah izin akses dengan `chmod`:**
  ```bash
  chmod u+w file.txt  # Menambah izin tulis ke pemilik
  chmod 755 script.sh # rwxr-xr-x
  ```
- **Mengubah kepemilikan dengan `chown`:**
  ```bash
  chown user:group file.txt
  ```
- **Mengubah grup dengan `chgrp`:**
  ```bash
  chgrp groupname file.txt
  ```

## Shebang (`#!`)
Dalam skrip, shebang (`#!`) digunakan untuk menentukan interpreter:
```bash
#!/bin/bash  # Skrip Bash
#!/usr/bin/python3  # Skrip Python
```
Tanpa shebang, skrip akan dijalankan oleh shell default.

## Access Control Lists (ACLs)
ACLs memungkinkan pengaturan izin yang lebih fleksibel dibanding sistem UNIX tradisional.
- **Melihat ACL:**
  ```bash
  getfacl file.txt
  ```
- **Menambahkan izin ACL:**
  ```bash
  setfacl -m u:username:rw file.txt
  ```

## Kesimpulan
Sistem berkas merupakan bagian fundamental dari sistem operasi. Pemahaman tentang struktur direktori, izin akses, dan manajemen sistem berkas akan membantu dalam administrasi dan keamanan sistem.
