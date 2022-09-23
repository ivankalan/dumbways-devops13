# Cara menggunakan text editor nano, memanipulasi text, memonitoring server, dan mengatur firewall pada server

## 1. Menggunakan text editor nano

Text editor adalah aplikasi/software yang memungkinkan seseorang untuk membuka, melihat, dan mengedit file plain text atau teks biasa. Disini saya akan membahas mengenai nano yaitu text editor yang berjalan di atas terminal dan merupakan text editor default dari sistem operasi Linux. Jika ingin memanage sebuah server maka wajib mengetahui penggunaan text editor nano ini karena diserver tidak ada aplkasi berbasis GUI.

  ### - Cara membuka nano

Karena nano sudah default terinstall pada sistem operasi Linux, maka tidak perlu repot lagi untuk menginstallnya, ketikkan perintah berikut untuk membuka nano:

    nano
    
![Screenshot from 2022-08-30 14-07-34](https://user-images.githubusercontent.com/56712612/187372423-d9ea23f5-b5dc-4da4-a944-08c30b0c4dee.png)

![Screenshot from 2022-08-30 14-07-58](https://user-images.githubusercontent.com/56712612/187372488-5e57b67e-3e14-427b-afd0-036ab993a309.png)
  
Untuk membuka sebuah file menggunakan nano:

    nano (nama-file)
    
![Screenshot from 2022-08-30 14-08-32](https://user-images.githubusercontent.com/56712612/187372615-5fbeb355-e54b-45fd-9140-3754dfee0237.png)

![Screenshot from 2022-08-30 14-09-04](https://user-images.githubusercontent.com/56712612/187372691-50e64d70-a145-470b-8ee4-2b8e8d091cb0.png)

atau

    nano (location/folder/nama-file)
    
![Screenshot from 2022-08-30 14-12-13](https://user-images.githubusercontent.com/56712612/187373316-12321ac2-44eb-4ab3-a976-427f18fd2587.png)

![Screenshot from 2022-08-30 14-12-21](https://user-images.githubusercontent.com/56712612/187373341-90011a42-5421-46a9-be60-28f348defb13.png)

  ### - Shortcut nano
  
#### 1. Keluar dan menyimpan file dari text editor nano

Tekan `ctrl+x` lalu ketik Y dan enter
    
![Screenshot from 2022-08-30 14-14-27](https://user-images.githubusercontent.com/56712612/187373721-730f2db3-77be-40d4-bd81-5b1cc4f53b82.png)

Atau jika ingin menyimpan saja tanpa keluar nano, tekan `ctrl+o` dan enter

![Screenshot from 2022-08-30 14-33-01](https://user-images.githubusercontent.com/56712612/187377626-f35e8cc7-8520-42ce-8c10-fc3a6d74fb5d.png)

#### 2. Mencari text

Tekan `ctrl+w` dan ketikkan text yang ingin dicari lalu enter
    
![Screenshot from 2022-08-30 14-36-42](https://user-images.githubusercontent.com/56712612/187378195-6528f451-db26-43a3-8fda-d58dc2d16ed4.png)

#### 3. Memilih text

Tekan `alt+a` untuk memilih text, cukup arahkan kursor ke text yang ingin dipilih

![Screenshot from 2022-08-30 14-48-01](https://user-images.githubusercontent.com/56712612/187381103-391a4f2e-ecc0-420a-9f4f-476efb5476d4.png)

#### 4. Copy dan Paste

Tekan `alt+6` untuk mengcopy text yang telah dipilih tadi dan tekan `ctrl+u` untuk paste

![Screenshot from 2022-08-30 14-48-01](https://user-images.githubusercontent.com/56712612/187381393-27099ed7-c12b-497d-908d-c5dc4d64cbcb.png)

![Screenshot from 2022-08-30 14-49-18](https://user-images.githubusercontent.com/56712612/187381406-179ed596-08ae-4fa1-9932-b48f381de286.png)

#### 5. Cut dan Paste

Tekan `ctrl+k` untuk mengcut text yang sudah di pilih tadi dan tekan `ctrl+u` untuk paste

![Screenshot from 2022-08-30 14-58-25](https://user-images.githubusercontent.com/56712612/187382625-f8ad0856-64ce-45c9-bad7-3c24708da072.png)

![Screenshot from 2022-08-30 14-57-40](https://user-images.githubusercontent.com/56712612/187382714-0ce1cfa4-50cf-407d-a70c-3de235bf9383.png)

#### 6. Pindah kursor

Tekan `ctrl+a` untuk pindah kursor ke awal baris, dan tekan `ctrl+e` untuk pindah ke akhir baris

![Screenshot from 2022-08-30 15-17-02](https://user-images.githubusercontent.com/56712612/187386424-a6fb03b1-5de8-4346-ab71-96fb39a811b0.png)

![Screenshot from 2022-08-30 15-17-22](https://user-images.githubusercontent.com/56712612/187386493-ce197c6d-2c85-4702-aac7-d78c5f89cf63.png)

#### 7. Mengambil isi dari file lain

![Screenshot from 2022-08-30 18-36-26](https://user-images.githubusercontent.com/56712612/187427119-435da41b-45e5-4f27-9a82-23402dd1da3a.png)

Disini saya punya file `index.html` didalam direktori test, dan saya akan mengambil isi dari file `index.html` dan memasukkannya kedalam file readme.md

tekan `ctrl+r` untuk mengambil isi suatu file dan masukkan lokasi file yang isinya ingin diambil

![Screenshot from 2022-08-30 18-47-01](https://user-images.githubusercontent.com/56712612/187428942-9609c586-a711-4011-aa18-a66fcb40cae0.png)

![Screenshot from 2022-08-30 18-47-16](https://user-images.githubusercontent.com/56712612/187428962-5d4f59d1-d285-4b5d-8069-409e2a8f8c7a.png)

## 2. Memanipulasi text

Berikut adalah beberapa perintah yang digunakan dalam memanipulasi teks

### 1. cat

`cat` adalah perintah yang digunakan untuk membaca suatu file, tapi bisa juga digunakan untuk menggabungkan 2 buah file menjadi 1

membaca file:

    cat (nama-file)

![Screenshot from 2022-08-30 19-05-44](https://user-images.githubusercontent.com/56712612/187432308-9a0a5405-2037-4295-95d4-f2fd780feb08.png)

menggabungkan isi 2 file menjadi 1

    cat file1 file2 > file3
    
![Screenshot from 2022-08-30 19-08-46](https://user-images.githubusercontent.com/56712612/187432959-32c9adfa-cafe-4ed0-8512-c6af50c8fc1a.png)
   
### 2. sed

Sed adalah singkatan dari stream editor. Gunanya untuk memanipulasi teks dasar pada file. Dengan sed kita dapat mengganti teks dengan cepat.

![Screenshot from 2022-08-30 19-21-55](https://user-images.githubusercontent.com/56712612/187435318-b88cb145-a099-47a9-95e9-77b59da8bdfb.png)

### 3. grep

Grep merupakan perintah untuk melakukan pencarian sebuah text didalam file yang telah dibuat.

    grep text-yang-dicari direktori-teks

![Screenshot from 2022-08-30 19-36-25](https://user-images.githubusercontent.com/56712612/187438319-dd1b1f77-8c33-4d47-924c-1e51735b1f5a.png)

Mencari text dalam sebuah file

    grep -c text-yang-dicari direktori-teks

![Screenshot from 2022-08-30 19-39-37](https://user-images.githubusercontent.com/56712612/187438814-a5a421f2-0d32-4a70-9b5b-f9dd59e21c2a.png)

Menghitung jumlah text yang ditulis dalam sebuah file
    
    grep text-yang-dicari *

![Screenshot from 2022-08-30 19-42-40](https://user-images.githubusercontent.com/56712612/187439520-06bcfc06-84bf-4248-8366-12de3a590b5c.png)

Mencari text didalam semua direktori

## 3. Memonitoring server

Monitoring adalah aktivitas untuk melihat kinerja sistem secara realtime. Berikut ini adalah beberapa perintah yang dapat kita gunakan untuk memonitoring sebuah server.

### 1. htop

htop merupakan perintah untuk memonitoring sistem, kita dapat melihat penggunaan memory, cpu, swap. Ketikkan perintah `htop` diterminal untuk membukanya, jika htop belum terinstall maka install dulu menggunakan perintah dibawah

    sudo apt install htop -y
  
Lalu buka htop dengan ketik `htop` diterminal

![Screenshot from 2022-08-30 20-04-15](https://user-images.githubusercontent.com/56712612/187444466-5e702978-10b4-44d5-96fd-977ab0ef5905.png)

Keterangan :
  - CPU adalah berapa jumlah core yang kita miliki.
  - Mem adalah total penggunaan memory.
  - Swp adalah Memory cadangan.
  - Tasks adalah aplikasi yang sedang berjalan di server.
  - Load average adalah rata-rata aplikasi yang berjalan.
  - Uptime adalah berapa lama server kita hidup.
  - PID adalah nomor proses id setiap proses yang berjalan di linux.
  - VIRT adalah memory yang terpakai.
  - Command adalah perintah apa yang sedang di jalankan.
  
### 2. nmon
  
Untuk instalasi nmon bisa menggunakan perintah berikut:
  
      sudo apt install nmon
    
![Screenshot from 2022-08-30 20-09-22](https://user-images.githubusercontent.com/56712612/187448718-3a56cbff-e080-4417-ad28-72a6dbb5bdc2.png)
  
Lalu untuk menjalankannya ketikkan `nmon` diterminal

![Screenshot from 2022-08-30 20-10-30](https://user-images.githubusercontent.com/56712612/187448851-6bd883ba-3c83-4668-8386-6cc61dc80fbe.png)

Keterangan : Kita dapat memilih ingin memonitoring apa saja, Disini kita coba saja untuk menampilkan beberapa saja.
  - c adalah CPU
  - m adalah Memory
  - d adalah Disk
  - n adalah network

### 3. lsof

Lsof merupakan singkatan list open files, berfungsi untuk melihat seluruh file yang terbuka berdasarkan proses aktif yang berjalan di sistem. Ketikkan perintah dibawah untuk membuka lsof

    lsof
    
![Screenshot from 2022-08-30 20-33-05](https://user-images.githubusercontent.com/56712612/187450652-89b82f09-0d9a-49d0-ac02-38b9ac25fa62.png)
  
### 4. ps

Ps merupakan singkatan dari process status, untuk mengetahui daftar proses yang berjalan pada sistem. Untuk menjalankan ps ketikkan perintah berikut ini.

    ps -f -u (your-user)
    
![Screenshot from 2022-08-30 20-36-06](https://user-images.githubusercontent.com/56712612/187451613-18eec404-6556-4111-ad4e-8886492fb5e6.png)
 
## 4. Mengatur firewall pada server     

Untuk melakukan Instalasi ufw bisa menggunakan perintah dibawah ini

    sudo apt install ufw -y
    
![Screenshot from 2022-08-30 21-15-33](https://user-images.githubusercontent.com/56712612/187460801-057d4196-3d0a-4400-9076-7e022af713f8.png)

Untuk mengaktifkan firewall ketikkan perintah `sudo ufw enable` diterminal dan untuk melihat status ufw bisa ketikkan `sudo ufw status` diterminal

![Screenshot from 2022-08-30 21-25-05](https://user-images.githubusercontent.com/56712612/187463040-f4367594-8115-46be-a20c-250350cfbb29.png)

![Screenshot from 2022-08-30 21-25-25](https://user-images.githubusercontent.com/56712612/187463148-3749d6f6-b84c-4456-9ebe-05e94de05cb4.png)

Lalu jika ingin mengaktifkan ufw pada port tertentu, ketikkan perintah ini diterminal, disini saya ingin mengaktifkan firewall untuk port 3000 misalnya

    sudo ufw allow port-yang-dituju

![Screenshot from 2022-08-30 21-27-51](https://user-images.githubusercontent.com/56712612/187463808-07c045f2-c8ee-4eef-a540-37fe73b97414.png)

## Challenge

1. Buat sebuah file bash sederhana yang bertugas untuk update dan upgrade sistem

Pertama buat dulu file yang akan digunakan sebagai wadah dari bash script yang akan ditulis

    touch update

![Screenshot from 2022-08-30 21-32-44](https://user-images.githubusercontent.com/56712612/187464890-3fe175d5-4fc1-4580-ba98-fc1da6c27a22.png)
    
Lalu tulis bash script menggunakan nano didalam file `update` seperti gambar dibawah ini dan simpan

    sudo apt update && sudo apt upgrade -y

![Screenshot from 2022-08-30 21-33-38](https://user-images.githubusercontent.com/56712612/187465062-ae84cad9-03a1-4c97-9aaa-4f625e241eb1.png)

Selanjutnya jalankan bash script yang telah dibuat tadi menggunakan perintah berikut ini

    bash update

![Screenshot from 2022-08-30 21-36-11](https://user-images.githubusercontent.com/56712612/187465669-d7cc2235-3bfc-4455-969f-df26ce95c4ca.png)

2. Buat sebuah file bash serderhana yang bertugas untuk membuat firewall port 22, 80 dan 443 

Sama seperti sebelumnya, buat dulu file yang akan digunakan sebagai wadah dari bash script yang akan ditulis

    touch ufw-allow

![Screenshot from 2022-08-30 21-51-56](https://user-images.githubusercontent.com/56712612/187469807-ed41265a-a71c-4dee-862f-5a0b378fe444.png)

    
Lalu tulis bash script mengguanakan nano didalam file `ufw-allow` seperti gambar dibawah dan simpan

    sudo ufw allow 22 && sudo ufw allow 80 && sudo ufw allow 443
    
![Screenshot from 2022-08-30 21-54-14](https://user-images.githubusercontent.com/56712612/187469957-4dc3f83b-9d54-41ee-8d3d-57a9bf8cee4f.png)

Selanjutnya jalankan bash script yang telah dibuat tadi menggunakan perintah dibawah

    bash ufw-allow
    
![Screenshot from 2022-08-30 21-52-55](https://user-images.githubusercontent.com/56712612/187470021-6179ffa2-1469-49cf-8286-17ca5fb0b24f.png)

Maka jika di cek menggunakan perintah `sudo ufw status` firewall untuk port 22, 80, dan 443 sudah aktif

![Screenshot from 2022-08-30 21-53-12](https://user-images.githubusercontent.com/56712612/187470300-749e1798-2ba4-4ed6-a54d-39f14280e7bf.png)
