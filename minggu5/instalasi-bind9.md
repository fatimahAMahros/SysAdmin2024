# Instalasi Bind9
Untuk dokumentasi dari bind9 dapat diakses melalui [Bind9 - Debian Wiki](https://wiki.debian.org/Bind9).

Berikut langkah-langkah instalasi dan konfigurasi dari bind9

### Install Bind9 beserta dokumentasinya dan dnsutils
![intall nid9 beserta dnsutils dan dokumentasinya](../assets/install-bind9.png)

### Konfigurasi file named
masuk ke direktori /etc/bind
![](../assets/cd-etc-bind.png)

Edit file named.conf menggunakan nano editor.
![masuk ke nano editor file conf](../assets/sudo-nano-named.conf.png)

![](../assets/sudo-nano-named.conf-edit.png)

Edit file named.conf.options menggunakan nano editor.
![masuk ke nano editor conf.options](../assets/sudo-nano-named.conf.options.png)

![](../assets/sudo-nano-named.conf.options-edit1.png)

![](../assets/sudo-nano-named.conf.options-edit2.png)

![](../assets/sudo-nano-named.conf.options-edit3.png)

Edit file named.conf.local menggunakan nano editor.
![masuk ke nano editor conf.local](../assets/sudo-nano-named.conf.local.png)

Buat 2 zone, zone pertama bernama kelompok1.local dan yang kedua 2.0.10.in-addr.arpa.
![](../assets/sudo-nano-named.conf.local-edit1.png)

![](../assets/sudo-nano-named.conf.local-edit2.png)

### Konfigurasi file db.kelompok
Masuk ke direktori /var/lib/bind untuk mengakses file db.kelompok1

![masuk ke direktori /var/lib/bind](../assets/cd-var-lib-bind.png)

Konfigurasikan file db.kelompok1.local. Isi serial dengan tanggal saat ini.

![masuk ke nano editor file db.kelompok1.local](../assets/sudo-nano-db.kelompok1.local.png)

![](../assets/sudo-nano-db.kelompok1.local-edit.png)

Konfigurasikan file db.kelompok1.local.inv. Isi serial dengan tanggal saat ini.

![masuk ke nano editor file db.kelompok1.local.invers](../assets/sudo-nano-db.kelompok1.local.inv.png)

![](../assets/sudo-nano-db.kelompok1.local.inv-edit.png)

### Konfigurasi file resolv.conf
konfigurasikan file resolv.conf yang terdapat pada direkotri /etc

![masuk ke nano editor resolv.conf](../assets/sudo-nano-etc-resolv.conf.png)

![](../assets/sudo-nano-etc-resolv.conf-edit.png)

### Mengecek hasil konfigurasi dan zone
Pada saat mengecek konfigurasi menggunakan perintah `sudo named-checkconf`, ketika sudah benar semua, tidak ada yang dikembalikan dari perintah tersebut.

![cek konfigurasi](../assets/sudo-named-checkconf-etc-bind-named.conf.png)

Sedangkan saat mengecek zone menggunakan perintah `sudo named-checkzone`, jika sudah benar maka akan muncul **OK** pada bagian akhirnya

![cek zone local](../assets/sudo-named-checkzone-kelompok1.local-db.kelompok1.local.png)

![cek zone local invers](../assets/sudo-named-checkzone-2.0.10.inaddr-arpa-db.kelompok1.local.inv.png)

### Melakukan systemctl restart dan mengecek status
Setiap kali setelah merubah file konfigurasi, lakukan restart seperti berikut.

![systemctl restart](../assets/sudo-systemctl-restart-named.png)

Jiak proses restart sudah berhasil, maka tidak akan menampilkan apapun.

![systemctl status](../assets/sudo-systemctl-status-named.png)

### Melakukan dig dan nslookup
Saat sudah benar semua konfigurasinya, kita dapat melakukan dig pada kelompok.local serta pada 10.0.2.15, dan juga dapat melakukan nslookup terhadap ns yang telah diset serta pada mail.

![dig kelompok1.local](../assets/dig-kelompok1.local.png)

![](../assets/dig-kelompok1.local-result.png)

![dig -x 192.168.1.10](../assets/dig--x-10.0.2.15.png)

![nslookup ns](../assets/nslookup-ns.png)

![](../assets/nslookup--d=MX.png)