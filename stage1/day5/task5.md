# Membuat CI/CD sederhana menggunakan Cloudflare

## 1. Registrasi akun Cloudfare

Pertama silahkan registrasi terlebih dahulu ke https://cloudflare.com/ , atau jika sudah punya akun Cloudflare tinggal login saja.

![Screenshot from 2022-08-29 12-50-22](https://user-images.githubusercontent.com/56712612/187159380-850521a0-ccb9-420a-b788-f121d9503ae8.png)

## 2. Masuk ke halaman Cloudflare Pages

  - Setelah melakukan registrasi, masuk ke halaman Cloudflare Pages dan klik "Connect to GitHub" agar repository GitHub bisa terdeteksi oleh Cloudflare     Pages.

![Screenshot from 2022-08-29 12-53-36](https://user-images.githubusercontent.com/56712612/187159868-3ef653fd-0707-4442-bb7a-aa609421cf68.png)

  - Pilih akun yang akan dikoneksikan ke Cloudflare.

![Screenshot from 2022-08-29 12-54-32](https://user-images.githubusercontent.com/56712612/187160689-ec60fd0e-8bc8-42a1-aadc-3cdc2185a033.png)

  - Dibagian ini bisa memilih apakah akan dihubungkan dengan semua repository atau hanya satu repository saja. disini saya hanya akan menghubungkan 1 repository saja, lalu klik Begin setup.

![Screenshot from 2022-08-29 13-28-32](https://user-images.githubusercontent.com/56712612/187161777-ac04035b-b4e1-4d9b-aa0a-d408b42cc79e.png)

  - Isi nama dan pilih branch yang akan digunakan, lalu pada bagian build settings pilih framework yang digunakan dan pastikan untuk memasukkan build sebagai commandnya. Jika sudah klik saja "Save and Deploy".

![Screenshot from 2022-08-29 13-30-12](https://user-images.githubusercontent.com/56712612/187163863-abd35984-4d03-4058-b99b-85de29454da7.png)


![Screenshot from 2022-08-29 13-30-21](https://user-images.githubusercontent.com/56712612/187163869-3ae11069-867b-485c-99b0-91e6a06817b7.png)

  - Lalu tunggu hingga proses selesai.

![Screenshot from 2022-08-29 13-30-52](https://user-images.githubusercontent.com/56712612/187164796-2c5fe2a8-cebc-4310-ae46-d005b16f95ae.png)

  - Jika proses sudah berhasil maka akan tampil halaman seperti dibawah ini.

![Screenshot from 2022-08-29 13-35-09](https://user-images.githubusercontent.com/56712612/187164977-4b43ae35-8a64-4047-ab59-a4104717823a.png)

  - Lalu coba akses aplikasi yang sudah di deploy menggunakan Cloudflare dengan url yang telah dibuat (lihat dibagian production)
  
![Screenshot from 2022-08-29 13-36-34](https://user-images.githubusercontent.com/56712612/187198881-b248b18c-4f34-49ea-b54a-d13ef30c8d80.png)

  - Copy url tersebut dan buka di browser, dan inilah website yang berhasil dijalankan menggunakan Cloudflare Pages

![Screenshot from 2022-08-29 13-36-41](https://user-images.githubusercontent.com/56712612/187199449-604b75eb-00ae-4a6b-a068-66f7564b5587.png)

## 3. Update code

Sekarang saya akan mempraktekkan cara kerja CI/CD ini, setiap ada perubahan di code tersebut, maka Cloudflare Pages akan secara otomatis membuild dan mendeploy ulang code tersebut ke server sehingga aplikasi akan terupdate secara otomatis.

  - Saya akan merubah code pada bagian title, saya ubah di bagian <title> ... </title>, lalu kita lihat apakah proses CI/CD berhasil atau tidak.
 
![Screenshot from 2022-08-29 13-38-42](https://user-images.githubusercontent.com/56712612/187201110-f2c1276c-4377-4f5d-8267-3f3acdae351a.png)

  - Lalu kita lihat di Cloudflare Pages, disini CLoudflare Pages secara otomatis membuild ulang code yang sudah saya ubah tadi, itu berarti proses CI/CD sudah berhasil

![Screenshot from 2022-08-29 13-39-16](https://user-images.githubusercontent.com/56712612/187201206-39c7b195-a0e9-466e-96df-1a4ed698e9b3.png)

  - Karena proses build sudah selesai, buka kembali halaman website tadi atau refresh maka akan berubah seperti di bawah ini. Pada bagian title yang sebelumnya Wayshub telah berubah menjadi Wayshub - Ivanka Alan

![Screenshot from 2022-08-29 13-41-18](https://user-images.githubusercontent.com/56712612/187202952-d020e989-b983-41c0-b745-cdda03027072.png)


