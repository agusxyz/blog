---
title: 'Format Number with commas in T-SQL Sql Server'
date: 2017-03-19T21:05:00.000-07:00
draft: false
tags : [Sql Server]
---

**Demo 1**  
  
Demonstrates adding commas:  
  
\[sql\] PRINT FORMATMESSAGE('The number is: %s', format(5000000, '#,##0'))  
\[/sql\]  
  
\-\- Output  
The number is: 5,000,000  
  
**Demo 2**  
  
Demonstrates commas and decimal points. Observe that it rounds the last digit if necessary.  
  
\[sql\] PRINT FORMATMESSAGE('The number is: %s', format(5000000.759145678, '#,##0.00'))  
\[/sql\]  
  
\-\- Output  
The number is: 5,000,000.76  
  
**Compatibility**  
  
SQL Server 2012+.