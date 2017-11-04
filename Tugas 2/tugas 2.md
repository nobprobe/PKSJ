#### Anggota:
* I Made Fandy Aditya Wirana    5114100026
* Muhammad Fahmi Abdurrahman    5114100028
* I Gede Putu Nobby Aswi Phala  5114100048

### Pendahuluan

  Laporan ini berisi uji penetrasi Wordpress. OS server yang digunakan yaitu Ubuntu Server 16.04.3 dan OS penyerang yang digunakan yaitu Kali Linux 2017.1. Tools yang digunakan untuk menyerang yaitu WPScan, sqlmap.
  
### Dasar Teori

  * #### Ubuntu Server
    Ubuntu Server Edition mendukung arsitektur Intel x86 dan AMD64. Edisi server menyediakan fitur seperti file/print services, web hosting, email hosting, dll. Ada beberapa perbedaan antara edisi server dan edisi desktop walaupun keduanya menggunakan repositori apt yang sama. Perbedaan utamanya adalah, pada edisi server X window environment tidak diinstall scara standar, walaupun antarmuka grafik dapat diinstall secara manual seperti Ubuntu desktop. CD Ubuntu Server Edition juga memiliki pilihan untuk menginstall Ubuntu Enterprise Cloud.
    
  * #### Kali Linux
    Kali Linux adalah distribusi Linux berbasis Debian yang ditujukan untuk uji penetrasi dan pengecekan keamanan. Kali memiliki ratusan tools yang disematkan untuk menjalankan berbagai task yang berkaitan dengan keamanan, seperti uji penetrasi, forensik digital, dan *Reverse Engineering*. Kali Linux dikembangkan oleh Offensive Security, perusahaan yang berkembang di bidang keamanan informasi.
    
  * #### WPScan
    WPScan adalah tools untuk mendeteksi keamanan dari wordpress dengan metode blackbox. Fitur yang dimiliki antara lain:
    * pencacah username
    * multithreaded password bruteforcing
    * pencari versi plugin WordPress dan
    * pencari kerentanan sistem web wordpress
    
  * #### sqlmap
    sqlmap adalah alat pengujian open source yang mendeteksi dan mengeksploitasi kelemahan dalam SQL injection dan mengambil alih server database. Muncul dengan mesin pendeteksi yang hebat, banyak fitur untuk tester penetrasi akhir dan berbagai switch yang bertahan dari sidik jari database, melebihi pengambilan data dari database, untuk mengakses sistem berkas yang mendasarinya dan menjalankan perintah pada sistem operasi melalui sistem out- koneksi band.
    Mendukung  DBMS MySQL, Oracle, PostgreSQL, Microsoft SQL Server, Microsoft Access, IBM DB2, SQLite, Firebird, Sybase, SAP MaxDB, HSQLDB dan Informix.

### Instalasi Ubuntu Server + OpenSSH Server

  1. Download file instalasi Ubuntu Server dan mount ke virtual machine
      https://www.ubuntu.com/download/server
      
  2. Pilih "*Install Ubuntu Server*"
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-choose-server.png)
  3. Set Hostname, Username, dan Password
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-host-server.png)
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-user-server.png)
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-pwd-server.png)
  4. Set Partition Disk Menjadi *Guided - use entire disk*
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-part-server.png)
  5. Tunggu instalasi selesai
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-wait-server.png)
  6. Lakukan konfigurasi lainnnya
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/config-taskkel-server.png)
  7. Pilih software yang akan diinstall
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-soft-server.png)
  8. Tunggu instalasi software
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-soft-wait-server.png)
  9. Install Bootloader Grub
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-grub-server.png)
  10. Selesai!!!
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/done-server.png)
### Instalasi Kali Linux
  
  1. Download file instalasi Kali Linux dan mount ke virtual machine
      https://www.kali.org/downloads/

  2. Pilih *Graphical Install*
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-choose-kali.png)
  3. Set Hostname, Username, dan Password
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-host-kali.png)
      ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-user-kali.png)
  4. Set Partition Disk menjadi *Guided - use entire disk*
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-part-kali.png)
  5. Set Disk yang akan dibuat menjadi partisi
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-disk-kali.png)
  6. Set Partition Scheme menjadi *All files in one partition*
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-scheme-kali.png)
  7. Tunggu Instalasi Selesai
     ![SS](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/install-wait-kali.png)
  8. Selesai!!!

### Instalasi LAMP server

  1. Gunakan perintah seperti berikut
     >```sudo tasksel install_lamp-server```
  2. Tunggu file didownload
  3. Set password untuk user root dari mysql
  4. Tunggu instalasi selesai
  5. Selesai!!!
    
### Instalasi Wordpress
  1. Dowload Wordpress dengan perintah seperti berikut
  >```wget http://wordpress.org/latest.zip```
  2. Extract file ke /var/www/html
  >```sudo unzip latest.zip -d /var/www/html```
  3. Ganti kepemilikan dan hak akses dari folder wordpress
  >```sudo chown -R www-data:www-data /var/www/html/wordpress///```
  >```sudo chmod -R 775 /var/www/html/wordpress/```
  4. Berikan Port Forwarding Rules ke Vitual Machine agar dapat diakses dari luar
  5. Berikan rules firewall di ubuntu server, lalu restart firewall
  6. Buka mysql, lalu buat database dengan nama wordpress
  7. Buka halaman depan dari Wordpress, lalu akan ada inisialisasi
  8. Isi konfigurasi database dengan yang telah dibuat sebelumnya
  9. Set konfigurasi website
  10. Selesai!!!

### Instalasi Plugin
   1. Masuk ke menu Plugin -> Add New
    2. Klik tombol Upload Plugin
    3. Pilih file plugin, lalu klik Install Now
    4. Tunggu instalasi selesai
    5. Selesai!!!
 
### Uji Penetrasi
   * #### WPScan
      Lakukan tes dengan cara berikut
    > ```wpscan --url http://192.168.1.1 --enumerate -u```
    
   * sqlmap
    > ```oeeoaeoaeoaeaoeo```

### Kesimpulan dan Saran
   Serangan SQL Injection adalah memodifikasi perintah sql dari aplikasi client dengan cara menyisipkan kedalamnya. Dalam hal ini terdapat plugin dari wordpress yang tidak di optimasi querynya, sehingga rentan SQL Injection tersebut. Dengan tools tools tersebut, developer dapat memeriksa keamanan dari plugin dan seisi websitenya, sehingga developer dapat memperbaharui plugin atau mengganti plugin yang tidak aman.
