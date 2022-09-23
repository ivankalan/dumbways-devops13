# Reverse Proxy dan Load Balancing

## Reverse Proxy

Reverse proxy adalah konfigurasi standar yang digunakan untuk mengubah jalur traffic, misalkan aplikasi menggunakan port 3000 tetapi agar dapat di akses melalui port 80 maka harus menggunakan reverse proxy. Disini saya menggunakan webs server nginx yang akan saya konfigurasi dengan reverse proxy

  - Pertama masuk ke folder nginx lalu buat direktori baru

        cd /etc/nginx
   
![Screenshot from 2022-09-01 20-07-12](https://user-images.githubusercontent.com/56712612/187921341-af07d7bb-4653-4585-baed-317a4540f449.png)

    sudo mkdir hotcig
    
![Screenshot from 2022-09-01 20-08-55](https://user-images.githubusercontent.com/56712612/187921757-32da7914-7e6e-4411-8ecc-6eeef3e36ff3.png)

  - Masuk ke direktori yang sudah dibuat tadi, lalu buat file dengan nama `reverse-proxy.conf`

        cd hotcig
        
 Lalu
 
    sudo nano reverse-proxy.conf
    
![Screenshot from 2022-09-01 20-17-29](https://user-images.githubusercontent.com/56712612/187923517-2a7d807c-516e-4b85-b001-c80cb30bf8f9.png)
 
 Lalu ketikkan konfigurasi berikut ke dalam file `reverse-proxy.conf`
 
    server { 
        server_name mydomain.xyz; 

        location / { 
                 proxy_pass http://127.0.0.1:3000;
        }
    }
    
![Screenshot from 2022-09-01 20-19-30](https://user-images.githubusercontent.com/56712612/187923902-25bbc1d3-4e43-42f4-9964-d11107a5a701.png)

  - Setelah itu simpan file nya, keluar dari direktori `hotcig`  dan masuk ke file `nginx.conf`

![Screenshot from 2022-09-01 20-22-23](https://user-images.githubusercontent.com/56712612/187924506-eeeca865-b5a9-45e1-addc-b522f6d017c6.png)

  - Pergi ke bagian include, lalu masukkan lokasi direktori yang berisi konfigurasi tadi dan simpan

![Screenshot from 2022-09-01 20-24-16](https://user-images.githubusercontent.com/56712612/187924922-905592df-442e-4b5b-8ab4-8d6239a634b3.png)

  - Lalu cek konfigurasi yang sudah dibuat tadi menggunakan perintah berikut

        sudo nginx-t

![Screenshot from 2022-09-01 20-26-00](https://user-images.githubusercontent.com/56712612/187925258-a718b7e9-66ae-4bce-9a21-8af05ca6b4ef.png)

  - Lalu restart nginx

        sudo systemctl restart nginx

![Screenshot from 2022-09-01 20-27-11](https://user-images.githubusercontent.com/56712612/187925517-ad1aab8a-543b-42be-b100-e85449bca435.png)

  - Lalu sekarang buat virtual host, untuk membuat virtual host masuk ke server lokal dan ketikkan perintah berikut

        sudo nano /etc/hosts
        
![Screenshot from 2022-09-01 21-03-58](https://user-images.githubusercontent.com/56712612/187933756-4d906975-113f-4699-b19c-7d0525ac1db3.png)

  - Lalu ketikkan IP dari server tadi dan nama domain yang di inginkan

![Screenshot from 2022-09-01 21-05-23](https://user-images.githubusercontent.com/56712612/187934124-56409faf-7a2e-42ce-9127-7a352305e5ae.png)

  - Setelah itu buka web browser dan ketikkan nama domain tadi, jika keluar 502 bad gateway seperti gambar dibawah, itu sudah benar karena pada server belum di install aplikasi, sekarang coba untuk install aplikasi wayshub

        git clone https://github.com/dumbwaysdev/wayshub-frontend.git

![Screenshot from 2022-09-01 21-13-25](https://user-images.githubusercontent.com/56712612/187935820-cf63e0cf-0806-4b4f-830a-ff493fd0ed51.png)

    cd wayshub-frontend
    
lalu

    npm install

![Screenshot from 2022-09-01 21-42-13](https://user-images.githubusercontent.com/56712612/187942591-0970e9ba-aedb-4e48-b2f5-abcedec39c7d.png)

    npm start
    
![Screenshot from 2022-09-01 21-46-08](https://user-images.githubusercontent.com/56712612/187943656-3a41e998-bb2b-4700-ba9f-cab420ae20ca.png)

  - Lalu refresh browser tadi dan sudah berhasil

![Screenshot from 2022-09-01 21-45-55](https://user-images.githubusercontent.com/56712612/187943793-9cd99c80-b15a-4ddc-8f32-8ff5489ec3d5.png)

## Load Balancing

Load Balancing adalah suatu jaringan komputer yang menggunakan metode untuk mendistribusikan beban kerjaan pada dua atau bahkan lebih suatu koneksi jaringan secara seimbang agar pekerjaan dapat berjalan optimal dan tidak overload (kelebihan) beban pada salah satu jalur koneksi.

  - Untuk membuat konfigurasi load balancing, buatlah satu server baru terlebih dahulu dan install aplikasi pada server baru tersebut

![Screenshot from 2022-09-01 22-14-53](https://user-images.githubusercontent.com/56712612/187951479-e703866a-ab60-49d9-90c4-14c572ac7406.png)

![Screenshot from 2022-09-01 22-22-01](https://user-images.githubusercontent.com/56712612/187951671-606672a0-de9f-48ea-8cc3-eab743634c7f.png)

![Screenshot from 2022-09-01 22-23-46](https://user-images.githubusercontent.com/56712612/187952038-7b34e119-f608-49c5-b70a-f8a1bbb862cd.png)

  - Sekarang kita sudah punya 2 server untuk aplikasinya, untuk membuat konfigurasi load balancing, masuk ke file konfigurasi reverse proxy yang sudah dibuat tadi dan tambahkan konfigurasi dibawah ini:

![Screenshot from 2022-09-01 22-25-13](https://user-images.githubusercontent.com/56712612/187953629-1b3903c9-5501-4bf5-9495-98181f1d3e48.png)


        upstream domain { 
            server 192.168.64.6:3000;
            server 192.168.64.2:3000;
        }
        server { 
            server_name mydomain.xyz; 

            location / { 
                     proxy_pass http://domain;
            }
        }

![Screenshot from 2022-09-01 22-30-16](https://user-images.githubusercontent.com/56712612/187953593-3413ee77-6a1a-4b62-b10c-83d4f09fe4ac.png)

  - Keterangan :
    - Pada bagian upstream kalian dapat mengganti nama domain dengan nama yang kalian inginkan.

    - Pada bagian server masukan IP dari server kalian, setelah itu diikuti dengan port aplikasi.

    - Selanjutnya pada bagian proxy_pass ubah dari yang sebelumnya adalah alamat IP dari aplikasi kalian, sekarang kalian samakan dengan nama upstream yang ada di konfigurasi kalian.

    - Jika sudah sekarang kita coba cek apakah konfigurasi yang sudah kita buat tadi itu error atau tidak.

          sudo nginx -t 

![Screenshot from 2022-09-01 22-31-50](https://user-images.githubusercontent.com/56712612/187954837-3faa9a41-679b-4906-b707-56109c749e44.png)

  - Lalu restart nginx untuk memperbarui konfigurasi yang sudah dibuat

![Screenshot from 2022-09-01 22-37-49](https://user-images.githubusercontent.com/56712612/187955103-a40c5dc3-68fc-498b-8459-d543d77173a7.png)

  - Lalu jalankan aplikasi yang ada pada server ini, dan cek di browser menggunakan domain tadi

![Screenshot from 2022-09-01 22-40-00](https://user-images.githubusercontent.com/56712612/187955570-f7d67df3-739f-44f1-a32d-d6fda37c8ec4.png)

![Screenshot from 2022-09-01 22-40-18](https://user-images.githubusercontent.com/56712612/187955641-44e508be-676c-4e4d-a847-2bffc274e40a.png)

  - Lalu untuk mengecek apakah load balancing sudah berjalan atau tidak, coba matikan satu server dan refresh webnya

![Screenshot from 2022-09-01 22-41-28](https://user-images.githubusercontent.com/56712612/187955930-db4040f4-ca11-48ae-a924-b866c0460b25.png)

![Screenshot from 2022-09-01 22-42-59](https://user-images.githubusercontent.com/56712612/187956249-43481c0b-e996-4462-ac26-66e1ba5df4b0.png)

# Konfigurasi pm2 dengan reverse proxy dan load balancing

  - Pertama install dulu pm2 pada kedua server menggunakan perintah berikut
        
        sudo npm install pm2 -g
       
   - ini install diserver roamer (pertama)
       
![Screenshot from 2022-09-01 22-52-02](https://user-images.githubusercontent.com/56712612/187958296-18366369-5381-405a-beeb-cafc3e0b7ea5.png)

   - ini install diserver jungler (kedua)

![Screenshot from 2022-09-01 22-54-15](https://user-images.githubusercontent.com/56712612/187958826-ebe34e79-3b2d-4190-8bc7-0dfbec218765.png)

  - Lalu masuk ke direktori aplikasi tadi
    
        cd wayshub-frontend

  - Lalu ketikkan perintah berikut untuk mengaktifkan pm2

        pm2 start --name wayshub npm -- start

![Screenshot from 2022-09-01 23-35-14](https://user-images.githubusercontent.com/56712612/187966668-88a7f2c2-1e28-486f-8f64-91c82f9dda02.png)

  - Lalu buka browser anda dan ketikkan domain yang sudah dibuat, jadi meski terminal anda tutup aplikasi anda tetap berjalan karena sudah terintegrasi dengan pm2

![Screenshot from 2022-09-01 23-35-40](https://user-images.githubusercontent.com/56712612/187966854-17843a0c-97f3-428e-bebf-434a1dd65085.png)
