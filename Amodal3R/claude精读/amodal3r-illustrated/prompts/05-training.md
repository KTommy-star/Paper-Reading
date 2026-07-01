Nature / IEEE-inspired minimal academic figure, publication-quality clean white background, precise training pipeline diagram.

Create a two-stage training strategy diagram.

Layout:
- Top title: "Training Strategy / 训练策略" (bilingual)

- Upper section "Stage 1: Occlusion Simulation":
  Left: Complete 3D object from Objaverse (3 small multi-view thumbnails)
  Center: Random occlusion mask generation — several random mask shapes (blobs, rectangles) overlaying on the object
  Right: Occluded training input — object with mask applied
  Annotation: "Random object occlusion during training. Model never sees real occlusions."

- Lower section "Stage 2: Multi-View Rendering Loss":
  Center: Triplane output → 4-6 camera icons around it → rendered views
  Rendered views compared to ground truth, loss arrows connecting them
  Highlighted loss formula box: "L_total = L_rgb + λ_mask·L_mask + λ_percep·L_LPIPS"
  Bottom right: small training curve inset (loss decreasing over epochs)

- Bottom: "Trained on synthetic occlusions only. Zero-shot generalizes to real occluded images." / "仅合成遮挡训练，零样本泛化到真实场景"

Colors: white BG, Stage 1 elements red-tinted #FEE2E2, Stage 2 elements green-tinted #DCFCE7, loss box light yellow #FEF9C3, dark text. Clean sans-serif. No logos, no watermarks, no 3D renders.
