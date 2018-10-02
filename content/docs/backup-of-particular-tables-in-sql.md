---
title: 'Backup of particular tables in SQL Server using T-SQL Script'
date: 2017-07-06T19:41:00.000-07:00
draft: false
tags : [backup of particular tables, T-SQL Script, Sql Server]
---

**Questions**  
I want to take a backup of particular tables available in my database in .bak file And all these should be done using T-SQL script  
  
**Answers**  
Backup Types are dependent on SQL Server Recovery Model. Every recovery model lets you back up whole or partial SQL Server database or individual files or filegroups of the database. Table-level backup cannot be created, there is no such option. But there is a workaround for this  
  
  
  
Taking backup of SQL Server table possible in SQL Server. There are various alternative ways to backup a table in sql SQL Server  
  
BCP (BULK COPY PROGRAM)  
Generate Table Script with data  
Make a copy of table using SELECT INTO  
SAVE Table Data Directly in a Flat file  
Export Data using SSIS to any destination  
I am here explaining only the first one rest of you might be know  
  
Method 1 – Backup sql table using BCP (BULK COPY PROGRAM)  
  
To backup a SQL table named "Person.Contact", which resides in SQL Server AdventureWorks, we need to execute following script, which  
  

  
   
DECLARE @table VARCHAR(128),  
@file VARCHAR(255),  
@cmd VARCHAR(512)  
SET @table = 'AdventureWorks.Person.Contact' --  Table Name which you want    to backup  
SET @file = 'C:\\MSSQL\\Backup\\' + @table + '_' + CONVERT(CHAR(8), GETDATE(), 112) --  Replace C:\\MSSQL\\Backup\ to destination dir where you want to place table data backup  
\+ '.dat'  
SET @cmd = 'bcp ' + @table + ' out ' + @file + ' -n -T '  
EXEC master..xp_cmdshell @cmd  
  

  
  
Note -  
  
You must have bulk import / export privileges  
In above Script -n denotes native SQL data types, which is key during restore  
-T denotes that you are connecting to SQL Server using Windows Authentication, in case you want to connect using SQL Server Authentication use -U -P  
This will also tell, you speed to data transfer, in my case this was 212468.08 rows per sec.  
Once this commands completes, this will create a file named "AdventureWorks.Person.Contact_20120222" is a specified destination folder  
Alternatively, you can run the BCP via command prompt and type the following command in command prompt, both operation performs the same activity, but I like the above mentioned method as that’s save type in opening a command prompt and type.  
  
bcp AdventureWorks.Person.Contact out C:\\MSSQL\\Backup\\AdventureWorks.Person.Contact_20120222.dat -n -T  
  
  
source : https://dba.stackexchange.com/questions/102745/how-can-i-take-backup-of-particular-tables-in-sql-server-2008-using-t-sql-script