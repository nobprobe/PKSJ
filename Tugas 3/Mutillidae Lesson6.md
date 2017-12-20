
# Lesson 6
## SQL Injection, Burpsuite, cURL, Man-In-The-Middle Attack

Instruksi berdasarkan http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson6/index.html

Berikut dibawah ini merupakan hasil percobaan kami

1. Atur proxy pada browser menjadi `127.0.0.1`

>>> ![SS2](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/23.png)

2. Install dan Konfigurasi Burpsuite

>>> ![SS2](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/2-1.png)
>>> ![SS2](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/2-2.png)

3. Mencoba Login dengan menginputkan `' or 1=1-- ` 

>>> ![SS3](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/3.png)

4. Hasil POST login yang dilakukan ditangkap oleh Burpsuite

>>> ![SS4](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/4.png)

5. Mencoba login dengan Curl yang menggunakan data pada Burpsuite dan menyimpan session&cookies pada crack_cookies.txt 

>>> ![SS5](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/5.png)

6. Login kembali dengan username samurai dan password `' or (1=1 and username='samurai')--` dan menangkap hasil POST ke Burpsuite

>>> ![SS6](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/6-1.png)

7. Simpan hasil POST ke file txt

>>> ![SS7](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/7.png)

8. Tambahkan PHPSESSID cookie, show hint cookie dan username cookie pada browser sesuai dengan yang disimpan di file txt

>>> ![SS8](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/8-1.png)
>>> ![SS8](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/8-2.png)
>>> ![SS8](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/8-3.png)

9. Web akan otomatis login ke akun samurai

>>> ![SS9](https://github.com/fandyaditya/PKSJ/blob/master/Tugas%203/Gambar/Lesson6/9.png)
