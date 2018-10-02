---
title: 'SSMS 17 Dark Theme'
date: 2018-01-21T18:47:00.002-08:00
draft: false
tags : [Sql Server]
---

Have you ever wanted SQL Server Management Studio (SSMS) 17 to have a dark theme? Seeing the below image (visual experience color theme options) really got me excited.

![DarkTheme](https://blobeater.files.wordpress.com/2017/09/darktheme.jpg?w=584)

To do this you have to edit system files, don’t get me wrong, it obviously is not a supported means to get the dark theme but I was curious to experience it. Here are the steps for SSMS 17.

*   Navigate to C:\\Program Files (x86)\\Microsoft SQL Server\\140\\Tools\\Binn\\ManagementStudio\

  

*   Look for ssms PKGUNDEF File (Like the below)

![pkgundef](https://blobeater.files.wordpress.com/2017/09/pkgundef.jpg?w=584)

  

*   Search for // Remove Dark theme header and what you need to do is comment the whole block out with //

![REMOVEDARK](https://blobeater.files.wordpress.com/2017/09/removedark.jpg?w=584)

*   SAVE FILE

Restart SQL Server Management Studio and head to Tools > Options to  select the dark theme . This is what you will get. It does look like a work in progress.

![TheDarkside](https://blobeater.files.wordpress.com/2017/09/thedarkside.jpg?w=584)

The connection and results pane seems to still be white but I still like it!

_Note: If the above does not work you may need to open notepad (Run as Admin) then navigate to the PKGUNDEF file._