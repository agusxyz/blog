---
title: 'Comparison of NULLIF and ISNULL Sql Server'
date: 2017-05-17T20:14:00.000-07:00
draft: false

---

###### **NULLIF**

  
Returns a null value if the two specified expressions are equal.  
**Syntax :**  
`NULLIF ( expression , expression )`  
**Arguments :**  
expression :Is any valid scalar expression.  

###### **ISNULL**

  
Replaces NULL with the specified replacement value.  
**Syntax :**  
`ISNULL ( check_expression , replacement_value )`  
**Arguments :**  
check\_expression : Is the expression to be checked for NULL. check\_expression can be of any type.  
  
replacement\_value : Is the expression to be returned if check\_expression is NULL. replacement\_value must be of a type that is implicitly convertible to the type of check\_expresssion.  

###### Comparison

  
  
**Syntax :**  
DECLARE  
@budgets TABLE  
(  
current_year DECIMAL NULL  
,previous_year DECIMAL NULL  
)  
INSERT INTO @budgets  
VALUES  
(NULL  
,40  
)  
INSERT INTO @budgets  
VALUES  
(50  
,50  
)  
INSERT INTO @budgets  
VALUES  
(50  
,60  
)  
INSERT INTO @budgets  
VALUES  
(50  
,70  
)  
  
SELECT  
NULLIF(current\_year,previous\_year) AS 'Average Budget'  
,isnull(current_year,0)  
FROM @budgets  
**Arguments :** 
  
Exemple 2  
\[sql\]  
SELECT  
NULLIF(doc_totalitem,0)  
,ISNULL(doc\_discvalue * (trans\_total / NULLIF(doc_totalitem,0)),0)  
FROM Sales.\[Invoice.Header\] a  
INNER JOIN Sales.\[Invoice.Detail\] b ON a.doc\_id = b.doc\_id  
\[/sql\]