---
slide: 04
title: "Pipeline Overview — 方法总览"
role: method-overview
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/04-slide-pipeline.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Show the complete Amodal3R pipeline from input to output in 5 stages: Encode → Token Injection → Decode → Triplane → Render.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise method diagram, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Pipeline Overview / 方法总览"
- Main area: Horizontal left-to-right flow with 5 modules connected by bold arrows:
  - Module 1 (far left): "Occluded RGB" / "遮挡RGB图像" — a small image icon with a red occlusion overlay
  - Arrow →
  - Module 2: "DINOv2 Encoder" / "DINOv2 编码器" — blue rounded rectangle, label "ViT-L", output "Image Tokens N×D"
  - Arrow →
  - Module 3 (highlighted with orange border and star): "Amodal Tokens" / "非模态Token" — orange rounded rectangle, label "Learnable M×D", merged with image tokens via a "+" node
  - Arrow →
  - Module 4: "Transformer Decoder" / "Transformer 解码器" — purple rounded rectangle, label "N stacked blocks", internal mini-diagram showing 3 stacked layers
  - Arrow →
  - Module 5 (far right): "Triplane + Render" / "三平面+渲染" — green rounded rectangle, showing three orthogonal planes (XY/XZ/YZ in blue/green/orange) and a camera icon → "Novel Views"
- Bottom: One-line summary "Single Image → Encoder → Amodal Tokens → Decoder → Triplane → Render / 单图→编码→Token→解码→三平面→渲染"

Content:
- Module labels: bilingual (Chinese / English, English larger)
- Dimension annotations: N×D, M×D, 3×(H×W×C)
- Star marker on Amodal Token module

Visual Details:
- Background: pure white #FFFFFF
- Module colors: Encoder blue #DBEAFE / #2563EB, Amodal Token orange #FFEDD5 / #F97316, Decoder purple #F3E8FF / #9333EA, Triplane green #DCFCE7 / #16A34A
- Arrows: dark gray #666666, 2px, bold arrowheads
- Clean sans-serif typography
- Module border radius: 8px

Constraints:
- The output must be a polished 16:9 slide.
- All 5 modules must be clearly distinguishable.
- The Amodal Token module must visually stand out (orange, thicker border, star).
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
