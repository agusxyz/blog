---
title: 'How to execute multiple long running SQL Statements Asynchronously in
small chunks'
date: 2017-04-04T19:00:00.000-07:00
draft: false
tags : [T-SQL, SQL Statements Asynchronous, Sql Server]
---

Introduction
------------

  
Completing task  Asynchronously in case of long running query processing is very helpful in some scenario. It ensures maximum use of hardware resources as well. In case of non set based modern high level programming language such as C# or Java has versatile facilities, libraries and patterns  for asynchronous programming. But what about SET based language such as SQL? There is no straight forward way to execute SQL statements  in parallel mode. In SQL Server there some way to do such stuff like using SQL Server Service Broker or through CLR stored procedure. Service Broker actually is a process of sending and receiving messages which can be sent to same or any remote database of another SQL Server instance. Whereas CLR needs different set of programming expertise, it also has some deployment issue. Today I am going to show you the same implementation using SQL Server Agent Job. In this article you also came to know, how huge number of long running SQL statements will be executed in some smaller configurable chunks.  
  
[Read More ](https://www.codeproject.com/Articles/541834/How-to-execute-multiple-long-running-SQL-Statement)