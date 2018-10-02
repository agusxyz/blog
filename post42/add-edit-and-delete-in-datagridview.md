---
title: 'Add, Edit, and Delete in DataGridView with Paging'
date: 2017-06-05T03:34:00.000-07:00
draft: false
tags : [Explore]
---

Introduction  
The article, or rather code snippet, demonstrates a simple application to insert, update, and delete using a DataGridView. The application uses an asynchronous architecture for most of the calls to the database. This is to show that without a hanging UI, we can allow the user to continue with his tasks. The application has the following outline:  

  
2.  Get all SQL Server instances from the network.
  
4.  Get all databases from the selected instance. If the user provides an empty user name or password, or a wrong user name or password, the same list of SQL Server instances will be returned. The code is available here\[^\].
  
6.  Get all tables from the selected database.
  
8.  Get all records from selected table.
  
10.  Add, edit, delete records from the DataGridView.
  
12.  A paging feature with number of records per page is also provided.
  

  
source [here](https://www.codeproject.com/Articles/17318/Add-Edit-and-Delete-in-DataGridView-with-Paging)