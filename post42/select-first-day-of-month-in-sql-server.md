---
title: 'select the first day of a month in SQL Server'
date: 2017-08-28T02:46:00.000-07:00
draft: false
---

select the first day of a month in SQL Server  
SELECT DATEADD(month,DATEDIFF(month,0,GETDATE()),0) AS StartOfMonth ,DATEFROMPARTS(YEAR(GETDATE()),MONTH(GETDATE()),1) as StartOfMonth_1