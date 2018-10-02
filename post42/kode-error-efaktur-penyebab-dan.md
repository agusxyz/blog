---
title: 'Kode Error eFaktur, Penyebab dan Solusinya'
date: 2017-05-15T18:52:00.000-07:00
draft: false
tags : [eFaktur, Explore, Kode Error eFaktur]
---

Kumpulan Kode Error eFaktur, Penyebab dan Solusi  

  
2.  **ETAX-10001 : Error Database Terjadi Kesalahan, tidak dapat membentuk header lampiran**  
    Penyebab :  
    Posting SPT di database selain ETaxInvoice  
    Solusi :
  
4.  **ETAX-10001 : Error Database**  
    Penyebab : \[1\] File di dalam folder db ada yang corrupt atau hilang (misal : corrupt karena mengcopy data base saat aplikasi menyala) \[2\] Di dalam folder db tidak terdapat folder ETaxInvoice atau terdapat folder selain folder ETaxInvoice yang bukan tercreate dari proses tambah database \[3\] Versi aplikasi tidak sama dengan versi db \[4\] PC server PKP mati / Database belum distart sebagai server (dalam hal menggunakan konfigurasi network db)    
      
    Solusi :  
    \[1\] Pastikan dalam folder db > ETaxInvoice terdapat folder log, seg0 dan tmp serta file db.lck, README\_DO\_NOT\_TOUCH\_FILE, dan service.properties \[2\]Pastikan folder db berisi folder ETaxInvoice dengan isi folder sesuai pada nomor \[1\] dan tidak ada folder selain ETaxInvoice yang ditambahkan sendiri. \[3\] Jalankan Aplikasi saat terhubung dengan internet untuk dapat melakukan update database aplikasi. \[4\] Pastikan PC server menyala dan aplikasi eFaktur berjalan / Lakukan start database sebagai server dari menu File > Administrasi Db dan tekan tombol Start Db Sebagai Server
  
6.  **ETAX-10002 : Tidak dapat mengambil data**  
    Penyebab :  
    \[1\] Koneksi antara server dan client terputus (Network Database)  
    Solusi :  
    Pastikan PC Server dan Client terkoneksi dengan baik. Tutup aplikasi di Client, koneksi kembali ke Server dan kemudian ulangi proses
  
8.  **ETAX-10003 : Input ke database tidak berhasil, periksa kembali data yang akan diinput**  
    Penyebab :  
    \[1\] Koneksi antara server dan client terputus (Network Database)  
    Solusi :  
    Pastikan PC Server dan Client terkoneksi dengan baik. Tutup aplikasi di Client, koneksi kembali ke Server dan kemudian ulangi proses
  
10.  **ETAX-10003 : Input ke database tidak berhasil, periksa kembali data yang akan diinput. "" Exception \[EclipseLink-4002\] (Eclipse Persistence Services - 2.5.0.v20130507-3faac2b): org.eclipse.persistence.exceptions.DatabaseException Internal Exception: java.sql.SQLIntegrityConstraintViolationException:... ""**  
    Penyebab :  
    \[1\] Merekam atau mengubah data user, referensi lawan transaksi, referensi barang/jasa di database selain ETaxInvoice. \[2\] Mengupdate profil PKP di database selain ETaxInvoice.  
    Solusi :  
    Rekam/ubah user, referensi lawan transaksi, referensi barnag/jasa serta update data Profil hanya bisa dilakukan dari default database yaitu ETaxInvoice.
  
12.  **ETAX-10003 : Input ke database tidak berhasil, periksa kembali data yang akan diinput \[EclipseLink-4002\] (Eclipse Persistence Services - 2.5.0.v20130507-3faac2b): org.eclipse.persistence.exceptions.DatabaseException Internal Exception: java.sql.SQLDataException: A truncation error was encountered trying to shrink VARCHAR**  
    Penyebab :  
    Ada isi data Faktur yang lebih dari 255 char baik untuk Nama Lawan Transaksi, Alamat Lawan Transaksi, Nama Barang, ataupun Referensi  
    Solusi :  
    Cek faktur. Kolom Nama LT, Alamat LT, Nama Barang, Kode Barang atau Referensi tidak boleh lebih dari 255 char
  
14.  **ETAX-10004 : Data tidak ditemukan**
  
16.  **ETAX-10005 : Database tidak ditemukan**  
    Penyebab :  
    Beberapa kemungkinan yang dapat terjadi antara lain folder DB terhapus, terkena virus yang menyebabkan aplikasi tidak menemukan posisi database e-faktur  
    Solusi :  
    Pastikan Database e-faktur terdapat dalam folder DB aplikasi
  
18.  **ETAX-10006 : Tidak dapat menstart database sebagai network server**  
    Penyebab :  
    Port yang digunakan untuk koneksi database belum dibuka  
    Solusi :  
    Pastikan port yang dipakai untuk koneksi database telah dibuka
  
20.  **ETAX-20001 : NPWP tidak lengkap**  
    Penyebab :  
    \[1\] Merekam/mengimpor referensi lawan transaksi dengan isian npwp kurang dari 15 digit \[2\] Merekam/mengimpor faktur/dokumen lain dengan isian npwp lawan transaksi null atau kurang dari 15 digit  
    Solusi :  
    Isikan npwp dengan benar baik di form inputan maupun di file csv yang akan diimpor
  
22.  **ETAX-20002 : Nomor Faktur sudah terdaftar**  
    Penyebab :  
    Merekam/mengimpor faktur dengan nomor faktur yang sudah pernah diinput sebelumnya  
    Solusi :
  
24.  **ETAX-20003 : Nomor Faktur tidak ditemukan**  
    Penyebab :  
    \[1\] Meretur faktur eTax yang belum terapprove \[2\] Merekam/impor dokumen lain pengganti untuk dokumen lain yang belum pernah diinput ke database lokal  
    Solusi :
  
26.  **ETAX-20004 : Format Angka salah**  
    Penyebab :  
    Isian data tidak sesuai dengan format yang ditentukan.  
    Solusi :  
    Isi kolom DPP, PPN, PPnBM, Harga, Jumlah Barang, Diskon dengan angka. Jika ada nilai pecahan, gunakan : - karakter titik sebagai sebagai pemisah pecahan untuk mekanisme impor - karakter koma sebagai tanda pemisah pecahan untuk input dari interface
  
28.  **ETAX-20005 : Format NPWP tidak sesuai**  
    Penyebab :  
    Isian data NPWP tidak sesuai dengan format dan/atau tidak sesuai dengan cek digit  
    Solusi :  
    Isikan NPWP dengan angka 15 digit dan benar
  
30.  **ETAX-20006 : Format tanggal salah**  
    Penyebab :  
    Isian data tanggal tidak sesuai dengan format yang ditentukan  
    Solusi :  
    Isikan tanggal sesuai dengan format yang ditentukan yaitu tanggal/bulan/tahun.
  
32.  **ETAX-20007 : Nomor Faktur tidak lengkap**  
    Penyebab :  
    Format Nomor Seri Faktur Pajak tidak sesuai dengan format yang ditentukan  
    Solusi :  
    Lakukan cek ulang atas Nomor Seri Faktur Pajak yang direkam pada referensi NSFP
  
34.  **ETAX-20008 : Error Validasi**  
    Penyebab :  
    1\. Tidak mengisi inputan mandatori 2. Data inputan tidak sesuai dengan format yang ditentukan.  
    Solusi :  
    \[1\] Pastikan mengisi semua kolom isian yang mandatory \[2\] Isikan data sesuai format pengisian.
  
36.  **ETAX-20009 : Lawan Transaksi terpakai sebagai referensi**
  
38.  **ETAX-20010 : Barang/Jasa terpakai sebagai referensi di Faktur**
  
40.  **ETAX-20011 : Tidak dapat mengupload faktur**
  
42.  **ETAX-20012 : NPWP terdaftar**
  
44.  **ETAX-20013 : Lawan Transaksi tidak lengkap**  
    Penyebab :  
    \[1\] Kolom pertama Baris LT pada file csv tidak memakai diisi LT \[2\] Kolom isian pada baris LT kurang atau format isi data nya tidak sesuai dengan skema impor  
    Solusi :  
    Periksa file CSV, cek kolom dan isian data pada baris LT.Pastikan sesuai dengan skema impor dari DJP
  
46.  **ETAX-20014 : Nilai tidak boleh kosong**  
    Penyebab :  
    Field yang tertera pada pesan error belum diisi  
    Solusi :  
    Pastikan data diisi dengan benar
  
48.  **ETAX-20015 : Belum memasukkan pilihan**  
    Penyebab :  
    Mengklik tombol buka SPT tanpa memilih SPT yang akan dibuka  
    Solusi :  
    Untuk membuka SPT, klik baris SPT yang akan dibuka kemudian tekan tombol Buka SPT untuk Diubah
  
50.  **ETAX-20016 : Range nomor faktur sudah terdaftar**  
    Penyebab :  
    Menginputkan referensi range nomor faktur yang sama atau beririsan dengan salah satu range nomor faktur yang sudah direkam  
    Solusi :  
    Periksa kembali range nomor faktur. Pastikan range yang akan direkam belum ada di daftar referensi range nomor faktur
  
52.  **ETAX-20017 : Nomor Faktur tidak termasuk dalam range Referensi Nomor Faktur**  
    Penyebab :  
    Merekam atau mengimpor faktur keluaran dengan nomor yang tidak ada dalam range di referensi nomor faktur  
    Solusi :  
    Periksa kembali nomor faktur yang digunakan dan pastikan nomor faktur tersebut berada dalam range di referensi nomor faktur
  
54.  **ETAX-20018 : Range Nomor Faktur tidak tersedia, Daftarkan Referensi Nomor Faktur terlebih dahulu**  
    Penyebab :  
    \[1\] Belum menginputkan range nomor faktur \[2\] Nomor faktur yang terpakai sudah sampai ke range nomor terakhir yang ada  
    Solusi :  
    \[1\] Inputkan range nomor faktur yang diperoleh dari KPP \[2\] Dalam hal nomor merekam faktur dengan nomor yang terlewat dan masih didalam range, klik OK pada Error dan lanjutkan rekam faktur dengan mengisi 8 digit nomor seri secara manual atau bisa dengan melakukan impor
  
56.  **ETAX-20019 : Tidak bisa mengubah data. Data yang akan dihapus dipakai sebagai referensi**  
    Penyebab :  
    Menghapus data referensi lawan transaksi atau barang/jasa yang sudah pernah dipakai dalam pembuatan faktur pajak  
    Solusi :  
    Data referensi yang sudah pernah dipakai tidak bisa dihapus
  
58.  **ETAX-20020 : Kode Barang/Jasa sudah terdaftar. Tidak dapat memakai Kode yang sama**  
    Penyebab :  
    Merekam/Impor data barang dengan kode barang yang sudah ada di referensi barang/jasa  
    Solusi :  
    Data referensi yang sudah pernah dipakai tidak bisa dihapus
  
60.  **ETAX-20021 : Nama Barang/Jasa sudah terdaftar. Tidak dapat memakai Nama yang sama**  
    Penyebab :  
    Merekam/Impor data barang dengan nama barang yang sudah ada di referensi barang/jasa  
    Solusi :  
    Data referensi yang sudah pernah dipakai tidak bisa dihapus
  
62.  **ETAX-20022 : Barang/Jasa tidak lengkap**  
    Penyebab :  
    \[1\] Baris OF pada file csv tidak memakai flag OF \[2\] Kolom isian pada baris OF kurang atau format isi data nya tidak sesuai dengan skema impor  
    Solusi :  
    Periksa file CSV, cek kolom dan isian data pada baris OF.Pastikan sesuai dengan skema impor dari DJP
  
64.  **ETAX-20023 : Format faktur salah**  
    Penyebab :  
    Format isian data csv yang diimpor tidak sesuai dengan sekma impor dari DJP  
    Solusi :  
    \[1\] Periksa kembali file csv dan pastikan isian data telah sesuai dengan skema impor DJP. \[2\] Periksa karakter pemisah (delimiter) yang dipakai, pastikan karakter pemisah pada form Impor sama dengan karakter pemisah di file CSV
  
66.  **ETAX-20024 : Masa Faktur tidak boleh kurang dari tanggal faktur**  
    Penyebab :  
    Merekam/impor faktur dengan isian masa kurang dari bulan tanggal faktur  
    Solusi :  
    Pastikan masa pelaporan faktur keluaran pada form Input Faktur atau pada file csv impor diisi dengan benar
  
68.  **ETAX-20025 : Masa Faktur melebihi batas ketentuan pelaporan Faktur Pajak**  
    Penyebab :  
    Merekam/Impor faktur pajak masukan dengan isian masa lapor lebih dari 3 bulan dari tanggal faktur  
    Solusi :  
    Periksa masa pelaporan faktur masukan, pastikan masa lapor tidak lebih 3 bulan dari tanggal faktur
  
70.  **ETAX-20026 : Flag Pengganti tidak sesuai format**  
    Penyebab :  
    Kolom fg_pengganti di skema impor diisi selain angka 0 dan 1  
    Solusi :  
    Isikan kolom fg_pengganti dengan : - 0 untuk faktur normal - 1 untuk faktur penganti
  
72.  **ETAX-20027 : Tanggal Faktur Pengganti tidak boleh kurang dari Faktur Pajak**  
    Penyebab :  
    Tanggal Faktur Pengganti kurang dari Tanggal Faktur Pajak yang diganti  
    Solusi :  
    Tanggal Faktur Pajak Pengganti minimal sama dengan Tanggal Faktur Pajak yang diganti.
  
74.  **ETAX-20028 : Jumlah Dpp, Ppn, PPnBm Objek Faktur tidak sama dengan nilai Faktur**  
    Penyebab :  
    Nilai Jumlah DPP, PPN dan PPnBM pada baris FK tidak sama dengan total nilai DPP, PPN dan PPnBM pada baris OF  
    Solusi :  
    Cek file CSV. Kolom Jumlah DPP/Jumlah PPN/Jumlah PPnBM baris FK nilainya harus sama dengan total nilai DPP/PPN/PPnBM pada baris Ofnya
  
76.  **ETAX-20029 : Masa Faktur lebih besar dari tanggal ETAXReady, Faktur harus direkam dengan ETax Invoice**  
    Penyebab :  
    Merekam retur manual untuk Faktur Pajak Keluaran yang seharusnya sudah menggunakan efaktur  
    Solusi :  
    1\. Rekam Pajak Keluaran nya terlebih dahulu dan lakukan upload
  
78.  **ETAX-20030 : Tanggal Retur tidak boleh lebih kecil dari tanggal Faktur**  
    Penyebab :  
    Menginput tanggal Retur lebih kecil dari tanggal faktur yang diretur  
    Solusi :  
    Isikan tanggal retur lebih besar sama dengan tanggal faktur pajak yang diretur
  
80.  **ETAX-20031 : Masa Retur tidak boleh lebih kecil dari tanggal Retur**  
    Penyebab :  
    Menginput masa Retur lebih kecil dari tanggal retur  
    Solusi :  
    Isikan masa retur sama dengan bulan retur
  
82.  **ETAX-20032 : Saldo DPP untuk retur kurang**  
    Penyebab :  
    Mengisi nilai DPP retur lebih besar dari nilai DPP faktur yang diretur  
    Solusi :
  
84.  **ETAX-20033 : Saldo PPN untuk retur kurang**  
    Penyebab :  
    Mengisi nilai PPN retur lebih besar dari nilai DPP faktur yang diretur  
    Solusi :
  
86.  **ETAX-20034 : Saldo PPnBm untuk retur kurang**  
    Penyebab :  
    Mengisi nilai PPnBM retur lebih besar dari nilai DPP faktur yang diretur  
    Solusi :
  
88.  **ETAX-20035 : Masa Faktur kurang dari tanggal ETAXReady, Faktur Non ETax**  
    Penyebab :  
    Merekam/impor faktur dengan masa pelaporan sebelum ditetapkan sebegai pengguna efaktur  
    Solusi :  
    Cek tanggal faktur pajak. Faktur pajak dengan tanggal transaksi sebelum ditetapkan sebagai pengguna etax tidak bisa dibuat melalui aplikasi eFaktur.
  
90.  **ETAX-20035 : DPP tidak boleh lebih kecil dari 0**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    cukup jelas
  
92.  **ETAX-20036 : NPWP tidak terdaftar**
  
94.  **ETAX-20036 : PPN tidak boleh lebih kecil dari 0**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    cukup jelas
  
96.  **ETAX-20037 : PPnBM tidak boleh lebih kecil dari 0**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    cukup jelas
  
98.  **ETAX-20038 : Faktur Pajak Batal tidak ditemukan**
  
100.  **ETAX-20039 : Tidak ditemukan faktur yang akan diganti**  
    Penyebab :  
    Salah mengisi Nomor Seri Faktur Pajak yang akan diganti  
    Solusi :  
    Pastikan kembali Nomor Seri Faktur Pajak yang akan diganti
  
102.  **ETAX-20040 : Faktur tidak dapat dibuat**
  
104.  **ETAX-20040 : Faktur tidak dapat dibuat. (Kode Jenis transaksi 07… )**  
    Penyebab :  
    Skema impor kolom id\_keterangan\_tambahan tidak diisi atau diisi tapi dengan nilai data yg tidak sesuai dengan ketentuan  
    Solusi :  
    Untuk kode jenis transaksi 07/08, kolom id\_keterangan\_tambahan harus diisi dan nilai nya sesuai dengan ketentuan skema impor.
  
106.  **ETAX-20041 : Nilai DPP tidak cukup**
  
108.  **ETAX-20042 : Nilai PPN tidak cukup**
  
110.  **ETAX-20043 : Nilai PPnBM tidak cukup**
  
112.  **ETAX-20044 : SPT Kurang Bayar**  
    Penyebab :  
    \[1\] Membuat File CSV untuk SPT Kurang Bayar tanpa merekam SSP terlebih dahulu  
    Solusi :  
    \[1\] Dalam hal SPT Kurang Bayar, rekam terlebih dahulu SSP nya
  
114.  **ETAX-20045 : SPT Lebih Bayar**
  
116.  **ETAX-30001 : Tidak dapat melakukan enkripsi / dekripsi**
  
118.  **ETAX-30002 : Tidak dapat melakukan hashing**  
    Penyebab :  
    Sertifikat dipindah atau Folder aplikasi dipindah  
    Solusi :  
    Pastikan file sertifikat ada dan tidak berpindah tempat penyimpanan. Dalam hal memindahkan sertifikat, setting kembali dari menu Administrasi Sertifikat
  
120.  **ETAX-30003 : Library Sigar Error**
  
122.  **ETAX-30004 : Error Upload Faktur**
  
124.  **ETAX-30005 : Error objek mapping**  
    Penyebab :  
    Format isian data csv yang diimpor tidak sesuai dengan skema impor dari DJP  
    Solusi :  
    Periksa kembali file csv dan pastikan isian data telah sesuai dengan skema impor DJP.
  
126.  **ETAX-30006 : File tidak ditemukan**  
    Penyebab :  
    File CSV yang akan diimpor tidak ada  
    Solusi :  
    \[1\] Periksa kembali lokasi tempat file CSV yang akan diimpor telah sesuai dengan lokasi file CSV yang ada di form Impor. \[2\] Ulangi kembali proses impor dengan mengklik tombol Open dan arahkan ke folder file csv yang sebenarnya.
  
128.  **ETAX-30007 : File tidak dapat dibaca**
  
130.  **ETAX-30008 : Algoritma Hash tidak ditemukan**
  
132.  **ETAX-30009 : Report tidak dapat dibuat**
  
134.  **ETAX-30010 : Disk I/O error**
  
136.  **ETAX-30011 : Profile Belum Diregister**  
    Penyebab :  
    Belum melakukan update profile pada aplikasi e-faktur  
    Solusi :  
    Lakukan update profile pada menu update profile
  
138.  **ETAX-30022 : File Certificate belum tersedia. Pilih file certificate terlebih dahulu di Administrasi**  
    Penyebab :  
    Belum pernah mendaftarkan file certificate pada aplikasi e-faktur  
    Solusi :  
    Daftarkan file Certificate yang dimiliki pada menu administrasi sertifikat
  
140.  **ETAX-30023 : File Certificate tidak bisa di pakai**  
    Penyebab :  
    \- Format Certificate Salah - File Certificate tidak ditemukan - Certificate bukan milik user terdaftar - Tidak ditemukan Certificate yang benar untuk user  
    Solusi :  
    Pastikan menggunakan file sertifikat digital yang telah diberikan oleh DJP
  
142.  **ETAX-30024 : Harga Barang/Jasa tidak boleh lebih kecil sama dengan 0**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    cukup jelas
  
144.  **ETAX-30025 : Faktur sedang dalam proses upload ke DJP**
  
146.  **ETAX-30026 : Faktur sudah diapproved oleh DJP**
  
148.  **ETAX-30027 : Tanggal Faktur sebelum ETAX ready**  
    Penyebab :  
    Merekam / mengimpor data faktur pajak keluar dengan tanggal faktur sebelum PKP ditetapkan sebagai pengguna efaktur  
    Solusi :  
    Cek tanggal faktur pajak. Faktur pajak dengan tanggal transaksi sebelum ditetapkan sebagai pengguna etax tidak bisa dibuat melalui aplikasi eFaktur.
  
150.  **ETAX-30028 : Tanggal salah**
  
152.  **ETAX-30029 : Nomor Faktur tidak benar**  
    Penyebab :  
    \[1\] Nomor faktur yang diinput tidak sesuai dengan tanggal faktur \[2\] Merekam/impor dokumen lain pengganti untuk dokumen lain yang belum direkam di aplikasi  
    Solusi :  
    \[1\] Cek nomor faktur dan tanggal faktur. Faktur dengan nomor xxx-yy.xxxxxxxx hanya bisa dipakai untuk penyerahan di tahun yy \[2\] Rekam/Impor terlebih dahulu dokumen lain yang akan diganti. Setelah itu rekam/impor dokumen lain pengganti nya
  
154.  **ETAX-30030 : Nomor Retur sudah terdaftar**  
    Penyebab :  
    Nomor retur dan nomor faktur pajak yang diretur yang direkam/diimpor sudah ada didatabase.  
    Solusi :  
    Cek kembali data dokumen retur yang akan direkam. Pastikan nomor retur dan faktur pajak nya sudah benar dan belum pernah direkam/impor sebelumnya
  
156.  **ETAX-30031 : Dokumen Lain tidak lengkap**  
    Penyebab :  
    \[1\] Mengisi kolom DK_DM untuk dokumen lain dengan isian selain DK / DM \[2\] Kolom isian kurang atau format isi data nya tidak sesuai dengan skema impor dokumen lain  
    Solusi :  
    Periksa file CSV, cek kolom dan isian datanya.Pastikan sesuai dengan skema impor dari DJP
  
158.  **ETAX-40001 : Tidak dapat menghubungi E-TaxInvoice Server**  
    Penyebab :  
    \[1\] Tidak terhubung dengan internet \[2\] Sertifikat Elektronik sudah expired atau direvoke. \[3\] Koneksi ke DJP di https://svc.efaktur.pajak.go.id diblok sehingga tidak bisa terkoneksi.  
    Solusi :  
    \[1\] Cek koneksi internet, pastikan PC terhubung dengan internet. Apabila koneksi internet dengan proxy, pastikan sudah melakukan setting proxy aplikasi dengan benar di menu Referensi > Setting Aplikasi \[2\] Silahkan ajukan permintaan sertifikat elektronik yang baru.
  
160.  **ETAX-40002 : Error di service**  
    Penyebab :  
    \[1\] Koneksi ke DJP di https://svc.efaktur.pajak.go.id diblok sehingga tidak bisa terkoneksi. \[2\] Bisa dari antivirus, firewall atau settingan proxy nya \[3\] Date-Time PC tidak sesuai dengan kondisi real  
    Solusi :  
    \[1\] Silahkan hubungi Network Administrator untuk melakukan pengaturan agar dapat terhubung ke https://svc.efaktur.pajak.go.id Atau gunakan internet direct/modem untuk menjalankan eFaktur. \[2\] Periksa antivirus, firewall dan setting proxy pastikan koneksi ke DJP tidak diblok \[3\] Silahkan setting date-time PC sesuai dengan tanggal saat ini
  
162.  **ETAX-40003 : Error di service session**
  
164.  **ETAX-40004 : User tidak dapat mengakses service**  
    Penyebab :  
    Salah mengisi capctha, password ataupun passphrase  
    Solusi :  
    \[1\] Pastikan sudah menginputkan password, captcha ataupun passphrase dengan benar. \[2\] Pastikan PC terhubung dengan koneksi internet
  
166.  **ETAX-40005 : Error di service registrasi**  
    Penyebab :  
    Salah mengisi passphrase, kode aktivasi, captcha atau password.  
    Solusi :  
    \[1\] Pastikan sudah menginputkan passphrase dengan benar. Dalam hal muncul error setelah merekam passphrase silahkan ulangi dari proses load sertifikat elektronik \[2\] Pastikan menginputkan kode aktivasi dengan benar. Kode Aktivasi berupa kombinasi huruf kapital-angka dan tanpa format. \[3\] Pastikan menginputkan captcha dengan benar. Jika kurang jelas, silahkan tekan tombol refresh. \[4\] Pastikan menginputkan password dengan benar.
  
168.  **ETAX-40006 : Error update**
  
170.  **ETAX-40007 : URL tidak sesuai dengan format**
  
172.  **ETAX-40008 : Versi Aplikasi E-Faktur belum terupdate**
  
174.  **ETAX-40009 : Tidak dapat meload konfigurasi aplikasi**
  
176.  **ETAX-40010 : Tidak dapat menyimpan konfigurasi aplikasi**  
    Penyebab :  
    Folder Aplikasi EFaktur berada di drive yang membutuhkan UAC (User Account Control) tinggi yakni Administrator.  
    Solusi :  
    Pindahkan lokasi folder Aplikasi EFaktur ke drive yang tidak membutuhkan UAC Administrator.
  
178.  **ETAX-40011 : Tidak dapat melanjutkan**
  
180.  **ETAX-50001 : Tidak dapat mendapatkan summary dokumen PK PM**
  
182.  **ETAX-50002 : Tidak dapat membentuk SPT baru**
  
184.  **ETAX-50003 : Tidak dapat membentuk SPT**  
    Penyebab :  
    Terdapat prosedur-prosedur yang belum dilakukan dalam proses membentuk SPT  
    Solusi :  
    \[1\] Pastikan seluruh isian data di Induk dan Lampiran AB sudah diisi dan disimpan \[2\] Dalam hal membuat SPT Pembetulan, pastikan SPT normal nya sudah dibuat
  
186.  **ETAX-50004 : Tidak dapat membentuk file CSV**  
    Penyebab :  
    Terdapat kolom-kolom dalam aplikasi yang belum diisi dengan lengkap (misalnya: tanggal lapor) atau belum melakukan update profile  
    Solusi :  
    Pastikan kolom-kolom dalam SPT Masa telah diisi dan telah mengisi profile PKP dengan lengkap
  
188.  **ETAX-50005 : Tidak dapat membentuk file PDF**  
    Penyebab :  
    Terdapat kolom-kolom dalam aplikasi yang belum diisi dengan lengkap (misalnya: tanggal lapor) atau belum melakukan update profile  
    Solusi :  
    Pastikan kolom-kolom dalam SPT Masa telah diisi dan telah mengisi profile PKP dengan lengkap
  
190.  **ETAXSERVICE-10001 : Error Database.**
  
192.  **ETAXSERVICE-10002 : Tidak dapat mengambil data.**
  
194.  **ETAXSERVICE-10003 : Tidak dapat mengambil data.**
  
196.  **ETAXSERVICE-10004 : Data digunakan sebagai referensi.**
  
198.  **ETAXSERVICE-10005 : Data tidak ditemukan.**
  
200.  **ETAXSERVICE-20001 : Nomor Faktur tidak ditemukan.**  
    Penyebab :  
    Faktur Pajak belum diupload oleh PKP penjual atau di DB efaktur statusnya gantung  
    Solusi :  
    Pastikan PKP penjual melakukan upload Faktur Pajak Keluaran, call TIP
  
202.  **ETAXSERVICE-20002 : Session tidak ditemukan.**
  
204.  **ETAXSERVICE-20003 : Lawan Transaksi bukan ENofa.**
  
206.  **ETAXSERVICE-20004 : Lawan Transaksi bukan ETax user.**
  
208.  **ETAXSERVICE-20005 : Faktur dibuat sebelum PKP ETax.**
  
210.  **ETAXSERVICE-20006 : Nomor Faktur yang akan diganti tidak ditemukan.**  
    Penyebab :  
    Salah mengisi Nomor Seri Faktur Pajak yang akan diganti  
    Solusi :  
    Pastikan Nomor Seri Faktur Pajak yang akan diganti adalah benar
  
212.  **ETAXSERVICE-20007 : Tanggal Faktur Pengganti tidak boleh lebih kurang dari tanggal Faktur.**  
    Penyebab :  
    Tanggal Faktur Pengganti kurang dari Tanggal Faktur Pajak yang diganti  
    Solusi :  
    Tanggal Faktur Pajak Pengganti minimal sama dengan Tanggal Faktur Pajak yang diganti.
  
214.  **ETAXSERVICE-20008 : Nomor Faktur sudah digunakan.**  
    Penyebab :  
    Atas Nomor Seri Faktur Pajak tersebut telah dilakukan upload.  
    Solusi :  
    Ganti dengan Nomor Seri Faktur Pajak yang lain
  
216.  **ETAXSERVICE-20009 : Flag Pengganti untuk Nomor Faktur salah.**
  
218.  **ETAXSERVICE-20010 : Retur Faktur untuk Faktur sudah terdaftar.**
  
220.  **ETAXSERVICE-20011 : Saldo DPP lebih kecil dari nilai retur.**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    Pastikan nilai retur harus lebih kecil dari Saldo DPP
  
222.  **ETAXSERVICE-20012 : Saldo PPN lebih kecil dari nilai retur.**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    Pastikan nilai PPN retur lebih kecil dari saldo PPN
  
224.  **ETAXSERVICE-20013 : Saldo PPnBM lebih kecil dari nilai retur.**  
    Penyebab :  
    cukup jelas  
    Solusi :  
    Pastikan nilai PPnBM atas retur lebih kecil dari saldo PPnBM
  
226.  **ETAXSERVICE-20014 : Tidak dapat menggenerate approval code.**
  
228.  **ETAXSERVICE-20015 : Retur dibuat sebelum PKP Etax Ready.**
  
230.  **ETAXSERVICE-20015 : NPWP Lawan Transaksi tidak ditemukan.**  
    Penyebab :  
    NPWP lawan transaksi tidak ditemukan dalam database masterfile DJP atau merupakan NPWP NE (Non Efektif) / NPWP telah dicabut.  
    Solusi :  
    Melakukan konfirmasi kepada pembeli atas NPWP yg bersangkutan. Dalam hal tidak akan melakukan pengkreditan maka dapat menggunakan NPWP 00.000.000.0-000.000. Dalam PKP pembeli akan mengkreditkan faktur pajak tersebut maka disarankan untuk mengaktifkan NPWP-nya terlebih dahulu.
  
232.  **ETAXSERVICE-20016 : Retur harus terdaftar di ETax Invoice DJP.**  
    Penyebab :  
    Lawan Transaksi adalah pengguna eFaktur dan belum mengupload Retur PM nya  
    Solusi :  
    Konfirmasikan ke Lawan Transaksi untuk mengupload Retur PM nya, kemudian upload ulang Retur PK nya
  
234.  **ETAXSERVICE-20017 : Client tidak terdaftar.**  
    Penyebab :  
    Menjalankan aplikasi eFaktur yang sudah direset (status nya non aktif).  
    Solusi :  
    1\. Silahkan cek status aktivasi aplikasi eFaktur di efaktur.pajak.go.id halaman Profile User. 2. Dalam hal statusnya belum aktiv : - Silahkan lakukan registrasi ulang aplikasi eFaktur dengan installer yang baru. - Dalalm hal sudah menginput faktur di aplikasi yang sudah non aktif, silahkan lakukan ekspor data faktur. - File csv hasil ekspor dari aplikasi eFaktur yang sudah non aktiv, silahkan diimpor ke aplikasi eFaktur yang baru saja di registrasi. 3. Dalam hal status nya sudah aktiv : - Pastikan untuk menjalankan aplikasi dari folder aplikasi yang diregistrasi terakhir kali. - Dalam hal sudah menginput faktur di aplikasi yang sudah non aktif, silahkan lakukan ekspor data faktur untuk diimpor ke aplikasi eFaktur yang aktif. - Dalam hal aplikasi yang statusnya aktif tidak juga ditemukan silahkan lakukan reset aplikasi Client kembali dari eNofa Online
  
236.  **ETAXSERVICE-20018 : Client desktop aktif terdaftar lebih dari satu.**
  
238.  **ETAXSERVICE-20019 : Client sudah diaktifasi.**  
    Penyebab :  
    Melakukan registrasi aplikasi EFaktur yang sudah pernah diregister/diaktivasi sebelumnya. Terjadi karena : \[1\] Pada saat proses Registrasi EFaktur, PKP menjalankan aplikasi EFaktur langsung dari file installer yang masih berbentuk zip tanpa melakukan ekstrak file terlebih dahulu. \[2\] Menjalankan aplikasi dari folder yang berbeda dengan folder aplikasi yang dilakukan pada saat proses registrasi  
    Solusi :  
    \[1\] Jalankan aplikasi dari folder aplikasi dengan folder db yang sudah teregister \[2\] Dalam hal folder db tidak ada (hilang/terhapus/dll), silahkan lakukan reset aplikasi efaktur dari akun pkp di efaktur.pajak.go.id
  
240.  **ETAXSERVICE-20020 : Nomor seri faktur pajak tidak valid. Nomor Pajak Bukan Jatah**  
    Penyebab :  
    Bagi PKP penerbit: Nomor seri faktur pajak tidak valid (bukan merupakan jatah PKP yang bersangkutan) Bagi PKP pembeli: Nomor seri faktur pajak PKP penjual tidak valid  
    Solusi :  
    Pastikan kepada PKP penjual atas validitas NSFP tersebut.
  
242.  **ETAXSERVICE-20021 : Upload Faktur Corrupt, ulang kembali.**  
    Penyebab :  
    Ada karakter yang bukan standar UTF-8 pada kolom inputan Nama/Alamat Lawan Transaksi, Referensi, Kode/Nama Barang. Biasanya terjadi karena pada saat input data melakukan copy-paste dari excell/word atau pun karena outputan dari sistem lain pada file csv impor faktur. Contoh : karakter â€Ž  
    Solusi :  
    \[1\] Perbaiki faktur. Pastikan menginput langsung dengan menggunakan keyboard standar US dan hindari copy-paste. \[2\] upload ulang faktur
  
244.  **ETAXSERVICE-20022 : Lawan Transaksi bukan PKP.**  
    Penyebab :  
    Faktur Pajak diterbitkan oleh bukan PKP.  
    Solusi :  
    Faktur Pajak hanya dapat diterbitkan oleh Pengusaha Kena Pajak.
  
246.  **ETAXSERVICE-20023 : Faktur tidak valid, dibuat sebelum PKP.**  
    Penyebab :  
    Faktur Pajak diterbitkan pada saat penjual tidak berstatus sebagai PKP.  
    Solusi :  
    Pastikan tanggal transaksi apakah dilakukan setelah dikukuhkan menjadi PKP atau sebelumnya
  
248.  **ETAXSERVICE-20025 : Tanggal Faktur Pajak lebih kecil dari tanggal Nomor Seri Faktur, Tanggal Faktur tidak dapat diterima**  
    Penyebab :  
    Tanggal Faktur Pajak lebih muda dari tanggal Surat Pemberitahuan Nomor Seri Faktur Pajak  
    Solusi :  
    Pastikan kembali nomor Seri Faktur Pajak digunakan setelah tanggal pemberitahuan
  
250.  **ETAXSERVICE-40002 : User tidak ditemukan**  
    Penyebab :  
    Kode Aktivasi/Serial Number yang diinputkan salah.  
    Solusi :  
    Pastikan menginputkan Kode Aktivasi / Serial Number dengan benar. Kode Aktivasi/Serial Number merupakan kombinasi huruf kapital-angka tanpa format. Kode Aktivasi EFaktur bisa dilihat di efaktur.pajak.go.id menu Profil User
  
252.  **: Tidak dapat menghubungi E-TaxInvoice Server null**  
    Penyebab :  
    \[1\] Setelah input passphrase muncul error ""Failed to decrypt..."" akan tetapi oleh WP diklik OK dan melanjutkan proses registrasi \[2\] Setelah input passphrase muncul error certificate bukan milik user kemudian mengubah NPWP sesuai dengan NPWP sertifikat dan melanjutkan proses registrasi tanpa meload ulang sertifikat.  
    Solusi :  
    Pastikan untuk selalu meload ulang sertifikat elektronik apabila muncul error setelah menginputkan passprhase.
  
254.  **: Tidak dapat menghubungi E-TaxInvoice Server 2 counts of InaccessibleWSDLException**  
    Penyebab :  
    pakai invisible proxy  
    Solusi :  
    Silahkan gunakan internet direct/modem untuk menjalankan aplikasi eFaktur
  
256.  **: Failed to decrypt safe contents entry: javax.crypto.BadPaddingException: Given final block not properly padded**  
    Penyebab :  
    Passphrase yang diinputkan salah.  
    Solusi :  
    Pastikan untuk menginputkan passphrase dengan benar. Perhatikan huruf kapital dan huruf kecil karena passphrase case sensitive
  
258.  **: toDerInputStreamRejectType…**  
    Penyebab :  
    File sertifikat elektronik corrupt  
    Solusi :  
    Unduh ulang sertifikat elektronik. Untuk memastikan sertifikat elektronik tersebut berfungsi silahkan install di PC dan impor ke browser untuk mengakses menu Permintaan NSFP dari efaktur.pajak.go.id
  
260.  **: Integrity check failed: java.lang.SecurityException: Failed PKCS12 Integrity Checking.**  
    Penyebab :  
    Sertifikat elektronik yang digunakan salah  
    Solusi :  
    Pastikan untuk menggunakan sertifikat elektronik yang sesuai. Sertifikat Elektronik dapat diunduh di laman http://efaktur.pajak.go.id/
  
262.  **: java virtual version 1.8.0_45, version between 1.7 and 1.7 required**  
    Penyebab :  
    bug di file ETaxInvoiceMain.config untuk installer dan update versi hingga 1.0.0.42  
    Solusi :  
    buka file di notepad, cek di belakang ""… jvm.dll"" pastikan tidak ada spasi. Jika ada spasi silahkan hapus spasi nya dan simpan kembali. Atau unduh di http://svc.efaktur.pajak.go.id/installer/mem_config.zip
  
264.  **: The Exe Cannot Be Modified After It Generated**  
    Penyebab :  
    Aplikasi eFaktur corrupt karena terkena virus/mallware  
    Solusi :  
    Unduh aplikasi eFaktur yang baru kemudian pindahkan folder db dari aplikasi lama ke aplikasi yang baru. Pastikan untuk menjalankan aplikasi eFaktur baru di PC yang berbeda dengan PC yang sudah terkena virus tersebut
  
266.  **: Tidak dapat melakukan registrasi**  
    Penyebab :  
    File sertifikat elektronik corrupt.  
    Solusi :  
    Silahkan hubungi DJP agar dapat dilakukan pengecekan dan perbaikan data.