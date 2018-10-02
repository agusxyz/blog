---
title: 'Desain Chart Of Account'
date: 2017-05-04T23:16:00.000-07:00
draft: false
tags : [Sql Server]
---

###### Table Subcode Group

  
  
  
\[sql\]  
CREATE TABLE \[Accounting\].\[Subcode.Group\]  
(  
\[group_id\] \[INT\] IDENTITY(1,1)  
NOT NULL  
,\[group_name\] \[NVARCHAR(50)\] NOT NULL  
,\[group_manual\] \[BIT\] NOT NULL  
,CONSTRAINT \[PK\_Subcode.Group\] PRIMARY KEY CLUSTERED(\[group\_id\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON)  
)  
  
GO  
  
ALTER TABLE \[Accounting\].\[Subcode.Group\]  
ADD CONSTRAINT \[DF\_Subcode.Group\_group\_manual\] DEFAULT((1)) FOR \[group\_manual\]  
GO  
\[/sql\]  
  

###### Table Subcode Item

  
  
\[sql\]  
CREATE TABLE \[Accounting\].\[Subcode.Item\]  
(  
\[subcode_id\] \[INT\] IDENTITY(1,1)  
NOT NULL  
,\[group_id\] \[INT\] NOT NULL  
,\[gl_subcode\] \[VARCHAR\](50) NULL  
,\[subcode_desc\] \[NVARCHAR(250)\] NULL  
,\[cc_id\] \[INT\] NULL  
,\[loc_id\] \[TINYINT\] NULL  
,\[loc_linkid\] \[INT\] NULL  
,CONSTRAINT \[PK\_Subcode.Item\] PRIMARY KEY CLUSTERED(\[subcode\_id\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON)  
)  
  
GO  
  
ALTER TABLE \[Accounting\].\[Subcode.Item\]  
ADD CONSTRAINT \[DF\_Subcode.Item\_group\_id\] DEFAULT((1)) FOR \[group\_id\]  
GO  
  
ALTER TABLE \[Accounting\].\[Subcode.Item\]  
WITH CHECK  
ADD CONSTRAINT \[FK\_Subcode.Item\_Subcode.Group\] FOREIGN KEY(\[group_id\]) REFERENCES \[Accounting\].\[Subcode.Group\](  
\[group_id\]) ON UPDATE CASCADE ON DELETE CASCADE  
GO  
  
ALTER TABLE \[Accounting\].\[Subcode.Item\] CHECK CONSTRAINT \[FK\_Subcode.Item\_Subcode.Group\]  
GO  
\[/sql\]  
  

###### Table Accounting Group

  
  
\[sql\]  
CREATE TABLE \[Accounting\].\[Group\]  
(  
\[group_id\] \[INT\] IDENTITY(1,1)  
NOT NULL  
,\[group_category\] \[VARCHAR\](50) NOT NULL  
,\[group_idx\] \[TINYINT\] NOT NULL  
,\[group_name\] \[NVARCHAR(50)\] NOT NULL  
,CONSTRAINT \[PK\_Group\] PRIMARY KEY CLUSTERED(\[group\_id\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON)  
)  
  
GO  
\[/sql\]  
  

###### Table Chart Of Account

  
  
\[sql\]  
CREATE TABLE \[Accounting\].\[COA\]  
(  
\[acc_id\] \[INT\] IDENTITY(1,1)  
NOT NULL  
,\[acc_no\] \[CHAR(10)\] NOT NULL  
,\[acc_name\] \[NVARCHAR(50)\] NULL  
,\[acc_journal\] \[BIT\] NULL  
,\[acc_pl\] \[BIT\] NULL  
,\[acc_bs\] \[BIT\] NULL  
,\[acc_exclusive\] \[BIT\] NULL  
,\[acc_currency\] \[CHAR(3)\] NULL  
,\[acc_group\] \[TINYINT\] NOT NULL  
,\[subcode_group\] \[INT\] NULL  
,\[acc_remark\] \[NVARCHAR(250)\] NULL  
,\[acc_level\] \[NVARCHAR(500)\] NULL  
,\[acc_nature\] \[TINYINT\] NOT NULL  
,\[acc_cf\] \[TINYINT\] NOT NULL  
,\[acc_cfnature\] \[TINYINT\] NOT NULL  
,\[acc_enable\] \[BIT\] NOT NULL  
,\[book_version\] \[TINYINT\] NULL  
,\[cc_id\] \[INT\] NOT NULL  
,CONSTRAINT \[PK\_COA\] PRIMARY KEY CLUSTERED(\[acc\_id\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON)  
,CONSTRAINT \[IX\_COA\] UNIQUE NONCLUSTERED(\[acc\_no\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON)  
)  
  
GO  
  
ALTER TABLE \[Accounting\].\[COA\]  
ADD CONSTRAINT \[DF\_COA\_acc\_nature\] DEFAULT((1)) FOR \[acc\_nature\]  
GO  
  
ALTER TABLE \[Accounting\].\[COA\]  
ADD CONSTRAINT \[DF\_COA\_acc\_cf\] DEFAULT((1)) FOR \[acc\_cf\]  
GO  
  
ALTER TABLE \[Accounting\].\[COA\]  
ADD CONSTRAINT \[DF\_COA\_acc\_cfnature\] DEFAULT((1)) FOR \[acc\_cfnature\]  
GO  
  
ALTER TABLE \[Accounting\].\[COA\]  
ADD CONSTRAINT \[DF\_COA\_acc\_enable\] DEFAULT((1)) FOR \[acc\_enable\]  
GO  
  
ALTER TABLE \[Accounting\].\[COA\]  
ADD  
DEFAULT((1)) FOR \[cc_id\]  
GO  
\[/sql\]