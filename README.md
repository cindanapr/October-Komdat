# Aplikasi Web "October-CMS"
![aplikasi-october](https://raw.githubusercontent.com/cindanapr/october-Komdat/master/october.png)

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Maintenance](#maintenance) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:

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

![GitHub Logo](/AdvancedOctober.png)

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
	
## Maintenance
[`^ kembali ke atas ^`](#aplikasi-october)

PageKit menyediakan fitur *maintenance* apabila admin web ingin melakukan perbaikan pada situs. 
1. Pada halaman *dashboard* admin (http://URL/admin/dashboard), klik tombol *hamburger* di pojok kiri atas, kemudian pilih ikon *Site*
2. Pada halaman *site*, pilih tab *Settings*, kemudian pilih submenu *Maintenance*
3. Setelah itu, centang *Put the site offline and show the offline message.*, kemudian isikan pesan yang akan ditampilkan untuk memberitahukan bahwa situs sedang ada perbaikan (opsional), lalu tambahkan gambar (opsional).
4. Terakhir, tekan tombol *Save* kemudian coba akses kembali situsnya (dalam keadaan tidak *login* sebagai admin).

## Cara Pemakaian
[`^ kembali ke atas ^`](#aplikasi-october)

1. Tampilan aplikasi web
	1. Tampilan utama (*default*)
	2. Tampilan halaman blog (*default*)
	3. *Dashboard admin*
	
2. Fungsi-fungsi utama
	1. Register *User* Baru
		* Fungsi ini digunakan apabila ada *guest* yang ingin menjadi penulis blog atau agar dapat menulis komentar di blog. Langkah pertama, lihat *widgets Login* yang terletak di *sidebar* kanan. Kemudian, klik tombol *Sign Up*
		
		* Setelah itu, isikan semua *field* yang diberikan
	
		* Setalahnya, klik tombol *Sign Up* dan akan muncul pemberitahuan bahwa *user* telah berhasil didaftarkan.
	
		* Lakukan login, kemudian akses http://YourURL/admin/.
	
	2. Buat Pos
		* Untuk membuat *post*, di halaman *dashboard admin*, klik *hamburger button* yang terletak di pojok kiri atas, kemudian pilih *Blog*
	
		* Setelah itu, klik tombol *Add Post*

		* Isikan *post* yang ingin dibuat, setelah selesai klik tombol *Save*
	
	3. Buat *Page* Baru
		* Untuk membuat *page*, dari halaman *dashboard admin*, klik *hamburger button* yang terletak di pojok kiri atas, kemudian pilih *Site*

		* Setelah itu, klik tombol *Add Page*, kemudian pilih *Page*

		* Isikan *page* yang ingin dibuat sesuai *field* yang tersedia, kemudian klik tombol *Save*

	4. Mengganti Tema
		* Unduh koleksi tema di halaman *Marketplace* dan pilih tab Tema

		* Pilih salah satu tema, kemudian klik

		* Setelah terunduh, klik tombol *Enable* untuk mengaktifkan tema

		* Tema yang telah terunduh dapat dilihat di halaman *System* dan pilih tab *Theme*
	
	5. Menambahkan Widget
		* Buka halaman *Site* melalui menu di *hamburger button*, kemudian pilih tab *Widgets*
	
		* Klik tombol *Add Widgets*

		* Pilih salah satu kategorinya, *Menu* untuk menambahkan *list* halaman, *Text* untuk menambahkan ukiran kata-kata, dan *Link* untuk menambahkan pranala ke halaman lain.

		* Isikan *field* yang perlu isi, kemudian atur tata letaknya di menu *dropdown* sebelah kanan

		* Setelah selesai, klik *Save*. Cek halaman awal apakah *widget* sudah berhasil ditambahkan.

	6. Manajemen *User* dan Mengatur *Permission* berdasarkan *role*
		* Buka halaman *Users* melalui menu di *hamburger button*
	
		* Diberikan *list* *user* yang sudah terdaftar, apabila *role*-nya adalah *admin*, maka ia bisa menghapus/memblokir *user*

		* Untuk mengatur *Permission* untuk *Role* tiap-tiap *user*, klik tab *Permission*.
		* Di situ, kita bisa memberikan/melepas izin untuk tiap jenis aktivitas yang dapat dilakukan.


## Pembahasan
[`^ kembali ke atas ^`](#aplikasi-october)

Aplikasi web PageKit merupakan CMS yang bisa dikatakan baru, namun memiliki beberapa fitur yang diunggulkan, di antaranya:
1. Tampilan yang terlihat sederhana, namun tetap modern dan sangat *responsive*
2. Dibuat menggunakan *framework* Vue.js dan PHP Symfony 
3. Proses instalasi dan konfigurasi yang mudah dan serba otomatis
4. Terdapat *file manager* yang berfungsi mengatur *file* apa saja yang diunggah ke server
5. Terdapat editor teks berupa HTML dan Markdown
6. Terdapat Pengaturan kontrol *cache*
7. Personalisasi dan pengaturan halaman situs yang tidak rumit

Namun dibalik beberapa keunggulan PageKit di atas, masih terdapat beberapa kekurangan, di antaranya:
1. Walaupun dapat dikatakan penggunaanya mudah, tapi untuk mengatur tata letak *widget* yang akan ditampilkan di situs masih menggunakan menu *dropdown*. Tidak seperti wordpress yang memiliki *live preview*. 
2. Variasi tema dan ekstensi (*plugin*) yang diberikan juga masih sedikit, selain itu kita tidak dapat membuat tema sendiri(kustomisasi) dan hanya dapat menggunakan tema yang disediakan.

### Perbandingan aplikasi PageKit dengan aplikasi web 'Subrion'
Subrion merupakan CMS yang dapat digunakan mempermudah user dalam membangun situs web. Dengan berbagai macam fitur yang ditawarkan, terdapat beberapa kesamaan dengan aplikasi PageKit, di antaranya:
1. Aplikasi subrion digunakan untuk membuat situs blog.
2. Terdapat *storage management* untuk mengatur *file-file* yang terunggah ke server.
3. Kustomisasi halaman (membuat baru, menghapus, mengubah status (aktif/inaktif/draft)).
4. Memiliki *user management* lengkap dengan *permission* sesuai *role*-nya.

Namun ada beberapa hal yang perlu diperhatikan sebagai ciri pembeda.
1. Pada PageKit Halaman *admin* memiliki tampilan yang sederhana (tidak banyak *content* yang ditampilkan dalam suatu halaman), sedangkan Subrion menampilkan banyak *content*.
2. Pada PageKit hanya terdapat pengaturan HTTPS saja, sedangkan Subrion dilengkapi dengan fitur keamanan di antaranya HTTPS, anti-CSRF, Build-in Captcha).
3. Pada subrion juga rerdapat fitur unik, yaitu adanya fitur *SQL Tools*, tanpa perlu membuka *phpMyAdmin* kita dapat melihat isi *database*-nya

## Referensi
[`^ kembali ke atas ^`](#aplikasi-october)

1. [About | PageKit](https://pagekit.com/about) - PageKit
2. [CLI | Pagekit](https://pagekit.com/docs/developer/cli) - PageKit
3. [How To Rewrite URLs with mod_rewrite for Apache on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04) - DigitalOcean
4. [Installation | PageKit](https://pagekit.com/docs/getting-started/installation) - PageKit
