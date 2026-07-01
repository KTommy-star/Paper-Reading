---
slide: 05
title: "可见区域注意力"
role: "mechanism-detail"
style_preset: "journal-minimal"
language: "zh"
aspect_ratio: "16:9"
output: "images/05-slide-visible-attention.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Explain mask-weighted cross-attention: visible mask weights bias attention toward reliable visible object patches.

Style:
Nature / IEEE-inspired minimal academic presentation slide, clean scientific diagram, white background, blue heatmap accents, compact formula callout.

Composition:
Left: image patch grid with visible object patches highlighted. Middle: c_vis weight vector as a vertical or horizontal strip. Right: attention heatmap before and after weighting. Bottom right: short formula callout showing "A_ij ~ c_vis,j exp(S_ij)".

Content:
- Title: "可见区域注意力"
- Labels: "图像 patch", "可见权重", "注意力重加权", "可靠特征"
- Formula text: "A_ij ~ c_vis,j exp(S_ij)"

Visual Details:
- Blue intensity shows high visibility and high attention.
- Orange or gray shows occluded/background patches being suppressed.
- Use crisp matrix blocks and arrows.

Constraints:
- Formula must be short; no dense derivation.
- No fake numbers except the stated formula.
- No decorative 3D objects.
