---
title: 'Sp_who Dynamic Quert SQL Server'
date: 2017-03-09T21:15:00.000-08:00
draft: false
tags : [Sql Server]
---

View spesifik process wp_who Sql Server  
  
   
  
\[sql\]  
SELECT  
spid  
,sp.\[status\]  
,loginame \[Login\]  
,hostname  
,blocked BlkBy  
,sd.name DBName  
,cmd Command  
,dbo.spidprocess(spid) AS process  
,cpu CPUTime  
,physical_io DiskIO  
,last_batch LastBatch  
,program_name AS ProgramName  
FROM master.dbo.sysprocesses sp  
JOIN master.dbo.sysdatabases sd ON sp.dbid = sd.dbid  
ORDER BY  
spid  
\[/sql\]