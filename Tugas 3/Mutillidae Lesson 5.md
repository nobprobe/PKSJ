
# Lesson 5
## Sql Injection With Firebug

### Mendapatkan akun dan login
Instruksi pelaksanaan berdasarkan 
http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson5/index.html

Berikut dibawah ini adalah hasil dari percobaan kami

1. Mencoba insert single quotes `'` pada kolom username

>>> ![SS1](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/3.png)

2. Error insert single quotes `'`

>>> ![SS2](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/4.png)

3. Menambahkan `' or 1=1-- (spasi)` pada kolom username yang membuat kondisi selalu benar sehingga akan mengambil semua user. Karakter -- adalah karakter komentar di mysql sehingga akan meniadakan query pemeriksaan password sehingga password tidak di periksa.

>>> [SS3](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/5.png)

4. Berhasil login sebagai admin. Langsung login sebagai admin karena user admin merupakan user paling atas di database.

>>> [SS4](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/6.png)

5. Mencoba analysis single quotes pada field password. (Field password dirubah typenya ke text menggunakan inspect elemen untuk memudahkan mencoba injection

>>> [SS5](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/10.png)

6.  Single quotes membuat query tetap gagal

>>> [SS6](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/11.png)

7. Menambahkan `' or 1=1--` pada field password untuk mencoba login sebagai samurai

>>> [SS7](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/12.png)

8. Login berhasil namun sebagai admin karena admin merupakan user paling atas dalam database

>>> [SS8](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/13.png)

9. Tambahkan `' or (1=1 and username='samurai')--` agar username yang di ambil adalah samurai

>>> [SS9](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/14.png)

10. Berhasil login sebagai samurai

>>> [SS10](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/15.png)


### Database Practice

1. Membuka isi database mutillidae dan melihat table - table dengan `"show tables;"`

>>> [SS10](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/16.png)

2. Membuka isi table accounts menggunakan `"select * form accounts;"` yang berisi informasi creditential akun

>>> [SS11](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/17.png)

3. Mencoba mengambil username samurai jika menggunakan password salah. Syntax: `"select * from accounts where username = 'samurai'  and password = 'wrongpassword';"` dan ternyata tidak menghasilkan apa-apa

>>> [SS12](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/18.png)

4. Menambahkan karakter `--` pada query yang membatalkan pengecekan password. Syntax menjadi `"select * from accounts where username = 'samurai';-- and password = 'wrongpassword';"` dan berhasil mengambil user

>>> [SS13](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/19.png)

5. Mencoba syntax `"select * from accounts where username = '' or 1=1; --   and password = '';"` dan membuat mysql mengeluarkan seluruh isi table. Hal ini yang membuat kita login sebagai admin walaupun menggunakan username samurai pada percobaan pertama

>>> [SS14](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson5/20.png)
