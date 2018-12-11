---
title: How To Get The Clamp-To-Edge Effect In Imagemagick
tags: info
---

<p style="text-align:center">
    <img src="/assets/2018-08-02/image1.jpg" alt="Base image" height="250" width="250"/>
    <br>
    <em>The base image</em>
</p>

Let's start with a 500x500 image.

```
convert image1.jpg -define distort:viewport=1000x1000 -filter point -distort SRT "%[fx:w/2],%[fx:h/2] 1 0 %[fx:1000/2],%[fx:1000/2]" +repage image2.jpg
```

A more copy-paste friendly script is

```
W=1000; H=1000; convert image1.jpg -define distort:viewport=${W}x${H} -filter point -distort SRT "%[fx:w/2],%[fx:h/2] 1 0 %[fx:${W}/2],%[fx:${H}/2]" +repage image2.jpg
```

Where you can set W and H to be your desired width and height respectively.

This snippet resizes an image to 1000x1000.

<p style="text-align:center">
    <img src="/assets/2018-08-02/image2.jpg" alt="Clamp-to-edge image" height="250" width="250"/>
    <br>
    <em>The final result</em>
</p>

The general gist of how this works is that we use the [distort and viewport](https://www.imagemagick.org/Usage/distorts/#distort_viewport) filters to stretch our image. This will only stretch the right and bottom, so we have to set the SRT argument to `X,Y Scale Angle NewX,NewY` to ensure our new image is centered.
