---
title: 'Cara mudah menginstall ZeosLib di Lazarus'
date: 2017-03-23T01:44:00.000-07:00
draft: false
tags : [Lazarus]
---

ZeosLib menurut pembuatnya adalah komponen database (meliputi MySQL, Postgresql, MSSQL, Firebird, Sybase, Oracle dan SQLite) populer, gratis dan opensource yang dapat digunakan di Freepascal/Lazarus, Delphi, Kylix dan C++ Builder.  
  
Berikut ini adalah cara mudah untuk menginstall ZeosLib di Lazarus, saya coba di Lazarus 1.x dan Freepascal 2.6.2.  

**1\. Download ZeosLib**

  

Download file ZeosLib di sini : [http://sourceforge.net/projects/zeoslib/](http://sourceforge.net/projects/zeoslib/). Pastikan anda mendownload versi yang paling baru. Pada saat tulisan ini saya tulis, versi stabil terbaru adalah versi 7.1.4. Simpan file tersebut di tempat yang anda suka.

  

  

**2\. Extract ZeosLib**

  

File yang kita download biasanya dalam bentuk .zip, oleh karena itu silahkan extract. Hasilnya seperti gambar di bawah ini.

  

  

[![](http://1.bp.blogspot.com/-D3y6t6-_Pjo/VJ4A6busWnI/AAAAAAAAE0U/uwge98CXk9g/s1600/Selection_119.jpg)](http://1.bp.blogspot.com/-D3y6t6-_Pjo/VJ4A6busWnI/AAAAAAAAE0U/uwge98CXk9g/s1600/Selection_119.jpg)

  

  

Optional:

  
Pindahkan folder hasil extract ZeosLib tersebut ke dalam folder **components** di tempat lazarus terinstall. Kemudian rename folder tersebut dengan nama yang lebih umum, misalnya cukup **zeosdbo**.  
  
Hal ini tidak harus anda lakukan, akan tetapi menurut saya pribadi sangat saya rekomendasikan. Alasannya, untuk mengurangi resiko folder tersebut tidak sengaja terhapus atau menghindari konflik jika komponent tersebut anda gunakan pada 2 atau lebih lazarus.  
  
**3\. Install ZoesLib**  
Jalankan lazarus anda, kemudian klik menu **Package > Open Package File** .  

[![](http://2.bp.blogspot.com/-JXCqoJrhRUI/VJ4EVT5CecI/AAAAAAAAE0o/hLfUAuk_2H4/s1600/Workspace%2B1_121.jpg) ](http://2.bp.blogspot.com/-JXCqoJrhRUI/VJ4EVT5CecI/AAAAAAAAE0o/hLfUAuk_2H4/s1600/Workspace%2B1_121.jpg)

  

  

Browse ke folder tempat anda meng-extract ZoesLib sebelumnya, atau ke folder **zoesdbo** jika anda memindah dan merename-nya menjadi zoesdbo. File yang harus anda cari adalah **zcomponent.lpk** yang terletak pada sub folder **packages/lazarus**. Untuk lebih jelas, silahkan perhatikan gambar di bawah ini.

  

  

[![](http://1.bp.blogspot.com/-Yo73OSKI3Y4/VJ4F6ZX5ZXI/AAAAAAAAE00/OSOouHpRTp8/s1600/Open%2BPackage%2BFile_122.jpg)](http://1.bp.blogspot.com/-Yo73OSKI3Y4/VJ4F6ZX5ZXI/AAAAAAAAE00/OSOouHpRTp8/s1600/Open%2BPackage%2BFile_122.jpg)

  

  

Tekan tombol **Open**, maka akan muncul tampilan seperti gambar di bawah ini.

  

  

[![](http://4.bp.blogspot.com/-cOzbdLS8aig/VJ4GQOzspwI/AAAAAAAAE08/OPJ0kNHQdYQ/s1600/Package%2Bzcomponent_123.jpg)](http://4.bp.blogspot.com/-cOzbdLS8aig/VJ4GQOzspwI/AAAAAAAAE08/OPJ0kNHQdYQ/s1600/Package%2Bzcomponent_123.jpg)

  

  

Tekan tombol **Use > Install** untuk mulai menginstall komponen ZoesLib.

  

  

[![](http://2.bp.blogspot.com/-2clr7racW0g/VJ4HblHzmtI/AAAAAAAAE1Q/qC-o3dmjjnU/s1600/Package%2Bzcomponent_124.jpg)](http://2.bp.blogspot.com/-2clr7racW0g/VJ4HblHzmtI/AAAAAAAAE1Q/qC-o3dmjjnU/s1600/Package%2Bzcomponent_124.jpg)

  
Lalu tekan tombol **OK** jika muncul konfirmasi seperti gambar di bawah ini.   
  

[![](http://3.bp.blogspot.com/-L9iwCHK7iiE/VJ4HJSobQRI/AAAAAAAAE1I/tjLytzEyD7g/s1600/Selection_125.jpg)](http://3.bp.blogspot.com/-L9iwCHK7iiE/VJ4HJSobQRI/AAAAAAAAE1I/tjLytzEyD7g/s1600/Selection_125.jpg)

  

  

  

Konfirmasi ini artinya bahwa jika kita menginstall komponen zcomponent.lpk, maka komponen-komponen pendukungnya secara otomatis akan terinstall, meliputi **zdbc, zplain zparsesql** dan **zcore**.

  

  

Tekan tombol **Yes** untuk mulai proses compile dan install. Proses compile dan install ini memperlukan waktu beberapa saat, jadi sabarlah menunggu.

  

  

[![](http://4.bp.blogspot.com/-IUbQAfe8eXY/VJ4JBPZMn1I/AAAAAAAAE1c/yKkA2C4Ld_0/s1600/Selection_126.jpg)](http://4.bp.blogspot.com/-IUbQAfe8eXY/VJ4JBPZMn1I/AAAAAAAAE1c/yKkA2C4Ld_0/s1600/Selection_126.jpg)

  

  

Jika semuanya berjalan lancar, maka lazarus akan secara otomatis restart, dan munculah tab komponen baru dengan nama **Zeos Access**. Selamat, komponen ZeosLib sudan berhasil terinstall dan siap untuk digunakan.

  

  

[![](http://4.bp.blogspot.com/-r-qwStvTTdM/VJ4L7ulYS-I/AAAAAAAAE1o/ppdL_2JJrLo/s1600/Lazarus%2BIDE%2Bv1.2.0%2B-%2Bproject1_127.jpg)](http://4.bp.blogspot.com/-r-qwStvTTdM/VJ4L7ulYS-I/AAAAAAAAE1o/ppdL_2JJrLo/s1600/Lazarus%2BIDE%2Bv1.2.0%2B-%2Bproject1_127.jpg)

  

  

Sekian tip kali ini, selamat mencoba dan semoga bermanfaat.

  
   
  
http://sinau-freepascal.blogspot.my/