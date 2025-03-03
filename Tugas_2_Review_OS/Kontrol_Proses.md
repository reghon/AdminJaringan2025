## ADMINISTRASI JARINGAN

### PERTEMUAN 1 (REVIEW)

**Dosen Pengampu:**  
Dr. Ferry Astika Saputra St, M.Sc

**Dibuat oleh:**  
Muhammad Raihan Ghani  
3123600027  
Teknik Informatika D4 A  

---

# Kontrol Proses

## 1. Konsep Dasar Proses di Linux
- Proses terdiri dari **ruang alamat** (kode, data, stack) dan **struktur data kernel** (status, prioritas, sumber daya).
- Setiap proses memiliki **PID (Process ID)** dan **PPID (Parent Process ID)** untuk identifikasi serta **UID/EUID** untuk kontrol akses.
- **Thread** berbagi ruang alamat dan sumber daya dengan proses induknya, memungkinkan eksekusi paralel yang lebih efisien.
- **Fork dan Clone** digunakan untuk membuat proses baru, sementara **init/systemd (PID 1)** mengelola proses saat sistem berjalan.
- **Namespace** digunakan dalam container untuk mengisolasi proses dengan PID yang sama dalam lingkungan berbeda.

## 2. Manajemen Sinyal Proses
Sinyal digunakan untuk komunikasi antar-proses dan notifikasi. Beberapa sinyal utama:
- **SIGKILL (9)** → Menghentikan proses secara paksa, tidak dapat ditangkap atau diblokir.
- **SIGINT (2)** → Dikirim saat pengguna menekan `Ctrl + C`, meminta proses berhenti.
- **SIGTERM (15)** → Meminta proses berhenti secara normal agar dapat membersihkan sumber daya.
- **SIGHUP (1)** → Menangani pemutusan terminal atau memuat ulang konfigurasi daemon.
- **SIGQUIT (3)** → Mirip SIGTERM tetapi menghasilkan **core dump** jika tidak ditangani.

## 3. Perintah untuk Mengontrol Proses
- **kill -9 <PID>** → Menghentikan proses berdasarkan PID dengan SIGKILL.
- **killall <nama_proses>** → Menghentikan semua proses dengan nama tertentu.
- **pkill <kriteria>** → Menghentikan proses berdasarkan nama, pengguna, atau pola lain.

## 4. Monitoring dan Pemantauan Proses
- **ps aux** → Menampilkan daftar semua proses dengan detail.
- **top** → Menampilkan proses real-time dengan informasi penggunaan CPU dan memori.
- **htop** → Versi lebih interaktif dari `top` dengan navigasi lebih baik.
- **pgrep <nama_proses>** → Mendapatkan PID proses berdasarkan nama.
- **pidof <path_proses>** → Mendapatkan PID dari program tertentu.

## 5. Mengatur Prioritas Proses
- **nice -n <nilai> <command>** → Menjalankan proses dengan prioritas tertentu (`-20` hingga `+19`).
- **renice -n <nilai> -p <PID>** → Mengubah prioritas proses yang sedang berjalan.

## 6. Melihat Informasi dan Aktivitas Proses
- **/proc/<PID>/** → Direktori virtual berisi informasi tentang proses tertentu.
- **strace -p <PID>** → Melacak sistem panggilan (syscall) dari proses (Linux).
- **truss -p <PID>** → Alternatif `strace` untuk FreeBSD.
- **lsof -p <PID>** → Melihat file yang sedang digunakan oleh proses.

## 7. Menjadwalkan Proses (Scheduled Tasks)
### **Cron Job** untuk tugas terjadwal berbasis waktu:
- Format: `* * * * * command` *(menit, jam, hari, bulan, hari dalam seminggu)*
- Contoh: `30 2 * * * /usr/bin/python3 /path/to/script.py` → Menjalankan skrip setiap pukul 02:30.

### **Systemd Timer** untuk tugas yang lebih fleksibel:
- `systemctl list-timers` → Melihat daftar timer yang aktif.

## 8. Penggunaan Scheduled Tasks dalam Linux
- **Mengirim email otomatis** dengan laporan sistem.
- **Membersihkan file sementara** menggunakan `find` dan `rm`.
- **Rotasi log file** untuk menghindari ukuran log yang terlalu besar.
- **Menjalankan batch jobs** untuk pemrosesan data dalam jumlah besar.
- **Backup otomatis** menggunakan `rsync`.
