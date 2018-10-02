---
title: 'Format Number With Commas in Sql Server'
date: 2017-06-14T23:55:00.000-07:00
draft: false
tags : [Number To String, Format Number, Sql Server]
---

In SQL Server 2012 and higher, this will format a number with commas:  
`SELECT FORMAT([Number], 'N0')`  
You can also change `0` to the number of decimal places you want.  
  
  
  
**Demo 1**  
Demonstrates adding commas:  
SELECT FORMAT(5000000, '#,##0')  
Result  
`5,000,000`  
  
**Demo 2**  
Demonstrates commas and decimal points. Observe that it rounds the last digit if necessary.  
SELECT FORMAT(5000000.759145678, '#,##0.00')  
Result  
`5,000,000.76`  
  
**Compatibility**  
`SQL Server 2012+`