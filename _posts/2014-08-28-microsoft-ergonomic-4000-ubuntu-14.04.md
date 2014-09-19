---
layout: post
title: Setup and Customize the Microsoft Ergonomic 4000 Keyboard with Ubuntu 14.04
permalink: microsoft-ergonomic-4000-with-ubuntu-14.04
---

The slider in the middle of the keyboard should do  pageup / pagedown for scrolling. Change key mapping in /lib/udev/hwdb.d/60-keyboard.hwdb. Lock for the Microsoft block and change like this:

```
###########################################################
# Microsoft
###########################################################

# Microsoft Natural Ergonomic Keyboard 4000
keyboard:usb:v045Ep00DB*
 KEYBOARD_KEY_c022d=pageup						# Slider up
 KEYBOARD_KEY_c022e=pagedown					# Slider down
```

After this change you need to run:
```
sudo udevadm hwdb --update
```
and reboot.
