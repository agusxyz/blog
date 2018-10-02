---
title: 'Update Browser Colom Http '
date: 2017-12-05T20:27:00.001-08:00
draft: false
---

SELECT  
       hdr\_callback, REPLACE(hdr\_callback, 'https', 'http')  
FROM System.\[Form.Headers\]  
WHERE hdr_callback LIKE '%https%'  
  
UPDATE a  
  SET  
      a.hdr\_callback = REPLACE(hdr\_callback, 'https', 'http')  
FROM System.\[Form.Headers\] a  
WHERE  
      hdr_callback LIKE '%https%'  
  
SELECT  
       a.col\_controlexpr, REPLACE(col\_controlexpr, 'https', 'http')  
FROM System.\[Form.Details\] a  
WHERE col_controlexpr LIKE '%https%'  
  
UPDATE a  
  SET  
      a.col\_controlexpr = REPLACE(col\_controlexpr, 'https', 'http')  
FROM System.\[Form.Details\] a  
WHERE  
      col_controlexpr LIKE '%https%'