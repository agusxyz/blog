---
title: 'Search GETDATE() Function in Sql Server'
date: 2017-05-21T02:52:00.000-07:00
draft: false
tags : [tsql, Search, GETDATE, Sql Server]
---

Search GETDATE in All stored procedure and function  
  

SELECT DISTINCT   
   o.name AS Object\_Name, o.type\_desc, LEFT(m.definition, 500) AS def  
FROM sys.sql_modules m  
 INNER JOIN sys.objects o ON m.object\_id = o.object\_id  
 WHERE m.definition LIKE '%GETDATE%' ESCAPE '\\'  

  
  
Search GETDATE in Default value on tables  
  
\[sql\]  
SELECT  
table_schema  
,table_name  
,COLUMN_NAME  
,column_default  
FROM INFORMATION_SCHEMA.COLUMNS  
WHERE column_default LIKE '%GETDATE%' ESCAPE '\\'  
ORDER BY  
table_schema  
,table_name  
\[/sql\]  
  
Search GETDATE in Computed column formula on tables  
  
\[sql\]  
SELECT  
a.definition  
,a.name  
,b.name  
FROM sys.computed_columns a  
INNER JOIN sys.tables b ON a.object\_id = b.object\_id  
WHERE definition LIKE '%GETDATE%' ESCAPE '\\'  
\[/sql\]