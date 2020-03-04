# OctoberCMS
![aplikasi-october](https://raw.githubusercontent.com/cindanapr/october-Komdat/master/october.png)

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) |[Fitur-fitur](#Fitur-fitur) | [Pembahasan](#pembahasan) | [Referensi](#referensi)


## Sekilas Tentang 
[`^ kembali ke atas ^`](#aplikasi-october)

OctoberCMS adalah sebuah content management system (CMS) gratis, open source dan self-hosted yang berbasiskan pada bahasa pemrograman PHP dan framework Laravel. Saat ini, OctoberCMS telah mendukung MySQL, SQLite, dan PostgreSQL untuk backend basis data dan basis data flat file untuk struktur front end-nya.

## Instalasi
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

#### Kebutuhan
- Install apache, mysql, php, dan package lain yang dibutuhkan pada server
```shell
sudo apt install apache2
sudo apt install mysql-server
sudo apt install php7.0
sudo apt install libapache2-mod-php
sudo apt install php7.0-mysql
sudo apt install php7.0-gd php7.0-mcrypt php7.0-xml php7.0-ssh2
sudo service apache2 restart
```  
- Instal Virtual Box
- Instal Web Server Virtual
	1. **Membuat VM Ubuntu Server**

    Dalam instalasi, digunakan *Ubuntu Server 16.04*. Kemudian, buat *Virtual Machine* baru pada *VirtualBox* dengan tipe "Ubuntu 64-bit".
    - Jalankan *VirtualBox* lalu klik *New*. Berikan nama bebas, tapi pastikan *version: Ubuntu (64-bit)*.
    
      ![1](/name.jpeg)
      
    - *Memory Size (RAM)* cukup 8 MB, lalu klik *Use an Existing VH* dan pilih file *ubuntu-server.vdi*. *(Ubuntu Server dapat didownload [disini](https://ubuntu.com/download/server))*, klik *Create*.
    
      ![2](/hardisk.jpeg)
      

	2. **Setting Port-Forwarding**

    *Port-forwarding* berfungsi agar server dapat diakses dari luar melalui alamat host (IP host).
    - Klik *setting* pada ``Ubuntu Server``, klik *Network*, pilih *Advance*, lalu klik *Port Forwarding*.
    
      ![3](/portford.jpeg)
      
    - Tambah *port* dan atur seperti tabel dibawah ini:
    
      | Name | Protocol | Host IP | Host Port | Guest IP | Guest Port |
      |:----:|:--------:|:-------:|:---------:|:--------:|:----------:|
      | http | TCP      |         | 8888      |          | 3000         |
      | ssh  | TCP      |         | 2222      |          | 20         |

    Dengan demikian, ketika mengakses ``localhost:8888`` di *host*, maka akan diteruskan ke ``localhost:80`` di *guest (VM)*.
    ![9](/port.jpeg)
- Instal package yang dibutuhkan untuk menginstall **October CMS**
1. PDO PHP Extension
```shell
sudo apt-get install php7.0-mysql
```  


2. cURL PHP Extension
```shell
sudo apt-get install php7.0-curl
```  


3. Mbstring PHP Library
```shell
sudo apt-get install php7.0-mbstring
```

4. ZipArchive PHP Library
```shell
sudo apt-get install php7.0-zip
```
5. GD PHP Library 
```shell
sudo apt-get install php7.0-gd
```

#### Cara instalasi October-CSM
1. Download installation file pada halaman http://octobercms.com/download
```shell
sudo wget http://octobercms.com/download
```

2. Pindahkan file download ke download.zip
```shell
sudo mv download download.zip
```

3. Ekstrak file download.zip
```shell
sudo unzip download.zip
```

4. Copy semua file yang berada pada folder "install-master" dan masukkan ke "/var/www/html/"
```shell
sudo cp -r ~/install-master/* /var/www/html/
```

5. Setting permission dan ganti kepemilikan dari folder "/var/www/html/"
```shell
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```
6. Buat database baru untuk October CMS di mysql dan ubah status kepemilikannya
```shell
CREATE DATABASE october;
CREATE USER october IDENTIFIED by 'secret';
GRANT ALL PRIVILEGES ON october.* TO october;
```

7. Atur database, administrator, dan backend environment
Masuk ke browser dan ketikkan alamat localhost:8000/install.php
Atur database dan arahkan ke database yang telah dibuat sebelumnya.

![GitHub Logo](/database.jpg)

Klik tombol administrator. Masukkan identitas untuk admin: nama, password, dan yang lainnya

![GitHub Logo](/administrator.jpg)

Klik tombol advanced. Masukkan URL untuk mengakses sistem admin.

![GitHub Logo](/AdvancedOctober.jpeg)

	- Selesai! (Tampilan halaman *admin*)

## Konfigurasi
[`^ kembali ke atas ^`](#aplikasi-october)
Pastikan pada konfigurasi Apache, module ``` mod_rewrite ``` sudah dalam keadaan diaktifkan. Untuk melihat module mana yang sudah aktif, ketikkan perintah ``` apache2ctl -M ```. Jika belum ada di list, ketikkan perintah ``` sudo a2enmod rewrite ``` pada terminal kemudian restart apache dengan mengetikkan perintah ``` sudo service apache2 restart ```.

Selanjutnya, cek juga file konfigurasi apache2.conf yang terletak di ``` /etc/apache2/ ```.
```
$ cat /etc/apache2/apache2.conf
....
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>
....
```
Jika pengaturan AllowOverride pada direktori /var/www masih None, ubah menjadi All agar ``` mod_rewrite ``` bisa dijalankan dengan sepenuhnya.
```
$ sudo nano /etc/apache2/apache2.conf
....
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>
....
```
Kemudian simpan (ctrl+o) dan keluar (ctrl+x)
	
## Fitur-fitur
[`^ kembali ke atas ^`](#aplikasi-october)

1. Page Components
   Fitur ini sangat membantu sekali dalam membangun sebuah page. Di October CMS sudah tersedia beberapa komponen yang sudah siap kamu    gunakan untuk membangun page. Hanya perlu menambahkan sebuah komponen kedalam page kemudian mengkonfigutrasinya dengan Inspector (sebuah visual tool untuk memanage properties dari sebuah komponen di October). You don’t need to program anymore!
2. Extensible platform
   Penggunaan plugin yang sederhana
3. Simple AJAX framework
   AJAX (Asynchronous JavaScript and XML) merupakan suatu teknik baru dalam dunia web namun bukan merupakan bahasa pemrograman baru. AJAX merupakan teknik pengembangan web untuk membuat suatu aplikasi web interaktif. Tujuannya adalah untuk membuat website agar lebih responsive, sehingga seluruh halaman web tidak harus reload setiap kali pengguna meminta request.
4. Easy administrative interfaces
   Dengan tampilan modern, ini bakal bikin Kamu betah menggunakan halaman adminnya
5. Completely file-based CMS templates
   Yang menarik lainnya adalah, templating di October CMS adalah file-based, dan ini akan sangat membuat aktivitas theming akan menjadi    lebih mudah.
	
## Pembahasan
[`^ kembali ke atas ^`](#aplikasi-october)
  -KELEBIHAN\
1. Di October CMS sudah tersedia beberapa komponen yang sudah siap kamu gunakan untuk membangun page. 
2. Plugin yang sederhana
2. Front end ringan dan cepat.
3. Dengan tampilan modern, ini bakal bikin betah menggunakan halaman adminnya.
4. Templating di October CMS adalah file-based, dan ini akan sangat membuat aktivitas theming akan menjadi lebih mudah.

  -KEKURANGAN
1. Theme sangat sedikit. Cuma ada 95 theme (saat thread ini dibuat), dan itupun bercampur antara berbayar dan gratis nya emoticon-Hammer (S).
2. Komunitas di Indonesia sangat sedikit.
3. Tidak cocok bagi orang awam karena butuh skill ngoding (Laravel).
4. Serba manual. 
5. Super simple.


###
## Referensi
[`^ kembali ke atas ^`](#aplikasi-october)

1. [About | OctoberCMS](https://www.codepolitan.com/october-cms-berbasis-laravel-sebuah-opsi-lain-untuk-membangun-website) -OctoberCMS
2. [Installation | OctoberCMS](http://octobercms.com/download) - OctoberCMS
3. [Installation Virtual Machine](https://github.com/auriza)
