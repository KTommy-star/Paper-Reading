---
slide: 05
title: "Architecture Details — 架构细节"
role: method-detail
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/05-slide-architecture.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Dive deeper into architectural details: DINOv2 encoder (frozen), DETR-style decoder, triplane representation dimensions.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise method diagram, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Architecture Details / 架构细节"
- Left column (55%): Detailed architecture diagram
  - DINOv2 ViT-L block: "Frozen Encoder", output "Image Tokens ∈ R^(257×1024)"
  - Amodal Token block: "Learnable", "M=256 tokens, D=256", concatenation node
  - Decoder block expanded: 3 visible layers, each showing Self-Attn → Cross-Attn → FFN with residual connections. Labels: "8× DETR-style Decoder Blocks"
  - Output: "Triplane 3×(64×64×32)", "MLP head → (σ, RGB)"
- Right column (40%): Key specifications panel — a clean spec card with:
  - Encoder: DINOv2 ViT-L, frozen
  - Image tokens: 257 × 1024
  - Amodal tokens: 256 × 256
  - Decoder layers: 8
  - Triplane resolution: 64×64, 32 channels
  - Rendering: 64 samples per ray
- Bottom: "DINOv2 (frozen) provides robust visual features; Decoder learns to complete 3D geometry via Amodal Tokens"

Content:
- Dimension callouts on each component
- Specification card on right
- Bilingual labels

Visual Details:
- Background: pure white #FFFFFF
- Encoder: blue #DBEAFE, Decoder: purple #F3E8FF, Amodal Token: orange #FFEDD5
- Spec card: light gray #F9FAFB background, subtle border #E5E7EB
- Dimension labels: small monospace-style text in dark gray #555555
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- Dimension numbers must be clearly legible.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
