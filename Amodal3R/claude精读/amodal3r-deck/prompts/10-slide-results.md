---
slide: 10
title: "Key Results — 关键实验结果"
role: evidence
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/10-slide-results.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Present the key quantitative results: Amodal3R outperforms all baselines, especially on occluded regions.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise data visualization, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Key Results / 关键实验结果"
- Left side (45%): Quantitative comparison table
  - Clean table with rows: Method | PSNR↑ | SSIM↑ | LPIPS↓ | Amodal-PSNR↑
  - 4-5 rows: Baseline A, Baseline B, Baseline C, Amodal3R (Ours)
  - Amodal3R row highlighted with light orange background #FFEDD5
  - Best values in each column shown in bold
  - Key callout: "+3.2 dB PSNR on occluded regions" with an arrow pointing to Amodal-PSNR column
- Right side (50%): Qualitative comparison
  - Three rows (chair, table, car)
  - Each row: tiny Input (occluded) | Baseline output (broken 3D, red ✗) | Amodal3R output (complete 3D, green ✓)
  - Occluded regions marked with red dashed circles on inputs
  - Amodal3R outputs show orange-highlighted recovered regions
- Bottom: "Amodal3R consistently outperforms baselines, especially on heavily occluded regions" / "在所有指标上超越基线，遮挡区域优势显著"

Content:
- Table headers and values
- Qualitative comparison rows with object labels
- Key callout annotation
- Bottom summary

Visual Details:
- Background: pure white #FFFFFF
- Table: clean grid with thin #E5E7EB borders, header row #F9FAFB
- Highlight row: #FFEDD5
- Green checkmark: #16A34A, Red cross: #EF4444
- Recovered regions: orange #F97316 shading
- Clean sans-serif typography, monospace for numbers

Constraints:
- The output must be a polished 16:9 slide.
- Table numbers must be clearly legible.
- Qualitative examples must show clear visual difference between baseline and Amodal3R.
- No page numbers, logos, watermarks.
- No fake data — use placeholder "X.XX" if exact numbers unknown, but make the table look real.
- No fake UI or AI robot imagery.
