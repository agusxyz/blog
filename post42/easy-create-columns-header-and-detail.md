---
title: 'Easy create columns header and detail SQL Server'
date: 2017-03-17T20:08:00.000-07:00
draft: false
tags : [Sql Server]
---

Create StoredProcedure System.\[Utility.CreateTable_HeaderDetail\]  
Generate Columns Header Detail and Browser ,Form ,Grid  
  
  
  
\[sql\]  
/\*\*\*\*\*\* Object: StoredProcedure \[System\].\[Utility.CreateTable_HeaderDetail\] Script Date: 3/18/2017 9:57:05 AM ******/  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
  
CREATE PROCEDURE \[System\].\[Utility.CreateTable_HeaderDetail\]  
@schema NVARCHAR(50)  
,@table NVARCHAR(100)  
,@doctypeid INT  
,@createbrowserdetailgrid BIT = 0  
AS  
BEGIN  
  
DECLARE  
@sql NVARCHAR(MAX)  
SET NOCOUNT ON;  
  
  
SET @sql = '  
CREATE TABLE \['+@schema+'\].\['+@table+'.Header\](  
\[doc_id\] \[int\] IDENTITY(1,1) NOT NULL,  
\[doc\_no\] \[dbo\].\[Key.Doc\_No\] NOT NULL,  
\[doc_date\] \[date\] NOT NULL,  
\[docflow_seq\] \[smallint\] NOT NULL,  
\[doctype_id\] \[smallint\] NOT NULL,  
\[cc_id\] \[tinyint\] NOT NULL,  
\[doc_remark\] \[dbo\].\[Remark.Long\] NULL,  
CONSTRAINT \[PK_'+@table+'.Header\] PRIMARY KEY CLUSTERED  
(  
\[doc_id\] ASC  
)WITH (PAD\_INDEX = OFF, STATISTICS\_NORECOMPUTE = OFF, IGNORE\_DUP\_KEY = OFF, ALLOW\_ROW\_LOCKS = ON, ALLOW\_PAGE\_LOCKS = ON)  
);  
ALTER TABLE \['+@schema+'\].\['+@table+'.Header\] ADD CONSTRAINT \[DF_'+@table+'.Header\_doc\_date\] DEFAULT (\[dbo\].\[getlocaldate\]()) FOR \[doc_date\];  
ALTER TABLE \['+@schema+'\].\['+@table+'.Header\] ADD CONSTRAINT \[DF_'+@table+'.Header\_docflow\_seq\] DEFAULT ((0)) FOR \[docflow_seq\];  
ALTER TABLE \['+@schema+'\].\['+@table+'.Header\] ADD CONSTRAINT \[DF_'+@table+'.Header\_doctype\_id\] DEFAULT (('+CONVERT(NVARCHAR(3),@doctypeid)+')) FOR \[doctype_id\];  
ALTER TABLE \['+@schema+'\].\['+@table+'.Header\] ADD CONSTRAINT \[DF_'+@table+'.Header\_cc\_id\] DEFAULT ((1)) FOR \[cc_id\];  
'  
  
EXEC sp_executesql @sql;  
  
SET @sql = '  
CREATE TABLE \['+@schema+'\].\['+@table+'.Detail\](  
\[trans_id\] \[int\] IDENTITY(1,1) NOT NULL,  
\[trans_idx\] \[smallint\] NULL,  
\[doc_id\] \[int\] NOT NULL,  
\[trans_remark\] \[dbo\].\[Remark.Long\] NULL  
CONSTRAINT \[PK_'+@table+'.Detail\] PRIMARY KEY CLUSTERED  
(  
\[trans_id\] ASC  
)WITH (PAD\_INDEX = OFF, STATISTICS\_NORECOMPUTE = OFF, IGNORE\_DUP\_KEY = OFF, ALLOW\_ROW\_LOCKS = ON, ALLOW\_PAGE\_LOCKS = ON)  
);  
ALTER TABLE \['+@schema+'\].\['+@table+'.Detail\] WITH CHECK ADD CONSTRAINT \[FK_'+@table+'.Detail_'+@table+'.Header\] FOREIGN KEY(\[doc_id\])  
REFERENCES \['+@schema+'\].\['+@table+'.Header\] (\[doc_id\]);  
ALTER TABLE \['+@schema+'\].\['+@table+'.Detail\] CHECK CONSTRAINT \[FK_'+@table+'.Detail_'+@table+'.Header\];  
'  
  
EXEC sp_executesql @sql;  
  
/\*\-\- Create Triger Delete Protect --*/  
SET @sql = '  
CREATE TRIGGER \['+@schema+'\].\['+@table+'.Header.DeleteProtect\]  
ON \['+@schema+'\].\['+@table+'.Header\]  
INSTEAD OF DELETE  
AS  
BEGIN  
SET NOCOUNT ON;  
delete from \['+@schema+'\].\['+@table+'.Header\] where doc\_id in (select doc\_id from deleted where docflow_seq=0)  
END'  
  
EXEC sp_executesql @sql;  
  
IF @createbrowserdetailgrid = 1  
BEGIN  
  
  
  
\-\- Create Browser  
  
DECLARE  
@hdrcode NVARCHAR(200)  
,@hdrexpr NVARCHAR(MAX)  
,@dtlcode NVARCHAR(200)  
,@hdrid INT  
  
SET @hdrcode = 'Browser.'+@schema+'.'+@table  
SET @dtlcode = 'Form.'+@schema+'.'+@table  
SET @hdrexpr = 'select a.*, b.flow_state  
from '+@schema+'.\['+@table+'.header\] a  
inner join system.\[flow.state\] b on a.docflow\_seq = b.docflow\_seq and a.doctype\_id = b.doctype\_id  
where a.doc_date between ::ADate:: and ::BDate::';  
  
INSERT INTO system.\[form.headers\]  
(  
hdr_code  
,hdr_expr  
,hdr_basetable  
,hdr_cap  
,hdr_type  
,dtl_type  
,dtl_code  
,hdr_level  
,hdr_remark  
,doc_header  
,hdr_addremove  
,cc_link  
,hdr_report  
,dtl_journal  
,hdr_callback  
)  
SELECT  
@hdrcode  
,@hdrexpr  
,''  
,@table  
,'BROWSER'  
,0  
,@dtlcode  
,'All'  
,''  
,'All'  
,NULL  
,1  
,''  
,1  
,''  
  
SET @hdrid = @@IDENTITY  
  
INSERT INTO system.\[form.browsers\]  
(  
hdr_id  
,col_order  
,col_key  
,\[col_name\]  
,col_cap  
,col_type  
,col_width  
,col_hide  
,col_lock  
,col_readonly  
,col_scale  
)  
SELECT  
@hdrid  
,1  
,1  
,'doc_id'  
,'doc_id'  
,'integer'  
,70  
,1  
,0  
,1  
,0  
UNION  
SELECT  
@hdrid  
,2  
,0  
,'doc_no'  
,'Document'  
,'text'  
,80  
,0  
,0  
,1  
,0  
UNION  
SELECT  
@hdrid  
,3  
,0  
,'doc_date'  
,'Date'  
,'date'  
,80  
,0  
,0  
,1  
,0  
UNION  
SELECT  
@hdrid  
,4  
,0  
,'flow_state'  
,'State'  
,'text'  
,100  
,0  
,0  
,1  
,0  
UNION  
SELECT  
@hdrid  
,5  
,0  
,'doc_remark'  
,'Remark'  
,'text'  
,200  
,0  
,0  
,1  
,0  
  
INSERT INTO system.\[form.variables\]  
(  
hdr_id  
,var_order  
,var_name  
,var_remark  
,var_controlexpr  
,var_aggr  
,var_uitype  
,var_nullable  
,var_datatype  
,var_labelwidth  
,var_uiwidth  
,var_offset  
,var_scale  
,var_hide  
,var_readonly  
)  
SELECT  
@hdrid  
,1  
,'ADate'  
,'From'  
,''  
,'FDOM(TODAY())'  
,'date'  
,0  
,'date'  
,100  
,100  
,0  
,0  
,0  
,0  
UNION  
SELECT  
@hdrid  
,2  
,'BDate'  
,'From'  
,''  
,'EDOM(TODAY())'  
,'date'  
,0  
,'date'  
,100  
,100  
,0  
,0  
,0  
,0  
  
  
--Create Detail  
  
SET @hdrcode = 'Form.'+@schema+'.'+@table  
SET @dtlcode = ''  
SET @hdrexpr = 'select * from '+@schema+'.\['+@table+'.header\]';  
  
DECLARE  
@doctypeheader NVARCHAR(10)  
SELECT  
@doctypeheader = doctype_header  
FROM system.\[flow.document\]  
WHERE doctype_id = @doctypeid  
  
INSERT INTO system.\[form.headers\]  
(  
hdr_code  
,hdr_expr  
,hdr_basetable  
,hdr_cap  
,hdr_type  
,dtl_type  
,dtl_code  
,hdr_level  
,hdr_remark  
,doc_header  
,hdr_addremove  
,cc_link  
,hdr_report  
,dtl_journal  
,hdr_callback  
)  
SELECT  
@hdrcode  
,@hdrexpr  
,@schema+'.\['+@table+'.Header\]'  
,@table  
,'DETAIL'  
,0  
,''  
,'All'  
,''  
,@doctypeheader  
,NULL  
,1  
,NULL  
,0  
,''  
  
SET @hdrid = @@IDENTITY  
  
INSERT INTO system.\[form.details\]  
(  
hdr_id  
,tab_name  
,col_caption  
,col_name  
,col_order  
,col_controlvalue  
,col_datatype  
,col_uitype  
,col_length  
,col_prec  
,col_scale  
,col_PK  
,col_controlexpr  
,col_readonly  
,col_hide  
,\[object_id\]  
,col_offset  
,col_labelwidth  
,col_update  
,col_defaultvalue  
)  
SELECT  
@hdrid  
,'General'  
,'doc_id'  
,'doc_id'  
,1  
,''  
,'number'  
,'integer'  
,70  
,0  
,0  
,1  
,''  
,0  
,1  
,NULL  
,0  
,100  
,0  
,''  
UNION  
SELECT  
@hdrid  
,'General'  
,'Document'  
,'doc_no'  
,2  
,''  
,'string'  
,'text'  
,150  
,0  
,0  
,4  
,''  
,1  
,0  
,NULL  
,0  
,100  
,0  
,''  
UNION  
SELECT  
@hdrid  
,'General'  
,'Date'  
,'doc_date'  
,3  
,''  
,'date'  
,'date'  
,150  
,0  
,0  
,0  
,''  
,0  
,0  
,NULL  
,-1  
,100  
,1  
,''  
UNION  
SELECT  
@hdrid  
,'General'  
,'Remark'  
,'doc_remark'  
,5  
,''  
,'string'  
,'textarea'  
,400  
,0  
,0  
,0  
,''  
,0  
,0  
,NULL  
,0  
,100  
,1  
,''  
UNION  
SELECT  
@hdrid  
,'General'  
,'doctype_id'  
,'doctype_id'  
,6  
,''  
,'number'  
,'integer'  
,70  
,0  
,0  
,0  
,''  
,0  
,1  
,NULL  
,0  
,100  
,0  
,''  
UNION  
SELECT  
@hdrid  
,'General'  
,'cc_id'  
,'cc_id'  
,7  
,''  
,'number'  
,'integer'  
,70  
,0  
,0  
,0  
,''  
,0  
,1  
,NULL  
,0  
,100  
,0  
,'_CCID'  
UNION  
SELECT  
@hdrid  
,'General'  
,'docflow_seq'  
,'docflow_seq'  
,8  
,''  
,'number'  
,'integer'  
,70  
,0  
,0  
,0  
,''  
,0  
,1  
,NULL  
,0  
,100  
,0  
,''  
UNION  
SELECT  
@hdrid  
,'General'  
,''  
,''  
,4  
,''  
,''  
,'grid'  
,100  
,0  
,0  
,0  
,'Grid.'+@schema+'.'+@table  
,0  
,0  
,NULL  
,0  
,100  
,0  
,''  
  
/\*\-\- Update Default Form System Document --*/  
UPDATE \[System\].\[Flow.Document\]  
SET hdr_id = @hdrid  
WHERE  
doctype_id = @doctypeid  
  
--create grid  
  
SET @hdrcode = 'Grid.'+@schema+'.'+@table  
SET @dtlcode = ''  
SET @hdrexpr = 'select * from '+@schema+'.\['+@table+'.detail\]';  
  
INSERT INTO system.\[form.headers\]  
(  
hdr_code  
,hdr_expr  
,hdr_basetable  
,hdr_cap  
,hdr_type  
,dtl_type  
,dtl_code  
,hdr_level  
,hdr_remark  
,doc_header  
,hdr_addremove  
,cc_link  
,hdr_report  
,dtl_journal  
,hdr_callback  
)  
SELECT  
@hdrcode  
,@hdrexpr  
,@schema+'.\['+@table+'.Detail\]'  
,@table  
,'GRID'  
,0  
,''  
,'All'  
,''  
,NULL  
,1  
,1  
,NULL  
,1  
,''  
  
SET @hdrid = @@IDENTITY  
  
INSERT INTO system.\[form.grids\]  
(  
hdr_id  
,col_key  
,col_order  
,col_cap  
,col_datatype  
,col_uiwidth  
,col_controlvalue  
,\[col_name\]  
,col_readonly  
,col_hide  
,col_uitype  
,col_controlexpr  
,\[object_id\]  
,col_scale  
,col_update  
,col_defaultvalue  
)  
SELECT  
@hdrid  
,1  
,1  
,'trans_id'  
,'number'  
,70  
,''  
,'trans_id'  
,0  
,1  
,'integer'  
,''  
,NULL  
,0  
,0  
,''  
UNION  
SELECT  
@hdrid  
,3  
,3  
,'No'  
,'number'  
,50  
,''  
,'trans_idx'  
,1  
,0  
,'integer'  
,''  
,NULL  
,0  
,1  
,''  
UNION  
SELECT  
@hdrid  
,0  
,4  
,'Remark'  
,'string'  
,200  
,''  
,'trans_remark'  
,0  
,0  
,'text'  
,''  
,NULL  
,0  
,1  
,''  
UNION  
SELECT  
@hdrid  
,2  
,2  
,'doc_id'  
,'number'  
,70  
,''  
,'doc_id'  
,0  
,1  
,'integer'  
,''  
,NULL  
,0  
,1  
,''  
END  
END  
\[/sql\]