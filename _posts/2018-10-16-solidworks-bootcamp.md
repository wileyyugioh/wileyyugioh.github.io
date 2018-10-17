---
title: Fixing Performance Issues With Solidworks On Bootcamp
---

For some reason, Solidworks absolutely craps the bed in Bootcamp. The software works perfectly after a fresh re-install, but after a while it just...breaks. Opening any part/assembly instantly nukes the fps.

I used to just reinstall Solidworks from scratch everytime, but I found a better solution I want to share.

**JUST RUN SOLIDWORKS IN 'BYPASS THE TOOLS/OPTIONS SETTINGS' MODE**

This is normally done through opening SOLIDWORKS RX and launching it from there, but I want to share a less annoying way.

Steps:
1. Right-click on the desktop and select New > Shortcut
2. Copy paste ```"C:\Program Files\SOLIDWORKS Corp\SOLIDWORKS\sldworks.exe" /SWSafeMode /SWDisableExitApp``` into the location bar.

<p align="center">
    <img src="/assets/2018-10-16/image1.jpg" alt="Image of creating shortcut" />
</p>

{:start="3"}
3. Give it a cute name. Maybe, 'Solidworks 20XX Safe Mode```
4. Congrats! You now have a shortcut that launches Solidworks in safe mode. You can pin this to your taskbar or whatever.
