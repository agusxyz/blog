---
title: 'Query to Find Column From All Tables of Database'
date: 2017-05-25T18:19:00.000-07:00
draft: false
tags : [Table, Sql Server]
---

**How many tables in database have column name like ‘doc_date’?**  
  
It was quite an interesting question and I thought if there are scripts which can do this would be great. I quickly wrote down following script which will go return all the tables containing specific column along with their schema name.  
  
\[sql\]  
SELECT  
t.name AS table_name  
,SCHEMA\_NAME(schema\_id) AS schema_name  
,c.name AS column_name  
FROM sys.tables AS t  
INNER JOIN sys.columns c ON t.OBJECT\_ID = c.OBJECT\_ID  
WHERE c.name LIKE '%doc_date%'  
ORDER BY  
schema_name  
,table_name;  
\[/sql\]