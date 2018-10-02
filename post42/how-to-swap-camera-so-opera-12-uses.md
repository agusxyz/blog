---
title: 'How to swap the camera so Opera 12 uses front camera for getUserMedia()'
date: 2017-06-15T18:20:00.000-07:00
draft: false
tags : [Explore, camera, android]
---

Essentially you only need to swap the tags 'front' and 'back' in the file /etc/nvcamera.conf  
  
The change is permanent across reboots, but messes the orientation/mirror image of the cameras, so the rear camera becomes a mirror image, not the front. This messes all portrait shots as the camera pic becomes upside down.  
  
Device needs to be rooted.  
  
  
  
Need to make /system directory read/write:  
  
\# mount -o rw,remount /system  
  
\# vi /etc/nvcamera.conf# format, cameraName=device,direction,orientation,type  
  
This is the file before mods  
\# type can be 'stereo' for stereo capable, 'mono' for not stereo capable,  
\# 'usb' to enable searching for a usb device and where to put it in the list  
\# if found. Lines must be shorter then 256 characters  
version=1  
camera0=/dev/ov5640,back,0,mono  
#camera1=/dev/ov5650,back,0,mono // 2nd camera for stereo once supported  
camera1=/dev/mi1040,front,0,mono  
#camera4=/dev/ov5650,back,0,stereo // virtual stereo device once supported  
  
  
Change this line:  
camera0=/dev/ov5640,back,0,mono  
  
to:  
camera0=/dev/ov5640,front,0,mono  
  
And this line:  
camera1=/dev/mi1040,front,0,mono  
  
to:  
camera1=/dev/mi1040,back,0,mono  
  
  
Save and it works.  
  
source : [https://forum.xda-developers.com/showthread.php?t=1699299](https://forum.xda-developers.com/showthread.php?t=1699299)