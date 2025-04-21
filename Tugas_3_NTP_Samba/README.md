
# NTP dan Samba

## NTP

1. Install NTP

```bash
apt install ntp
```

![gambar.png](images/gambar.png)

1. Lihat pool address server ntp indonesia di [https://www.ntppool.org/en/zone/id](https://www.ntppool.org/en/zone/id)

![gambar.png](images/gambar%201.png)

1. Pindah ke direktori **/etc/ntpsec** dan edit konfigurasi file ntp.conf

```bash
cd /etc/ntpsec
nano ntp.conf
```

![gambar.png](images/gambar%202.png)

![gambar.png](images/gambar%203.png)

Berikan comment untuk default pool adress, lalu tambahkan pool address indonesia

```bash
server 0.id.pool.ntp.org
server 1.id.pool.ntp.org
server 2.id.pool.ntp.org
server 3.id.pool.ntp.org
```

1. Restart service ntp dan cek statusnya 

```bash
systemctl restart ntp
systemctl status ntp
```

![gambar.png](images/gambar%204.png)

1. Periksa hasil konfigurasi ntp

```bash
ntpq -p
```

![gambar.png](images/gambar%205.png)

Dengan ini, maka ntp sudah sesuai dengan waktu di Indonesia

## Samba

1. Install Samba Server

```bash
ntpq -p
```

![gambar.png](images/gambar%206.png)

1. Buat direktori baru dengan nama **share** pada direktori /**home** dan ubah mode aksesnya untuk mengizinkan semua akses dengan perintah chmod

```bash
cd home
mkdir share
chmod 777 share
```

![gambar.png](images/gambar%207.png)

Setelah mengizinkan akses, cek kembali izin akses nya

```bash
ls -l
```

![gambar.png](images/gambar%208.png)

1. Cek IP Address yang digunakan debian

```bash
ip a
```

![gambar.png](images/gambar%209.png)

1. Masuk ke direktori **/etc/samba** dan konfgiurasi file **smb.conf**

```bash
cd /etc/samba
nano smb.conf
```

![gambar.png](images/gambar%2010.png)

Tambahkan **unix charset = UTF-8,** uncomment pada bagian **interfaces** dan tambahkan IP network dari IP address pada server atau IP yang digunakan pada debian

![gambar.png](images/gambar%2011.png)

Tambahkan definisi untuk **share** folder seperti gambar diatas

1. Restart samba service

```bash
systemctl restart smbd
systemctl status smbd
```

![gambar.png](images/gambar%2012.png)

1. Connect ke **share** folder dari PC Client, sya menggunakan windows

![gambar.png](images/gambar%2013.png)

1. Share folder pada samba server sudah dapat diakses dari client

![gambar.png](images/gambar%2014.png)

1. Testing dengan menambahkan file melalui server, dan melihat di client

![gambar.png](images/gambar%2015.png)

![gambar.png](images/gambar%2016.png)
