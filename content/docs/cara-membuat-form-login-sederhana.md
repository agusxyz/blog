---
title: 'CARA MEMBUAT FORM LOGIN SEDERHANA DENGAN KONEKSI DATABASE PADA C#'
date: 2017-06-07T18:26:00.000-07:00
draft: false
---

Pertama yaitu buat kelas Koneksi.cs dengan klik kanan pada project Anda => Pilih Add Class => Beri nama dengan Koneksi dan ketikkan kode berikut nama databasenya disesuaikan :  
\[csharp\]  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Data.SqlClient;  
  
namespace KeretaApi  
{  
class Koneksi  
{  
static string conn;  
  
public static SqlConnection Conn  
{  
get  
{  
return new SqlConnection(conn);  
}  
}  
  
static Koneksi()  
{  
string connStr = "server=localhost;" +  
"database=KeretaApi;" +  
"Integrated Security=TRUE";  
conn = connStr;  
}  
}  
}  
\[/csharp\]