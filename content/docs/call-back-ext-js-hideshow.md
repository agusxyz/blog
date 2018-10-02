---
title: 'Call Back Ext JS (hide,show)'
date: 2017-04-13T00:07:00.000-07:00
draft: false
tags : [javascript, extjs, graylite]
---

Cara hide,show,set value ExtJs Call Back  
  
Get ID Componen Callback and hide  
  
\[java\]  
  
if(docflow_seq==5) {  
Ext.getCmp('button-1031').hide();  
}  
  
Ext.getCmp('buttonsavedetailsform').hide();  
try{  
\_COM\_btnprint.setDisabled(false);  
}catch(e){}  
  
\[/java\]  
  
  
  
Get ID Componen Callback and hide (graylite)  
  
\[java\]  
  
\_COM\_flowhistory.show().setDisabled(false);  
  
if(doc_term==0) {  
\_COM\_doc_cashpaid.setValue(1);  
}else{  
\_COM\_doc_cashpaid.setValue(0);  
}  
  
if (docflow_seq==10) {  
\_COM\_btncop.show().setDisabled(false);  
  
} else {  
\_COM\_btncop.show().setDisabled(false);  
  
if (docflow\_seq&lt;10) { \_COM_rejournal.show().setDisabled(true); }  
  
}  
  
if(!window.openlink){  
window.openlink = function(promoid){  
OPENLINK('http://'+window.location.host+'/web/application/index.php/details/index?code=Form.Sales.Promotion&amp;mode=open&amp;doc_id='+promoid,1,'Sales Promotion')  
}  
}  
\[/java\]  
  
inline if in JavaScript  
`condition==1 ? true : false`  
  
\[java\]  
/\*\-\-\-\- One Condition ----*/  
trans\_pack==1? item\_sellprice : item_sellpack  
  
/\*\-\-\-\- Multi Condition ----*/  
(trans\_pack>0)?trans\_pack\*item\_subqty:trans\_qty2\*1 || trans_qty  
  
trans\_bonus==1?0:(trans\_price!=0 &amp;&amp; trans\_price2==0)?trans\_price:((trans\_qty==0)?0:(trans\_price2 &gt;0)? trans\_price2:(trans\_pack==0)?item\_sellprice: item\_sellpack)  
  
/\*\-\-\-\- in Grid ----*/  
if(\_ROWS.get('trans\_qty2')!=trans_qty){  
\_ROWS.set('trans\_qty2', trans_qty);  
}  
  
  
\[/java\]