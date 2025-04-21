# DNS Internal

### [1] Install BIND

```bash
apt install bind9 bind9utils
```

![gambar.png](images/gambar.png)

### [2] Konfigurasi BIND

- named.conf

```bash
cd /etc/bind
nano named.conf
```

![gambar.png](images/gambar%201.png)

Tambahkan **“/etc/bind/named.conf.internal-zones”**

- named.conf.options

```bash
nano named.conf.options
```

Tambahkan baris berikut

```bash
acl internal-network {
        [your-netowrk-address]/24;
};
```

![gambar.png](images/gambar%202.png)

- named.conf.internal-zones

```bash
nano named.conf.internal-zones
```

![gambar.png](images/gambar%203.png)

### [3] Konfigurasi zone files

- ani.world.lan

```bash
nano ani.world.lan
```

![gambar.png](images/gambar%204.png)

- 1.168.192.db

```bash
nano 1.168.192.db
```

![gambar.png](images/gambar%205.png)

### [4] Testing

- Restart BIND untuk mengaktifkan konfigurasi

```bash
systemctl restart named
```

- Ganti DNS ke DNS sendiri

```bash
nano /etc/resolv.conf
```

![gambar.png](images/gambar%206.png)

- Verifikasi DNS dan IP Address

```bash
dig dlp.ani.world
```

![gambar.png](images/gambar%207.png)

```bash
dig -x 192.168.1.38
```

![gambar.png](images/gambar%208.png)
