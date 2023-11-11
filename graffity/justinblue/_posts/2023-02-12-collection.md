---
date: 2023-02-12 17
title:  "Collection"
csdb: 229327
coders:
  - name: "Cheesion"
    csdb: 391
size: 294x196
fps: 50
tags: fli fli-multi bitmapstretch
---
![Image 1](/c64wrd/graffity/justinblue/collection1.png)

Horizontal multicolor FLI image stretcher.

<!--more-->

This part shows a multicolor FLI image and stretches from the left side. It displays a vertically stretched sprite overlay in front of the image and changes the sprite color every line. As the stretching point moves right, it turns on more and more sprites. That pushes the FLI $ff bug more and more into the image, but it is invisible because the sprites cover them. The colors are calculated realtime from the FLI image data.

The FLI images had to be drawn in a way that the lowest d800 line have >= $08 values otherwise the scroller in the 26th line would change from multicolor (only 2 colors and background) to hires garbage.

![Image 2](/c64wrd/graffity/justinblue/collection2.png)

![Image 3](/c64wrd/graffity/justinblue/collection3.png)

![Image 4](/c64wrd/graffity/justinblue/collection4.png)

![Image 5](/c64wrd/graffity/justinblue/collection5.png)
