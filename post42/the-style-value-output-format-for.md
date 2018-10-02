---
title: 'The style value the output format for the date/time'
date: 2017-05-30T19:19:00.000-07:00
draft: false
tags : [time, style date, date, format style date time, date time, Sql Server, style time]
---

The _style_ value can be one of the following values:  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

Without century

With century

Input/Output

Standard

-

0 or 100

mon dd yyyy hh:miAM (or PM)

Default

1

101

1 = mm/dd/yy  
101 = mm/dd/yyyy

USA

2

102

2 = yy.mm.dd  
102 = yyyy.mm.dd

ANSI

3

103

3 = dd/mm/yy  
103 = dd/mm/yyyy

British/French

4

104

4 = dd.mm.yy  
104 = dd.mm.yyyy

German

5

105

5 = dd-mm-yy  
105 = dd-mm-yyyy

Italian

6

106

6 = dd mon yy  
106 = dd mon yyyy

-

7

107

7 = Mon dd, yy  
107 = Mon dd, yyyy

-

8

108

hh:mm:ss

-

-

9 or 109

mon dd yyyy hh:mi:ss:mmmAM (or PM)

Default + millisec

10

110

10 = mm-dd-yy  
110 = mm-dd-yyyy

USA

11

111

11 = yy/mm/dd  
111 = yyyy/mm/dd

Japan

12

112

12 = yymmdd  
112 = yyyymmdd

ISO

-

13 or 113

dd mon yyyy hh:mi:ss:mmm (24h)

Europe default + millisec

14

114

hh:mi:ss:mmm (24h)

-

-

20 or 120

yyyy-mm-dd hh:mi:ss (24h)

ODBC canonical

-

21 or 121

yyyy-mm-dd hh:mi:ss.mmm (24h)

ODBC canonical (with milliseconds) default for time, date, datetime2, and datetimeoffset

-

126

yyyy-mm-ddThh:mi:ss.mmm (no spaces)

ISO8601

-

127

yyyy-mm-ddThh:mi:ss.mmmZ (no spaces)

ISO8601 with time zone Z

-

130

dd mon yyyy hh:mi:ss:mmmAM

Hijiri

-

131

dd/mm/yy hh:mi:ss:mmmAM

Hijiri