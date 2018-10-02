---
title: 'Split String On Table value fungtion SQL Server'
date: 2017-04-02T21:22:00.000-07:00
draft: false
tags : [Split String, T-SQL, Sql Server]
---

Split String from string to row entry.  
  
  
\[sql\]  
CREATE FUNCTION \[dbo\].\[SplitString\](  
               @String    NVARCHAR(8000)  
              ,@Delimiter CHAR(1))  
RETURNS TABLE  
AS  
     RETURN(  
     WITH SplitData(  
          stpos  
         ,endpos)  
          AS (  
          SELECT  
                 0 AS stpos  
                ,CHARINDEX(@Delimiter,@String) AS endpos  
          UNION ALL  
          SELECT  
                 endpos + 1  
                ,CHARINDEX(@Delimiter,@String,endpos+1)  
          FROM SplitData  
          WHERE endpos > 0)  
          SELECT  
                 ROW_NUMBER() OVER(ORDER BY  
                                            (  
                                             SELECT  
                                                    1  
                                            )) AS RowID  
                ,RTRIM(LTRIM(SUBSTRING(@String,stpos,COALESCE(NULLIF(endpos,0),LEN(@String) + 1)-stpos))) AS RowData  
          FROM SplitData)  
\[/sql\]