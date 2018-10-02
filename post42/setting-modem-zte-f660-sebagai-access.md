---
title: 'Setting Modem ZTE F660 Sebagai Access Point'
date: 2017-08-16T10:41:00.000-07:00
draft: false
---

1. Reset terlebih dahulu modem Zte F660 anda dengan menekan tombol reset pada bagian samping Modem

- Setting IP komputer anda sesuai dengan IP Modem Zte F660,

- Login ke modem menggunakan web browser dengan memasukkan alamat IP 192.168.1.1, gunakan username dan password "admin".

2. Selanjunya buka menu Network >> Wan >> Wan Connection, dan buatlah 1 Wan Connection baru seperti ini :

- _IP Version : IPV4_

- _Type : DHCP_

- _Connection Name: Create Wan Connection_

- _Service List : INTERNET_

- _VLAN Mode : TRANSPARENT_

- Kemudian klik tombol **Create**.

3. Selanjutnya buka menu  _Network>>WLAN >> Basic_

- Centang pada bagian _Wireless RF Mode_, dan klik tombol **Submit**.

4. Buka menu _Network>>LAN>>DHCP Server_, 

- Buang centang pada bagian _Enable DHCP Server_, lalu berikan centang pada bagian_Assign IspDNS_ dan juga pada_Enable TCP DNS_. dan tekan tombol **Submit**

  

5. Buka tab _DHCP Mode_, pada bagian ini set Port _LAN1, LAN2, LAN3, LAN4, dan SSID1_ pada DHCP Mode _Default_. lalu tekan tombol **Submit.**