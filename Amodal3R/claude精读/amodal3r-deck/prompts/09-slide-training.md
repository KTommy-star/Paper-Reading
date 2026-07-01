---
slide: 09
title: "Training Strategy — 训练策略"
role: method
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/09-slide-training.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Explain the two-stage training strategy: synthetic occlusion generation + multi-view rendering supervision.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise method diagram, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Training Strategy / 训练策略"
- Upper section (45%): "Stage 1: Occlusion Simulation / 遮挡模拟"
  - Left: Complete 3D object from Objaverse (multi-view thumbnails, 3-4 small images)
  - Center: Random occlusion mask generation — show a few random mask shapes (blobs, rectangles) and how they overlay on the object
  - Right: Occluded training input — the object with mask applied
  - Annotation: "Random object occlusion during training. Model never sees real occlusions."
- Lower section (45%): "Stage 2: Multi-View Rendering Loss / 多视图渲染损失"
  - Center: Triplane from model → multiple camera icons around it (4-6 angles) → rendered views
  - Rendered views compared to GT with loss arrows
  - Loss box (highlighted): "L_total = L_rgb + λ_mask·L_mask + λ_percep·L_LPIPS"
  - Right: Small training curve inset (loss decreasing over epochs)
- Bottom: "Trained on synthetic occlusions only. Zero-shot generalizes to real occluded images." / "仅用合成遮挡训练，零样本泛化到真实遮挡"

Content:
- Stage labels
- Random mask illustrations
- Loss formula (compact)
- Training curve inset

Visual Details:
- Background: pure white #FFFFFF
- Stage 1: red-tinted occlusion elements #FEE2E2
- Stage 2: green-tinted rendering elements #DCFCE7
- Loss box: light yellow #FEF9C3 background, dark text
- Camera icons: simple line-art cameras, dark gray
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- Two stages must be visually separated (horizontal divider or distinct background tints).
- Loss formula must be clearly readable.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
