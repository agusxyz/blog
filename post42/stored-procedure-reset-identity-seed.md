---
title: 'Stored Procedure Reset Identity Seed Table'
date: 2017-05-01T21:35:00.000-07:00
draft: false
tags : [Stored Procedure, Table, Reset Identity Seed, T-SQL, Sql Server]
---

Stored Procedure Reset IdentitySeed Table,  
  
  
\[sql\]  
CREATE PROCEDURE \[dbo\].\[Utility.Reset_IdentitySeed\]  
@SeedTable NVARCHAR(250) = ''  
AS  
BEGIN  
\-\- SET NOCOUNT ON added to prevent extra result sets from  
\-\- interfering with SELECT statements.  
  
SET NOCOUNT ON;  
DECLARE  
@Column VARCHAR(50)  
,@Table VARCHAR(200)  
,@SQL NVARCHAR(500)  
,@ID INT  
  
DECLARE MyID CURSOR LOCAL STATIC READ\_ONLY FORWARD\_ONLY  
FOR SELECT  
a.name  
,c.name+'.\['+b.name+'\]' AS tablename  
FROM sys.identity_columns a  
INNER JOIN sys.tables b ON a.object\_id = isnull(OBJECT\_ID(@SeedTable),b.object_id)  
AND b.object\_id = isnull(OBJECT\_ID(@SeedTable),b.object_id)  
INNER JOIN sys.schemas c ON b.schema\_id = c.schema\_id  
  
OPEN MYID  
FETCH NEXT FROM MYID INTO  
@Column  
,@Table  
WHILE @@FETCH_STATUS = 0  
BEGIN  
SELECT  
@SQL = N'select @IDResult=isnull(max('+@Column+'),0) from '+@Table  
EXECUTE sp_executesql @SQL  
,N'@IDResult int output'  
,@IDResult = @ID OUTPUT;  
PRINT @Table  
DBCC CHECKIDENT(@Table,RESEED,@ID)  
FETCH NEXT FROM MYID INTO  
@Column  
,@Table  
END  
CLOSE MyID  
DEALLOCATE MyID  
END  
\[/sql\]