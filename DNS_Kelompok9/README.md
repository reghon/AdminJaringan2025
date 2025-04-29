
# DNS_C306_Kelompok9
Dosen Pengampu : Dr.Derry Astika ST., M.Sc
1. 3123600012 Adrian Mendienta Tumanggor
2. 3123600027 Muhammad Raihan Ghani
3. 3123600030 Aldino Matasik

## Topologhy

![gambar.png](gambar.png)

## Konfigurasi IP

Set IP ke 192.168.9.10/24 dan gateway 192.168.9.1 seperti gambar dibawah berikut atau dapat melalui terminal

```bash
nano /etc/network/interfaces
```

![WhatsApp Image 2025-04-29 at 15.28.29_b7671696.jpg](WhatsApp_Image_2025-04-29_at_15.28.29_b7671696.jpg)

## Konfigurasi Zone Files

### [1] named.conf

```bash
nano /etc/bind/named.conf
```

![WhatsApp Image 2025-04-29 at 13.35.51_63da1ad9.jpg](WhatsApp_Image_2025-04-29_at_13.35.51_63da1ad9.jpg)

Tambahkan baris terakhir pada file ini untuk menambahkan zona internal

### [2] named.conf.options

```bash
nano /etc/bind/named.conf.options
```

![WhatsApp Image 2025-04-29 at 13.35.52_66b2c332.jpg](WhatsApp_Image_2025-04-29_at_13.35.52_66b2c332.jpg)

Ganti internal-network dengan network yang ada pada IP address kita, yaitu `192.168.9.0/24`

### [3] named.conf.internal-zones

```bash
nano /etc/bind/named.conf.internal-zones
```

![WhatsApp Image 2025-04-29 at 16.47.11_724b718e.jpg](WhatsApp_Image_2025-04-29_at_16.47.11_724b718e.jpg)

### [4] db.kelompok9.home

```bash
nano /etc/bind/db.kelompok9.home
```

![WhatsApp Image 2025-04-29 at 13.35.53_891d2228.jpg](WhatsApp_Image_2025-04-29_at_13.35.53_891d2228.jpg)

Buat file db.kelompok9.home dan buat konfigurasi seperti foto diatas

### [5] db.9.168.192

```bash
nano /etc/bind/db.9.168.192
```

![WhatsApp Image 2025-04-29 at 16.47.44_21270e18.jpg](WhatsApp_Image_2025-04-29_at_16.47.44_21270e18.jpg)

## Cek Konfigurasi

### [1] kelompok9.home

```bash
sudo named-checkzone kelompok9.home ./db.kelompok9.home
```

![WhatsApp Image 2025-04-29 at 13.35.53_d0048731.jpg](WhatsApp_Image_2025-04-29_at_13.35.53_d0048731.jpg)

Jika balasannya adalah “OK” maka file konfigurasi kelompok9.home sudah benar

### [2] db.9.168.192

```bash
sudo named-checkzone 9.168.192.in-addr.arpa ./db.9.168.192
```

![WhatsApp Image 2025-04-29 at 16.48.37_9f691094.jpg](WhatsApp_Image_2025-04-29_at_16.48.37_9f691094.jpg)

Jika balasannya adalah “OK” maka file konfigurasi [9.168.192.in-adddr.arpa](http://9.168.192.in-adddr.arpa) sudah benar

## Testing

### [1]nslookup

![WhatsApp Image 2025-04-29 at 13.35.55_9612d365.jpg](WhatsApp_Image_2025-04-29_at_13.35.55_9612d365.jpg)

### [2]Cek IP Address dengan DNS

![WhatsApp Image 2025-04-29 at 13.35.54_e2f8733b.jpg](WhatsApp_Image_2025-04-29_at_13.35.54_e2f8733b.jpg)

### [3]Cek di Browser Apache

![WhatsApp Image 2025-04-29 at 16.51.45_87b87e58.jpg](WhatsApp_Image_2025-04-29_at_16.51.45_87b87e58.jpg)

Jika semua testing diatas berhasil dilakukan, berarti konfigurasi DNS telah berhasil dilakukan.
