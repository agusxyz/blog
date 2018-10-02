---
title: 'Number To Roman Numeric'
date: 2017-04-09T18:37:00.000-07:00
draft: false
tags : [Function Rowman Numeric, T-SQL, Sql Server]
---

Simple Function Convert Type Numeric to Rowman Numeric Sql Server.

  
  
\[sql\]  
CREATE FUNCTION \[System\].\[ToRomanNumeric\](  
@Number INT)  
RETURNS NVARCHAR(100)  
AS  
BEGIN  
IF @Number < 0 BEGIN RETURN 'De romanorum non numero negative' END IF @Number > 200000  
BEGIN  
RETURN 'O Juppiter, magnus numerus'  
END  
DECLARE  
@RomanNumeral AS NVARCHAR(100)  
DECLARE  
@RomanSystem TABLE  
(  
symbol NVARCHAR(20) COLLATE SQL\_Latin1\_General\_Cp437\_BIN  
,DecimalValue INT PRIMARY KEY  
)  
INSERT INTO @RomanSystem  
(  
symbol  
,DecimalValue  
)  
VALUES  
('I', 1),  
('IV', 4),  
('V', 5),  
('IX', 9),  
('X', 10),  
('XL', 40),  
('L', 50),  
('XC', 90),  
('C', 100),  
('CD', 400),  
('D', 500),  
('CM', 900),  
('M', 1000),  
(N'|ↄↄ', 5000),  
(N'cc|ↄↄ', 10000),  
(N'|ↄↄↄ', 50000),  
(N'ccc|ↄↄↄ', 100000),  
(N'ccc|ↄↄↄↄↄↄ', 150000)  
  
WHILE @Number > 0  
SELECT  
@RomanNumeral = COALESCE(@RomanNumeral,'')+symbol  
,@Number = @Number - DecimalValue  
FROM @RomanSystem  
WHERE DecimalValue =  
(  
SELECT  
MAX(DecimalValue)  
FROM @RomanSystem  
WHERE DecimalValue <= @number  
)  
RETURN COALESCE(@RomanNumeral,'nulla')  
END  
\[/sql\]