---
title: 'How to customize tab colors in SSMS'
date: 2018-01-21T18:38:00.001-08:00
draft: false
tags : [Sql Server]
---

Applies to  
[ApexSQL Complete](https://www.apexsql.com/sql_tools_complete.aspx)

Summary  
This article describes how to set a custom connection color to a query tab in Microsoft [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) (SSMS) using a feature called Tab coloring in ApexSQL Complete.

Description
-----------

Tab coloring can set custom connection colors for individual instances of SQL Server, down to the database level. The user has ability to assign SQL servers, and databases to a specific environment to help quickly identify which connection a tab is currently using.  
  
  

Tab coloring
------------

To associate a query color with a specific server node, go to ApexSQL Complete main menu in SSMS, choose Options from the submenu, and then select the Tab coloring tab:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-73ab.png)

  

Under the Tab coloring tab, select an avaiable SQL Server instance from the right Server drop-down box:

[![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-74a.png)](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-74a.png)

When a server is selected, the Database drop-down box shows all avaiable databases for that specific server. From here, the user can either select a specific database for which an environment will be assigned or simply assign to all databases by choosing the All databases at the very top of the list:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-75ab.png)

The Environment drop-down box has five built-in color presets for each environment. From here, the user can choose between Development, Local, Production, Staging, and Testing environment:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-76ab.png)

Once the Server, Database, and Environment are set, the final step is to click the Add button and the newly created tab coloring rule is added to the list:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-77ab.png)

![Quick tip icon](https://knowledgebase.apexsql.com/wp-content/uploads/2014/05/42x42red-01.png)

Quick tip:

When a new tab coloring connection is added, and the Cancel button or the close (x) button is clicked in the Options dialog, then the newly added connection will be discarded. Make sure to click the Save button after adding the connection, or the OK button in the Options dialog if you want to close the dialog

From now on, all tabs connected to the _AdventureWorks2012_ database, on the DESKTOP-MQH0VFT\\SQLEXPRESS server will be colored green, indicating that the active connection is to the Development environment:

[![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-78a.png)](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-78a.png)

Tab coloring feature helps users who frequently work on many different servers and databases simultaneously by giving them a better overview of which connection they are currently using:

[![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-79a.png)](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-79a.png)

To delete a tab coloring rule, simply select the rule from the list and click the Delete button:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-80ab.png)

A confirmation dialog box will appear that asks if the user wants to proceed with the action. Just click the Yes button, and the rule will be removed from the list:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-81ab.png)

To change server, database, or environment for a connection, select a tab coloring connection rule from the list, from the drop-down boxes make needed changes, and then click the Save button to apply them:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-82ab.png)

To edit environments and colors, click the Edit environments button and a new dialog will open showing the five built-in color presets for each environment:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-83ab.png)

To change the color of an environment, click any color from the Color column and the Color picker dialog will pop-up:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-84a1b.png)

Pick any predefined basic color from the grid for the selected environment, or click the More Colorsbutton for more options:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-85ab.png)

To create a unique environment, click the New button and enter a name under the Name column. Optionally, change the default white color to any other following the previous step:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-86ab.png)

To delete an environment, select one from the list, and then click the Delete button:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-87ab.png)

A confirmation dialog box will appear that asks if the user wants to proceed with the action. Just click the Yes button, and the environment will be removed from the list:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-88bc.png)

If the selected environment is currently assigned to a server or database connection, the following warning message will appear:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-89bc.png)

FAQs:
-----

Q: Where are the Tab coloring settings stored?

A: The Tab coloring settings are stored in the Options.xml file that can be found at the following location: C:\\Users\\<user_name>\\AppData\\Local\\ApexSQL\\ApexSQLComplete

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-90b.png)

Q: Can I edit the Tab coloring settings outside the host application (SQL Server Management Studio and Visual Studio)?

A: Yes, as the setting are stored in the Options.xml file, you can use a simple text editor to preview and edit settings.

Information about environments is stored between the <GlobalEnvironments> tags:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-91b2.png)

Information about Tab coloring connections is stored between the <GlobalTabColorings> tags:

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-92b2.png)

Q: If I click the ApexSQL defaults button from some other tabs what will happen with tab coloring connections that I’ve created?

A: Loading defaults does not effect user defined tab coloring connections and colors.

![](https://knowledgebase.apexsql.com/wp-content/uploads/2017/08/word-image-93bc.png)

Q: There was an update available, I downloaded it, and during the installation process it says that previous versions of ApexSQL Complete will be removed from my computer. What will happen with tab coloring connections that I’ve created?

A: The update process does not effect user defined tab coloring connections.

Q: Can I copy tab coloring settings to another machine e.g. share them with my colleagues?

A: Yes, you can use the Export option in the Options dialog and save all user settings to an .xml file that can be imported on any machine where ApexSQL Complete is already installed. Bear in mind, this option saves all user settings, not only Tab coloring.