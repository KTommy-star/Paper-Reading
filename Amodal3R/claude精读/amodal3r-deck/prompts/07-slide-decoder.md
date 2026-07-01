---
slide: 07
title: "Transformer Decoder — 解码器内部"
role: mechanism-detail
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/07-slide-decoder.png"
---

Create one complete 16:9 presentation slide image.

Purpose:
Show the internal structure of the Transformer Decoder: 8 stacked blocks, each with Self-Attention (token coordination) and Cross-Attention (image feature retrieval).

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise method diagram, clear restrained scientific color palette, compact readable labels.

Composition:
- Top: Title "Transformer Decoder / Transformer 解码器内部"
- Left side (45%): Stacked decoder blocks
  - 8 blocks vertically stacked, labeled "Block 1" through "Block 8"
  - Each block shown as a compact horizontal strip with 4 sub-modules: [Self-Attn] → [+ residual] → [Cross-Attn] → [+ residual] → [FFN] → [+ residual]
  - Input: "Amodal Tokens + Image Tokens" (merged)
  - Output: "Refined Tokens → Triplane"
- Right side (50%): Two zoomed-in mechanism diagrams
  - Top right: "Self-Attention: Token Coordination" — shows all M tokens connected in a complete graph, with annotation "Tokens share information, coordinate which parts each covers" / "Token 之间协调分工"
  - Bottom right: "Cross-Attention: Image Retrieval" — shows tokens (orange) attending to image features (blue grid), with annotation "Tokens retrieve geometric cues from visible regions" / "Token 从可见区域检索几何线索"
- Bottom: "8 blocks. Self-attn for coordination. Cross-attn for geometric retrieval." / "8层解码器：Self-attn 协调，Cross-attn 检索"

Content:
- Block labels: Self-Attn, Cross-Attn, FFN, residual connections
- Right panel annotations
- Bottom summary

Visual Details:
- Background: pure white #FFFFFF
- Decoder blocks: purple #F3E8FF, border #9333EA
- Self-attention graph: dark gray #555555 nodes and edges
- Cross-attention: orange #F97316 tokens → blue #2563EB image grid
- Residual connections: thin curved arrows in light gray #AAAAAA
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- The stacked blocks must be clearly readable (8 distinct layers).
- Self-attn vs Cross-attn difference must be visually obvious.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
