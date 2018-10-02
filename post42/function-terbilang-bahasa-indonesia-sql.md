---
title: 'Function Terbilang Bahasa Indonesia SQL Server'
date: 2017-03-17T02:35:00.000-07:00
draft: false
tags : [Sql Server]
---

Function Terbilang SQL Server : Konversi numeric terbilang bahasa Indonesia  
  
\[sql\]  
CREATE FUNCTION \[dbo\].\[Terbilang\]  
(  
@number NUMERIC(19,6)  
)  
RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
DECLARE  
@position INT  
,@length INT  
,@words NVARCHAR(MAX)  
,@ends NVARCHAR(MAX)  
,@numStr NVARCHAR(MAX)  
,@foreStr NVARCHAR(MAX)  
,@backStr NVARCHAR(MAX)  
,@char NVARCHAR(1)  
,@charafter NVARCHAR(1)  
,@charprev NVARCHAR(1)  
,@charprev2 NVARCHAR(1)  
  
SELECT  
@numStr = STR(@number,19,2)  
SELECT  
@numStr = LTRIM(RTRIM(@numStr))  
SELECT  
@foreStr = SUBSTRING(@numStr,0,  
(  
SELECT  
CHARINDEX('.',@numStr,1)  
))  
SELECT  
@backStr = SUBSTRING(@numStr,  
(  
SELECT  
CHARINDEX('.',@numStr,1)+1  
),LEN(@numStr))  
SELECT  
@length = LEN(@foreStr)  
SELECT  
@position = @length  
SELECT  
@words = ''  
  
--Memproses "angka di depan koma"  
  
WHILE(@position > 0)  
BEGIN  
  
SELECT  
@char = SUBSTRING(@numStr,@length+1-@position,1)  
SELECT  
@charafter = SUBSTRING(@numStr,@length+2-@position,1)  
SELECT  
@charprev = SUBSTRING(@numStr,@length-@position,1)  
SELECT  
@charprev2 = SUBSTRING(@numStr,@length-@position-1,1)  
  
IF((@char = '1')  
AND (  
(  
SELECT  
(@position - 1) / 3.0  
) = 1)  
AND (@charafter != '')  
AND (  
(  
SELECT  
CAST(@charprev AS INT)  
) = 0))  
BEGIN  
SELECT  
@words = @words+'se'  
END  
ELSE  
BEGIN  
IF((@char = '1')  
AND (  
(  
SELECT  
@position % 3  
) = 1))  
BEGIN  
SELECT  
@words = @words+'satu '  
END  
ELSE  
BEGIN  
IF((@char = '1')  
AND (  
(  
SELECT  
CAST(@charafter AS INT)  
) \> 1)  
AND (  
(  
SELECT  
@position % 3  
) = 2))  
BEGIN  
IF(@charafter = '1')  
BEGIN  
SELECT  
@words = @words+'se'  
END  
ELSE  
BEGIN  
IF(@charafter = '2')  
BEGIN  
SELECT  
@words = @words+'dua '  
END  
ELSE  
BEGIN  
IF(@charafter = '3')  
BEGIN  
SELECT  
@words = @words+'tiga '  
END  
ELSE  
BEGIN  
IF(@charafter = '4')  
BEGIN  
SELECT  
@words = @words+'empat '  
END  
ELSE  
BEGIN  
IF(@charafter = '5')  
BEGIN  
SELECT  
@words = @words+'lima '  
END  
ELSE  
BEGIN  
IF(@charafter = '6')  
BEGIN  
SELECT  
@words = @words+'enam '  
END  
ELSE  
BEGIN  
IF(@charafter = '7')  
BEGIN  
SELECT  
@words = @words+'tujuh '  
END  
ELSE  
BEGIN  
IF(@charafter = '8')  
BEGIN  
SELECT  
@words = @words+'delapan '  
END  
ELSE  
BEGIN  
IF(@charafter = '9')  
BEGIN  
SELECT  
@words = @words+'sembilan '  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
ELSE  
BEGIN  
IF(@char = '1')  
BEGIN  
SELECT  
@words = @words+'se'  
END  
ELSE  
BEGIN  
IF(@char = '2')  
BEGIN  
SELECT  
@words = @words+'dua '  
END  
ELSE  
BEGIN  
IF(@char = '3')  
BEGIN  
SELECT  
@words = @words+'tiga '  
END  
ELSE  
BEGIN  
IF(@char = '4')  
BEGIN  
SELECT  
@words = @words+'empat '  
END  
ELSE  
BEGIN  
IF(@char = '5')  
BEGIN  
SELECT  
@words = @words+'lima '  
END  
ELSE  
BEGIN  
IF(@char = '6')  
BEGIN  
SELECT  
@words = @words+'enam '  
END  
ELSE  
BEGIN  
IF(@char = '7')  
BEGIN  
SELECT  
@words = @words+'tujuh '  
END  
ELSE  
BEGIN  
IF(@char = '8')  
BEGIN  
SELECT  
@words = @words+'delapan '  
END  
ELSE  
BEGIN  
IF(@char = '9')  
BEGIN  
SELECT  
@words = @words+'sembilan '  
END  
ELSE  
BEGIN  
IF((@char = '0')  
AND (  
(  
SELECT  
CAST(@charprev AS INT)  
) \> 1)  
AND (  
(  
SELECT  
@position % 3  
) = 1))  
BEGIN  
SELECT  
@words = @words  
END  
ELSE  
BEGIN  
IF((@char = '0')  
AND (  
(  
SELECT  
@charprev  
) = '0')  
AND (  
(  
SELECT  
CAST(@charprev2 AS INT)  
) \> 0)  
AND (  
(  
SELECT  
@position % 3  
) = 1))  
BEGIN  
SELECT  
@words = @words  
END  
ELSE  
BEGIN  
IF(@char = '0')  
BEGIN  
SELECT  
@position = @position - 1 CONTINUE  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
END  
  
IF(  
(  
SELECT  
@position % 3  
) = 0)  
BEGIN  
SELECT  
@words = @words+'ratus '  
END  
ELSE  
BEGIN  
IF((  
(  
SELECT  
@position % 3  
) = 2)  
AND (  
(  
SELECT  
CAST(@char AS INT)  
) \> 1))  
BEGIN  
SELECT  
@words = @words+'puluh '  
END  
ELSE  
BEGIN  
IF((  
(  
SELECT  
@position % 3  
) = 2)  
AND (  
(  
SELECT  
CAST(@char AS INT)  
) = 1)  
AND (  
(  
SELECT  
CAST(@charafter AS INT)  
) \> 0))  
BEGIN  
SELECT  
@words = @words+'belas '  
SELECT  
@position = @position - 1  
END  
ELSE  
BEGIN  
IF((  
(  
SELECT  
@position % 3  
) = 2)  
AND (  
(  
SELECT  
CAST(@char AS INT)  
) = 1)  
AND (  
(  
SELECT  
CAST(@charafter AS INT)  
) = 0))  
BEGIN  
SELECT  
@words = @words+'puluh '  
SELECT  
@position = @position - 1  
END  
END  
END  
END  
  
IF(  
(  
SELECT  
(@position - 1) / 3.0  
) = 1)  
BEGIN  
SELECT  
@words = @words+'ribu '  
END  
ELSE  
BEGIN  
IF(  
(  
SELECT  
(@position - 1) / 3.0  
) = 2)  
BEGIN  
SELECT  
@words = @words+'juta '  
END  
ELSE  
BEGIN  
IF(  
(  
SELECT  
(@position - 1) / 3.0  
) = 3)  
BEGIN  
SELECT  
@words = @words+'milyar '  
END  
ELSE  
BEGIN  
IF(  
(  
SELECT  
(@position - 1) / 3.0  
) = 4)  
BEGIN  
SELECT  
@words = @words+'triliun '  
END  
END  
END  
END  
  
SELECT  
@position = @position - 1  
END  
  
--Memproses "koma" dan "angka di belakang koma"  
  
IF(  
(  
SELECT  
CAST(@backStr AS INT)  
) \> 0)  
BEGIN  
--Menambahkan "koma" pada terbilang  
  
SELECT  
@words = @words+'koma '  
  
--Menambahkan "Angka di belakang koma" pada terbilang  
  
SELECT  
@length = LEN(@backStr)  
SELECT  
@position = @length  
  
WHILE(@position > 0)  
BEGIN  
  
SELECT  
@char = SUBSTRING(@backStr,@length+1-@position,1)  
SELECT  
@words = @words+(CASE @char  
WHEN '0'  
THEN 'nol '  
WHEN '1'  
THEN 'satu '  
WHEN '2'  
THEN 'dua '  
WHEN '3'  
THEN 'tiga '  
WHEN '4'  
THEN 'empat '  
WHEN '5'  
THEN 'lima '  
WHEN '6'  
THEN 'enam '  
WHEN '7'  
THEN 'tujuh '  
WHEN '8'  
THEN 'delapan '  
WHEN '9'  
THEN 'sembilan '  
ELSE ''  
END)  
SELECT  
@position = @position - 1  
END  
END  
  
SELECT  
@words = LTRIM(RTRIM(@words))  
  
\-\- Huruf pertama huruf besar  
  
IF LEN(@words) > 0  
BEGIN  
SET @words = UPPER(LEFT(@words,1)) + RIGHT(@words,LEN(@words) - 1)  
END  
  
/\* FINAL RETURN */  
RETURN  
(  
SELECT  
@words  
)  
END  
\[/sql\]