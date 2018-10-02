---
title: 'Procedure and Trigger System Flow'
date: 2017-05-04T23:16:00.001-07:00
draft: false
tags : [Sql Server]
---

###### PROCEDURE \[System\].\[Flow.Execute\]

  
  
  
\[sql\]  
CREATE PROCEDURE \[System\].\[Flow.Execute\]  
@FlowID INT  
AS  
BEGIN  
  
SET NOCOUNT ON;  
  
DECLARE  
@DoctypeID INT  
,@DocID INT  
,@PrevSeq TINYINT  
,@NextSeq TINYINT  
,@DocHeader CHAR(3)  
,@ErrMsg NVARCHAR(1000)  
,@TableName NVARCHAR(50)  
,@SqlCommand NVARCHAR(MAX)  
,@LogicID INT  
,@ProcCheck VARCHAR(100)  
,@ProcUpdate VARCHAR(100)  
,@ProcFail VARCHAR(100)  
,@ProcNotify VARCHAR(100)  
,@DocNo VARCHAR(50)  
,@GLNo VARCHAR(50)  
  
IF EXISTS  
(  
SELECT  
flow_id  
FROM System.\[Flow.History\]  
WHERE flow_id = @FlowID  
)  
BEGIN  
UPDATE System.\[Flow.History\]  
SET flow_processed = 1  
WHERE  
flow_id = @FlowID  
END  
ELSE  
BEGIN  
PRINT 'Flow '+CONVERT(VARCHAR(9),@FlowID)+' not found'  
END  
  
SELECT  
@DoctypeID = a.doctype_id  
,@DocID = a.doc_id  
,@PrevSeq = a.docflow_prev  
,@NextSeq = a.docflow_next  
,@DocHeader = c.doctype_header  
,@TableName = c.doctype_table  
FROM System.\[Flow.History\] a  
INNER JOIN System.\[Flow.Logic\] b ON a.doctype\_id = b.doctype\_id  
INNER JOIN System.\[Flow.Document\] c ON a.doctype\_id = c.doctype\_id  
WHERE flow_id = @FlowID  
  
SELECT  
@LogicID = a.logic_id  
,@ProcCheck = a.proc_check  
,@ProcUpdate = a.proc_update  
,@ProcFail = a.proc_fail  
,@ProcNotify = b.proc_notify  
FROM System.\[Flow.Logic\] a  
INNER JOIN System.\[Flow.State\] b ON a.doctype\_id = b.doctype\_id  
AND a.next\_seq = b.docflow\_seq  
WHERE a.doctype_id = @DoctypeID  
AND a.prev_seq = @PrevSeq  
AND a.next_seq = @NextSeq  
  
\-\-\- Error if logic_id not found  
  
IF @LogicID IS NULL  
BEGIN  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update_log = 'Document flow logic for '+@DocHeader+'-'+LTRIM(CONVERT( VARCHAR(3),@PrevSeq))+'-'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))+' is not found'  
WHERE  
flow_id = @FlowID  
RETURN 0  
END  
  
\-\- set default StoredProcedure if not defined  
  
IF isnull(@ProcCheck,'') = ''  
BEGIN  
SET @ProcCheck = 'DocFlow.'+RTRIM(@DocHeader)+'.Check.'+LTRIM(CONVERT(VARCHAR(3),@PrevSeq))+'.'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))  
END  
IF isnull(@ProcUpdate,'') = ''  
BEGIN  
SET @ProcUpdate = 'DocFlow.'+RTRIM(@DocHeader)+'.Update.'+LTRIM(CONVERT(VARCHAR(3),@PrevSeq))+'.'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))  
END  
IF isnull(@ProcFail,'') = ''  
BEGIN  
SET @ProcFail = 'DocFlow.'+RTRIM(@DocHeader)+'.Fail.'+LTRIM(CONVERT(VARCHAR(3),@PrevSeq))+'.'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))  
END  
IF isnull(@ProcNotify,'') = ''  
BEGIN  
SET @ProcNotify = 'DocFlow.'+RTRIM(@DocHeader)+'.Notify.'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))  
END  
  
SET @ErrMsg = ''  
  
  
\-\- Run check procedure  
  
BEGIN TRY  
IF isnull(@ProcCheck,'') <> ''  
BEGIN  
IF EXISTS  
(  
SELECT  
name  
FROM sys.procedures  
WHERE name = @ProcCheck  
)  
BEGIN  
SET @ProcCheck = 'System.\['+@ProcCheck+'\]'  
EXEC @ProcCheck @DocID  
,@ErrMsg OUTPUT  
END  
END  
END TRY  
BEGIN CATCH  
PRINT 'Catch error at CHECK Procedure : '+@ProcCheck+' - '+ERROR_MESSAGE()  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update\_log = 'SQL Error: '+ERROR\_MESSAGE()  
WHERE  
flow_id = @FlowID  
RETURN 0  
END CATCH;  
  
  
\-\- If check procedure running and failed - RUN Fail Procedure  
  
BEGIN TRY  
IF @ErrMsg <> ''  
BEGIN  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update_log = @ErrMsg  
WHERE  
flow_id = @FlowID  
  
IF isnull(@ProcFail,'') <> ''  
BEGIN  
IF EXISTS  
(  
SELECT  
name  
FROM sys.procedures  
WHERE name = @ProcFail  
)  
BEGIN  
SET @ProcFail = 'System.\['+@ProcFail+'\]'  
EXEC @ProcFail @DocID  
END  
END  
  
RETURN 0  
END  
END TRY  
BEGIN CATCH  
PRINT 'Catch error at Fail Procedure : '+@ProcFail+' - '+ERROR_MESSAGE()  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update\_log = 'SQL Error: '+ERROR\_MESSAGE()  
WHERE  
flow_id = @FlowID  
RETURN 0  
END CATCH;  
  
  
\-\- Run update procedure  
  
IF @ErrMsg = ''  
BEGIN  
  
BEGIN TRY  
IF isnull(@ProcUpdate,'') <> ''  
BEGIN  
IF EXISTS  
(  
SELECT  
name  
FROM sys.procedures  
WHERE name = @ProcUpdate  
)  
BEGIN  
SET @ProcUpdate = 'System.\['+@ProcUpdate+'\]'  
EXEC @ProcUpdate @DocID  
,@ErrMsg OUTPUT  
END  
ELSE  
BEGIN  
SET @ErrMsg = 'Update procedure '+@ProcUpdate+' for '+@DocHeader+'-'+LTRIM(CONVERT(VARCHAR(3),@PrevSeq))+'-'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))+' is not found'  
END  
END  
  
IF @ErrMsg <> ''  
BEGIN  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update_log = @ErrMsg  
WHERE  
flow_id = @FlowID  
END  
END TRY  
BEGIN CATCH  
PRINT 'Catch error at UPDATE Procedure : '+@ProcUpdate+' - '+ERROR_MESSAGE()  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update\_log = 'SQL Error: '+ERROR\_MESSAGE()  
WHERE  
flow_id = @FlowID  
  
RETURN 0  
END CATCH;  
  
BEGIN TRY  
UPDATE System.\[Flow.History\]  
SET update_success = 1  
,update_log = @ErrMsg  
WHERE  
flow_id = @FlowID  
END TRY  
BEGIN CATCH  
PRINT 'Catch error at UPDATING LOG to Success : '+CONVERT(VARCHAR(10),@FlowID)+' - '+ERROR_MESSAGE()  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update_log = 'Can not set update flag'  
WHERE  
flow_id = @FlowID  
END CATCH  
  
BEGIN TRY  
INSERT INTO \[System\].\[Notification\]  
(  
\[notice_form\]  
,\[doctype_id\]  
,\[doc_id\]  
,\[notice_user\]  
,\[notice_subject\]  
,\[notice_email\]  
)  
SELECT  
\[notice_form\]  
,@DoctypeID  
,@DocID  
,\[notice_user\]  
,\[notice_subject\]  
,\[notice_email\]  
FROM \[System\].\[Flow.Notice\]  
WHERE doctype_id = @DoctypeID  
AND docflow_seq = @NextSeq  
END TRY  
BEGIN CATCH  
PRINT 'Catch error at sending email notification: '+ERROR_MESSAGE()  
END CATCH  
  
\-\- Run notify procedure  
  
BEGIN TRY  
IF isnull(@ProcNotify,'') <> ''  
BEGIN  
IF EXISTS  
(  
SELECT  
name  
FROM sys.procedures  
WHERE name = @ProcNotify  
)  
BEGIN  
SET @ProcNotify = 'System.\['+@ProcNotify+'\]'  
  
EXEC @ProcNotify @DocID  
,@ErrMsg OUTPUT  
END  
ELSE  
BEGIN  
SET @ErrMsg = 'Notify procedure '+@ProcNotify+' for '+@DocHeader+'-'+LTRIM(CONVERT(VARCHAR(3),@NextSeq))+' is not found'  
END  
END  
  
IF @ErrMsg <> ''  
BEGIN  
UPDATE System.\[Flow.History\]  
SET update_success = 0  
,update_log = 'Notify : '+@ErrMsg  
WHERE  
flow_id = @FlowID  
END  
END TRY  
BEGIN CATCH  
PRINT 'Catch error at NOTIFY Procedure: '+@ProcNotify+' - '+ERROR_MESSAGE()  
UPDATE System.\[Flow.History\]  
SET update\_log = 'SQL Error on notify: '+ERROR\_MESSAGE()  
WHERE  
flow_id = @FlowID  
RETURN 0  
END CATCH;  
END  
END  
\[/sql\]  
  

###### TRIGGER \[System\].\[Flow.History\]

  
  
\[sql\]  
CREATE TRIGGER \[System\].\[Flow.ExecuteTrigger\] ON \[System\].\[Flow.History\]  
AFTER INSERT  
AS  
BEGIN  
SET NOCOUNT ON;  
  
DECLARE  
@Result TABLE  
(  
\[doctype_id\] \[TINYINT\]  
,\[doc_id\] \[INT\]  
,\[docflow_prev\] \[TINYINT\]  
,\[docflow_next\] \[TINYINT\]  
,\[update_log\] \[NVARCHAR\](MAX)  
,\[update_success\] \[BIT\]  
)  
  
DECLARE  
@FLOW_ID INT  
,@LastID INT  
,@Show BIT  
SELECT TOP 1  
@FLOW\_ID = flow\_id  
,@Show = flow_result  
FROM System.\[Flow.History\]  
WHERE flow_processed = 0  
ORDER BY  
1 ASC  
  
WHILE @FLOW_ID IS NOT NULL  
BEGIN  
  
BEGIN TRY  
EXEC System.\[Flow.Execute\] @Flow_ID  
END TRY  
BEGIN CATCH  
UPDATE System.\[Flow.History\]  
SET flow_processed = 1  
,update_success = 0  
,update\_log = ERROR\_MESSAGE()  
WHERE  
flow\_id = @Flow\_ID  
END CATCH  
  
IF @Show = 1  
BEGIN  
INSERT INTO @Result  
SELECT  
doctype_id  
,doc_id  
,docflow_prev  
,docflow_next  
,update_log  
,update_success  
FROM System.\[Flow.History\]  
WHERE flow\_id = @Flow\_ID  
END  
SELECT  
@LastID = @Flow_ID  
,@FLOW_ID = NULL  
SELECT TOP 1  
@FLOW\_ID = flow\_id  
FROM System.\[Flow.History\]  
WHERE flow_processed = 0  
ORDER BY  
1 ASC  
PRINT 'Execute Flow : '+CONVERT(VARCHAR,@Flow_ID)  
END  
  
IF  
(  
SELECT  
COUNT(*)  
FROM @Result  
) \> 0  
BEGIN  
SELECT  
*  
FROM @Result  
END  
END  
\[/sql\]