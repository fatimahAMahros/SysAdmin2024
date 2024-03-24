# Instalasi Bind9
Untuk dokumentasi dari bind9 dapat diakses melalui [Bind9 - Debian Wiki](https://wiki.debian.org/Bind9).

Berikut langkah-langkah instalasi dan konfigurasi dari bind9

![intall nid9 beserta dnsutils dan dokumentasinya](../assets/install-bind9.png)

![](../assets/cd-etc-bind.png)

![masuk kek nano editor file conf](../assets/nano-named.conf.png)

![](../assets/nano-named.conf-edit.png)

![masuk ke nano editor conf.options](../assets/nano-named.conf.options.png)

![](../assets/nano-named.conf.options-edit-1.png)

![](../assets/nano-named.conf.options-edit-2.png)

![masuk ke nano editor conf.local](../assets/nano-named.conf.local.png)

![](../assets/nano-named.conf.local-edit-1.png)

![](../assets/nano-named.conf.local-edit-2.png)

`cd /var/lib/bind`
`sudo nano db.kelompok1.local`

![masuk ke nano editor file db.kelompok1.local](../assets/nano-db.kelompok1.local.png)

`sudo nano db.kelompok1.local.inv`

![masuk ke nano editor file db.kelompok1.local.invers](../assets/nano-db.kelompok1.local.inv.png)

`sudo nano /etc/resolv.conf`

![masuk ke nano editor resolv.cof](../assets/nano-etc-resolv-conf.png)

![cek konfigurasi](../assets/checkconf-named.conf.png)

![cek zone local](../assets/checkzone-db.kelompok1.local.png)

![cek zone local invers](../assets/checkzone-db.kelompok1.local.inv.png)

![systemctl restart](../assets/systemctl-restart.png)

![systemctl status](../assets/systemctl-status.png)

![dig kelompok1.local](../assets/dig-kelompok1.local.png)

![](../assets/dig-kelompok1.local-result.png)

![dig -x 192.168.1.10](../assets/dig--x-192.168.1.10.png)

![](../assets/dig--x-192.168.1.10-result.png)

![nslookup ns](../assets/nslookup-ns.png)

![](../assets/nslookup-ns-result.png)