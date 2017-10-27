#### Anggota:
* I Made Fandy Aditya Wirana    5114100026
* Muhammad Fahmi Abdurrahman    5114100028
* I Gede Putu Nobby Aswi Phala  5114100048

### Pendahuluan

  Laporan ini berisi uji penetrasi server. OS server yang digunakan yaitu Ubuntu Server 16.04.3 dan OS penyerang yang digunakan yaitu Kali Linux 2017.1. Tools yang digunakan untuk menyerang yaitu Ncrack, Hydra, dan Medusa. Dilakukan 2 kali uji penetrasi, penetrasi pertama server hanya diinstall OpenSSH, penetrasi kedua server terinstall fail2ban.
  
### Dasar Teori

  * #### Ubuntu Server
    Ubuntu Server Edition mendukung arsitektur Intel x86 dan AMD64. Edisi server menyediakan fitur seperti file/print services, web hosting, email hosting, dll. Ada beberapa perbedaan antara edisi server dan edisi desktop walaupun keduanya menggunakan repositori apt yang sama. Perbedaan utamanya adalah, pada edisi server X window environment tidak diinstall scara standar, walaupun antarmuka grafik dapat diinstall secara manual seperti Ubuntu desktop. CD Ubuntu Server Edition juga memiliki pilihan untuk menginstall Ubuntu Enterprise Cloud.
    
  * #### Kali Linux
    Kali Linux adalah distribusi Linux berbasis Debian yang ditujukan untuk uji penetrasi dan pengecekan keamanan. Kali memiliki ratusan tools yang disematkan untuk menjalankan berbagai task yang berkaitan dengan keamanan, seperti uji penetrasi, forensik digital, dan *Reverse Engineering*. Kali Linux dikembangkan oleh Offensive Security, perusahaan yang berkembang di bidang keamanan informasi.
    
  * #### Ncrack
    Ncrack adalah alat cracking otentikasi jaringan berkecepatan tinggi. Ini dibangun untuk membantu perusahaan mengamankan jaringan mereka dengan secara proaktif menguji semua host dan perangkat jaringan mereka dengan kata kunci yang buruk. Profesional keamanan juga mengandalkan Ncrack saat mengaudit klien mereka. Ncrack dirancang menggunakan pendekatan modular, sintaks baris perintah yang mirip dengan Nmap dan mesin dinamis yang dapat menyesuaikan perilakunya berdasarkan umpan balik jaringan. Ini memungkinkan dilakukannya audit berskala besar yang cepat namun dapat diandalkan dari beberapa host.
    
    Fitur Ncrack mencakup antarmuka yang sangat fleksibel yang memberi pengguna kontrol penuh atas operasi jaringan, memungkinkan serangan bruteforcing yang sangat canggih, template waktu untuk kemudahan penggunaan, interaksi runtime yang mirip dengan Nmap dan banyak lagi. Protokol yang didukung meliputi RDP, SSH, HTTP (S), SMB, POP3 (S), VNC, FTP, SIP, Redis, PostgreSQL, MySQL, dan Telnet.
   
  * #### THC Hydra
    Sebuah tools crack yang semakin unggul dalam hal exploit dan THC-Hydra salah satu yang sangat cepat meretas jaringan logon cracker yang mendukung banyak layanan yang berbeda. Lihat fitur dan layanan cakupan halaman - termasuk. perbandingan kecepatan terhadap ncrack dan medusa.
    
    Tools ini mendukung Asterisk, AFP, Cisco AAA, Cisco auth, Cisco, CVS, Firebird, FTP, HTTP-FORM-GET, HTTP-FORM-POST, HTTP GET, HTTP-KEPALA, HTTP-PROXY, HTTPS-FORM-GET, HTTPS-FORM-POST, HTTPS-GET, HTTP-Proxy, ICQ, IMAP, IRC, LDAP, MS-SQL, MYSQL, NCP, NNTP, Oracle Listener, Oracle SID, Oracle, PCNFS, POP3, POSTGRES, RDP, rexec, rlogin, rsh, S7-300, SAP/R3,  SIP, SMB, SMTP, SMTP Enum, SNMP, Socks5, SSH (v1 dan v2), Subversion,TeamSpeak (TS2), Telnet, VMware-Auth, VNC dan XMPP.
    
  * #### Medusa
    Medusa dimaksudkan untuk menjadi cepat, massal paralel, modular, Login brute-pompa kecil. Tujuannya adalah untuk mendukung banyak layanan yang memungkinkan otentikasi remote mungkin. Penulis menganggap item sebagai beberapa fitur kunci dari aplikasi ini sebagai berikut:
    
    * Thread based parallel testing
    * Flexible user input
    * Modular Design
    
    Medusa adalah alat baris perintah, sehingga kamu perlu belajar perintah sebelum menggunakan alat ini. Efisiensi dari alat tergantung pada konektivitas jaringan. Pada sistem lokal, dapat menguji 2000 password per menit.
  
### Instalasi Ubuntu Server + OpenSSH Server

  1. Download file instalasi Ubuntu Server dan mount ke virtual machine
      https://www.ubuntu.com/download/server
      
  2. Pilih "*Install Ubuntu Server*"
  
  3. Set Hostname, Username, dan Password
  
  4. Set Partition Disk Menjadi *Guided - use entire disk*
  
  5. Tunggu instalasi selesai
  
  6. Lakukan konfigurasi lainnnya
  
  7. Pilih software yang akan diinstall, dalam hal ini yaitu OpenSSH Server
  
  8. Tunggu instalasi software
  
  9. Selesai!!!

### Instalasi Kali Linux
  
  1. Download file instalasi Kali Linux dan mount ke virtual machine
      https://www.kali.org/downloads/

  2. Pilih *Graphical Install*
  
  3. Set Hostname, Username, dan Password
  
  4. Set Partition Disk menjadi *Guided - use entire disk*
  
  5. Set Disk yang akan dibuat menjadi partisi
  
  6. Set Partition Scheme menjadi *All files in one partition*
  
  7. Tunggu Instalasi Selesai
  
  8. Selesai!!!

### Uji Penetrasi 1


### Uji Penetrasi 2

#### Fail2ban
Fail2ban adalah sebuah tools untuk melindungi akses server dari serangan brute force pada user maupun root password. Fail2ban akan melakukan ban ip yang gagal melakukan login sebanyak yang telah diatur. Defaultnya, fail2ban akan memblokir ip yang gagal melakukan login sebanyak 5 kali dengan waktu 60 menit.


#### Konfigurasi Fail2ban
Pertama kita install fail2ban terlebih dahulu
> ```apt-get install fail2ban```

lalu lakukan konfigurasi fail2ban dengan mengedit file :
> etc/fail2ban/jail.conf

Pada konfigurasi fail2ban, kita mengubah setingan pada **max retry** / maksimal gagal login dari 5 menjadi 2, dan **bantime** dari 60 menit menjadi 1 menit. 

![SS 1](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/setting-fail2ban.PNG "Setting pada maxretry dan bantime")

Setelah itu atur ip dari masing – masing virtual machine pada file :
> /etc/network/interfaces

![SS 2](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/config-ip-server.PNG "Setting IP pada ubuntu server")

![SS 3](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/config-ip-kali.PNG "Setting IP pada kali linux")

Jangan lupa lakukan restart
> ```service networking restart```

Setelah disetting, ubuntu server siap untuk diserang.


#### Testing Fail2ban

Tools penyerangan sama menggunakan nCrack, Medusa dan Hydra. Berikut hasil darin penyerangan tersebut.

![SS 4](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/attack-hydra.PNG "Penyerangan hydra dengan fail2ban terinstall")

![SS 5](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%201/Gambar/attack-medusa.PNG "Penyerangan medusa dan ncrack dengan fail2ban terinstall")

Bisa dilihat penyerang gagal mendapatkan password karena ip nya telah diblokir terlebih dahulu.


#### Kesimpulan

Serangan brute force walaupun membutuhkan waktu yang lama, password yang rumit sekalipun pasti akan didapatkan. Namun dengan menggunakan fail2ban, percobaan brute force akan gagal karena adanya pembatasan percobaan oleh fail2ban. Dengan fail2ban serangan brute force dapat terpenuhi.

