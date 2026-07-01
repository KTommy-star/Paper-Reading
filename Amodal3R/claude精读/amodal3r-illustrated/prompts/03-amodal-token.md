Nature / IEEE-inspired minimal academic figure, publication-quality clean white background, precise mechanism diagram.

Create a detailed mechanism diagram for Amodal Token's internal workings.

Layout (two-panel vertical):
- Top title: "Amodal Token Mechanism / 非模态Token机制" (bilingual)

- Upper panel (Cross-Attention computation):
  Left: M amodal tokens shown as orange circles (T1...TM) → Linear_Q → Query Q (orange matrix)
  Right: N image tokens shown as blue squares (I1...IN) → Linear_K, Linear_V → Key K (blue), Value V (blue)
  Center: Q × K^T → Scale 1/√d → Softmax → Attention Weights (heatmap matrix M×N, red=high attention)
  Output: Weights × V → Updated Tokens (orange circles with brighter fill)

- Lower panel (Token Specialization):
  6 small heatmap overlays on a schematic occluded object silhouette
  Each token specializes: "visible base", "occlusion edge", "global shape", "texture", "hidden parts", "scene context"
  Labels in English with small Chinese subtitles

Colors: white BG, Amodal tokens orange #F97316/#FFEDD5, Image features blue #2563EB/#DBEAFE, heatmap yellow→orange→red gradient. Clean sans-serif. No logos, no watermarks, no 3D renders.
