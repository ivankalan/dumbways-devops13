# Cloud Computing with IDCloudHost

## Pengertian Cloud Computing

Cloud computing adalah konsep komputasi berbasis internet, dengan cloud computing anda bisa melakukan pekerjaan yang menggunakan komputer seperti menyimpan, mengakses, dan mengolah data dengan mudah. Bedanya jika menggunakan cloud computing perangkat yang digunakan komputasi adalah server, jadi selama ada internet anda bisa mengakses nya kapanpun dimanapun.

## Pengenalan IDCloudHost

PT Cloud Hosting Indonesia (IDCloudHost) Merupakan Salah Satu Web Hosting Provider yang Ada di Indonesia dengan Menawarkan Layanan Seperti Pendaftaran Domain, Cloud Hosting, Server (VPS & Dedicated Server), Reseller Domain & Hosting, dan Beberapa Layanan Lainnya.

## Deploy aplikasi ke server IDCloudHost

  - Buka idcloudhost.com dan login untuk console

![Screenshot from 2022-09-06 14-18-20](https://user-images.githubusercontent.com/56712612/188571608-0e11ea9c-1d27-471f-bc1d-2c637028fbec.png)

  - Setelah login nanti akan muncul dashboard, scroll kebawah dan ganti user sebagai dumbways.dev

![Screenshot from 2022-09-06 14-23-42](https://user-images.githubusercontent.com/56712612/188572420-68175758-4629-460a-b8da-15264c27cac1.png)

  - Klik bagian compute dan pilih create new resource dan lengkapi data yang dibutuhkan lalu klik create

![Screenshot from 2022-09-06 14-26-18](https://user-images.githubusercontent.com/56712612/188572931-78c7e26b-c340-4f5c-8944-82918546414b.png)

  - Lalu setelah proses pembuatan selesai akan muncul informasi seperti ini

![Screenshot from 2022-09-06 14-40-06](https://user-images.githubusercontent.com/56712612/188575705-9fd86952-6ed0-4b25-9d73-48b47e3c6dd9.png)

  - Buka terminal dan akses server yang telah dibuat menggunakan command berikut

        ssh username@public-ip

![Screenshot from 2022-09-06 14-50-30](https://user-images.githubusercontent.com/56712612/188578478-08c89ba2-6102-468f-8330-f4bbf04b9886.png)

  - Install nodejs dan nvm terlebih dahulu
  - Clone aplikasi menggunakan command berikut
          
          git clone https://github.com/dumbwaysdev/dumbflix-frontend

![Screenshot from 2022-09-06 15-38-49](https://user-images.githubusercontent.com/56712612/188588780-117cc786-cd1a-4bae-8ad0-9f79f3dda6aa.png)

  - Lalu install pm2 menggunakan command berikut

        sudo npm install pm2 -g
       
![Screenshot from 2022-09-06 15-54-38](https://user-images.githubusercontent.com/56712612/188592313-ba33078e-b0e9-44a9-86d2-b2feba7d086e.png)
    
  - Lalu buat ecosystem pm2 menggunakan command berikut

        pm2 init simple  

![Screenshot from 2022-09-06 16-14-13](https://user-images.githubusercontent.com/56712612/188596596-817dfedc-afa5-46eb-945c-07e1de0dc092.png)

  - Lalu edit konfigurasi ecosystem pm2 seperti ini

![Screenshot from 2022-09-06 16-15-54](https://user-images.githubusercontent.com/56712612/188597736-7cd00a1d-e708-488f-9c48-d506f637fef0.png)

## Konfigurasi reverse proxy menggunakan nginx

  - Install nginx terlebih dahulu  

![Screenshot from 2022-09-06 16-12-33](https://user-images.githubusercontent.com/56712612/188598153-f0022123-c63d-4e60-88ab-804f90796bea.png)

  - Buka direktori `cd /etc/nginx` dan buat sebuah folder

![Screenshot from 2022-09-06 16-43-03](https://user-images.githubusercontent.com/56712612/188602864-3e7154b2-f47e-49ae-a5af-2654dc859f59.png)

  - Buat sebuah file yang nanti akan digunakan sebagai wadah konfigurasi reverse proxy dan isikan konfigurasi berikut lalu save

        server { 
            server_name domain-anda.my.id; 

            location / { 
                     proxy_pass http://public-ip:3000;
            }
        }

![Screenshot from 2022-09-06 18-28-40](https://user-images.githubusercontent.com/56712612/188624743-ede340a3-8ce6-4351-9256-1ad430740116.png)

  - Setelah di save, keluar dari direktori `ursa` dan masuk ke file `nginx.conf` dan tambahkan lokasi direktori konfigurasi reverse proxy yang tadi sudah dibuat

![Screenshot from 2022-09-06 18-33-41](https://user-images.githubusercontent.com/56712612/188625579-c5ea5d4f-276f-472a-842c-7e3ca8d6152c.png)

  - Lalu cek konfigurasi nginx dengan command berikut
  
        sudo nginx -t

![Screenshot from 2022-09-06 18-36-18](https://user-images.githubusercontent.com/56712612/188626439-c499eb29-93dc-4ae4-b4f6-b8e693ef47bf.png)

  - Lalu restart nginx dengan command berikut

        sudo systemctl restart nginx
        
## Setup domain menggunakan Cloudflare

  - Buka cloudflare.com dan login dengan akun anda atau akun yang sudah disediakan dan pilih domain yang ada diberanda

![Screenshot from 2022-09-06 19-46-48](https://user-images.githubusercontent.com/56712612/188638946-a9cca0c7-ee6d-4906-9d0b-f648543de2e9.png)

  - Pilih bagian `DNS` dimenu bar samping kiri lalu klik add record dan isi username serta ip yang ada di cloudhost tadi dan klik save

![Screenshot from 2022-09-06 19-49-47](https://user-images.githubusercontent.com/56712612/188639555-b6c1ab14-bfcd-4526-a2b9-dd68f8fa40f6.png)

![Screenshot from 2022-09-06 19-50-35](https://user-images.githubusercontent.com/56712612/188639851-2107d01d-4bb9-4b51-82b1-dbc1e7ab5c09.png)

  - Setelah setup domain di cloudflare selesai, buka terminal anda dan jalankan command `pm2 start ecosystem.config.js` untuk menjalankan aplikasi

![Screenshot from 2022-09-06 19-55-53](https://user-images.githubusercontent.com/56712612/188640852-586e5ae4-87ed-4da5-bb4a-9175fa045045.png)

  - Lalu buka browser anda dan ketik domain `ivanka.studentdumbways.my.id`
 
![Screenshot from 2022-09-06 19-57-00](https://user-images.githubusercontent.com/56712612/188641056-552e057a-8295-4ce1-a454-2091dd03c26c.png)
