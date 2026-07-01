---
slide: 11
title: "Qualitative Comparison — 定性对比"
role: evidence
style_preset: "journal-minimal"
language: "bilingual"
aspect_ratio: "16:9"
output: "images/11-slide-qualitative.md"
---

Create one complete 16:9 presentation slide image.

Purpose:
Show detailed qualitative comparisons across diverse object categories — even under heavy occlusion, Amodal3R recovers complete 3D structure.

Style:
Nature / IEEE-inspired minimal academic presentation slide, publication-quality scientific figure aesthetic, clean white background, precise visual comparison layout, clear restrained scientific color palette.

Composition:
- Top: Title "Qualitative Comparison / 定性对比"
- Main area: A 4×3 grid (4 rows, 3 columns) showing diverse examples
  - Column headers: "Occluded Input" | "Baseline" | "Amodal3R (Ours)"
  - Row 1: Chair (heavily occluded by table)
  - Row 2: Sofa (partially hidden by wall)
  - Row 3: Car (occluded by tree)
  - Row 4: Table (occluded by chair)
  - Each cell: small but clear illustration
    - Input column: object with red occlusion overlay and dashed outline marking hidden region
    - Baseline column: incomplete 3D output with visible missing parts, red ✗ badge
    - Amodal3R column: complete 3D output with orange-highlighted recovered regions, green ✓ badge
  - The visual difference between Baseline and Amodal3R should be immediately obvious
- Bottom: "Even under heavy occlusion, Amodal3R recovers complete and plausible 3D structure" / "即使严重遮挡，Amodal3R 仍能恢复完整合理的 3D 结构"

Content:
- Column headers
- Row labels (object categories)
- ✓/✗ badges
- Bottom summary

Visual Details:
- Background: pure white #FFFFFF
- Grid lines: subtle light gray #E5E7EB
- Red occlusion overlay: #FEE2E2 with #EF4444 dashed border
- Green checkmark: #16A34A, Red cross: #EF4444
- Recovered geometry: orange #F97316 shading
- Each comparison cell: clean 2D schematic rendering, not photorealistic
- Clean sans-serif typography

Constraints:
- The output must be a polished 16:9 slide.
- The 4×3 grid must be well-proportioned, each cell clearly visible.
- The difference between Baseline (broken) and Ours (complete) must be obvious at a glance.
- No page numbers, logos, watermarks.
- No fake UI or AI robot imagery.
