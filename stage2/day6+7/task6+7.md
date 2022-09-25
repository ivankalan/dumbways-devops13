# Monitoring Server & Automation Ansible

## Prerequisite
- Create vm IDCH (1 core cpu, 2gb ram, 20gb storage)

## Install Ansible

Diambil dari dokumentasi resmi Ansible, Ansible membutuhkan PPA untuk menginstallnya. Pertama jalankan command `sudo apt install software-properties-common` lalu tambah repo dengan menjalankan command `sudo add-apt-repository --yes --update ppa:ansible/ansible` dan terakhir jalankan command `sudo apt install ansible` untuk menginstall Ansible.

![Screenshot from 2022-09-20 16-11-10](https://user-images.githubusercontent.com/56712612/192133582-c6722f88-a642-4db4-984f-03be638e0668.png)

![Screenshot from 2022-09-20 16-11-41](https://user-images.githubusercontent.com/56712612/192133585-f58b7471-7939-4ec7-b63d-97441f94888b.png)

![Screenshot from 2022-09-20 16-11-56](https://user-images.githubusercontent.com/56712612/192133588-b5b8bc93-5899-4019-9c4c-53166393b016.png)

Lalu cek apakah Ansible sudah terinstall dengan command `ansible --version`

![Screenshot from 2022-09-20 16-20-51](https://user-images.githubusercontent.com/56712612/192133639-b4d11e76-d3fa-4dfa-b920-7a26c830294c.png)

Setelah Ansible berhasil di install, langkah selanjutnya yaitu setup konfigurasi awal dengan membuat file `inventory` dan file `ansible.cfg`

![Screenshot from 2022-09-25 14-53-43](https://user-images.githubusercontent.com/56712612/192133768-0e9ad5db-c8ed-446b-844a-f995c1f85526.png)

Setelah file `inventory` dan file `ansible.cfg` dibuat, isi file `inventory` dengan IP dari server yang akan di koneksikan dengan Ansible dan isi file `ansible.cfg` dengan konfigurasi dasar Ansible

![Screenshot from 2022-09-25 14-57-31](https://user-images.githubusercontent.com/56712612/192133945-ec75a23e-7e2a-404f-b13a-6f43d683f557.png)

![Screenshot from 2022-09-25 14-57-46](https://user-images.githubusercontent.com/56712612/192133949-0fa3c2bc-b0a9-4303-905b-8527ea8fed0c.png)

Lalu disini saya akan menerapkan konfigurasi agar Ansible dapat terkoneksi dengan server tanpa menggunakan private key

Pertama buat dulu folder yang bernama `group_vars` lalu buat sebuah file bernama `all` didalam folder `group_vars` dan isikan file `all` dengan konfigurasi berikut

![Screenshot from 2022-09-25 15-01-01](https://user-images.githubusercontent.com/56712612/192134085-55e81720-0615-49d5-b29d-d6820ecedc04.png)

Nb: isi ansible_ssh_pass dengan password dari server kalian

lalu tambahkan konfigurasi `remote_user` didalam file `ansible.cfg`

![Screenshot from 2022-09-25 14-57-46](https://user-images.githubusercontent.com/56712612/192134130-79968a5b-0b3e-4e58-a7b1-f34fdc485846.png)

dan save, sekarang kita tidak perlu lagi menambahkan private key untuk mengkoneksikan Ansible dengan server kita

## Create user

Pertama buat file bernama `user.yaml` dan isikan konfigurasi seperti gambar dibawah ini

![Screenshot from 2022-09-25 15-08-03](https://user-images.githubusercontent.com/56712612/192134277-07cdc3f7-127e-4f32-8d0f-fe1558d55965.png)

Untuk password user kita harus mengisinya dengan password yang sudah di enkripsi, untuk membuat password yang di enkripsi kita memerlukan package yang bernama `whois`, install `whois` dengan command `sudo apt install whois -y` lalu jalankan command `mkpasswd --method=sha-512` dan ketikkan password yang akan di enkripsi

![Screenshot from 2022-09-21 09-43-47](https://user-images.githubusercontent.com/56712612/192134384-47fe4842-b0e2-4ed3-8a2e-7243c0bb8b19.png)

![Screenshot from 2022-09-21 09-44-39](https://user-images.githubusercontent.com/56712612/192134386-a76f70ee-a627-4bef-a8a2-50a6345a2e4b.png)

Setelah mendapatkan password yang sudah di enkripsi, copy password tersebut dan tambahkan kedalam file `user.yaml` . Setelah itu jalankan file `user.yaml` menggunakan Ansible Playbook dengan command `ansible-playbook user.yaml`

![Screenshot from 2022-09-21 14-12-30](https://user-images.githubusercontent.com/56712612/192134429-2b0b6269-87a4-4677-888d-09c013634aec.png)

## Install Docker, Docker SDK & Nginx using Ansible Playbook

Pertama buat file `.yaml` sebagai wadah untuk menginstall docker, docker sdk, dan nginx menggunakan ansible playbook. Lalu ketik konfigurasi seperti gambar dibawah ini

![Screenshot from 2022-09-25 15-21-30](https://user-images.githubusercontent.com/56712612/192134647-9612446c-c64a-4278-949c-ab39cfc22563.png)

![Screenshot from 2022-09-25 15-21-47](https://user-images.githubusercontent.com/56712612/192134649-9e348763-85f6-4da1-8353-ef4b07a01ea3.png)

Disini saya menggunakan ansible collection yang bernama `community.docker` untuk mempermudah konfigurasi docker, untuk menginstallnya gunakan command `ansible-galaxy collection install community.docker`

![Screenshot from 2022-09-21 14-49-00](https://user-images.githubusercontent.com/56712612/192134960-9773d83c-274b-4249-96f9-e9e7763e4987.png)

Lalu run file `.yaml` yang sudah dibuat tadi menggunakan ansible playbook dengan command `ansible-playbook [nama file].yaml`

![Screenshot from 2022-09-21 15-36-49](https://user-images.githubusercontent.com/56712612/192135001-435fca4d-9790-49c7-a589-1dcb4400cf39.png)


















