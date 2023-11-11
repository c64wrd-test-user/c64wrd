---
date: 2023-02-12 16
title:  "Retrospection"
csdb: 229327
coders:
  - name: "Cheesion"
    csdb: 391
size: 296x273
fps: 50
tags: fli fli-multi upscroll upscroll-hires
---
![Retrospection](/c64wrd/graffity/justinblue/retrospection.png)

24 char wide hires scroll over a multicolor FLI image going out to the upper and lower border. This is 2-line FLI, only every second line changes the vram colors.

<!--more-->

![Transition](/c64wrd/graffity/justinblue/retrospection_transition.png)

The transition effect uses a randomized pixel offset table, and simply copies every nth pixel in every 256 pixel block from the background picture to the visible picture until every pixel is copied.
