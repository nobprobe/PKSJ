## Installasi
1. Install seluruh software pendukung untuk snort terlebih dahulu

> ```sudo apt install -y gcc libpcre3-dev zlib1g-dev libpcap-dev openssl libssl-dev libnghttp2-dev libdumbnet-dev bison flex libdnet```

2. Buat folder untuk menampung file installasi dan masuk ke folder tersebut

> ```mkdir ~/snort_src && cd ~/snort_src```

3. Download DAQ (Data Aquisition) library dan Snort dari website

> ```wget https://www.snort.org/downloads/snort/daq-2.0.6.tar.gz```

> ```wget https://www.snort.org/downloads/snort/snort-2.9.11.tar.gz```

4. Ekstrak dan masuk ke dalam folder DAQ tersebut

> ```tar -xvzf daq-2.0.6.tar.gz```

> ```cd daq-2.0.6```

5. Jalankan script konfigurasi dan install DAQ

> ```./configure && make && sudo make install```

6. Kembali ke folder file instalasi lalu ekstrak dan masuk ke dalam folder Snort

> ```tar -xvzf snort-2.9.9.0.tar.gz```

> ```cd snort-2.9.9.0```

7. Jalankan script konfigurasi dan install Snort

> ```./configure --enable-sourcefire && make && sudo make install```

Done!!!
