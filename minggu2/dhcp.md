# dhcp
Pertama-tama, kita perlu menginstall net-tools terlebih dahulu. Package net-tools ini nantinya akan digunakan untuk menampilkan tabel routing dari kenrel. Untuk menginstallnya dapat menggunakan perintah
`sudo apt install net-tools`

Kemudian kita gunakan peirntah:
`sudo dhclient -v`
Untuk mengakses alamat IP secara dinamis dari server DHCP untuk network interface yang tertentu menggunakan hak akses superuser. Penggunaan superuser ini nantinya akan dibutuhkan pada saat mengkonfigurasi network interface. Di sini dapat dilihat IP yang dikembalikan adalah 10.0.2.15 .
![](/assets/sudodhclient-v.jpg)

Dengan menggunakan perintah:
`ip addr`
Kita dapat melihat informasi tentang konfigurasi network interface yang sudah diterapkan pada server.
![](/assets/ipaddr.jpg)

Untuk mengubah konfigurasi IP koneksi secara manual, dapat diakses melalui pengaturan Wired Connections dan mengkonfigurasi secara manual pada tab IPv4. Pastikan IPv4 Method yang dipilih adalah yang **manual** dan bukan default. Kemudian kita dapat mengubah alamat IP-nya, misal menjadi 10.0.2.16 . Pastikan untuk mengatur subnet masknya dengan sesuai pula, disini berarti 255.255.255.0, dan untuk gateway kita atur menjadi 10.0.2.2 . Sedangkan untuk DNS nya kita atur menjadi 8.8.8.8, yakni DNS umum milik Google.
![](/assets/wiredsetting1.png)
![](/assets/wiredsetting2.png)
![](/assets/wiredsetting3.jpg)

Setelah itu, klik apply dan matikan koneksi wired dan nyalakan kembali. Pada saat kita mengakses routing table menggunakan perintah 
`sudo route -n` 
Akan muncul routing table dari kernel dalam bentuk numerik seperti gambar di bawah.
![](/assets/sudoroute-n.jpg)

Saat kita gunakan kembali perintah
`ip addr`
Kita dapat melihat bahwa alamat IP sudah berubah dari 10.0.2.15 menjadi 10.0.2.16, sesuai dnegan alamat yang kita ubah sebelumnya.
![](/assets/ipaddr2.jpg)

## Melakukan test ping
Saat sudah berhasil mengkonfigurasi dhcp dengan benar, maka saat kita mencoba untuk melakukan ping, akan kembali dengan sukses. Di bawah ini dilakukan test ping pada alamat 8.8.8.8 dan website detik.com.
![](/assets/testping1dhcp.jpg)
![](/assets/testping2dhcp.jpg)