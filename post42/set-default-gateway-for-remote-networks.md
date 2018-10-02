---
title: 'Set Default Gateway for remote networks in Windows 10'
date: 2017-04-26T00:49:00.000-07:00
draft: false
tags : [Windows]
---

How can I disable 'Use default Gateway for remote networks' setting in Windows 10.  
  
`Get-VpnConnection  
Set-VpnConnection -Name "VPN Name" -SplitTunneling $True`