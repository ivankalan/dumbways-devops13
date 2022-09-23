# Manage Database & Setup Backend

## Setup ssh key antar server

  - Siapkan 2 buah server, lalu jalankan command `ssh-keygen` dikedua server untuk membuat `ssh key`

![Screenshot from 2022-09-07 19-53-18](https://user-images.githubusercontent.com/56712612/189060833-317d4597-629e-4516-9950-9a07f71d698d.png)

  - Lalu jalankan command berikut

        ssh-copy-id username@user-ip 

![Screenshot from 2022-09-08 14-31-55](https://user-images.githubusercontent.com/56712612/189062362-0d549090-682b-483b-865e-d60239e34a14.png)

  - Lakukan hal yang sama pada server satunya
  - Jika selesai maka ketik command berikut agar bisa berpindah antar server dengan mudah

        ssh username@user-ip
        
  ![Screenshot from 2022-09-08 14-34-25](https://user-images.githubusercontent.com/56712612/189062868-0cd9e565-ab74-42fd-8873-fe78982913d8.png)
  
## Instalasi dan konfigurasi database MySql

  - Saya sudah menyiapkan server sendiri di IDCloudHost yang nanti akan saya gunakan sebagai database dan aplikasi backend nya
  
![Screenshot from 2022-09-08 14-53-53](https://user-images.githubusercontent.com/56712612/189066878-8e3847fd-7842-47b7-90a9-f2014462e2a6.png)

  - Install MySql menggunakan command berikut
  
        sudo apt install mysql-server

![Screenshot from 2022-09-08 14-55-12](https://user-images.githubusercontent.com/56712612/189067249-d921ea94-42f5-47b4-b6c4-63ee3cab95e2.png)

  - Jalankan mysql
  
![Screenshot from 2022-09-08 22-26-37](https://user-images.githubusercontent.com/56712612/189162605-7dbffc46-08aa-439e-bbd1-5148eeb67da1.png)

  - Buat password untuk root

![Screenshot from 2022-09-08 22-32-00](https://user-images.githubusercontent.com/56712612/189163884-5498524d-a3da-40e3-b73d-a01d9ac5662b.png)

  - Jalankan secure installation mysql

![Screenshot from 2022-09-08 22-36-06](https://user-images.githubusercontent.com/56712612/189164723-b603c7f9-73f2-44d4-99aa-f1c99de9cacb.png)

  - Buka mysql sebagai root dan buat user baru

![Screenshot from 2022-09-08 22-37-48](https://user-images.githubusercontent.com/56712612/189165135-f7c2bf31-c8f8-47a2-9291-31d51425f96c.png)

  - Beri privilege pada user baru

![Screenshot from 2022-09-08 22-39-46](https://user-images.githubusercontent.com/56712612/189165617-eeb06c9e-c8dc-40b1-9f60-8c46189fc416.png)

  - Buat database baru menggunakan user yang sudah dibuat

![Screenshot from 2022-09-08 22-58-44](https://user-images.githubusercontent.com/56712612/189169725-3b55a058-ad2c-4193-83eb-45a3efabd77d.png)


  - Buka direktori `/etc/mysql/mysql.conf.d/mysqld.cnf`

        sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

    Ubah `bind-address` dan `mysqlx-bind-address` menjadi seperti ini
        
        bind-address: 0.0.0.0
        mysqlx-bind-address: 0.0.0.0
        
![Screenshot from 2022-09-08 16-41-49](https://user-images.githubusercontent.com/56712612/189091367-1ae4823a-1446-4109-8513-e3313c862870.png)
     
  - Restart service mysql

        sudo systemctl restart mysql     

## Setup aplikasi backend

  - Clone aplikasi dumbflix

        git clone https://github.com/dumbwaysdev/dumbflix-backend.git

![Screenshot from 2022-09-08 17-38-20](https://user-images.githubusercontent.com/56712612/189101904-7356489c-2d23-4aed-a02e-d0723bd2dadc.png)

  - Install sequelize

        npm install sequelize-cli

![Screenshot from 2022-09-08 23-07-58](https://user-images.githubusercontent.com/56712612/189171629-f6b864e1-9fbe-4179-984b-6ab1da1d1975.png)

  - Install node versi 10 menggunakan nvm

![Screenshot from 2022-09-08 23-09-08](https://user-images.githubusercontent.com/56712612/189171879-026870fa-37a9-43ba-88e4-f02c60fa63fc.png)

  - Build aplikasi backend

![Screenshot from 2022-09-08 23-10-36](https://user-images.githubusercontent.com/56712612/189172185-72da74a2-8958-4d50-87a5-04cee136777e.png)

  - Build dan edit pm2 ecosystem file

![Screenshot from 2022-09-08 23-13-02](https://user-images.githubusercontent.com/56712612/189172706-4686b954-f235-41a2-899f-1f293cdd181f.png)

![Screenshot from 2022-09-08 23-14-55](https://user-images.githubusercontent.com/56712612/189173051-9572165f-23a9-45bf-a293-c9853b4c7a1e.png)

  - Edit file `config.json`

![Screenshot from 2022-09-08 23-16-24](https://user-images.githubusercontent.com/56712612/189174118-51745cb5-5ec7-40b1-a610-0ee11f61e1b6.png)

![Screenshot from 2022-09-08 23-20-07](https://user-images.githubusercontent.com/56712612/189174126-46a8f7e7-8548-4899-ac23-13d7df4b0102.png)

  - Migrate isi database aplikasi ke database server menggunakan sequelize

![Screenshot from 2022-09-08 23-21-42](https://user-images.githubusercontent.com/56712612/189174557-f594e9de-90f4-4b96-b35f-4ee2a7a4899e.png)

  - Cek apakah database sudah berhasil di migrate

![Screenshot from 2022-09-08 23-24-09](https://user-images.githubusercontent.com/56712612/189175084-ea336fd8-7ab6-417b-888f-7cfa7de66736.png)

  - Kembali dan jalankan aplikasi melalui pm2

![Screenshot from 2022-09-08 23-26-28](https://user-images.githubusercontent.com/56712612/189175607-5ce4ce25-1d54-403c-a6db-d365fac1062f.png)

  - Buka browser dan ketikkan alamat aplikasi

![Screenshot from 2022-09-08 23-27-06](https://user-images.githubusercontent.com/56712612/189175674-f3b359b7-630d-49ee-b31f-80400e3583c6.png)

  - Membuat konfigurasi reverse proxy

![Screenshot from 2022-09-08 23-43-48](https://user-images.githubusercontent.com/56712612/189178969-f2441bcc-d924-4c41-abcb-c21eb6a713de.png)

![Screenshot from 2022-09-08 23-41-44](https://user-images.githubusercontent.com/56712612/189178982-697f0e13-7171-41c9-b576-52b4db290a57.png)

  - Buat domain baru di cloudflare

![Screenshot from 2022-09-08 23-56-04](https://user-images.githubusercontent.com/56712612/189181360-cecb0f95-efba-4899-bb86-536a92d595af.png)

  - Coba akses domain yang sudah dibuat di browser
  - disini perlu untuk mendeploy ssl certificate menggunakan certbot agar domain bisa terkoneksi dengan aman

![Screenshot from 2022-09-08 23-57-47](https://user-images.githubusercontent.com/56712612/189181724-7c7c9ffc-c801-4187-8935-bce68b5b4d79.png)

  - Setup cerbot
  - Install core

![Screenshot from 2022-09-09 00-02-24](https://user-images.githubusercontent.com/56712612/189182461-d024805a-4173-4783-8edc-d294db0b146c.png)

  - install certbot

![Screenshot from 2022-09-09 00-04-08](https://user-images.githubusercontent.com/56712612/189182730-8b9fb945-fd62-44f7-9dbe-c35448c5b27a.png)

  - Jalankan certbot dan konfigurasi certbot  

![Screenshot from 2022-09-09 00-41-21](https://user-images.githubusercontent.com/56712612/189190185-aad4eec6-0d19-4fd2-a62c-28feb42ba914.png)

  - Buka cloudflare, dan atur domain menjadi `DNS only`

![Screenshot from 2022-09-09 00-43-29](https://user-images.githubusercontent.com/56712612/189190663-6d3ed21d-c60d-417f-a2bb-8df6941e4939.png)

  - Restart nginx

  - Buka kembali aplikasi backend melalui web browser

![Screenshot from 2022-09-09 00-45-48](https://user-images.githubusercontent.com/56712612/189191172-1fddfbfe-d5bb-4e18-8b7e-c20042abec20.png)

## Integrasi aplikasi frontend dan backend

  - Masuk ke direktori aplikasi frontend dan edit file `src/config/api.js`

![Screenshot from 2022-09-09 00-50-54](https://user-images.githubusercontent.com/56712612/189191725-db63130d-ae34-4702-a9f8-a4968ce1e344.png)

  - Buka aplikasi dan register user baru

![Screenshot from 2022-09-09 09-08-52](https://user-images.githubusercontent.com/56712612/189264966-9fb9d319-2679-4a51-9e54-9528506a5462.png)

  - Jika berhasil maka akan muncul profile seperti ini

![Screenshot from 2022-09-09 10-14-24](https://user-images.githubusercontent.com/56712612/189265085-ecd693cd-6304-4fb7-8922-4c673e653d69.png)
