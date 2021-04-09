---
title: 'Ubuntu: Loading Photos from Nikon D3300 DSLR Camera'
date: Sat, 10 Feb 2018 13:56:02 +0000
draft: false
tags: ['Camera', 'Desktop', 'Ubuntu']
---

I had some trouble loading photos from my Nikon D3300 camera. I had the USB cable, which came with and connected my PC to it. The camera was on. I use Xubuntu. My file manager is Thunar. The camera would appear in the file manager. Whenever I would try to browse the files in the camera, Thunar would freeze. gvfsd-ghoto2 would use up a huge chunk of the CPU. I would then have to close Thunar and try again. This happened everytime. If you are experiencing the same problems. Mys suggestion is to not use Thunar, but to download gtkam. It's a GUI for gphoto2. You can of course simply use the gphoto2 CLI if you want. ![](http://kevinkivi.com/wp-content/uploads/2018/02/1166290918_b739baedbd_o-300x182.png) Photo by Javler Martínez How to install gtkam:
```
sudo apt-get update
sudo apt-get install gtkam
```
This solved all my freezing issues. You can of course simply use and SD Card reader if you happen to have one.
