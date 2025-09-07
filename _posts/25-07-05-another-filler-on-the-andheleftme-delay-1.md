---
title: "Another filler on the Andheleftme delay #1"
---

- Continued from [HeModel: Snailtrail](/posts/250624-hemodel-snailtrail)

## An unoptimized cube
*25.07.02*
![/imgs_sketches/250702_ahlm_gs.gif](/imgs_sketches/250702_ahlm_gs.gif)

This is actually a 3D grid with a periodic ("toroidal") array, but as the dead (or insignificant) cells with zero pixel intensity occlude the cells behind them, rendered is this cube.
- To-be-done (not using `ΤΟΔΟ` here not to be confused w/ the actual ones on the code a-searched): Alpha channel blending, also much-more efficient rasterizing.

## An unoptimized reaction-diffusion chunk
*25.07.03*
![/imgs_sketches/250703_ahlm_gs_fixed.gif](/imgs_sketches/250703_ahlm_gs_fixed.gif)

Masked only significant cells (`intensity > 0.1`).

*∂u/∂t = Dᵤ∇²u - uv² + F(1-u)*

*∂v/∂t = Dᵥ∇²v + uv² - (F+k)v*

Here, *F*=0.039, *k*=0.058 with *Dᵤ*=0.2, *Dᵤ*/*Dᵥ*=2. It draws the element with lesser amount.


---

The graphics code *works* but is not optimized, especially for depth checking and rasterization. Considering its only dependency is numpy I'd try python-on-browser later.

For the next project I might get lazy and use OpenGL instead u~u

Also:

---

## Blueprint of *Andheleftme #10*
*25.06.29*
![/imgs_sketches/250629_ahlm10_s0.png](/imgs_sketches/250629_ahlm10_s0.png)

I'll be implementing a primitive physics engine: for this piece, simple acceleration and the spring force (= `-kx`) would be enough o~o

- I can't read what I've wrote...
