---
title: 'Missing Index Script'
date: 2017-05-01T21:05:00.000-07:00
draft: false
tags : [Sql Server Profiler, Index Script, tsql, T-SQL, Missing Index Script, Sql Server]
---

A proper index can improve the performance and a bad index can hamper the performance.  
Here is the script from my script bank, which I use to identify missing indexes on any database.  
  
  
\[sql\]  
SELECT TOP 10  
dm\_mid.database\_id AS DatabaseID  
,dm\_migs.avg\_user\_impact * (dm\_migs.user\_seeks + dm\_migs.user\_scans) Avg\_Estimated_Impact  
,dm\_migs.last\_user\_seek AS Last\_User_Seek  
,OBJECT\_NAME(dm\_mid.OBJECT\_ID,dm\_mid.database_id) AS \[TableName\]  
,'CREATE INDEX \[IX_'+OBJECT\_NAME(dm\_mid.OBJECT\_ID,dm\_mid.database\_id)+'\_'+REPLACE(REPLACE(REPLACE(ISNULL(dm\_mid.equality\_columns,''),', ','_'),'\[',''),'\]','')+CASE  
WHEN dm\_mid.equality\_columns IS NOT NULL  
AND dm\_mid.inequality\_columns IS NOT NULL  
THEN '_'  
ELSE ''  
END+REPLACE(REPLACE(REPLACE(ISNULL(dm\_mid.inequality\_columns,''),', ','_'),'\[',''),'\]','')+'\]'+' ON '+dm\_mid.statement+' ('+ISNULL(dm\_mid.equality_columns,'')+CASE  
WHEN dm\_mid.equality\_columns IS NOT NULL  
AND dm\_mid.inequality\_columns IS NOT NULL  
THEN ','  
ELSE ''  
END+ISNULL(dm\_mid.inequality\_columns,'')+')'+ISNULL(' INCLUDE ('+dm\_mid.included\_columns+')','') AS Create_Statement  
FROM sys.dm\_db\_missing\_index\_groups dm_mig  
INNER JOIN sys.dm\_db\_missing\_index\_group\_stats dm\_migs ON dm\_migs.group\_handle = dm\_mig.index\_group_handle  
INNER JOIN sys.dm\_db\_missing\_index\_details dm\_mid ON dm\_mig.index\_handle = dm\_mid.index_handle  
WHERE dm\_mid.database\_ID = DB_ID()  
ORDER BY  
Avg\_Estimated\_Impact DESC  
\[/sql\]  
  
Tuning performance with Sql [Server Profiler](http://codinglite.com/sql-server/sql-server-profiler/)