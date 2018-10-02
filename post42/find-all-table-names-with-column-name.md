---
title: 'Find all table names with column name In SQL Server'
date: 2017-09-06T22:20:00.001-07:00
draft: false
---

How can I get all the table names where the given column name exists? I want the names with "Like" in sql server.  
  
  
SELECT c.name AS ColName ,t.name AS TableName FROM sys.columns c JOIN sys.tables t ON c.object\_id = t.object\_id WHERE c.name LIKE '%MyCol%';