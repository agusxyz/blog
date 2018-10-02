---
title: 'Git Hub'
date: 2017-03-17T21:54:00.000-07:00
draft: false
tags : [Explore]
---

[![](http://codinglite.com/wp-content/uploads/2017/03/gihub-300x118.png)](http://codinglite.com/wp-content/uploads/2017/03/gihub.png)  
  
GIT merupakan sebuah _Version Control System_ (VCS) yang digunakan dalam tim pengembangan perangkat lunak untuk bekerja bersama. _Version Control_ maksudnya sistem Git akan mencatat setiap perubahan yang terjadi pada _source code_ kita sehingga memungkinkan untuk mengambil kembali _source code_ lama jika suatu saat kita ingin kembali ke versi berapapun dari aplikasi yang pernah kita tulis.  
  
Misal seperti ini. Kita sedang mengembangkan sebuah aplikasi web menggunakan PHP. Ketika kita sudah selesai melakukan koding maka kita menyimpannya ke dalam _repository_ Git atau istilahnya _commit_. Pada langkah ini kita sudah membuat versi _source code_ kita katakanlah versi 1. Besoknya kita melakukan perubahan pada versi 1 kita tadi dan seperti sebelumnya kita juga melakukan _commit_ ke dalam _repository_, maka versi 2 akan tercipta. Lantas apakah versi 1 akan hilang? tidak. Setelah kita bekerja beberapa kali memperbaiki atau menambahkan fitur pada _source code_ kita sampai 20 versi pun kita akan selalu bisa untuk kembali ke versi lama yang keberapapun begitu juga sebaliknya.  
  
_Commit_ yang tadi kita lakukan hanya akan disimpan pada _repository_ lokal yang ada pada komputer kita. Lantas bagaimana agar bisa diakses bersama-sama oleh anggota tim? maka kita membutuhkan sebuah repository central. Website yang menyediakan jasa _repository_ central untuk Git adalah **Github.com**. Pada tulisan ini saya akan mencoba untuk menjelaskan dari langkah awal instalasi Git, penggunaan dasar hingga mengupload proyek kita ke Github.com  
  
Step by step-nya adalah sebagai berikut  

  

  
2.  Buat terlebih dahulu akun di [Github.com](http://www.github.com/) , caranya segampang mendaftar Facebook
  
4.  Downloadl software Git di [http://git-scm.com/downloads](http://git-scm.com/downloads), sesuaikan dengan sistem operasi yang kamu gunakan. Saya menggunakan Windows, kemudian install
  
6.  Masuk ke direktori tempat proyek PHP kalian berada, misal “**C:/XAMPP/htdocs/ProyekPHP**“. Source code yang ada pada folder ProyekPHP ini yang akan kita masukkan ke repository Git dan kita upload ke Github
  
8.  Untuk pengguna Windows klik kanan didalam folder ProyekPHP dan pilih Git Bash. Berikut adalah gambarnya
  

  

  
![](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/git-bash-212x300.png)  
  
Lakukan inisialisasi dengan mengetikkan perintah berikut pada Git Bash tadi  
  
\[java\]git init\[/java\]  
  
Perintah tersebut akan membuat sebuah repository lokal untuk proyek kita  

  

  
2.  Langkah berikutnya adalah memasukkan file-file source code serta folder pada proyek kedalam staging area, yaitu suatu kondisi dimana file serta folder source code dimasukkan ke dalam repository namun dalam keadaan temporary, belum disimpan. Untuk melakukannya gunakan perintah berikut  
      
    \[java\] git add \[/java\]  
      
    Perintah tersebut akan memasukkan seluruh file dan folder yang ada pada folder ProyekPHP. Jika ingin memasukkan satu persatu cukup tuliskan nama file lengkap dengan ekstensinya atau nama folder jika hanya ingin menambahkan satu folder  
    
      
    
        git add index.php
    
      
    
      
    
      
    
      
    
        git add nama_folder
    
      
    
      
    
  
4.  Setelah itu kita siap untuk menyimpan source code kita kedalam repository. Ketikkan perintah berikut  
    
      
    
        git commit -m &quot;Commit Pertama, Versi 1&quot;
    
      
    
      
    
      
    Perintah diatas akan menyimpan source code kita sekaligus memberikan catatan supaya mudah kita ingat
  
6.  Sekarang login ke Github.com dan buatlah sebuah repository baru dengan mengeklik tombol yang terletak pada kanan atas. Perhatikan gambar berikut
  

  

  

[![Membuat Repo Baru](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/create-repo.png)](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/create-repo.png)

  

  

  

  
2.  Buat repository dengan nama “PHPKeren” misalnya  
    
      
      
    [![Membuat Gihub Repo](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/create-repo-github-450x272.png)](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/create-repo-github.png)  
    
    Membuat Gihub Repo
    
      
      
    
      
    Setelah itu klik tombol “Create repository”
  
4.  Sekarang kita bisa mengakses remote repository dengan url https://github.com/blinkawan/PHPKeren.git misalnya
  
6.  Kembali ke Git Bash. Tambahkan remote repository yang barusan kita buat supaya proyek kita bisa diupload. Berikut perintahnya  
    
      
    
        git remote add origin https://github.com/blinkawan/PHPKeren.git
    
      
    
      
    
  
8.  Selanjutnya kita download terlebih dahulu file readme yang ada secara default ketika kita membuat repository di github dengan mengetikkan perintah  
    
      
    
        git pull origin master
    
      
    
      
    
  

  

  
Maka file readme.md akan berada pada folder proyek kita  

  
  
[![Readme.md](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/readme.png)](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/readme.png)  

Readme.md

  
  

  

  
*   Terakhir adalah mengupload ke Github dengan perintah  
    
      
    
        git push origin master
    
      
    
      
    
      
    masukkan username serta password jika diminta
  
*   Cek pada github maka file ktia sudah berada disana
  

  

  
  
[![Repository Github](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/file-di-github-750x415.png)](http://www.tutorial-webdesign.com/wp-content/uploads/2013/05/file-di-github.png)  

Repository Github