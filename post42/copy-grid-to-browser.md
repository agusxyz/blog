---
title: 'Copy Grid To Browser'
date: 2017-04-21T02:57:00.000-07:00
draft: false
tags : [Copy Grid To Browser, browser csv, graylite, Sql Server]
---

Copy Grid to Browser,  
Tool Save Detail Grid To CSV For Graylite  
  
  
\[sql\]  
DECLARE  
@HdrCode NVARCHAR(50)  
,@HdrCopy NVARCHAR(50)  
,@NewHdr INT  
,@CompanyServer NVARCHAR(250)  
,@LinkCsv NVARCHAR(MAX)  
  
/\* Insert Nama Grid */  
SET @HdrCode = 'Grid.Production.Work.Order.Detail';  
  
SET @HdrCopy = 'Browser'+REPLACE(LTRIM(RTRIM(@HdrCode)),'Grid','')+'.CSV';  
IF EXISTS  
(  
SELECT  
hdr_id  
FROM System.\[Form.Headers\]  
WHERE hdr_code = @HdrCopy  
)  
BEGIN  
  
SELECT  
@CompanyServer = config_value  
FROM \[System\].\[Configuration\]  
WHERE config_id = 4  
  
  
  
SELECT  
'Module Is Ready ' AS Say_Msg  
,@HdrCopy AS module_name  
,'SELECT ''OPENLINK(''''bp.graylite.com/web/application/index.php/browser/csv?code='+@HdrCopy+'&DocID=''+LTRIM(RTRIM(::DocID::))+''&&page=1&start=0&limit=65536&subkey=-1'''')''' AS LinkCSV  
END  
ELSE  
BEGIN  
INSERT INTO System.\[Form.Headers\]  
(  
hdr_code  
,hdr_expr  
,hdr_basetable  
,hdr_cap  
,hdr_type  
,dtl_type  
,hdr_level  
,hdr_addremove  
,dtl_journal  
,hdr_callback  
)  
SELECT  
@HdrCopy AS hdr_code  
,hdr_expr  
,'' AS hdr_basetable  
,hdr_cap  
,'BROWSER' AS hdr_type  
,0 AS dtl_type  
,'All' AS hdr_level  
,0 AS hdr_addremove  
,0 AS dtl_journal  
,hdr_callback  
FROM system.\[form.Headers\]  
WHERE hdr_code = @HdrCode;  
SET @NewHdr = @@IDENTITY;  
INSERT INTO \[System\].\[Form.Browsers\]  
(  
hdr_id  
,col_order  
,col_key  
,col_name  
,col_cap  
,col_type  
,col_width  
,col_hide  
,col_lock  
,col_readonly  
,col_scale  
)  
SELECT  
@NewHdr AS hdr_id  
,col_order  
,col_key  
,col_name  
,col_cap  
,col\_uitype AS col\_type  
,col_uiwidth  
,col_hide  
,0 AS col_lock  
,1 AS col_readonly  
,col_scale  
FROM system.\[Form.Grids\] a  
INNER JOIN system.\[form.Headers\] b ON a.hdr\_id = b.hdr\_id  
WHERE hdr_code = @HdrCode  
  
SELECT  
'Module Generate ' AS Say_Msg  
,@HdrCopy AS module_name  
,'SELECT ''OPENLINK(''''http://bp.graylite.com/web/application/index.php/browser/csv?code='+@HdrCopy+'&DocID=''+LTRIM(RTRIM(::DocID::))+''&&page=1&start=0&limit=65536&subkey=-1'''')''' AS LinkCSV  
  
/\* --SELECT 'OPENLINK(''http://bp.graylite.com/web/application/index.php/browser/csv?code=Browser.Production.Wood.Control.Material.CSV&DocID='+LTRIM(RTRIM(::DocID::))+'&&page=1&start=0&limit=65536&subkey=-1'')' */  
END  
\[/sql\]