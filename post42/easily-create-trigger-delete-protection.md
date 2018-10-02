---
title: 'Easily Create Trigger Delete Protection SQL Server'
date: 2017-03-13T01:59:00.000-07:00
draft: false
tags : [Sql Server]
---

**First learn** : [Tricks For Document Delete Protection On Trigger](http://codinglite.com/uncategorized/tricks-for-document-delete-protection-on-trigger/)  
  
\[sql\]  
CREATE PROCEDURE \[System\].\[Utility.GenerateTriggerDeleteProtect\]  
@TableName NVARCHAR(250)  
AS  
BEGIN  
SET NOCOUNT ON;  
DECLARE  
@SQL NVARCHAR(MAX)  
  
  
IF NOT EXISTS  
(  
SELECT TOP 1  
name  
FROM sys.triggers  
WHERE parent\_id = OBJECT\_ID(@TableName)  
)  
BEGIN  
  
SET @SQL = '  
CREATE TRIGGER '+REPLACE(@TableName,'\]','.DeleteProtect\]')+'  
ON '+@TableName+'  
Instead of DELETE  
AS  
BEGIN  
SET NOCOUNT ON;  
delete from '+@TableName+' where doc\_id in (select doc\_id from deleted where docflow_seq=0)  
END'  
  
EXEC sp_executesql @SQL  
PRINT 'Create delete protect trigger for '+@TableName  
END  
END  
\[/sql\]