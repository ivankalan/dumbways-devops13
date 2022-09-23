# Install Ubuntu Server
## Requirements
Sebelum melakukan instalasi ubuntu server, hal pertama yang harus dilakukan adalah menginstall tools virtual machine serta mendownload file ISO ubuntu server terlebih dahulu. Kali ini, saya akan menggunakan tools VMware Workstation Player sebagai virtual machine.

Download VMware dan file ISO ubuntu server melalui link dibawah ini
1. https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html
2. https://ubuntu.com/download/server

## Instalasi Ubuntu Server
1. Setelah melakukan instalasi VMware, buka VMware anda dan klik dibagian "Creaate a New Virtual Machine"

![Screenshot from 2022-08-23 08-48-33](https://user-images.githubusercontent.com/56712612/186085021-8430c979-d25d-4a2b-a5a9-3de7445ff29f.png)

2. Setelah itu akan muncul halaman seperti gambar dibawah. Disini pilih saja di bagian use ISO image. Setelah itu klik di bagian browse lalu cari lokasi file ISO ubuntu server yang sudah di download sebelumnya lalu dan klik next

![Screenshot from 2022-08-23 08-52-10](https://user-images.githubusercontent.com/56712612/186085870-720c2e0d-c8d5-4e75-b7ec-8be88e409c1a.png)

3. Lalu pada bagian "Guest Operating System" pilih saja Linux dan versi Ubuntu 64-bit, klik next

![Screenshot from 2022-08-23 08-53-40](https://user-images.githubusercontent.com/56712612/186086068-7fa5fb59-d6d6-456c-9e51-06d997c3fd45.png)![Screenshot from 2022-08-23 08-58-11](https://user-images.githubusercontent.com/56712612/186093624-ca9e7d51-096b-4fef-b924-19c0d5dec909.png)![Screenshot from 2022-08-23 08-58-11](https://user-images.githubusercontent.com/56712612/186093635-82fd6f0c-f486-444f-8a4e-bd501c19895e.png)



4. Selanjutnya adalah menentukan lokasi dimana virtual machine akan disimpan. 

![Screenshot from 2022-08-23 08-54-01](https://user-images.githubusercontent.com/56712612/186087016-ca34c72f-d028-4231-adb3-beb6b6c49f5c.png)

5. Setelah itu atur size disk yang ingin digunakan. Disini sebagai contoh saya menggunakan 10GB. Disini ada 2 pilihan yaitu Store Disk as a single file dan Split virtual disk into multiple files.

    Keterangan : Store Disk as a single file maksudnya adalah disk yang di buat itu nantinya akan langsung terbuat 10Gb. (ini tidak disarankan untuk pengguna yang memiliki hardisk yang berkapasitas kecil).
        Split virtual disk into multiple files maksudnya adalah disk yang kita pakai untuk virtual machine kita nantinya itu akan dibagi menjadi beberapa bagian. Jadi walaupun kita menggunakan disk berkapasitas 10Gb itu nanti tidak akan terpakai seluruhnya.

![Screenshot from 2022-08-23 08-57-44](https://user-images.githubusercontent.com/56712612/186087173-a634d9a1-1999-4280-ae14-48a964422882.png)

6. Lalu disini saya akan mengcustomisasi hardware untuk server yang dibuat, tekan saja di bagian "Customize Hardware".

![Screenshot from 2022-08-23 08-58-11](https://user-images.githubusercontent.com/56712612/186089091-a4f13552-73a7-43f1-8f1f-2f88d7e68362.png)

7. Disini ada beberapa pilihan untuk melakukan customisasi seperti Memory, Processors dan Network adapter.

Keterangan:
    Memory berfungsi untuk penyimpanan data yang ingin digunakan untuk Virtual Machine yang ingin dibuat. Disini pilih gunakan saja defaultnya yaitu sebesar 4Gb tetapi misalkan merasa kurang boleh untuk menaikkannya sesuai keinginan.
    Processors adalah salah satu komponen penting untuk Virtual Machine yang ingin dibangun, serta berfungsi untuk memproses data dan mengontrol sistem yang ada pada Virtual Machine. Disini saya menggunakan defaultnya saja yaitu sebesar 2 core.
    Network adapter berfungsi untuk menghubungkan komputer ke jaringan. Untuk penjelasan lebih lanjut ada di poin berikutnya.

![Screenshot from 2022-08-23 14-11-23](https://user-images.githubusercontent.com/56712612/186094202-16d03f0d-b150-43ae-85fe-be4ef05aa418.png)

8. Jika sudah selesai untuk mengatur memory dan processor, selanjutnya pergi ke bagian Network Adapter. Setelah itu ubah dari defaultnya yaitu NAT menjadi Bridge.

Keterangan:
    kalau menggunakan NAT nantinya server yang dibuat ini akan mendapatkan IP yang sudah di sediakan oleh Virtual Machine.
    Kalau Menggunakan Bridge nantinya server yang dibuat akan mendapatkan IP dari internet yang sedang gunakan.
    
Jika sudah langsung klik saja close
    
![Screenshot from 2022-08-23 13-49-11](https://user-images.githubusercontent.com/56712612/186094702-9af078d5-10d2-49a1-8539-4a0a9a8292ec.png)

9. Setelah itu nanti akan muncul halamannya sebelumnya, lalu tekan saja di bagian Finish.

![Screenshot from 2022-08-23 13-49-55](https://user-images.githubusercontent.com/56712612/186095059-795fb606-5470-4419-9e65-df964d114d44.png)

10. Tunggu beberapa saat, lalu anda akan diarahkan ke halaman instalasi ubuntu server. Setelah muncul halaman seperti gambar dibawah, pilih saja "Try or Install Ubuntu Server"

![Screenshot from 2022-08-23 14-17-43](https://user-images.githubusercontent.com/56712612/186101128-ec76c7cc-1760-4c77-9a3c-f2d6e291ebaa.png)

11. Setelah itu anda akan diarahkan kehalaman selanjutnya untuk mimilih bahasa yang digunakan untuk menginstall ubuntu server, pilih saja "English" lalu tekan enter

![Screenshot from 2022-08-23 14-19-19](https://user-images.githubusercontent.com/56712612/186101858-b34e58e0-f0f7-4096-9513-f632b8d43ded.png)

12. Dihalaman selanjutnya langsung klik enter saja untuk men-skip step ini

![Screenshot from 2022-08-23 14-20-29](https://user-images.githubusercontent.com/56712612/186102070-971d4a28-e34a-47e8-ac1e-5df6bce6b801.png)

13. Selanjutnya pilih "Ubuntu Server" lalu klik enter

![Screenshot from 2022-08-23 14-20-36](https://user-images.githubusercontent.com/56712612/186102191-a0983ea8-f9ec-43ad-b7a4-6c3fa8aa7541.png)

14. Selanjutnya kita akan ubah konfigurasinya dari yang awalnya itu DHCPv4 menjadi Static.

    Keterangan:
        DHCP (Dynamic Host Protocol Configuration) : Alamat IP yang dapat berubah-ubah pada perangkat yang tersambung setiap kali terhubung kembali pada jaringan tersebut (otomatis).
        Static : Alamat IP tidak berubah-ubah dari yang telah diberikan oleh adminisitrator (setting manual)
        
15. Pilih di bagian ens33, setelah itu pada bagian "IPv4 Method" ubah dari yang awalnya automatic menjadi manual. Setelah itu masukan detail IP pada form yang tersedia(kalian bisa masukkan saja IP yang sudah tertera di bagian DHCPv4). Jika sudah langsung tekan saja Save.

    Keterangan:
        Subnet : Istilah teknologi Informasi yang membedakan Network ID dan Host ID atau sebagai penentu porsi Network ID dan Host ID pada deretan kode biner
        Address : Alamat IP yang akan digunakan untuk Virtual Machine yang akan kalian buat. (kalian dapat mengisi bagian ini dengan IP yang sudah ada di bagian DHCP)
        Gateway : Perangkat komputer yang berfungsi untuk mengkoneksikan sebuah Jaringan komputer terhadap satu jaringan komputer yang lain.
        Name servers : Dibagian Name servers ini kalian cukup memasukkan IP DNS dari google supaya dapat terhubung dengan browser. Setelag itu klik save

![Screenshot from 2022-08-23 14-23-47](https://user-images.githubusercontent.com/56712612/186103279-17ab8f3d-706a-4754-8104-a70298ef8d64.png)

16. Jika konfigurasi sudah selesai maka akan ada perubahan di bagian DHCPv4 tadi menjadi static.

17. Pada bagian ini skip saja dengan meng-klik enter

![Screenshot from 2022-08-23 14-24-24](https://user-images.githubusercontent.com/56712612/186105417-61a37d25-8c73-4ec3-b3b0-07bd6c8bf497.png)

18. Pada bagian ini juga skip saja dengan meng-klik enter

![Screenshot from 2022-08-23 14-24-36](https://user-images.githubusercontent.com/56712612/186105521-345e350f-2c5a-4aa5-8178-f1d530bb6156.png)

19. Disini saya akan memilih bagian Custom storage layout. Karena jika memilih Custom storage layout saya bisa membuat 2 buah partisi, jika sudah dipilih setelah itu langsung saja klik Done.

![Screenshot from 2022-08-23 14-25-02](https://user-images.githubusercontent.com/56712612/186106108-147f7f32-e75b-47b7-8065-6093862e9bfd.png)

20. Selanjutnya disini saya akan membuat 2 buah partisi untuk root dan swap. Langsung pilih saja di bagian "Free Space" lalu pilih di bagian Add GPT Partition. Untuk kapasitasnya bisa disamakan saja dengan gambar dibawah (kecuali untuk swap, kalian bisa setting semau kalian apabila merasa kurang).

    Keterangan :
        root adalah tempat dimana sistem kita itu ter-install.
        swap adalah suatu memory cadangan yang akan digunakan untuk server kita apabila memory utama sudah penuh.
        
![Screenshot from 2022-08-23 14-28-21](https://user-images.githubusercontent.com/56712612/186106365-c340a669-3e73-4a6a-95ba-53a640fe1228.png)

![Screenshot from 2022-08-23 14-28-43](https://user-images.githubusercontent.com/56712612/186106803-a4d77186-b317-47e3-9407-4aff402925f6.png)

![Screenshot from 2022-08-23 14-28-57](https://user-images.githubusercontent.com/56712612/186106819-18038f85-20bf-40d1-a3d5-acd49d0373ff.png)

21. Jika sudah, disini saya sudah berhasil membuat 2 partisi untuk root dan swap. Lalu langsung saja klik Done dan klik continue untuk lanjut ke step berikutnya.

![Screenshot from 2022-08-23 14-29-11](https://user-images.githubusercontent.com/56712612/186106996-c00eb0f5-f039-40d2-baf0-cbaefccd752a.png)

22. Selanjutnya masukan informasi seperti nama, username, dan password untuk server yang dibuat. Jika sudah klik saja Done.

![Screenshot from 2022-08-23 14-30-33](https://user-images.githubusercontent.com/56712612/186107384-100f7e49-7075-482b-bf94-a186562edd78.png)

23. Dihalaman berikutnya jangan lupa untuk checklist bagian Install OpenSSH server gunanya adalah untuk me-remote server yang sudah dibuat.

24. Selanjutnya skip saja dengan klik Done

![Screenshot from 2022-08-23 14-31-02](https://user-images.githubusercontent.com/56712612/186107713-d1eba82d-085d-4047-85c4-4230a02d9e25.png)

25. Pada tahap ini, instalasi ubuntu server sudah sampai akhir. Tunggu saja proses instalasi sampai selesai jika sudah selesai langsung saja klik Reboot Now.

![Screenshot from 2022-08-23 14-31-13](https://user-images.githubusercontent.com/56712612/186108137-b2f017b0-aeab-44ff-9c84-7611fd8b9a72.png)

![Screenshot from 2022-08-23 15-16-32](https://user-images.githubusercontent.com/56712612/186108186-0326ca9c-6c6d-45c8-9768-096268353c5e.png)

26. Jika tahapan instalasi sudah selesai. Masukkan id beserta password yang sudah di set-up sebelumnya, Jika sudah maka anda telah berhasil melakukan instalasi ubuntu server.

![Screenshot from 2022-08-23 15-20-49](https://user-images.githubusercontent.com/56712612/186109320-4901cd68-f708-4509-8659-5b2e86806d05.png)

27. Pada tahap ini, anda telah berhasil untuk menginstall ubuntu server pada virtual machine anda di VMware.

![Screenshot from 2022-08-23 15-21-02](https://user-images.githubusercontent.com/56712612/186109528-41401cc6-1915-44b7-8aa1-5d5d9e66b5a3.png)

28. Untuk memastikan apakah server yang telah dibuat ini sudah terhubung ke dalam internet bisa gunakan perintah dibawah ini

    ping google.com
    
    Jika server kalian sudah terhubung ke internet maka akan muncul seperti gambar dibawah ini

![Screenshot from 2022-08-23 15-23-34](https://user-images.githubusercontent.com/56712612/186110404-5fffb6ca-da76-4b3a-8851-7ffd300717ec.png)

