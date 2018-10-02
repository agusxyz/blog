---
title: 'The Dark Side of NVARCHAR'
date: 2017-05-04T23:40:00.000-07:00
draft: false
tags : [Sql Server]
---

Introduction
------------

  
In this article, we are going to talk about using the **nvarchar** data type. We will explore how SQL Server stores this data type on the disk and how it is processed in the RAM. We will also examine how the size of nvarchar may affect performance.  

Actual data size: nchar vs nvarchar
-----------------------------------

  
We use **[nvarchar](https://docs.microsoft.com/en-us/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)** when the size of column data entries are probably going to vary considerably. The storage size (in bytes) is twice as much the actual length of data entered + 2 bytes. This allows us to save disk storage in comparison of using **nchar** data type.  Let us consider following example. We are creating two tables. One table contains nvarchar column, another table contains nchar columns. The size of the column is 2000 characters (4000 bytes).  
  
\[sql\]  
CREATE TABLE dbo.testnvarchar  
(  
col1 NVARCHAR(2000) NULL  
);  
GO  
  
INSERT INTO dbo.testnvarchar  
(  
col1  
)  
SELECT  
REPLICATE('&',10)  
GO  
\[/sql\]  
  
[Source Link](http://codingsight.com/sql-server-dark-side-nvarchar/)