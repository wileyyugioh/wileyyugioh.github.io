---
title: How To Get The Clamp-To-Edge Effect In Imagemagick
---

<p align="center">
    <img src="/assets/2018-08-02/image1.jpg" alt="Base image" height="250" width="250" />
</p>

*The base image*

```
convert image1.jpg -define distort:viewport=1000x1000 -filter point -distort SRT "%[fx:w/2],%[fx:h/2] 1 0 %[fx:1000/2],%[fx:1000/2]" +repage image2.jpg
```

This resizes an image to 1000x1000.

<p align="center">
    <img src="/assets/2018-08-02/image2.jpg" alt="Clamp-to-edge image" height="250" width="250" />
</p>

*The final result*
