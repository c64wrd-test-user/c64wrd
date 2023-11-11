---
date: 2023-02-12 20
title:  "Cheesboarding"
csdb: 229327
coders:
  - name: "Cheesion"
    csdb: 391
size: 320x115
fps: 50
tags: chessboard chessboard-zoomer
---
![Cheesboarding](/c64wrd/graffity/justinblue/cheesboarding.png)

Four multicolor chessboards in front of each other. It creates 3 chessboards by using multicolor charsets, and overlays an x-steched hires sprite layer for the top chessboard.

<!--more-->

The chessboard pattern is generated real-time by generating 8 combinations of transparent/opaque versions of the 3 colored rectangles, and switching between them with $d018 charset (one char line is stretched vertically). The sprites have only 2 versions and switched by the $d018 vram (one sprite line is stretched vertically).

The $d018 values are calculated using EOR from the 4 layer tables during display. The $d018 pattern is generated in a way that for the chessboard layers close to the camera (large distances) only those entries cleared which had changes to save raster time.
