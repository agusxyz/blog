---
title: 'Stimulsoft Report - KeepHeaderTogether and KeepFooterTogether Property '
date: 2017-01-01T18:58:00.000-08:00
draft: false
tags : [stimulsoft]
---

### KeepHeaderTogether

Sometimes, when printing lists, a header will be printed on one page, and the first row of data on another. To escape this visual gap of data the KeepHeaderTogether property of the Header band can be used. If the property is true, then headers will be printed together with data. In other words as minimum one row with data will be output. If there is no enough free space for a header with data row, then they will be carried over on the next page. See a sample of a rendered report with  the KeepHeaderTogether property set to false.

  

![](https://www.stimulsoft.com/en/documentation/online/user-manual/embim670.png)

  

As the same report with keeping header together with the first data row.

  

![](https://www.stimulsoft.com/en/documentation/online/user-manual/embim671.png)

  

  

By default, the KeepHeaderTogether property is set to true. So headers will be kept together with the first row of data.

  

### KeepFooterTogether

The KeepFooterTogether property is used to print a list so that to output data row together with totals of data. If the property is true, then totals will be printed with the last row of data. If total cannot be placed after the last page printing, then it is output on the current page. If there is no enough free space to output totals, then it is carried over on the next page. On picture below a sample of a report with the KeepFooterTogether property set to false is shown.

  

![](https://www.stimulsoft.com/en/documentation/online/user-manual/embim672.png)

  

And the same report with keeping footer together with the last row of data.

  

![](https://www.stimulsoft.com/en/documentation/online/user-manual/embim673.png)

  

By default, the KeepFooterTogether property is set to true, so totals of data will be kept together with last row of data.

  
source : [https://www.stimulsoft.com/en/documentation/online/user-manual/index.html?report\_internals\_creating\_lists\_keepfootertogether_property.htm](https://www.stimulsoft.com/en/documentation/online/user-manual/index.html?report_internals_creating_lists_keepfootertogether_property.htm)