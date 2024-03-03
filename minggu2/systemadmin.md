# 8.4 Discover: Package manager KDE
Gnome menggunakan "Software" untuk mengatur aplikasi secara simple, KDE menerapkan **Discover**, program yang intuitive dan efisien.
**Discover** memungkinakan kita untuk mencari, mengintall, menghapus, dan memperbarui aplikasi melalui satu interface saja. Kita dapat memodifikasi software source untuk menginstall - atau tidak - beberapa aplikasi berbayar.
**Discover** dapat diluncurkan melalui main menu KDE > Applications > System > Software > Software Center

Tidak perlu ragu saat menulusuri aplikasi yang ada, kita akan dimintai konfirmasi atas semua modifikasi yang dilakukan pada package kita.

## 8.4.1 Mencari dan meng-install menggunakan Discover
Untuk mencari sebuah aplikasi, ketikkan namanya pada search field atau langsung buka berdasarkan kategori yang ada pada Discover. Kemudian satu klik pada tombol "Install" sudah cukup untuk menginstallnya.
Kita akan dimintai konfirmasi untuk action pada perangkat lunak dnegan password administartornya. Prosesnya akan dijalankan di latar belakang. Progres modifikasi dapat kita ikuti melalui area notifikasi KDE.

### 8.4.1.1 Install desktop widget Plasma dan addons
DIscover memungkinkan kita untuk menambahakan komponen tambahan pada environment Plasma kita. Untuk melakukan ini, buka bagian "Plasma add-ons".
Beberapa modul tambahan juga ada untuk aplikasi kita.

## 8.4.2 Uninstall aplikasi menggunakan Discover
Dengan menggunakan DIscover, hanya perlu membuka kategori "Installed" kemudian klik tombol "Remove".

## 8.4.3 Discover: memperbarui aplikasi kita
Ketika KDE memeritahukan pada satu atau lebih update, Discover-lah yang menjalankannya. Untuk melakukan pengecekan terhadap update secara "manual", tekan pada tombol "Refresh".
Hanya perlu menekan tombol "Update all" dan mengkonfirmasi dengan password administrator.
Sebgaaimana pada manajemen software, kita bisa mengikuti proses pada area notifikasi KDE, dan sebuah pesan akan memberitahu kita pada bagian akhir dari proses.

## 8.4.4 Discover: memanajemen repositori
Softaware library KDE memungkinkan kita untuk memodifikasi source dari aplikasi kita tanpa menggunakan terminal. Buka bagian "Settings" pada Discove, isinya akan menampilkan alamat-alamat repositiri dari *sources.list* kita

# 8.7 Menginstall package ".deb" eksternal
Debian GNU/Linux menggunkan sistem package repositoriy untuk mengatur software dengan lebih baik dan meningkatkan keamanan dari sistem kita. Akan tetapi, mungkin bagi kita untuk membutuhkan package eksternal untuk format ".deb".

... tapi siapa si "deb" ini??
**deb** adalah singkatan dari "debian", perusahaan induknya. Untuk mendistribusikan perangkat lunaknya, Debian menggunakan format file arsip yang spesifik: ".deb". Format ini berupa compressed format seperti ".zip" yang kita gunakan untuk menyimpan data. Arsip ".deb" ini dikenali oleh berbagai package manager Debian(APT dan graphical interface Synaptic-nya) sehingga dapat ditangani dengan lebih mudah.

## 8.7.1 Menginstall dalam mode grafis menggunakan GDebi
GDebi adalah utilitas grafik yang memungkinkan instalasi package eksternal dengan format ".deb", juga memanajemen dependency-nya.
Untuk meng-installnya, cari "gdebi" pada package manager kesukaan kita(Synaptic, Discover, Software) atau hanya melalui terminal pada mode administrator menggunakan "su".
`apt update && apt install gdebi`
Disaat kkita mengunduh package eksternal Debian, klik kanan pada package-nya dan pilih "Open with gdebi".
Di dalam menu, klik pada File > Open dan masukkan path menuju file ".deb"
Kemudian klik "Install Package". Password kita akan diminta untuk memvalidasi instalasi.
Untuk meng-uninstall pun sangat mudah: hanya perlu menekan pada "Remove Package"

## 8.7.2 Instalasi pada mode terminal menggunakan Dpkg
Dpkag adalah utilitas software yang menangani package, seperti halnya apt, tapi tanpa memanajemen dependency-nya. Ini berarti saat kita menggunakan dpkg untuk menginstall package eksternal, kita butuh menginstall package "dependen" satu demi satu melalui terminal kita. Secara default dpkg sudah terinstall pada Debian, dan harus digunakan dalam mode administrative.

**Untuk menginstall package eksternal**
`dpkg -i package_name.deb`
Sebuah pesan error akan memberitahu kita apabila terdapat dependency yang tidak ada. Lalu hanya perlu untuk menginstallnya secara jadul menggunakan apt:
`apt install dependency_1 dependency_2 ...`
Kemudian lakukan ulang instalasi package eksternalnya.
`dpkg -i package_name.deb`
**Untuk menghapus package eksternal**
`dpkg --purge package_name`

# 8.8 Menginstall aplikasi Flatpak
Flatpak (https://docs.flatpak.org/en/latest/getting-started.html) adalah sistem virtualisasi aplikasi untuk distribusi GNU/Linux. Tujuannya adalah untuk menyediakan lingkungan "sandbox" yang aman, terisolasi dari bagian lain dari sistem, dimana para pengguna bisa menjalankan aplikasi yang tidak disahkan oleh repositry distribusi(contohnya versi testing).

