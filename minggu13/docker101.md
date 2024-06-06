# Docker 101
Docker 101 adalah tutorial docker yang bersifat hands-on yang memberi tutorial dalam penggunaan docker seperti membuat image, menjalankan containaer, menggunakan volume untuk menyimpan data, dan menggunakan docker compose.

1. Akses halaman https://www.docker.com/101-tutorial/ . Dari situ bisa memilih untuk mengerjakannya pada docker deskytop milik sendiri atau melalui web. disini saya menggunakan web.
![](./assets/Screenshot%202024-05-20%20091941.png)
2. Klik new instance
![](./assets/Screenshot%202024-05-20%20092004.png)
3. Jalabnkan `docker run -dp 80:80 docker/getting-started:pwd` di terminal
![](./assets/Screenshot%202024-05-20%20092248.png)
4. Akan terlihat port 80 berjalan di atas terminal, klik untuk membuka guide dari tutorial.
![](./assets/Screenshot%202024-05-20%20092305.png)
![](./assets/Screenshot%202024-05-20%20092334.png)
5. Kita akan membuat aplikasi. unduh file zip yang tersedia pada guide, dan unggah ke terminal menggunakan drag & drop.
![](./assets/Screenshot%202024-05-20%20092421.png)
![](./assets/Screenshot%202024-05-20%20092451.png)
![](./assets/Screenshot%202024-05-20%20092510.png)
6. Extract file zip menggunakan perintah `unzip`
![](./assets/Screenshot%202024-05-20%20092605.png)
7. Masuk ke folder dari hasil ekstaksi zip, dapat kita lihat apa saja isinya menggunakan perintah ls.
![](./assets/Screenshot%202024-05-20%20092628.png)
8. Buat file bernama Dockerfile menggunakan vi editor
![](./assets/Screenshot%202024-05-20%20093332.png)
![](./assets/Screenshot%202024-05-20%20093312.png)
9. Buil container imagenya dengan menggunakan perintah `docker build -t docker-101 .`.
![](./assets/Screenshot%202024-05-20%20093545.png)
10. Jalankan container pada port 3000 menggunakan perintah `docker run -dp 3000:3000 docker-101`
![](./assets/Screenshot%202024-05-20%20093706.png)
11. Saat sudah berjalan, kita dapat mengakses port 3000 menggunakan link yang muncul di atas terminal. Saat membukanya, kita akan diarahkan ke halaman yang berisi aplikasi kita, yaitu sebuah todo list. Kita dapat mencoba-coba untuk menggunakannya seperti aplikasi pada umumnya.
![](./assets/Screenshot%202024-05-20%20093711.png)
![](./assets/Screenshot%202024-05-20%20093734.png)
12. Modifikasi kode dari aplikasi kita pada baris ke 56 dari app.js. Di sini saya menggunakan vi editor untuk melakukannya. Ubah seperti berikut:
-                <p className="text-center">No items yet! Add one above!</p>
+                <p className="text-center">You have no todo items yet! Add one above!</p>
Jangan lupa untuk menyimpan perubahannya
![](./assets/Screenshot%202024-05-20%20094239.png)
![](./assets/Screenshot%202024-05-20%20094225.png)
13. Lakukan buil ulang pada versi terbaru dari image yang kita ubah emnnggunakan `docker build -t docker-101 .`
![](./assets/Screenshot%202024-05-20%20093545.png)
14. Jalankan container yang barusan diubah menggunakan perintah `docker run -dp 3000:3000 docker-101` pasti akan terjadi error. Hal ini terjadi karena kita berusaha menjalankan pada sebuah port yang masih digunakan
![](./assets/Screenshot%202024-05-20%20094556.png)
15. Cek container apa saja yang sedang berjalan menggunakan docker ps
![](./assets/Screenshot%202024-05-20%20094635.png)
16. Kita dapat menghentikan sebuah docker container yang berjalan menggunakan perintah `docker stop [docker-id]`
![](./assets/Screenshot%202024-05-20%20094841.png)
17. Hapus containernya menggunakan perintah `docker rm [docker-id]`
![](./assets/Screenshot%202024-05-20%20095116.png)
18. Baru kita dapat menjalankan versi docker image terbaru pada port 3000 
![](./assets/Screenshot%202024-05-20%20095129.png)
![](./assets/Screenshot%202024-05-20%20095144.png)
19. Kit adapat membagikan aplikasi kita menggunakan docker hub. Pertama buka https://hub.docker.com/ dan masuk pada akun docker.
![](./assets/Screenshot%202024-05-20%20095442.png)
20. Buat repository publik dengan nama 101-todo-app pada docker hub
![](./assets/Screenshot%202024-05-20%20095506.png)
21. Setelah repository kita buat, akan muncul docker command yang memberi tahu kita cara mengakses repository docker tersebut menggunakan perintah di terminal. Saat kita jalankan akan terjadi error.
![](./assets/Screenshot%202024-05-20%20095543.png)
![](./assets/Screenshot%202024-05-20%20095707.png)
22. Untuk membenarkan error tersebut, kita perlu memberikan nama lain pada image tersebut. pertama-tama, kita perlu masuk ke akun docker hub kita. lakukan menggunakan perintah `docker login -u [USER-NAME]`.
![](./assets/Screenshot%202024-05-20%20100237.png)
23. Tambahkan nama lain/tag menggunakan perintah `docker tag`
![](./assets/Screenshot%202024-05-20%20100520.png)
24. Lakukan push ulang terhadap repository, bisa kita lihat bahwa kali ini tidak terjadi error. 
![](./assets/Screenshot%202024-05-20%20100612.png)
25. Buat new instance pad pwd
![](./assets/Screenshot%202024-05-20%20100649.png)
26. Jalanakan container menggunakan `docker run -dp 3000:3000 [USER-NAME]/101-todo-app .` pada terminal baru.
![](./assets/Screenshot%202024-05-20%20100823.png)
27. Akses port barunya menggunakan tombol di atas terminal baru, kit akan dapat mengakses aplikasi kita
![](./assets/Screenshot%202024-05-20%20100830.png)
![](./assets/Screenshot%202024-05-20%20100844.png)
28. Sejauh ini, dapat kita lihat setiap kali kita menjalankan aplikasinya, imte yang sudah kita buat sebelumnya tidak tersimpan.Untuk itu kita buat container ubuntu yang akan membuat file bernama /data.txt dengan angka random dari 1 hingga 10000 dengan perintah `docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"`
![](./assets/Screenshot%202024-05-20%20101906.png)
29. Lakukan validasi terhadapa outputnya dengan cara `docker exec [container-id] cat /data.txt`
![](./assets/Screenshot%202024-05-20%20102101.png)
30. Kemudian kita coba jalankan container ubuntu yang lain dengan image yang sama, dan kita akan lihat apakah file yang kit apunya sama dengan container ubuntu sebelumnya. Terlihat bahwa tidak ada file data.txt
![](./assets/Screenshot%202024-05-20%20102257.png)
![](./assets/Screenshot%202024-05-20%20102428.png)
31. Hapus container ubuntu pertama dengan printah `docker rm -f [CONTAINER-ID]`
![](./assets/Screenshot%202024-05-20%20102616.png)
32. Buat volume menggunakan perintah `docker volume create todo-db`
![](./assets/Screenshot%202024-05-20%20103139.png)
33. Jalankan container todo dan tambahan flag -v untuk menspesifikan volume mount.
![](./assets/Screenshot%202024-05-20%20103157.png)
34. Sekarang kita coba buat beberapa item pada aplikasi kita.
![](./assets/Screenshot%202024-05-20%20103340.png)
35. Hapus container todo appnya dengan menggunakan perintah `docker rm -f [container-id]`
![](./assets/Screenshot%202024-05-20%20103504.png)
36. Jalankan ulang container menggunakan tambahan flag -v dan buka kembali aplikasi kita pada port 3000. Dapat terlihat bahwa item yang seblumnya kita buat tersimpan
![](./assets/Screenshot%202024-05-20%20103538.png)
![](./assets/Screenshot%202024-05-20%20103549.png)
37. Kit adapat menggunakan perintah `docker volume inspect [name]` untuk mencari tahu dimana docker menyimpan data kita saat menggunakan named volemu.
![](./assets/Screenshot%202024-05-20%20103732.png)
38. Sekarang kita akan mencoba menggunakan bind mount. Pastikan terlebih dahulu bahwa tidak ada container docker-101 yang masih berjalan. jika ada, hentikan containernya.
![](./assets/Screenshot%202024-05-20%20104028.png)
39. Jalankan perintah berikut:
![](./assets/Screenshot%202024-05-20%20104251.png)
40. Jalanakan perintah `docker logs -f [container-id]`. JIka muncul "listening on port 300, maka aplikasi sudah berjalan.
![](./assets/Screenshot%202024-05-20%20104446.png)
41. Pada file app.js, kit aubah "Add Item" menjadi "Add" saja. Jangan lupa simpan perubahannya.
![](./assets/Screenshot%202024-05-20%20104730.png)
42. Buka port 3000, dapat kit alihat bahwa tombol sudah berubah menjadi "Add"
![](./assets/Screenshot%202024-05-20%20104846.png)
43. Sekarang kita akan membuat aplikasinya menjadi bentuk multicontainer. Pertama kit abuat networknya menggunakan perintah berikut:
![](./assets/Screenshot%202024-05-20%20105726.png)
44. Jalanakn perintah di bawah untuk menjalankan containr MYSQL
![](./assets/Screenshot%202024-05-20%20110127.png)
45. Kemudian, jalanakan perintah `docker exec -it [mysql-container-id] mysql -p` untuk mengecek apakah container mySQL kita udah jalan
![](./assets/Screenshot%202024-05-20%20110524.png)
46. Cek database yang ada dengan menjalankan perintah `SHOW DATABASES;`
![](./assets/Screenshot%202024-05-20%20110625.png)
47. Jalankan sebuah container baru dengan perintah `docker run -it --network todo-app nicolaka/netshoot`
![](./assets/Screenshot%202024-05-20%20110933.png)
48. Jalankan perintah `dig mysql` untuk mendapatkan IP.
![](./assets/Screenshot%202024-05-20%20111004.png)
49. Jalankan perintah berikut untuk menspesifikkan variabel enviroment dan menghubungkannya ke container.
![](./assets/Screenshot%202024-05-20%20105828.png)
50. Kita dapa mengecek log dengan menggunakan perintah `docker logs [container-id]`. Nanti akan muncul pesan memberitahukan bahwa saat ini sedang menggunakan sebuah database mysql.
![](./assets/Screenshot%202024-05-20%20111932.png)
51. Buka todo app kita, dan tambahkan beberapa item.
![](./assets/Screenshot%202024-05-20%20112105.png)
52. Hubungkan database ke mysql dengan perintah `docker exec -ti [mysql-container-id] mysql -p todos`. Jalanakn qury `select * from todo_items;`. Dapat kit alihat bahwa aplikasi kita berhasil connect ke database mysql.
![](./assets/Screenshot%202024-05-20%20112122.png)
![](./assets/Screenshot%202024-05-20%20112156.png)
53. Sekarang kita akan mencoba menggunakan Docker compose. Pada terminal di web docker 101, kit atidak perlu menginstallnya terlebih dahulu. Kita dapat melihat versinya dengan menggunakan perintah `docker-compose version`
![](./assets/Screenshot%202024-05-20%20112347.png)
54. Buat sebuah file bernama docker-compose.yml pada folder app
![](./assets/Screenshot%202024-05-20%20113136.png)
55. Isikan filenya seperti berikut:
![](./assets/Screenshot%202024-05-20%20113149.png)
56. Simpan file docker-compose.yml . Jalankan perintah `docker-compose up`
![](./assets/Screenshot%202024-05-20%20113621.png)
57. Kita dapat melihat log menggunakan perintah `docker-compose logs -f`. Kita dapat melihat log dari setiap layanan terhubung menjadi satu stream.
![](./assets/Screenshot%202024-05-20%20113758.png)
58. Gunakan perintah `docker image history` untuk menampilkan lapisan yang ada pada image docker-101. Setiap baris dalam hasil tampilan mewakili satu lapisan dalam image tersebut. Lapisan dasar terletak di bagian bawah, sementara lapisan terbaru berada di bagian atas. Selain itu, kita dapat melihat ukuran setiap lapisan, yang berguna untuk menganalisis dan mengidentifikasi image berukuran besar.
![](./assets/Screenshot%202024-05-20%20114258.png)
59. Dapat dilihat bahwa baris yang muncul ada yang terpotong. Agar tampilannya tidak terpotong, kita dapat menggunakan perintah `docker image history --no-trunc docker-101`. yang akan menampilkannya seperti berikut:
![](./assets/Screenshot%202024-05-20%20114406.png)
60. Sekarang kit aakan melakukan layer caching. Petrama-tama, ubah Dockerfile sebagai berikut:
![](./assets/Screenshot%202024-05-20%20114628.png)
61. Buat image baru menggunakan perintah `docker build -t docker-101 .`
![](./assets/Screenshot%202024-05-20%20114759.png)
62. Ubah title pada index.html dari aplikasi sebagi berikut: 
![](./assets/Screenshot%202024-05-20%20114958.png)
63. Lakukan build ulang menggunakan perintah `docker build -t docker-101 .`. Akan terasa bahwa proses buil memeakan waktu yang lebih cepat. Hal ini disebabkan oleh adanay caching.
![](./assets/Screenshot%202024-05-20%20115154.png)
