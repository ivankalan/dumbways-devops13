# Konfigurasi Apache2 agar dapat di akses publik dengan localtunnel
Disini saya akan mengerjakan beberapa task yaitu:
  - Ganti IP lama dengan IP baru
  - Install Web Server Apache2 secara manual
  - Apache2 dapat diakses melalui browser menggunakan IP
  - Konfigurasi Apache2 agar dapat di akses publik dengan localtunnel

## Mengganti IP lama dengan IP baru
Langkah pertama jika ingin mengganti IP dari server yang sudah dibuat, bisa menggunakan perintah berikut:

    sudo nano /etc/netplan/00-installer-config.yaml
    
Jika sudah maka akan muncul text editor seperti gambar dibawah ini. Selanjutnya di bagian addresses, bisa ubah dengan IP yang di inginkan. Lalu untuk keluar dari teks editor ini bisa menggunakan ctrl + x lalu Y setelah itu Enter.

![Screenshot from 2022-08-25 14-11-47](https://user-images.githubusercontent.com/56712612/186599158-986c44d0-d88f-412f-aa7e-84168446a186.png)

Selanjutnya untuk mengkonfirmasi customisasi IP yang sudah dibuat tadi, bisa menggunakan perintah dibawah.

    sudo netplan apply
  
Jika sudah, maka bisa di cek apakah sudah terhubung dengan internet atau tidak menggunakan perintah dibawah.

    ping google.com
    
Jika sudah terhubung dengan internet maka akan muncul notifikasi seperti gambar di bawah ini.

![Screenshot from 2022-08-25 14-14-21](https://user-images.githubusercontent.com/56712612/186599707-c0db780c-5b4f-4fe2-a068-ffd862b4d84f.png)

## Install web server Apache2 secara manual dan mengakses Apache2 melalui browser menggunakan alamat IP
Melanjutkan dari langkah diatas, jika ingin menginstall web server Apache2 secara manual, hal pertama yang harus dilakukan adalah mengecek apakah ada update dari paket terbaru menggunakan perintah berikut:

    sudo apt update; sudo apt upgrade
    
Selanjutnya langsung saja untuk menginstall web server Apache2 menggunakan perintah dibawah ini:

    sudo apt install apache2
    
Lalu nanti akan muncul notifikasi Do you want to continue? [Y/n] ketik saja Y. Jika sudah maka instalasi akan berjalan.

![Screenshot from 2022-08-25 14-25-58](https://user-images.githubusercontent.com/56712612/186602198-cba611cc-ad38-49b0-9ee0-35e261f3e189.png)

Jika instalasi sudah selesai, cek status apache2 dengan menggunakan perintah dibawah ini.

    sudo systemctl status apache2
    
![Screenshot from 2022-08-25 14-40-45](https://user-images.githubusercontent.com/56712612/186605164-be39137a-fbe3-48f5-89a6-9785b5355764.png)

Sekarang coba buka browser, lalu masukkan IP dari server kalian.

![Screenshot from 2022-08-25 14-41-48](https://user-images.githubusercontent.com/56712612/186605302-7170c1cd-8e7a-4353-92b1-11ffcc792b55.png)

##Konfigurasi Apache2 agar dapat di akses publik dengan localtunnel

Melanjutkan langkah diatas, agar Apache2 bisa diakses publik melalui localtunnel, langkah pertama adalah menginstall node.js menggunakan nvm, untuk bisa melakukan instalasi ikuti langkah-langkah dibawah ini:

Pertama ketik diterminal perintah berikut :

    sudo apt install curl
    
![Screenshot from 2022-08-25 14-49-00](https://user-images.githubusercontent.com/56712612/186606795-242d5811-8a1f-4de5-a991-78da0ab0d7bc.png)

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    
![Screenshot from 2022-08-25 14-49-48](https://user-images.githubusercontent.com/56712612/186606974-7c9cf159-4119-4e76-838e-19725bcc67ce.png)

    exec bash
    
lalu

    nvm install 14    
    
lalu

    node -v
     
lalu     

    npm -v
    
![Screenshot from 2022-08-25 14-54-48](https://user-images.githubusercontent.com/56712612/186608135-f57aacac-e11c-4785-bd41-8006cb558b12.png)

Selanjutnya lakukan instalasi localtunnel menggunakan npm yang sudah di install tadi

    npm install -g localtunnel

![Screenshot from 2022-08-25 14-56-09](https://user-images.githubusercontent.com/56712612/186608425-eebc9cea-2069-48ec-ad2f-6a2a195c1e30.png)

Lalu install lagi Apache2 sama seperti sebelumnya

    sudo apt install apache2
    
![Screenshot from 2022-08-25 14-57-44](https://user-images.githubusercontent.com/56712612/186608777-e8218fad-03eb-4707-890b-4788d8fbe332.png)

Jika telah selesai melakukan instalasi Apache2, Selanjutnya coba untuk mengakses Apache2 di web browser untuk mengecek apakah Apache2 sudah berjalan atau belum.

Ketikkan alamat IP di browser kalian.

![Screenshot from 2022-08-25 15-00-08](https://user-images.githubusercontent.com/56712612/186609287-ba959470-acf1-4564-a3bb-fe938a3b66bc.png)

Sekarang coba menggunakan localtunel untuk web server Apache2 yang sudah di install tadi.

Untuk menjalankan localtunel, ketikkan perintah di bawah ini.

    lt --port 80

![Screenshot from 2022-08-25 15-02-14](https://user-images.githubusercontent.com/56712612/186609761-c44ee436-a6ca-4b4c-ad10-2551c90640e8.png)

keterangan : pastikan dibagian port telah sesuai dengan aplikasi kalian. Karena setiap aplikasi pasti mempunyai port yang berbeda-beda, contoh saja dari aplikasi node.js, aplikasi node.js biasanya berjalan di atas port 3000.

Jika sudah copy url yang ada di terminal lalu buka browser dan paste url yang telah dicopy tadi.

![Screenshot from 2022-08-25 15-04-01](https://user-images.githubusercontent.com/56712612/186610174-914e31e5-5bc0-4e85-9e4b-79cca9a52b60.png)

Jika sudah klik tombol Click to Continue.

Setelah itu, aplikasi Apache2 tadi sudah bisa diakses oleh publik.

![Screenshot from 2022-08-25 15-04-09](https://user-images.githubusercontent.com/56712612/186610462-11fa69cc-5ee3-4858-9690-d6b4c8bd41f9.png)
