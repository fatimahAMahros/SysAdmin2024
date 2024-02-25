## INSTALSI DEBIAN DI VIRTUAL BOX

1. Download ISO Debian di website resmi Debian https://www.debian.org/download

2. Buka VM VirtualBox dan pilih opsi New
    ![](/assets/newVM.png)

3. Saat VM baru dibuat, akan muncul window baru berjudul Create Virtual Machine. Beri nama Debian, dan isi bagian ISO Image dengan address menuju file ISO Debian yang telah diunduh sebelumnya. Pastikan untuk mencentang bagian "Skip unattended installation".
    ![](/assets/VMName.png)
Klik next

4. Atur Hardware dari virtual machine berupa base memory dan processornya
    ![](/assets/VMHardware.png)
Klik next

5. Atur ukuran dari harddisk virtual yang akan digunakan pada VM
    ![](/assets/VMVirtualHarddisk.png)
Klik next

6. Setelah semua pilihan setup selesai, akan muncul Summary berupa detail konfigurasi yang telah dipilih pada bagian setup sebelum-sebelumnya. Pastikan semuanya sudah benar dan sesuai dengan yang diinginkan.
    ![](/assets/VMSummary.png)
Jika sudah sesuai, klik Finish

7. Setelah selesai setup, maka VM terbaru akan terbuat. Secara otomatis, VM akan mulai sendiri secara otomatis.
    ![](/assets/VMStarting.png)
Setelah itu, tunggu hingga VM menyala. Jika Tanda Start masih berwarna hijau, maka klik hingga bisa menyala.

8. Pilih graphical install pada menu installer, klik enter
    ![](/assets/graphicalinstall.png)

9. Konfigurasikan Bahasa, lokasi, dan keyboard yang ingin digunakan.
    ![](/assets/selectLanguage.png)
    ![](/assets/selectLocation.png)
    ![](/assets/selectContinents.png)
    ![](/assets/selectCountry.png)
    ![](/assets/configureLocale.png)
    ![](/assets/configureKeyboard.png)

10. Konfigurasikan network-nya. Untuk Hostname diisi dengan nama sysadmin-[NRP], untuk nama Domain dikosongi saja.
    ![](/assets/Hostname.png)
    ![](/assets/domainName.png)

11. Konfigurasikan user dan password untuk user dan root
    ![](/assets/username.png)
    ![](/assets/rootPassword.png)
    ![](/assets/userPassword.png)

12. Konfigurasikan partisi disk secara manual seperti berikut:
- 20GB, beginning, primary, ext4, mount point: /
- 5GB, end, primary, ext 4, mount point: /storage
- 1GB, beginning, primary, ext 4, mount point: /boot, bootable flag: on
- 843.1MB, end, logical, swap area.
    ![](/assets/partitionManual.png)
    ![](/assets/partitionSelect.png)
    ![](/assets/partitionConfigure.png)
    ![](/assets/partitionSettings.png)
    ![](/assets/partitionPreview.png)

13. Pada tahap berikutnya, Konfigurasikan package manager. Pilih lokasi Indonesia dan untuk archive mirror,pilih yang paling dekat dengan lokasi saat ini, atau jika tidak yakin, pilih deb.debian saja. Untuk proxy, apabila memang menggunakan, beri alamatnya, apabila tidak kosongi saja. Pada pertanyaan mengenai popularity survey, pilih saja "no". Untuk Software selection, pastikan bahwa pilihan "Debian desktop environment", "...GNOME", "web server", "SSH server", dan "standard system utilities" tertandai.
    ![](/assets/configurepackagemanager.png)
    ![](/assets/configurepackagemanagercountry.png)
    ![](/assets/configurepackagemanagerkartolo.png)
    ![](/assets/proxy.png)
    ![](/assets/softwareselection.png)

14. Pada bagian terakhir instalasi, setelah package manager selesai terinstall, Pilih yes untuk grub boot loader. setelah bagian ini selesai, maka proses intalasi selesai dan saat melakukan bootingg VM Debian akan dapat langsung membuka OS Debian yang telah diinstall.
    ![](/assets/grubboot.png)
    ![](/assets/grubbootloader.png)
    ![](/assets/finishinstalling.png)
    ![](/assets/bootingOS.png)
    ![](/assets/bootingLogin.png)
    ![](/assets/desktopview.png)

## Fungsi '/etc/group'
/etc/group adalah file konfigurasi di linux yang menyimpan informasi user groups. File ini berupa file teks, yang mana setiap barisnya mewakili satu user grup dan berisi beberapa kolom yang memuat informasi terkait grup tersebut. User group berfungsi untuk meengelompokkan users dalam kategori untuk memudahkan manajeman hak akses dan sistem administrasi.
Informasi yang tertulis dalam file /etc/group terdiri dari beberapa informasi yang setiap bagiannya dipisahkan dengan sebuah titik koma mengikuti format sbb:
    `group_name;password;GID;group_list`

Dengan keterangan:
- group_name: Nama grup, ketika menggunakan perintah ls -l, nama grup akan ditampilkan pada bagian 'group'
- Password: Pada umumnya password tidak digunakan sehingga tidak terisi. Bagian ini dapat menyiman passwork yang terenkripsi, berguna untuk menerapkan grup dengan hak tertentu.
- Group ID (GID): Digunakan untuk mengidentifikasikan grup. setiap user pasti memiliki GID yang dapat dilihat melaui file /etcpasswd.
- Group List: Berupa daftar username dari user yang menjadi nggota grup. Antar username dipisahkan dengan dengan tanda koma.

## Perbedaan 'su' dengan 'su-'
Perintah 'su' dan perintah 'su-' keduanya adalah perintah yang digunakan untuk pindah ke akun user lain pada sistem, seperti akun root. 
Akan tetapi, terdapat perbedaan antar keduanya, diantaranya daalah:
- Lingkungan Shell:
    - su: Tidak mengubah lingkungan shell saat ini.
    - su-: Mengubah lingkungan shell saat ini menjadi lingkungan shell dari pengguna yang beralih.
- Variabel Lingkungan:
    - su: Tetap menggunakan variabel lingkungan dari pengguna yang awal.
    - su-: Mengambil semua pengaturan lingkungan dari pengguna yang beralih.
- Path (Jalur):
    - su: Tetap menggunakan jalur (path) dari pengguna yang awal.
    - su-: Menggunakan jalur (path) dari pengguna yang beralih.
- Shell History (Riwayat Shell):
    - su: Riwayat shell tetap milik pengguna yang awal.
    - su-: Riwayat shell digunakan dari pengguna yang beralih.
- Akses ke Perintah dan Program:
    - su: Menggunakan perintah dan program yang mungkin berbeda tergantung pada hak akses pengguna yang awal.
    - su-: Menggunakan perintah dan program yang mungkin berbeda tergantung pada hak akses pengguna yang beralih.
- Keamanan:
    - su: Tidak memberikan isolasi penuh antara lingkungan kerja pengguna yang awal dan yang beralih.
    - su-: Memberikan isolasi penuh antara lingkungan kerja pengguna yang awal dan yang beralih, sehingga lebih disukai dari segi keamanan.

Jadi, perbedaan utama antara su dan su- adalah bahwa su- memberikan lingkungan shell lengkap dari user yang digunakan(dialihkan ke), sementara su tidak mengubah lingkungan shell. Dalam konteks keamanan, penggunaan su- lebih baik karena menerapkan isolasi yang lebih besar antara lingkungan kerja user yang asli dan lingkungan kerja user yang dituju.

## Fungsi 'sudo'
sudo(superuser do)adalah perintah yang diguankan untuk memungkinkan user untuk menjalankan perintah dengan hak akses superuser atau root. Fungsinya adalah untuk memberikan akses sementara kepada user untuk menjalankan perintah yang memerlukan hak akses superuser tanpa harus masuk secara penuh sebagai superuser.
Beberapa fungsi utama dari sudo adalah sbb:
- Kontrol akses: sudo memunngkinkan administrator sistem untuk mengontrol dengan cermat siapa yang memiliki akses ke perintah tertentu yang mungkin memiliki dampak besar pada sistem

- Auditabilitas: setiap penggunaan sudo dicatat dalam log audit yang memungkinkan admin untuk mememantau aktivitas pengguna dan menganalisis keamanan sistem

- Granular permissions: Admin dapat menyesuaikan izin sudo dengan rinci, memungkinkan penguna untuk menjalankan hanya perintah-perintah tertentu atau kumpulan perintah yang ditentukan.

- Keamanan: dengan menggunakan sudo, admin bisa mengurangi risiko kesalahan atau penyalahgunaan yg disebabkan oleh pengguna yang memiliki akses root penuh. sudo memungkinkan akses root hanya untuk tugas yang memerlukannya.

- Fleksibilitas: sudo memungkinkan admin untuk memberikan hak akses tambahan secara sementarar atau sesuai kebutuhan tanpa harus mengubah kata sandi root atau berbagi akses superuser secara permanen.