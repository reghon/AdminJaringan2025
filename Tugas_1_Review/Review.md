## ADMINISTRASI JARINGAN

### PERTEMUAN 1 (REVIEW)

**Dosen Pengampu:**  
Dr. Ferry Astika Saputra St, M.Sc

**Dibuat oleh:**  
Muhammad Raihan Ghani  
3123600027  
Teknik Informatika D4 A  

---

## 1. Analisa File "http.cap" dengan Wireshark

### a) Versi HTTP
Versi HTTP yang digunakan pada file ini adalah **versi 1.1**

### b) Client & Server IP Address
- **Client IP Address:** 145.254.160.237  
- **Server IP Address:** 65.208.228.223  

### c) Waktu Client Mengirimkan HTTP Request dan Server Mengirim Response Beserta Durasinya
- **Waktu Client mengirimkan HTTP request:** 0.911310 (nomor 4)
- **Waktu Server mengirimkan response:** 4.846969 (nomor 38)
- **Durasi:** 4.846969 - 0.911310 = **3.935659 detik**

---

## 2. Tipe – Tipe Pengiriman Data

### a. Node to Node (Data Link Layer)
Komunikasi dari **node ke node** berfungsi untuk mengirimkan frame dari satu perangkat jaringan ke perangkat lainnya dalam satu jaringan fisik. Setiap node bisa berupa komputer, switch, atau router yang saling terhubung dalam jaringan lokal (LAN) atau jaringan luas (WAN).  
Protokol yang digunakan dalam komunikasi ini termasuk **Ethernet, Wi-Fi, dan PPP**. Dalam tahap ini, **MAC Address** digunakan untuk mengidentifikasi perangkat dalam jaringan yang sama. Proses seperti **error detection** serta **frame synchronization** juga dilakukan untuk memastikan data sampai dengan benar ke node tujuan.

### b. Host to Host (Network Layer)
Komunikasi dari **host ke host** bertugas mengatur **pengalamatan dan routing** paket data agar sampai dari satu perangkat ke perangkat lain dalam jaringan yang lebih luas, seperti **internet**. Protokol utama yang digunakan dalam lapisan ini adalah **Internet Protocol (IP)**, yang memungkinkan setiap perangkat memiliki **IP Address** sebagai identifikator di dalam jaringan.  
**Router** berperan penting dalam komunikasi ini dengan meneruskan paket dari satu jaringan ke jaringan lain berdasarkan **alamat IP**. Dengan mekanisme ini, data dapat dikirimkan antara dua perangkat yang terpisah secara geografis tanpa harus berada dalam jaringan fisik yang sama.

### c. Process to Process (Transport Layer)
Pengiriman data dari **proses ke proses** memastikan bahwa data yang dikirim oleh suatu aplikasi di satu host dapat diterima dan diproses oleh aplikasi yang sesuai di host lain. Protokol utama yang digunakan di sini adalah **TCP dan UDP**.  
- **TCP** memastikan komunikasi tersampaikan dengan mekanisme error checking dan retransmission.
- **UDP** lebih cepat tetapi tidak menjamin pengiriman data dengan benar.

---

## 3. Tahapan Komunikasi dalam TCP

### a. Establishing Connection
Sebelum data dikirim, TCP harus membentuk koneksi antar pengirim dan penerima menggunakan mekanisme **Three-Way Handshake**:
1. **SYN (Synchronize)**: Pengirim (client) mengirimkan paket **SYN** ke penerima (server) untuk memulai komunikasi dan menentukan nomor urut awal.
2. **SYN-ACK (Synchronize-Acknowledge)**: Penerima merespon dengan paket **SYN-ACK**, yang berisi nomor urutnya sendiri serta acknowledgment terhadap SYN pengirim.
3. **ACK (Acknowledge)**: Pengirim mengirimkan paket **ACK** terakhir, mengonfirmasi bahwa koneksi telah berhasil dibentuk.

### b. Data Transfer
Setelah koneksi terbentuk, pengiriman data mulai terjadi antara pengirim dan penerima. Beberapa mekanisme utamanya meliputi:
1. **Segmentasi dan Sequencing**: Data dipecah menjadi segmen-segmen kecil dan masing-masing diberi nomor urut.
2. **Error Checking dan Acknowledgment**: Penerima mengirim **ACK** untuk setiap segmen yang diterima dengan benar. Jika segmen hilang atau rusak, pengirim akan mengirim ulang.
3. **Flow Control**: Menggunakan mekanisme seperti **Sliding Window** untuk menyesuaikan jumlah data yang dapat dikirim sebelum menerima **ACK**, guna menghindari kemacetan.
4. **Congestion Control**: TCP menyesuaikan kecepatan pengiriman data berdasarkan kondisi jaringan untuk mencegah kepadatan lalu lintas.

### c. Connection Termination
Setelah semua data dikirim dan tidak ada komunikasi yang diperlukan, TCP akan menutup koneksi menggunakan **Four-Way Handshake**:
1. **FIN (Finish)**: Pengirim mengirim paket **FIN** untuk meminta pemutusan koneksi.
2. **ACK (Acknowledge)**: Penerima mengonfirmasi permintaan dengan mengirim **ACK**.
3. **FIN (Finish)**: Penerima mengirim **FIN** ketika sudah siap menutup koneksi.
4. **ACK (Acknowledge)**: Pengirim mengirim **ACK** terakhir, dan setelah waktu tertentu koneksi ditutup sepenuhnya.

---
