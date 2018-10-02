---
title: 'EXCEPT Operator Sql Server'
date: 2017-05-21T01:59:00.000-07:00
draft: false
tags : [tsql, EXCEPT, Sql Server]
---

  
  
This SQL Server tutorial explains how to use the **EXCEPT operator** in SQL Server (Transact-SQL) with syntax and examples.  
  

  

  

###### Description

  
The SQL Server (Transact-SQL) EXCEPT operator is used to return all rows in the first SELECT statement that are not returned by the second SELECT statement. Each SELECT statement will define a dataset. The EXCEPT operator will retrieve all records from the first dataset and then remove from the results all records from the second dataset.  

  
  
**Explanation:** The EXCEPT query will return the records in the blue shaded area. These are the records that exist in Dataset1 and not in Dataset2.  
  
Each SELECT statement within the EXCEPT query must have the same number of fields in the result sets with similar data types.  
  

  

  

###### Syntax

  
The syntax for the EXCEPT operator in SQL Server (Transact-SQL) is:  
  

  

  
  
  
\[sql\]  
SELECT expression1, expression2, ... expression_n  
FROM tables  
\[WHERE conditions\]  
EXCEPT  
SELECT expression1, expression2, ... expression_n  
FROM tables  
\[WHERE conditions\];  
\[/sql\]  
  

  

###### Parameters or Arguments

  

  

expressions

  

The columns or calculations that you wish to compare between the two SELECT statements. They do not have to be the same fields in each of the SELECT statements, but the corresponding columns must be similar data types.

  

tables

  

The tables that you wish to retrieve records from. There must be at least one table listed in the FROM clause.

  

WHERE conditions

  

Optional. The conditions that must be met for the records to be selected.

  

  

  

  

###### Note

  

  
*   There must be same number of expressions in both SELECT statements.
  
*   The corresponding columns in each of the SELECT statements must have similar data types.
  
*   The EXCEPT operator returns all records from the first SELECT statement that are not in the second SELECT statement.
  
*   The EXCEPT operator in SQL Server is equivalent to the MINUS operator in Oracle.
  

  

  

  

###### Example - With Single Expression

  
Let's look at an example of the EXCEPT operator in SQL Server (Transact-SQL) that returns one field with the same data type.  
  
For example:  
  

  
  
\[sql\]SELECT contact\_id, last\_name, first_name  
FROM contacts  
WHERE last_name = 'Anderson'  
EXCEPT  
SELECT employee\_id, last\_name, first_name  
FROM employees;\[/sql\]  
  
In this EXCEPT example, the query will return the records in the contacts table with a contact\_id, last\_name, and first\_name value that does not match the employee\_id, last\_name, and first\_name value in the employees table.