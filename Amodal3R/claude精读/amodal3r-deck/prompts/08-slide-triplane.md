---
slide: 08
title: "Triplane & Volume Rendering — 三平面与体渲染"
role: mechanism-detail
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/08-slide-triplane.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Explain the Triplane representation and how volume rendering produces novel views from it.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise method diagram, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Triplane Representation & Volume Rendering / 三平面表示与体渲染"
- Left half (50%): Triplane structure
  - Three orthogonal planes shown in a 3D-like isometric view:
    - XY plane (blue tinted, labeled "XY: front-back × left-right")
    - XZ plane (green tinted, labeled "XZ: front-back × up-down")
    - YZ plane (orange tinted, labeled "YZ: left-right × up-down")
  - A query 3D point p=(x,y,z) shown as a red dot
  - Three dashed projection lines from p to each plane
  - On each plane: a small bilinear interpolation grid (2×2) around the projected point
  - Three interpolated features f_xy, f_xz, f_yz → sum → feature vector f(p)
  - f(p) → small MLP icon → outputs (σ, RGB)
- Right half (45%): Volume rendering
  - A camera icon on the left shooting a ray through the triplane space
  - Ray shown as a line with sample points (small colored dots, density indicated by dot size)
  - Sample points accumulate: "Volume Rendering: C = Σ T_i · α_i · c_i"
  - Final rendered pixel shown as a small color swatch
  - Small inset: rendered novel view example (a 3D chair from a new angle)
- Bottom: "Triplane = efficient 3D representation. Any 3D point → project + interpolate + sum → feature." / "三平面：高效 3D 表示，任意点→投影+插值+求和→特征"

Content:
- Plane labels: XY, XZ, YZ with descriptions
- Query point p and projection lines
- Volume rendering equation (compact)
- Rendered output inset

Visual Details:
- Background: pure white #FFFFFF
- XY plane: light blue #DBEAFE
- XZ plane: light green #DCFCE7
- YZ plane: light orange #FFEDD5
- Query point: red #EF4444
- Ray: dark gray #333333 with small sample dots (colored by density)
- MLP icon: small rounded rectangle, dark gray
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- The isometric view of three orthogonal planes must be geometrically clear.
- The projection + interpolation concept must be visually intuitive.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
