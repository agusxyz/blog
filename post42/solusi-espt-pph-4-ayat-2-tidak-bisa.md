---
title: 'Solusi eSPT PPh 4 Ayat 2 Tidak Bisa Cetak Application-Defined or Object-Defined Error'
date: 2018-07-11T20:39:00.001-07:00
draft: false
---

*   Yang pertama harus anda lakukan adalah tutup aplikasi eSPT PPh 4 ayat 2 kemudian silahkan cari file arpro2.dll. Banyak jika anda browsing, tetapi jika anda kesulitan dapat lihat di link berikut ini. **[https://drive.google.com/open?id=1ZQswTBtfZn-OFW4w9AKv-qCYIzilWBc7](https://drive.google.com/open?id=1ZQswTBtfZn-OFW4w9AKv-qCYIzilWBc7)**
*   Taruh file arpro2.dll misal di C:\
*   Setelah itu kita register file arpro2.dll dengan cara masuk CMD. Klik start ketik CMD, klik kanan Run As Administrator
*   Pada jendela CMD, ketik **regsvr32 c:\\arpro2.dll **lalu tekan enter
*   Setelah tekan Enter, pastikan arpro2.dll telah sukses teregister. Pesan yang akan muncul ketika sukses adalah "DllRegisterServer in c:\\arpro2.dll succeded".
*   Klik OK lalu buka kembali eSPT PPh 4 ayat 2 dan silahkan coba cetak ulang