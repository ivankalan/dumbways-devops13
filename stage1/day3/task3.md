# Simple application menggunakan pm2 dan localtunnel
Di sini saya akan menggunakan Node.js, Golang, dan Python sebagai dasar dari pembuatan simple application yang ter-integrasi dengan pm2 agar bisa diakses secara daemon dan localtunnel agar bisa diakses secara publik.

## Node.js

NodeJs adalah runtime untuk lingkungan JavaScript di luar peramban web yang dibangun di atas mesin JavaScript V8.

Pertama-tama install terlebih dahulu engine-nya. Untuk instalasi kalian bisa menggunakan beberapa perintah dibawah ini.
    
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
    
![Screenshot from 2022-08-25 15-44-54](https://user-images.githubusercontent.com/56712612/186619219-a7545dcf-645e-4c09-8570-25bbc88fdbba.png)

Disini saya akan menggunakan nvm versi 16, cara menginstallnya ketikkan perintah dibawah ini

    nvm install 16
    
![Screenshot from 2022-08-25 15-49-39](https://user-images.githubusercontent.com/56712612/186620078-a4be24fc-b53a-49a9-90d0-5ebdee57efce.png)

Jika tahapan di atas sudah di lakukan, maka instalasi node.js sudah berhasil. Untuk melakukan pengecekan bisa menggunakan perintah di bawah ini.

    node -v
    
 dan
    
    npm -v
    
![Screenshot from 2022-08-25 15-51-55](https://user-images.githubusercontent.com/56712612/186620630-692fbbef-75d9-4593-92b9-7ad5dae41adb.png)

Selanjutnya saya akan menjalankan perintah npm init gunanya untuk mengisiasi project, Hasil dari menjalankan perintah ini akan membuat file baru dengan nama package.json, package.json ini berisikan informasi dari aplikasi yang akan kalian buat. Sebelum menjalankan perintah dibawah ini, buatlah dulu direktori untuk project yang akan dibuat.

    npm init -y
    
![Screenshot from 2022-08-25 15-57-24](https://user-images.githubusercontent.com/56712612/186621789-e74e8932-7a15-40ee-9d12-0d97410b13d7.png)

Selanjutnya saya akan menginstall Express JS. Express JS adalah framework dari Node.js yang dirancang secara fleksibel dan sederhana untuk membantu tahap pengembangan aplikasi back-end. Menginstall express js dapat dilakukan menggunakan NPM dengan perintah berikut.

    npm install express --save
    
![Screenshot from 2022-08-25 16-00-18](https://user-images.githubusercontent.com/56712612/186622439-1e6e5692-a185-4bfa-ae35-b051d4fd5c90.png)

Jika sudah buat file dengan nama index.js, lalu masukan script dibawah ini

    nano index.js
    
lalu
    
    const express = require("express");
    const app = express();
    const port = 3000;

    app.get("/", (req, res) => {
      res.send("Hello World!");
    });

    app.listen(port, () => {
      console.log(`Example app listening on port ${port}`);
    });

![Screenshot from 2022-08-25 16-03-51](https://user-images.githubusercontent.com/56712612/186623301-da72cd4d-a0db-4432-90cc-cf123025e76c.png)

Jika sudah, save dulu filenya, lalu sekarang akan saya coba untuk menjalankan aplikasi sederhana yang sudah di buat. Untuk menjalankan dapat menggunakan perintah berikut ini.

    node index.js

![Screenshot from 2022-08-25 16-09-02](https://user-images.githubusercontent.com/56712612/186624631-a126b945-e2f1-4a1f-9406-11574ae1ccb1.png)

Lalu buka web browser dan ketikkan localhost:3000

![Screenshot from 2022-08-25 16-09-31](https://user-images.githubusercontent.com/56712612/186624863-a8864a41-2e82-4387-a22f-d8f5cca3b394.png)


### Konfigurasi dengan pm2 dan localtunnel

Aplikasi sederhana node.js sudah berhasil, tapi masalahnya jika saya menutup terminal maka aplikasi saya juga akan ikut tertutup juga. Nah disinilah pm2 berfungsi, saat aplikasi node.js kita sudah ter-integrasi dengan pm2 meskipun terminal ditutup, aplikasi node.js kita akan tetap berjalan. Langsung saja saya praktekkan langkah langkahnya dibawah ini

Pertama, install dulu pm2 secara global menggunakan npm, ketikkan saja perintah dibawah ini

    sudo npm install pm2 -g

![Screenshot from 2022-08-25 16-20-41](https://user-images.githubusercontent.com/56712612/186627224-8c367ad7-1cc7-44d5-933c-0cbda9b254bf.png)

Lalu cek apakah pm2 sudah terinstall, ketikkan perintah dibawah ini

![Screenshot from 2022-08-25 16-21-31](https://user-images.githubusercontent.com/56712612/186627614-62328fbe-e65e-4276-8cd6-261ffd8c8486.png)

Setelah pm2 berhasil terinstall, silahkan masuk ke direktori aplikasi node.js yang tadi telah dibuat untuk menjalankan aplikasi tersebut menggunakan pm2 dengan ketikkan perintah berikut

    pm2 start index.js

![Screenshot from 2022-08-25 16-26-25](https://user-images.githubusercontent.com/56712612/186628609-cf1bcdc5-a201-4970-9b02-e9172a762be7.png)

Jika sudah, maka pm2 sudah berhasil terintegrasi dengan aplikasi node.js sederhana yang sudah dibuat tadi, jadi meski kalian tutup terminalnya maka aplikasi akan tetap berjalan. Untuk memonitoring pm2 kalian bisa mengetikkan perintah berikut

    pm2 monit
    
![Screenshot from 2022-08-25 16-30-14](https://user-images.githubusercontent.com/56712612/186629345-425d8919-0795-4321-aa66-854f17a16b5d.png)

Nah, setelah mengerti cara meng-integrasikan aplikasi node.js dengan pm2, sekarang saya akan menghubungkan aplikasi node.js sederhana tadi yang sudah dilengkapi dengan pm2 agar bisa diakses secara publik menggunakan localtunnel, berikut langkah-langkahnya

Masih tetap diterminal saat menjalankan pm2 tadi, ketikkan perintah berikut lalu enter

    lt --port 3000
    
![Screenshot from 2022-08-25 20-55-47](https://user-images.githubusercontent.com/56712612/186684287-447b40d2-b9a7-44e6-a9cc-2aa0562c5cef.png)

![Screenshot from 2022-08-25 20-57-07](https://user-images.githubusercontent.com/56712612/186684776-66f8c557-dd40-4f09-b98a-19bb8e3a246b.png)

Lalu copy url yang tertera dan taruh di browser kalian, lalu klik continue, dan aplikasi sudah bisa diakses publik

![Screenshot from 2022-08-25 21-01-45](https://user-images.githubusercontent.com/56712612/186685660-7975491b-428c-4036-8f43-8e3b4d0b41ba.png)


## Golang

Go atau Golang adalah bahasa pemrograman yang dibuat di Google pada tahun 2009 oleh Robert Griesemer, Rob Pike, dan Ken Thompson. bahasa pemrograman sumber terbuka yang mudah, sederhana, efisien. Selain itu, Go memiliki level yang sama dengan Java.

Pertama-tama install terlebih dahulu engine-nya. Untuk instalasi kalian bisa menggunakan beberapa perintah dibawah ini.

    wget https://golang.org/dl/go1.16.5.linux-amd64.tar.gz && sudo su
    
![Screenshot from 2022-08-25 19-07-01](https://user-images.githubusercontent.com/56712612/186665050-0eb5dee3-fbd6-4cdd-84b8-709035af50fb.png)

    rm -rf /usr/local/go && tar -C /usr/local -xzf go1.16.5.linux-amd64.tar.gz && exit

![Screenshot from 2022-08-25 19-07-16](https://user-images.githubusercontent.com/56712612/186665172-5b69858a-e6e5-4492-9cbd-78faf850ecf3.png)

Lalu masukkan path go pada .bashrc

    sudo nano .bashrc

![Screenshot from 2022-08-25 19-33-39](https://user-images.githubusercontent.com/56712612/186665741-02715b93-a64e-43a4-be99-5d3f98345dca.png)

Lalu tambahkan command dibawah ini dibagian paling bawah dari .bashrc

    export PATH=$PATH:/usr/local/go/bin

![Screenshot from 2022-08-25 19-08-16](https://user-images.githubusercontent.com/56712612/186665880-eaf95364-f64a-4a44-8bac-73e1b800fce5.png)

Jika sudah, lakukan verifikasi apakah go sudah terinstall dengan perintah berikut

    go version
    
![Screenshot from 2022-08-25 19-29-03](https://user-images.githubusercontent.com/56712612/186666148-b958dc1f-681c-425e-b791-94b01b195b54.png)

Setelah go berhasil terinstal, sekarang saya akan membuat aplikasi sederhana menggunakan framework dari go yaitu Echo, Echo merupakan salah satu framework GoLang yang high performance, extensible, minimalist Go web framework. Langkah pertama yang dilakukan adalah menginstal Echo terlebih dahulu, ikuti perintah dibawah ini:

    go mod init simple-app-golang
    
![Screenshot from 2022-08-25 19-45-49](https://user-images.githubusercontent.com/56712612/186668280-57128963-63b4-42d3-ae68-c585bc4b8d66.png)

Keterangan:
    simple-app-golang adalah nama direktori yang saya buat, jika anda ingin inisialisasi go mod maka pastikan anda menggunakan nama direktori yang anda buat sendiri
    
    go get github.com/labstack/echo/v4
    
![Screenshot from 2022-08-25 19-48-12](https://user-images.githubusercontent.com/56712612/186668823-6b3ecb1f-770a-47bf-b15c-eebdcfa91e7e.png)

Lalu ketikkan perintah berikut

    sudo nano server.go
    
Lalu
    
    package main

    import (
        "net/http"

        "github.com/labstack/echo/v4"
    )

    func main() {
        e := echo.New()
        e.GET("/", func(c echo.Context) error {
            return c.String(http.StatusOK, "Hello, World!")
        })
        e.Logger.Fatal(e.Start(":1323"))
    }
     
![Screenshot from 2022-08-25 19-53-01](https://user-images.githubusercontent.com/56712612/186669851-565acce5-a924-429a-8c15-bd6099e5a970.png)

Setelah itu save, dan ketikkan lagi perintah berikut:

    go run server.go
    
![Screenshot from 2022-08-25 19-51-34](https://user-images.githubusercontent.com/56712612/186670100-dab8fb17-7dad-4fce-9582-1eaf1481eb22.png)

![Screenshot from 2022-08-25 19-55-24](https://user-images.githubusercontent.com/56712612/186670367-9798d624-8551-4d04-9123-f0e7f1d77ba5.png)

Setelah itu buka di browser kalian localhost:1323 dan aplikasi sederhana dari go menggunakan Echo sudah selesai

![Screenshot from 2022-08-25 19-52-14](https://user-images.githubusercontent.com/56712612/186670422-906b9f96-b4e4-4638-a2e7-c429e0393876.png)


### Konfigurasi dengan pm2 dan localtunnel

Karena pm2 sudah terinstal secara global tadi, maka kita tidak perlu untuk menginstal kembali pm2. Silahkan masuk ke direktori aplikasi golang yang tadi telah dibuat untuk menjalankan aplikasi tersebut menggunakan pm2 dengan ketikkan perintah berikut ini diterminal yang baru:

    pm2 start server.go
    
![Screenshot from 2022-08-25 21-08-53](https://user-images.githubusercontent.com/56712612/186687785-79d8f235-bf88-4900-86a6-fc76c73aa112.png)
    
pm2 sudah terkonfigurasi, sekarang tinggal mengkonfigurasi localtunnelnya. Masih tetap diterminal saat menjalankan pm2 tadi, ketikkan perintah berikut lalu enter

    lt --port 1323
  
![Screenshot from 2022-08-25 21-19-27](https://user-images.githubusercontent.com/56712612/186690093-dc552e7f-2e3c-4aae-95a6-47674d8cfb4f.png)

Lalu copy url yang tertera dan taruh di browser kalian, lalu klik continue, dan aplikasi sudah bisa diakses publik

![Screenshot from 2022-08-25 21-14-53](https://user-images.githubusercontent.com/56712612/186689916-65eff796-7c20-422f-8806-4957a92e8f43.png)

## Python

Python adalah Python merupakan bahasa pemrograman tingkat tinggi yang diracik oleh Guido van Rossum. Python banyak digunakan untuk membuat berbagai macam program, seperti: program CLI, Program GUI (desktop), Aplikasi Mobile, Web, IoT, Game, Program untuk Hacking.

Dikarenakan Python3 sudah terinstall secara default pada sistem operasi linux, maka langkah pertama yang harus dilakukan hanya mengupdate paket melalui perintah dibawah

    sudo apt update && sudo apt upgrade
    
Lalu setelah itu kita cek terlebih dahulu versi Python yang ada dengan perintah dibawah

    python3 -V
    
![Screenshot from 2022-08-25 20-07-53](https://user-images.githubusercontent.com/56712612/186675939-02a35d48-4aea-4aa3-9c65-73edd3510d25.png)

Setelah itu install dulu package manager dari python3. Kalian dapat menggunakan perintah berikut ini.

    sudo apt install python3-pip

![Screenshot from 2022-08-25 20-08-25](https://user-images.githubusercontent.com/56712612/186676161-a0f4dc59-0c96-46bc-aa80-dd46223bb75b.png)

Lalu jalankan perintah ini

    pip install flask

![Screenshot from 2022-08-25 20-10-47](https://user-images.githubusercontent.com/56712612/186676398-2889d2f0-b1c4-405b-836e-6d27a2a6b590.png)

PIP adalah sebuah package management system yang biasa digunakan untuk mengatur dan menginstall package yang berisi modul-modul Python. PIP digunakan untuk menginstall Flask, Flask adalah framework python yang digunakan untuk web development. Flask ditulis dan dikembangkan dengan bahasa dan modul-modul pemrograman Python. Dengan menggunakan PIP, semua hal yang dibutuhkan untuk instalasi Flask akan diunduh dan dipasang dalam satu perintah.
    Sekarang kita akan membuat aplikasi sederhana menggunakan Python3.
    Kalian buat terlebih dahulu file dengan nama index.py. Lalu masukan script dibawah ini.

    nano index.py
    
Lalu

    from flask import Flask
    app = Flask(__name__)
    @app.route("/")
    def helloworld():
        return "Hello World"
    if __name__ == "__main__":
        app.run()

![Screenshot from 2022-08-25 20-12-31](https://user-images.githubusercontent.com/56712612/186676803-0e19c463-7d9c-4889-9a77-884bc40ef807.png)

Setelah itu, jalankan aplikasi dengan menggunakan perintah ini

    python3 index.py

![Screenshot from 2022-08-25 20-13-03](https://user-images.githubusercontent.com/56712612/186677171-71448cf3-fb5e-4742-9fcd-5b6a1ade455c.png)

Lalu ketik localhost:5000 pada browser kalian dan aplikasi sudah berjalan

![Screenshot from 2022-08-25 20-16-37](https://user-images.githubusercontent.com/56712612/186677371-fd1a5098-2c13-4e5d-8ed1-40368213bbc8.png)


### Konfigurasi dengan pm2 dan localtunnel

Sama seperti sebelumnya, karena pm2 sudah terinstal secara global tadi, maka kita tidak perlu untuk menginstal kembali pm2. Silahkan masuk ke direktori aplikasi python yang tadi telah dibuat, untuk menjalankan aplikasi tersebut menggunakan pm2 silahkan ketikkan perintah berikut ini diterminal yang baru:

    pm2 start index.py --interpreter python3

![Screenshot from 2022-08-26 09-45-06](https://user-images.githubusercontent.com/56712612/186805553-caf2687b-6b3e-4f7d-82a6-0b392383e9e7.png)

pm2 sudah terkonfigurasi, sekarang tinggal mengkonfigurasi localtunnelnya. Masih tetap diterminal saat menjalankan pm2 tadi, ketikkan perintah berikut lalu enter

    lt --port 5000
    
![Screenshot from 2022-08-26 09-47-50](https://user-images.githubusercontent.com/56712612/186805923-f43a6a8b-706a-44a6-bb73-4700dc6a27e6.png)

Lalu copy url yang tertera dan taruh di browser kalian, lalu klik continue, dan aplikasi sudah bisa diakses publik

![Screenshot from 2022-08-26 09-48-16](https://user-images.githubusercontent.com/56712612/186805965-257c8c89-8886-4e64-8055-842927107000.png)
