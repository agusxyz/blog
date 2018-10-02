---
title: 'Tricks For Document Delete Protection On Trigger SQL Server'
date: 2017-03-13T01:43:00.000-07:00
draft: false
tags : [Sql Server]
---

Example Trigger  
  
\[sql\]SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
  
CREATE TRIGGER Accounting.\[General.Header.DeleteProtect\] ON Accounting.\[General.Header\]  
INSTEAD OF DELETE  
AS  
BEGIN  
SET NOCOUNT ON;  
DELETE FROM Accounting.\[General.Header\]  
WHERE  
doc_id IN  
(  
SELECT  
doc_id  
FROM deleted  
WHERE docflow_seq = 0  
)  
END  
\[/sql\]