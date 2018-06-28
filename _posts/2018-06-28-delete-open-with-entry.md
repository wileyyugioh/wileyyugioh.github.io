---
title: How To Delete An Open With Entry On Windows 10
---

<p align="center">
    <img src="/assets/2018-06-28/image1.png" alt="Windows's open with menu" />
</p>

After I accidentally misclicked and attempted to open a zip file with the wrong .exe, I slowly realized that my mistake was there forever.

I tried to use the method of using regedit to edit **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\\.zip**, but the method didn't work because it was affecting *every* filetype.

The solution that worked for me was to go to **HKEY_CURRENT_USER\Software\Classes\Applications** and delete the offending application.

<p align="center">
    <img src="/assets/2018-06-28/image2.png" alt="Screenshot of registry" />
</p>

**Remember, always make a backup before editing the registry**
