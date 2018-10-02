---
title: 'Row To Column SQL Server'
date: 2017-03-23T18:56:00.000-07:00
draft: false
tags : [Row To Column, T-SQL, Sql Server]
---

\[sql\]  
SELECT  
STUFF(  
(  
SELECT TOP 10  
' \+ '+item_name  
FROM Inventory.\[ITem.Master\]  
FOR XML PATH('')  
),1,3,'')\[/sql\]