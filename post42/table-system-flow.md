---
title: 'Table System Flow'
date: 2017-05-04T23:12:00.000-07:00
draft: false
tags : [Sql Server]
---

###### Flow Document

  
  
  
\[sql\]  
CREATE TABLE \[System\].\[Flow.Document\]  
(  
\[doctype_id\] \[TINYINT\] NOT NULL  
,\[doctype_header\] \[CHAR\](3) NOT NULL  
,\[doctype_desc\] \[NVARCHAR\](50) NOT NULL  
,\[doctype_table\] \[NVARCHAR\](50) NULL  
,\[hdr_id\] \[INT\] NULL  
,\[hdr_journal\] \[BIT\] NOT NULL  
,CONSTRAINT \[PK\_Flow.Document\] PRIMARY KEY CLUSTERED(\[doctype\_id\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON) ON \[PRIMARY\]  
)  
ON \[PRIMARY\]  
  
GO  
  
ALTER TABLE \[System\].\[Flow.Document\]  
ADD  
DEFAULT((1)) FOR \[hdr_journal\]  
GO  
\[/sql\]  
  

###### Flow Logic

  
  
\[sql\]  
CREATE TABLE \[System\].\[Flow.Logic\]  
(  
\[logic_id\] \[INT\] IDENTITY(1,1)  
NOT NULL  
,\[doctype_id\] \[TINYINT\] NOT NULL  
,\[logic_idx\] \[SMALLINT\] NOT NULL  
,\[prev_seq\] \[TINYINT\] NOT NULL  
,\[next_seq\] \[TINYINT\] NOT NULL  
,\[logic_desc\] \[VARCHAR\](250) NOT NULL  
,\[seq_privilege\] \[VARCHAR\](MAX) NOT NULL  
,\[proc_check\] \[VARCHAR\](100) NOT NULL  
,\[proc_update\] \[VARCHAR\](100) NOT NULL  
,\[proc_fail\] \[VARCHAR\](100) NOT NULL  
,CONSTRAINT \[PK\_Flow.Logic\] PRIMARY KEY CLUSTERED(\[logic\_id\] ASC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON) ON \[PRIMARY\]  
)  
ON \[PRIMARY\] TEXTIMAGE_ON \[PRIMARY\]  
  
GO  
  
ALTER TABLE \[System\].\[Flow.Logic\]  
ADD CONSTRAINT \[DF\_Flow.Logic\_logic\_idx\] DEFAULT((1)) FOR \[logic\_idx\]  
GO  
  
ALTER TABLE \[System\].\[Flow.Logic\]  
ADD CONSTRAINT \[DF\_Flow.Logic\_seq\_privilege\] DEFAULT('All') FOR \[seq\_privilege\]  
GO  
  
ALTER TABLE \[System\].\[Flow.Logic\]  
WITH CHECK  
ADD CONSTRAINT \[FK\_Flow.Logic\_Flow.Document\] FOREIGN KEY(\[doctype_id\]) REFERENCES \[System\].\[Flow.Document\](  
\[doctype_id\]) ON UPDATE CASCADE ON DELETE CASCADE  
GO  
  
ALTER TABLE \[System\].\[Flow.Logic\] CHECK CONSTRAINT \[FK\_Flow.Logic\_Flow.Document\]  
GO  
\[/sql\]  
  

###### Flow History

  
  
\[sql\]  
CREATE TABLE \[System\].\[Flow.History\]  
(  
\[flow_id\] \[INT\] IDENTITY(1,1)  
NOT NULL  
,\[flow_processed\] \[BIT\] NOT NULL  
,\[doctype_id\] \[TINYINT\] NOT NULL  
,\[doc_id\] \[INT\] NOT NULL  
,\[doc_no\] \[VARCHAR\](15) NOT NULL  
,\[gl_no\] \[VARCHAR\](50) NULL  
,\[docflow_prev\] \[TINYINT\] NOT NULL  
,\[docflow_next\] \[TINYINT\] NOT NULL  
,\[update_log\] \[NVARCHAR\](MAX) NOT NULL  
,\[update_success\] \[BIT\] NOT NULL  
,\[update_time\] \[dbo\].\[System.Time\] NOT NULL  
,\[update_user\] \[NVARCHAR\](50) NOT NULL  
,\[update_ws\] \[NVARCHAR\](250) NOT NULL  
,\[flow_result\] \[BIT\] NULL  
,CONSTRAINT \[PK\_Flow.History\] PRIMARY KEY CLUSTERED(\[flow\_id\] DESC)  
WITH(PAD\_INDEX = OFF,STATISTICS\_NORECOMPUTE = OFF,IGNORE\_DUP\_KEY = OFF,ALLOW\_ROW\_LOCKS = ON,ALLOW\_PAGE\_LOCKS = ON) ON \[PRIMARY\]  
)  
ON \[PRIMARY\] TEXTIMAGE_ON \[PRIMARY\]  
  
GO  
  
ALTER TABLE \[System\].\[Flow.History\]  
ADD CONSTRAINT \[DF\_Flow.History\_flow\_processed\] DEFAULT((0)) FOR \[flow\_processed\]  
GO  
  
ALTER TABLE \[System\].\[Flow.History\]  
ADD CONSTRAINT \[DF\_Flow.History\_update\_log\] DEFAULT('') FOR \[update\_log\]  
GO  
  
ALTER TABLE \[System\].\[Flow.History\]  
ADD CONSTRAINT \[DF\_Flow.History\_update\_success\] DEFAULT((0)) FOR \[update\_success\]  
GO  
  
ALTER TABLE \[System\].\[Flow.History\]  
ADD  
DEFAULT((0)) FOR \[flow_result\]  
GO  
  
ALTER TABLE \[System\].\[Flow.History\]  
WITH CHECK  
ADD CONSTRAINT \[FK\_Flow.History\_Flow.Document\] FOREIGN KEY(\[doctype_id\]) REFERENCES \[System\].\[Flow.Document\](  
\[doctype_id\]) ON UPDATE CASCADE ON DELETE CASCADE  
GO  
  
ALTER TABLE \[System\].\[Flow.History\] CHECK CONSTRAINT \[FK\_Flow.History\_Flow.Document\]  
GO  
\[/sql\]