---
slide: 12
title: "Ablation Study — 消融实验"
role: evidence
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/12-slide-ablation.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Show that design choices (token count, decoder depth, triplane resolution) are well-motivated through ablation studies.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise data visualization, clear restrained scientific color palette.

Composition:
- Top: Title "Ablation Study / 消融实验"
- Main area: Three side-by-side bar chart panels, equal width
  - Panel A: "Amodal Token Count / Token 数量"
    - X-axis: 16, 64, 128, 256, 512
    - Y-axis: PSNR (dB)
    - Bars in gray, optimal (256) highlighted in orange #F97316
    - Small annotation: "256 tokens: sweet spot"
  - Panel B: "Decoder Layers / 解码器层数"
    - X-axis: 4, 6, 8, 12
    - Y-axis: PSNR (dB)
    - Bars in gray, optimal (8) highlighted in orange
    - Small annotation: "8 layers: best speed/quality"
  - Panel C: "Triplane Resolution / 三平面分辨率"
    - X-axis: 32, 64, 128
    - Y-axis: PSNR (dB)
    - Bars in gray, optimal (64) highlighted in orange
    - Small annotation: "64²: diminishing returns beyond"
- Below charts: A compact table showing additional ablations
  - Rows: "w/o Amodal Tokens", "w/o Cross-Attn", "w/o Triplane", "Full Model"
  - 2 columns: PSNR, Amodal-PSNR
  - Full Model row highlighted
  - Large drop without Amodal Tokens emphasized with a red arrow ↓
- Bottom: "All components contribute. Amodal Tokens provide the largest gain." / "所有组件均有贡献，Amodal Token 收益最大"

Content:
- Chart titles and axis labels
- Bar value annotations (small numbers above bars)
- Highlight annotations
- Ablation table

Visual Details:
- Background: pure white #FFFFFF
- Bars: default gray #D1D5DB, optimal orange #F97316
- Chart axes: dark gray #333333, thin lines
- Ablation table: clean grid, header #F9FAFB, highlight #FFEDD5
- Red drop arrow: #EF4444
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- Bar charts must be clean and readable.
- Three panels must be equal width and aligned.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
