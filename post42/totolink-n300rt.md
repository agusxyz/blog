---
title: 'Totolink N300RT'
date: 2017-11-26T03:13:00.002-08:00
draft: false
---

Panduan singkat install OpenWrt Totolink N300RT  
Download  
  

1.  FrmUpg : [http://www.anphat.vn/download/FirmwareUpgradeTool.zip](http://www.anphat.vn/download/FirmwareUpgradeTool.zip "http://www.anphat.vn/download/FirmwareUpgradeTool.zip")
2.  Putty : http://www.putty.org/
3.  Frimware totolink v2.1.6 : [http://www.totolink.net/include/download.asp?path=down/010300&file=N300RT-V2.1.6_20160516.zip](http://www.totolink.net/include/download.asp?path=down/010300&file=N300RT-V2.1.6_20160516.zip)
4.  Bootloder boot96E_32M: [https://drive.google.com/open?id=1p0SreEifzElS_cyngZZRL2lmGnR-Mvvi](https://drive.google.com/open?id=1p0SreEifzElS_cyngZZRL2lmGnR-Mvvi)
5.  OpenWrt  : [https://drive.google.com/open?id=1ykv6QkrqXJ_8vnX-6imib44XGFVNJZoA](https://drive.google.com/open?id=1ykv6QkrqXJ_8vnX-6imib44XGFVNJZoA)

**A. Downgrade Frimware Totolink ke v2.1.6**

1.  Dalam router dalam keadaan mati tekan Tombol Reset lalu hidupkan power. tunggu sampai lampu indikator lan berkedip.
2.  Matikan Firewall dan Buka FrmUpg.exe dan colokan LAN ke Port 1,2,3,4
3.  Di Frimware File pilih file Totolink v2.1.6 dan klik send, Tunggu sampai prosess selesai lalu restart router, cek 192.168.1.1 apakah sudah berhasil downgrade.

  

[![](https://1.bp.blogspot.com/-q6CSzmB7jDg/WhqdlmuuFWI/AAAAAAAAHcc/EeQdztoREH89JgTo0eF8T-LEWcL0qV_FwCLcBGAs/s320/totok1.png)](https://1.bp.blogspot.com/-q6CSzmB7jDg/WhqdlmuuFWI/AAAAAAAAHcc/EeQdztoREH89JgTo0eF8T-LEWcL0qV_FwCLcBGAs/s1600/totok1.png)

  

**B. Upgrade OpenWrt**

1.  Ulangi langkah no 1, Pilih file bootloder boot96E_32M. klik send. tunggu sampai selesai. bila prosess installasi selesai tapi muncul pesan time out. klik ok saja.
2.  Kemudian Pilih File Openwrt. klik tombol send lagi dan tunggu sampai prosess selesai.
3.  Restart router.
4.  Tunggu beberapa saat biasanya 1-3 menit ,lalu buka 192.168.1.1 kalo sudah bisa masuk luci.
5.  Buka Putty kemudian ketikan perintah berikut. 

  

firstboot  
  
Y  
  
reboot -f

  
**Note : **  

1.  Jangan lupa untuk Non Aktifkan Windwos Firewall.
2.  Saya pernah mengalami kasus, setelah install openwrt, tapi router tidak dapat diakses. Coba pindahkan Port Lan ke Port WAN.

sumber : https://wiki.openwrt.org/inbox/toh/totolink_n300rt