# Amodal3R - paper-deck 幻灯片方案

## 当前状态

- 论文已下载并完成内容解析。
- `paper-deck` 按规则不能直接跳过确认生成 PPT，因为它需要确认页数、风格、用途，以及是否允许从 PDF 截取真实论文图表。
- 当前文件是生成前的 deck plan。你确认后，我会继续创建 `analysis.md`、`deck-brief.md`、`outline.md`、逐页 prompts，然后调用生图后端生成 slide images，并合成 `.pptx` 与 `.pdf`。

## 推荐配置

- 用途：组会 / reading group / 技术分享
- 页数：10 页
- 语言：中文
- 风格：`journal-minimal`
- 真实素材：建议允许使用 PDF 中的 Figure 2、Figure 3、Table 1、Table 3 局部截图，作为证据和方法图支撑。

## 为什么推荐 journal-minimal

这篇论文是典型 3D vision 方法文，核心是模型结构和实验对比。`journal-minimal` 可以保留论文图的可信感，同时把机制拆得比原图更清楚。`warm-notes` 更像学习笔记，适合轻松讲解；`liquid-glass` 更适合发布会式视觉，但机制页容易牺牲精确度。

## 10 页大纲

### 01. Cover
- Role: cover
- Message: Amodal3R reconstructs complete 3D assets from occluded 2D images.
- Visual: 被遮挡 2D 输入到完整 3D asset 的强视觉对比。
- Source visual: 可使用 Figure 1 的结果局部作为视觉锚点。

### 02. Problem
- Role: context
- Message: 真实场景中目标物体经常被遮挡，普通 image-to-3D 模型默认物体完整可见。
- Visual: 完整可见输入 vs 遮挡输入，两条路径输出差异。

### 03. Why two-stage fails
- Role: motivation
- Message: 2D amodal completion 缺少 3D 几何理解，多视角时还会互相不一致。
- Visual: `2D completion -> 3D reconstruction` pipeline，被红色标注指出错误传播。

### 04. Method overview
- Role: method
- Message: Amodal3R 直接把 visible mask 与 occlusion mask 注入 3D generator。
- Visual: 重新设计的 Figure 2 风格方法总览。
- Source visual: Figure 2 可作为参考或局部真实素材。

### 05. Mask-weighted cross-attention
- Role: mechanism
- Message: 可见区域越多的 patch，在 cross-attention 中权重越高。
- Visual: patch grid + attention heatmap + 公式 callout。
- Evidence: 公式 (2), (3)。

### 06. Occlusion-aware attention
- Role: mechanism
- Message: occlusion mask 告诉模型哪些不可见区域可能需要补全，而不是把所有不可见都当背景。
- Visual: background / visible / occluder 三类区域的分解。

### 07. Training and mask simulation
- Role: method
- Message: synthetic 3D assets + random 2D masks + 3D-consistent masks 支撑训练和评估。
- Visual: 随机遮挡生成流程，mesh triangle random-walk 生成多视角一致 mask。

### 08. Quantitative evidence
- Role: evidence
- Message: Amodal3R 在 GSO 和 Toys4K 上显著优于两阶段 baseline。
- Visual: 只突出 3 个关键数字：GSO FID 30.64 vs TRELLIS 58.82，GSO multi-view FID 26.27 vs 60.37，Toys4K FID 23.45 vs 43.05。
- Source visual: Table 1 / Table 2 可裁切或重新排版为证据面板。

### 09. Ablation
- Role: evidence
- Message: mask-weighted attention 管可靠视觉读取，occlusion-aware layer 管隐藏几何推理，二者互补。
- Visual: 四列对比：naive / only Mvis / only Mocc / full model。
- Source visual: Figure 7 或 Table 3。

### 10. Takeaway and limitations
- Role: takeaway
- Message: 遮挡不是图像缺口，而是 3D 生成条件；但方法仍受 synthetic data、mask 质量和补全不可控限制。
- Visual: 左侧 3 个 takeaways，右侧 3 个 limitations。

## 需要你确认

1. 页数和用途：是否按 10 页组会版来做？
2. 风格：`journal-minimal` / `warm-notes` / `business-research` / `liquid-glass`
3. 是否允许我从 PDF 中截取真实论文图表作为素材？

我的默认推荐：10 页，中文，`journal-minimal`，允许使用论文 Figure/Table 局部截图。
