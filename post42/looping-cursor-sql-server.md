---
title: 'Looping Cursor SQL Server'
date: 2017-04-18T21:38:00.000-07:00
draft: false
tags : [looping, cursor, Sql Server]
---

Looping Cursor SQL Server  
  
\[sql\]  
DECLARE  
@DocID INT  
DECLARE MyCursor CURSOR LOCAL STATIC READ\_ONLY FORWARD\_ONLY  
FOR SELECT  
a.doc_id  
FROM Sales.\[Invoice.Header\] a  
WHERE a.doc_id IS NULL  
  
OPEN Mycursor  
FETCH NEXT FROM MyCursor INTO  
@DocID  
WHILE @@FETCH_STATUS = 0  
BEGIN  
SELECT  
@DocID  
FETCH NEXT FROM MyCursor INTO  
@DocID  
END  
CLOSE MyCursor  
DEALLOCATE MYcursor  
\[/sql\]