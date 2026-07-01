---
slide: 06
title: "Amodal Token Mechanism — Token机制"
role: mechanism-detail
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/06-slide-amodal-token.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Explain how Amodal Tokens work internally: cross-attention with image features, each token learns to query different parts of the occluded object.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise method diagram, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Amodal Token Mechanism / 非模态Token机制"
- Upper half (50%): Cross-Attention computation diagram
  - Left side: M amodal tokens (orange circles, labeled T₁...T_M) → Linear_Q → Query matrix Q (orange)
  - Right side: N image tokens (blue squares, labeled I₁...I_N) → Linear_K, Linear_V → Key K (blue), Value V (blue)
  - Center: Q × K^T → Scale (1/√d) → Softmax → Attention Weights (shown as a heatmap matrix, M×N, orange=high attention)
  - Attention Weights × V → Output Tokens (orange circles with updated fill)
- Lower half (45%): Token Specialization visualization
  - 6 token attention maps shown as small heatmap overlays on a schematic occluded object
  - Token 1: attends to visible base → label "visible base"
  - Token 2: attends to occlusion boundary → label "occlusion edge"
  - Token 3: attends to global shape → label "global shape"
  - Token 4: attends to texture details → label "texture"
  - Token 5: attends to occluded region guess → label "hidden parts"
  - Token 6: attends to context (table, floor) → label "scene context"
- Bottom: "Tokens specialize: each learns to query different geometric cues" / "Token 各司其职：不同 Token 学会询问不同的几何线索"

Content:
- Cross-attention formula labels: Q, K, V, QK^T, Softmax, ×V
- Token specialization labels
- Bottom summary

Visual Details:
- Background: pure white #FFFFFF
- Amodal Token: orange #F97316, #FFEDD5
- Image features: blue #2563EB, #DBEAFE
- Attention heatmap: yellow (low) → orange (medium) → red (high), with clear color bar
- Token specialization maps: small orange heatmaps overlaid on a gray object silhouette
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- The cross-attention diagram must clearly show data flow (Q, K, V paths).
- Heatmap colors must be distinguishable.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
