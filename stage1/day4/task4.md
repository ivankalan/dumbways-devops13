# Version Control System (VCS)
Version Control Systems adalah sebuah tools yang digunakan untuk memanajemen perubahan dari code. Tools ini dapat membantu developer untuk mentracking setiap perubahan yang dilakukan secara terus-menerus. VCS pada dasarnya memiliki database terpusat yang bersifat online, jika ingin menggunakanya maka harus terhubung dengan jaringan.

## Membuat environment git pada sistem operasi Ubuntu
Langkah pertama adalah,install git terlebih dahulu menggunakan perintah berikut

    sudo apt install git

![Screenshot from 2022-08-26 12-46-27](https://user-images.githubusercontent.com/56712612/186831021-6fcbac46-dd1b-4ade-85a2-093e990c19f9.png)

    git --version
    
![Screenshot from 2022-08-26 10-18-26](https://user-images.githubusercontent.com/56712612/186831107-dea78370-88af-481c-969b-d079d43b304f.png)

Setelah itu, masukkan username dan email yang anda gunakan untuk login di website github.com, ketikkan perintah berikut

    git config --global user.name "username-github-anda"
    
Lalu
    
    git config --global user.mail "email-github@gmail.com"

Lalu cek dengan perintah berikut

    git config --list
    
![Screenshot from 2022-08-26 12-52-06](https://user-images.githubusercontent.com/56712612/186831702-05e92ea9-a3ea-4935-b821-243c44f34a18.png)

Setelah itu buat ssh key anda dengan ketikkan perintah dibawah

    ssh-keygen

![Screenshot from 2022-08-26 12-54-52](https://user-images.githubusercontent.com/56712612/186832020-76f0d50e-1f17-4e40-92d8-79ad4c039cb8.png)

Buka file ~/.ssh/id_rsa.pub yang sudah digenerate diatas dengan perintah berikut

    cat /home/ivankalan/.ssh/id_rsa.pub
    
![Screenshot from 2022-08-26 12-57-05](https://user-images.githubusercontent.com/56712612/186832302-c6ecbdb0-15fc-4e17-8e1c-49ee81ba4174.png)

Lalu copy teks diatas dan taruh di github.com > profil > settings > ssh dan gpg keys > klik new ssh key > isi di kolom > lalu klik add SSH key

![Screenshot from 2022-08-26 13-00-25](https://user-images.githubusercontent.com/56712612/186832704-7c6f14c8-446d-4120-9c00-4d143a18c0fb.png)

Jika sudah, cek koneksi ke github dengan perintah dibawah

    ssh -T git@@github.com

![Screenshot from 2022-08-26 13-03-33](https://user-images.githubusercontent.com/56712612/186833091-1ed3b452-8bd0-4227-9c60-14ea58b4f477.png)

## Membuat repository baru dan membuat branch serta mengisinya

Masuk ke direktori yang akan di upload ke github dan ketikkan perintah dibawah

    git init
    
![Screenshot from 2022-08-26 13-06-07](https://user-images.githubusercontent.com/56712612/186833712-5c96b94c-7724-49ca-9dce-897de133dd00.png)

Tambahkan file .gitignore untuk memilih folder atau file yang tidak akan diupload ke github, disini saya tidak akan mengupload folder node_modules, begini caranya

    touch .gitignore
    echo "node_modules" > .gitignore
    
![Screenshot from 2022-08-26 13-14-47](https://user-images.githubusercontent.com/56712612/186834900-1e21592f-f8fd-4be8-89b2-a33a28b74016.png)

Lalu pilih file atau folder yang akan diupload ke github, disini saya akan mengupload semua folder dan file menggunakan perintah berikut

    git add .
    
![Screenshot from 2022-08-26 13-16-42](https://user-images.githubusercontent.com/56712612/186835191-9659ffcd-0a79-4785-9b86-7569c8020ddc.png)

    git status
    
![Screenshot from 2022-08-26 13-19-25](https://user-images.githubusercontent.com/56712612/186835618-9d2b5a4e-65d1-40d4-8343-a532d4bd38f7.png)

Setelah itu, buka web github.com > klik tanda plus disamping profile > klik new repository > dan beri nama repository yang ingin dibuat

![Screenshot from 2022-08-26 13-22-59](https://user-images.githubusercontent.com/56712612/186836204-2007d62f-ca2f-4ace-b87c-33cac91f2852.png)

Lalu copy key ssh repository yang sudah dibuat

![Screenshot from 2022-08-26 13-24-27](https://user-images.githubusercontent.com/56712612/186836419-cd7b6264-ed0b-4c2b-9b82-01025f3e5e48.png)

Lalu kembali ke terminal dan tambahkan remote github dengan ssh key yang sudah dicopy tadi, lalu cek apakah remote sudah terdaftar menggunakan perintah dibawah

    git remote add origin git@github.com:ivankalan/nodejs-demo.git

![Screenshot from 2022-08-26 13-27-06](https://user-images.githubusercontent.com/56712612/186836735-07b4cfe8-a2c1-4d80-9595-245181a9570b.png)

    git remote -v
  
![Screenshot from 2022-08-26 13-28-19](https://user-images.githubusercontent.com/56712612/186836918-cd9bf15b-7e6b-4e4f-8070-3630e517630e.png)

Lalu lakukan commit menggunakan perintah ini

    git commit -m "first commit"

![Screenshot from 2022-08-26 13-29-22](https://user-images.githubusercontent.com/56712612/186837068-99853242-d9e0-487e-b0fb-19982e970861.png)

Selanjutnya, lakukan push dari direktori lokal ke github menggunakan perintah dibawah

    git push origin master

![Screenshot from 2022-08-26 13-31-29](https://user-images.githubusercontent.com/56712612/186837369-c51239df-07ff-4c1e-8a5a-b28cf9d8c182.png)

Lalu cek di github setelah melakukan push

![Screenshot from 2022-08-26 13-32-01](https://user-images.githubusercontent.com/56712612/186837525-6589da5c-dd51-4625-bd3f-4426bf4d5b65.png)

Setelah berhasil, selanjutnya buat branch baru yaitu development, staging, dan production menggunakan perintah dibawah

    'git branch development'
    
    'git branch staging'
    
    'git branch production'
    
![Screenshot from 2022-08-26 13-35-12](https://user-images.githubusercontent.com/56712612/186837939-8ba9a17d-0356-4faa-a824-cdc0c21cc365.png)

Lalu cek daftar branch menggunakan perintah ini

    git branch -a
    
![Screenshot from 2022-08-26 13-36-02](https://user-images.githubusercontent.com/56712612/186838076-2843c4e7-8093-4008-8d1f-12d1e1928819.png)

Untuk berpindah antara satu branch ke branch lain ketikkan perintah berikut ini

    git checkout 'nama-branch'
    
![Screenshot from 2022-08-26 13-37-27](https://user-images.githubusercontent.com/56712612/186838314-7a3b9adb-94e1-4620-8258-e4271ddce70b.png)




