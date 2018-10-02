---
title: 'sys.processes Status sp_who2 SQL Server'
date: 2017-03-13T01:35:00.000-07:00
draft: false
tags : [Sql Server]
---

Taken from the books online reference for [sys.processes](http://msdn.microsoft.com/en-us/library/ms179881.aspx) and the status column.  
  
**dormant** = SQL Server is resetting the session.  
**running** = The session is running one or more batches. When Multiple Active Result Sets (MARS) is enabled, a session can run multiple batches. For more information, see Using Multiple Active Result Sets (MARS).  
**background** = The session is running a background task, such as deadlock detection.  
**rollback** = The session has a transaction rollback in process.  
**pending** = The session is waiting for a worker thread to become available.  
**runnable** = The task in the session is in the runnable queue of a scheduler while waiting to get a time quantum.  
**spinloop** = The task in the session is waiting for a spinlock to become free.  
**suspended** = The session is waiting for an event, such as I/O, to complete.