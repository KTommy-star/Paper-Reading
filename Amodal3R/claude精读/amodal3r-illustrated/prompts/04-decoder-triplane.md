Nature / IEEE-inspired minimal academic figure, publication-quality clean white background, precise architecture diagram.

Create a two-column diagram showing Transformer Decoder internals and Triplane generation.

Layout:
- Top title: "Transformer Decoder & Triplane Generation / 解码器与三平面生成" (bilingual)

- Left column (60% width): Decoder Block structure
  Vertical stack of 3 representative decoder blocks (labeled Block 1, 2, ...8)
  Each block expanded: Input → [Self-Attention] → +residual → [Cross-Attention] → +residual → [FFN] → +residual → Output
  Self-Attn: complete graph of tokens interacting (labeled "Token Coordination")
  Cross-Attn: tokens attending to image features grid (labeled "Geometric Retrieval")
  Bottom annotation: "8× DETR-style Decoder Blocks, D=256"

- Right column (40% width): Triplane Generation
  Output tokens → Reshape + Upsample
  Three orthogonal planes in isometric view:
  XY plane (blue tint, "front-back × left-right")
  XZ plane (green tint, "front-back × up-down")
  YZ plane (orange tint, "left-right × up-down")
  Query point p=(x,y,z) → project to each plane → bilinear interpolation → sum features → MLP → (σ, RGB)
  Small rendering result inset at bottom right

Colors: white BG, decoder blocks purple #F3E8FF/#9333EA, self-attn gray, cross-attn orange/blue, triplane XY blue #DBEAFE, XZ green #DCFCE7, YZ orange #FFEDD5. Clean sans-serif. No logos, no watermarks.
