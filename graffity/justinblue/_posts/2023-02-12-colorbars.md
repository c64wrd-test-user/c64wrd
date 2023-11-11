---
date: 2023-02-12 22
title:  "Colorbars"
csdb: 229327
coders:
  - name: "Cheesion"
    csdb: 391
size: 252x122
fps: 50
tags: kefrens kefrens-16color
---
![Colorbars](/c64wrd/graffity/justinblue/colorbars.png)

39 vertical multicolor raster bars using all 16 colors.

<!--more-->

Every bar is 22 pixel wide, plus 2-2 pixels of background color on the sides. Every bar can use 5 different colors. The routine repeats the same top 3 pixel lines of a bitmap, and redraws the bitmap/vram/d800 of the line while they are displayed.

Notable is the hardware scroll below which draws the runes into several csets in a way that a single multicolor pixel separates the runes which are not aligned to character boundaries. (The font was created for a different - unfinished - intro and it would have been a sin to let it be wasted.)
