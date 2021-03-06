---
title: Installing Only The Drivers From Creative Labs
tags: info
---

Creative Labs does not allow you to only install audio drivers through the provided installer, requiring a completely unnecessary "control panel" instead. This is a guide on how to get around that.

1. Download the latest installer from Creative Labs.
2. Open the .exe file with an unarchiver. I am using 7-Zip.
3. Navigate to `program files\Creative\Sound Blaster Z-Series\` and extract the `Program` folder.

<p style="text-align:center">
    <img src="/assets/img/2018-07-20/image1.png" alt="Image of 7-Zip GUI">
</p>

{:start="4"}
4. Open the extracted `Program` folder and run `Setup.exe`. Afterwards, there will be *no* windows that open. Although it may seem like nothing happened, after a while, your drivers will be installed.
5. Verify the drivers were installed by clicking on the Speaker icon on the taskbar, where "(Sound Blaster Z)" should appear.
