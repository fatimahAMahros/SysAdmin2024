# NTP Client, Apache 2, PHP-FM, Mariadb-Server, Email System, DOVECOT

## Persiapan
1. Peratma-tama kita set up dulu mail server pada konfigurasi zone pada bind
![](./assets/confi-zone-local.png)
![](./assets/config-zone-local-inv.png)
2. Pastikan untuk melakukan restart pada system named

## NTP Client
1. Lakukan instalasi paket layanan sinkronisasi waktu
![](./assets/install-sinkronisasi-waktu.png)
2. Konfigurasikan timezone ke Asia/Jakarta
![](./assets/timezone-jakarta.png)
3. Lakukann konfigurasi RTC untuk merefer ke UTC
![](./assets/config-rtc.png)
4. Aktifkan NTP client untuk sikronisasi waktu
![](./assets/activate-ntp-client.png)
5. Edit file  timesyncd.conf untuk mengarah ke NTP server terdekat untuk mendapatkan delay waktu terpendek.
![](./assets/edit-timesyncd.conf.png)
6. Restart layanan sikronisasi waktu dan cek statusnya
![](./assets/restart-status-timesyncd.png)
7. Lakukan pengecekan kesesuaian tanggal system
![](./assets/timedatectl.png)

## Apache 2 & PHP-FM
1. Lakuakn instalasi apache2
![](./assets/install-apache2.png)
2. Konfigurasikan apache2
![](./assets/config-apache2-1.png)
![](./assets/config-apache2-2.png)
![](./assets/config-apache2-3.png)
![](./assets/config-apache2-4.png)
3. Lakukan reload pada service apache2
![](./assets/reload-apache2.png)
4. Lakukan test di web browser
![](./assets/apache-test.png)
5. Install PHP 8.2
![](./assets/php8.2-install.png)
6. Cek apakah sudah terinstall beserta versinya
![](./assets/php8.2-version.png)
7. Buat file php dan jalankan untuk memeriksa apakah PHP sudah berjalan
![](./assets/php8.2-test-script.png)
8. Install PHP FM
![](./assets/phpfm-install.png)
9. Lakukan konfigurasi pada file Apache untuk PHP FM
![](./assets/phpfm-config-default-ssl.png)
![](./assets/phpfm-setenvif.png)
![](./assets/phpfm-a2enconf.png)
10. Lakukan restart pada servicenya
![](./assets/php-fm-restart.png)
11. Buat file info.php dan lakukan test pada web
![](./assets/php-info.php.png)

## Mariadb Server
1. Lakukan instalasi Mariadb
![](./assets/mariadb-install.png)
2. Ubah charset ke utf8mb4, lalu restart service mariadb
![](./assets/mariadb-config.png)
![](./assets/mariadb-restart.png)
3. Lakukan instalasi mysql
![](./assets/mysql-install.png)
![](./assets/mysql-install-2.png)
![](./assets/mysql-install-3.png)
![](./assets/mysql-install-4.png)
![](./assets/mysql-install-5.png)
![](./assets/mysql-install-6.png)
![](./assets/mysql-install-7.png)
4. Masuk ek dalam perintah mysql dan lakukan langkah-langkah berikut
![](./assets/mysql-enter1.png)
![](./assets/mysql-enter2.png)
![](./assets/mysql-enter3.png)
![](./assets/mysql-enter4.png)
![](./assets/mysql-enter5.png)
![](./assets/mysql-enter6.png)
![](./assets/mysql-enter7.png)
![](./assets/mysql-enter8.png)
![](./assets/mysql-enter9.png)
![](./assets/mysql-enter10.png)

## POSTFIX mailserver(SMTP Server)
1. Install postfix
![](./assets/postfix-install.png)
2. Pada saaat instalasi, pilih yang maunal
![](./assets/postfix-config.png)
![](./assets/postfix-config2.png)
3. Salin isi file config /usr/share/postfix/main.cf.dist ke /etc/postfix/main.cf
![](./assets/postfix-copy.png)
4. Ubah beberapa isi dari file konfigurasi file postfix-main.cf
![](./assets/postfix-main1.png)
![](./assets/postfix-main2.png)
![](./assets/postfix-main3.png)
![](./assets/postfix-main4.png)
![](./assets/postfix-main5.png)
![](./assets/postfix-main6.png)
![](./assets/postfix-main7.png)
![](./assets/postfix-main8.png)
![](./assets/postfix-main9.png)
![](./assets/postfix-main10.png)
![](./assets/postfix-main11.png)
![](./assets/postfix-main12.png)
![](./assets/postfix-main13.png)
![](./assets/postfix-main14.png)
![](./assets/postfix-main15.png)
5. Buat newalias dan lakukan restart
![](./assets/postfix-newalias.png)
6. Tambahkan konfigurasi anti-spam dan restart
![](./assets/postfix-antispam.png)
![](./assets/postfix-restart.png)

## DOVECOT
1. Lakukan instalasi dovecot
![](./assets/dove-install.png)
2. Ubah listen IP-nya
![](./assets/dove-config.png)
3. Ubah file auth
![](./assets/dove-conf-auth.png)
![](./assets/dove-conf-auth2.png)
4. Konfigurasikan file mail
![](./assets/dove-conf-mail.png)
5. Tambahkan mode 0666, dan user,group postfix pada file master
![](./assets/dove-conf-master.png)
6. Lakukan restart pada service
![](./assets/dove-restart.png)
7. Cek netstat
![](./assets/netstat.png)
![](./assets/netstat2.png)
8. Lakukan test connection sebagai berikut
![](./assets/telnet%20mail.png)
![](./assets/telnet%20mail_result.png)