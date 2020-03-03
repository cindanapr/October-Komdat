# Aplikasi Web "PageKit"
<h1 align="center"><img src="https://pagekit.com/storage/pagekit-logo.svg" width="500px"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Maintenance](#maintenance) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:

## Sekilas Tentang 
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

PageKit merupakan aplikasi *web content management system*. PageKit digunakan untuk mempermudah pengguna dalam membangun situs web. Pagekit adalah CMS modular dan ringan yang dibangun dengan teknologi modern. Dengan market share kurang dari 0.1% dan 1,465 *website* yang aktif menggunakan CMS ini, menjadikan Pagekit sebagai salah satu CMS untuk *blogging* terpopuler di dunia, tepatnya berada di posisi ke-9 setelah Posthaven. PageKit memiliki beberapa fitur, di antaranya, menyediakan pengaturan untuk membuat halaman baru (contoh: membuat halaman untuk *blog*, mengorganisasi *file*, dan personalisasi *web*).

## Instalasi
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

#### Kebutuhan
- Apache 2.2+ atau Nginx
```
$ sudo apt install apache2
```

- MySQL Server 5.1+ atau SQLite 3
```
$ sudo apt install mysql-server
```

- PHP versi 5.5.9+
```
$ sudo apt install php
```

- Ekstensi PHP yang harus aktif: JSON, Session, ctype, Tokenizer, SimpleXML, DOM, mbstring, PCRE 8.0+, ZIP dan PDO dengan *driver* MySQL atau SQLite
```
$ sudo apt install libapache2-mod-php
$ sudo apt install php-mysql
$ sudo apt install php-gd php-mcrypt php-mbstring php-xml php-ssh2
$ sudo service apache2 restartapt-get install zip unzip
```

- (*opsional*) Ekstensi PHP: curl, iconv, XML Parser, APC atau XCache untuk *caching*
```
$ sudo apt-get install phpmyadmin php-mbstring php-gettext
```

#### Cara instalasi
1. Unduh arsip ZIP instalasi Pagekit dan simpan ke dalam direktori pagekit. 
```
$ mkdir pagekit
$ cd pagekit
$ wget bit.ly/KomdatAyakOciNisa
```

2. *Unzip* arsip yang sudah terunduh. 
```
$ unzip pagekit-1.0.13.zip
```

3. Pindahkan direktori pagekit ke /var/www/html/ (direktori sekarang "pagekit")
```
$ sudo mv ../pagekit/ /var/www/html/
```

4. Selanjutnya buka http://localhost (localhost -> alamat IP atau URL kamu). Selanjutnya ikuti langkah-langkah untuk konfigurasi.
	- Pengaturan Bahasa
	- Konfigurasi Database
	- Pengaturan Informasi Situs
	- Selesai! (Tampilan halaman *admin*)

## Konfigurasi
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)
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
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

PageKit menyediakan fitur *maintenance* apabila admin web ingin melakukan perbaikan pada situs. 
1. Pada halaman *dashboard* admin (http://URL/admin/dashboard), klik tombol *hamburger* di pojok kiri atas, kemudian pilih ikon *Site*
2. Pada halaman *site*, pilih tab *Settings*, kemudian pilih submenu *Maintenance*
3. Setelah itu, centang *Put the site offline and show the offline message.*, kemudian isikan pesan yang akan ditampilkan untuk memberitahukan bahwa situs sedang ada perbaikan (opsional), lalu tambahkan gambar (opsional).
4. Terakhir, tekan tombol *Save* kemudian coba akses kembali situsnya (dalam keadaan tidak *login* sebagai admin).

## Cara Pemakaian
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

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
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

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
[`^ kembali ke atas ^`](#aplikasi-web-pagekit)

1. [About | PageKit](https://pagekit.com/about) - PageKit
2. [CLI | Pagekit](https://pagekit.com/docs/developer/cli) - PageKit
3. [How To Rewrite URLs with mod_rewrite for Apache on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04) - DigitalOcean
4. [Installation | PageKit](https://pagekit.com/docs/getting-started/installation) - PageKit
