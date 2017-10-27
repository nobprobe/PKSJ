### Uji Penetrasi 2

#### Fail2ban
Fail2ban adalah sebuah tools untuk melindungi akses server dari serangan brute force pada user maupun root password. Fail2ban akan melakukan ban ip yang gagal melakukan login sebanyak yang telah diatur. Defaultnya, fail2ban akan memblokir ip yang gagal melakukan login sebanyak 5 kali dengan waktu 60 menit.


#### Konfigurasi Fail2ban
Pertama kita install fail2ban terlebih dahulu
> ```apt-get install fail2ban```

lalu lakukan konfigurasi fail2ban dengan mengedit file :
> etc/fail2ban/jail.conf

Pada konfigurasi fail2ban, kita mengubah setingan pada **max retry** / maksimal gagal login dari 5 menjadi 2, dan **bantime** dari 60 menit menjadi 1 menit. 

!(https://github.com/fandyaditya/PKSJ/tree/master/Tugas%201/Gambar/setting-fail2ban.png "Setting pada maxretry dan bantime")

Setelah itu atur ip dari masing – masing virtual machine pada file :
> /etc/network/interfaces

!(https://github.com/fandyaditya/PKSJ/tree/master/Tugas%201/Gambar/config-ip-server.png "Setting IP pada ubuntu server")

!(https://github.com/fandyaditya/PKSJ/tree/master/Tugas%201/Gambar/config-ip-kali.png "Setting IP pada kali linux")

Jangan lupa lakukan restart
> ```Service networking restart```

Setelah disetting, ubuntu server siap untuk diserang.


#### Testing Fail2ban

Tools penyerangan sama menggunakan nCrack, Medusa dan Hydra. Berikut hasil darin penyerangan tersebut.

!(https://github.com/fandyaditya/PKSJ/tree/master/Tugas%201/Gambar/attack-hydra.png "Penyerangan hydra dengan fail2ban terinstall")

!(https://github.com/fandyaditya/PKSJ/tree/master/Tugas%201/Gambar/attack-medusa.png "Penyerangan medusa dan ncrack dengan fail2ban terinstall")

Bisa dilihat penyerang gagal mendapatkan password karena ip nya telah diblokir terlebih dahulu.


#### Kesimpulan

Serangan brute force walaupun membutuhkan waktu yang lama, password yang rumit sekalipun pasti akan didapatkan. Namun dengan menggunakan fail2ban, percobaan brute force akan gagal karena adanya pembatasan percobaan oleh fail2ban. Dengan fail2ban serangan brute force dapat terpenuhi.

