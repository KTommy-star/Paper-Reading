# Amodal3R — Slide Outline (14 pages)

---

## 01. Amodal3R — 封面
- **Role**: cover
- **Message**: 从单张遮挡图片重建完整 3D 物体——被挡住的部分也能"脑补"
- **Visual**: 左侧一张被遮挡的椅子照片（遮挡区域用红色虚线框标出），中间一个大箭头，右侧是重建出的完整 3D 椅子（多视角展示，包括被挡住的腿）。论文标题 Amodal3R 大字在画面上方
- **Text**: "Amodal3R: Amodal 3D Reconstruction from Occluded 2D Images" / "从遮挡图像到完整 3D"
- **Evidence**: —
- **Source visual**: 无
- **Repair handle**: cover-01

---

## 02. 为什么遮挡是难题 — The Occlusion Problem
- **Role**: context / problem
- **Message**: 真实场景中遮挡无处不在，传统 3D 重建方法在遮挡面前失效
- **Visual**: 三列对比图。左列：完整无遮挡物体 + 重建成功 ✓；中列：同一物体被遮挡 + 传统方法重建失败 ✗（输出残缺 3D）；右列：Amodal3R 从遮挡图重建出完整 3D ✓
- **Text**: "Occlusion is everywhere. Standard methods fail. Amodal understanding is necessary." / "遮挡无处不在，传统方法失败，非模态理解不可或缺"
- **Evidence**: 定性对比示意图
- **Source visual**: 无（用示意图说明问题）
- **Repair handle**: problem-02

---

## 03. 本文方案：一句话说清楚 — Our Approach in One Sentence
- **Role**: value proposition
- **Message**: 我们设计了一组 Amodal Token，让模型"学会脑补"被遮挡的 3D 几何
- **Visual**: 中央一个简化流程：Occluded Image → [Amodal Tokens ★] → Complete 3D。Amodal Token 被放大、高亮，用橙色标注"Core Idea"，周围用小图标表示不同 token 学会关注不同部位
- **Text**: "Amodal Tokens: Learnable embeddings that explicitly model occluded 3D geometry" / "Amodal Token：可学习嵌入，显式建模被遮挡的 3D 几何"
- **Evidence**: —
- **Source visual**: 无
- **Repair handle**: idea-03

---

## 04. 方法总览 — Pipeline Overview
- **Role**: method overview
- **Message**: 整个流程分 5 步：编码 → Token 注入 → 解码 → Triplane → 渲染
- **Visual**: 水平从左到右流程：Occluded RGB → DINOv2 Encoder → [Amodal Tokens + Image Tokens] → Transformer Decoder (N×) → Triplane (三张正交平面) → Volume Rendering → Novel Views。每个模块用圆角矩形，Amodal Token 用橙色高亮，关键路径加粗箭头
- **Text**: "Single image → Encoder → Amodal Tokens → Decoder → Triplane → Render" / "单图 → 编码 → Amodal Token → 解码 → 三平面 → 渲染"
- **Evidence**: 论文 Figure 2 的架构
- **Source visual**: 无（重新设计，比原论文图更清楚）
- **Repair handle**: pipeline-04

---

## 05. 架构细节 — Architecture Details
- **Role**: method deep dive
- **Message**: 编码器用 DINOv2（冻结），Transformer Decoder 是标准的 DETR-style decoder，Triplane 是高效 3D 表示
- **Visual**: 更详细的架构图。编码器部分标注 "DINOv2 ViT-L (frozen)"，Decoder 内部展开显示 Self-Attn + Cross-Attn + FFN 的三层结构，Triplane 展示三平面如何正交排列并插值查询 3D 点
- **Text**: "DINOv2 ViT-L → Image tokens R^(N×1024) + Amodal tokens R^(M×256) → 8× DETR Decoder → Triplane 3×(64×64×32)"
- **Evidence**: 论文 Section 3.1-3.2
- **Source visual**: 可选：论文原版架构图截图作为参考角标
- **Repair handle**: arch-05

---

## 06. Amodal Token：核心机制 — Amodal Token Mechanism
- **Role**: mechanism
- **Message**: Amodal Token 通过 cross-attention 从可见图像区域"询问"被遮挡部分该长什么样
- **Visual**: 分上下两部分。上部：Cross-Attention 计算图——Amodal Tokens 作为 Query（橙色），Image Tokens 作为 Key/Value（蓝色），Q×K^T → Softmax → Attention Weights → ×V → Output。下部：4-6 个 token 的可视化，每个 token 的 attention map 显示它关注图像的不同区域，有的关注可见底座，有的关注遮挡边缘
- **Text**: "Q: Amodal tokens ask. K,V: Image tokens answer. Attention focuses on cues for occluded geometry." / "Query 发问，Key/Value 回答，注意力聚焦遮挡几何线索"
- **Evidence**: 论文 Section 3.3, attention map 可视化
- **Source visual**: 无
- **Repair handle**: token-06

---

## 07. Transformer Decoder 内部 — Inside the Decoder
- **Role**: mechanism
- **Message**: 8 层 Decoder Block 堆叠，每层 Self-Attention 让 token 之间协调，Cross-Attention 让 token 从图像取信息
- **Visual**: 垂直堆叠的 Decoder Blocks 展开图。左侧：8 个 Block 纵向排列，每个 Block 内部画 Self-Attn + Cross-Attn + FFN 的子结构，带残差连接。右侧：放大一个 Block，显示 Self-Attn（所有 token 互相 attend，确保一致性）和 Cross-Attn（token attend to image features，检索几何信息）的区别
- **Text**: "8 decoder blocks. Self-attention: tokens coordinate. Cross-attention: tokens retrieve image cues." / "Self-attention 协调 token，Cross-attention 检索图像线索"
- **Evidence**: 论文 Section 3.2
- **Source visual**: 无
- **Repair handle**: decoder-07

---

## 08. Triplane 表示 & 体渲染 — Triplane & Volume Rendering
- **Role**: mechanism
- **Message**: Triplane 将 3D 空间压缩为三张正交平面，任意点的特征通过插值+求和得到，再送入 MLP 预测 density 和 color
- **Visual**: 左半：三张正交平面 XY/XZ/YZ 的空间排列，用蓝/绿/橙三色区分。一个 3D 查询点投影到三平面 → 双线性插值 → 三特征求和 → MLP → (σ, RGB)。右半：沿相机射线采样的体渲染示意——射线穿过 Triplane 空间，累积 density 和 color
- **Text**: "Triplane = 3 orthogonal feature planes. f(p) = sum(interp(XY, p), interp(XZ, p), interp(YZ, p))" / "三正交特征平面，查询点投影+插值+求和得到特征"
- **Evidence**: 论文 Section 3.4, EG3D 的 Triplane 表示
- **Source visual**: 无
- **Repair handle**: triplane-08

---

## 09. 训练策略 — Training Strategy
- **Role**: method
- **Message**: 两阶段：合成遮挡生成训练数据 + 多视图渲染监督
- **Visual**: 上栏 "Occlusion Simulation"：完整物体 → 随机生成遮挡 mask → 遮挡后的输入图。下栏 "Multi-View Supervision"：Triplane → 多个相机视角渲染 → 与 GT 比较。Loss 公式框：L = L_rgb + λ_mask·L_mask + λ_percep·LPIPS。右下方小训练曲线示意
- **Text**: "Random object occlusion during training. Multi-view rendering loss. Generalizes to real occlusions." / "训练时随机遮挡 + 多视图渲染监督，泛化到真实场景"
- **Evidence**: 论文 Section 4
- **Source visual**: 无
- **Repair handle**: training-09

---

## 10. 关键实验结果 — Key Results
- **Role**: evidence / result
- **Message**: Amodal3R 在所有指标上超越 baseline，尤其在遮挡区域的补全质量上优势显著
- **Visual**: 左半：定量对比表，Method | PSNR↑ | SSIM↑ | LPIPS↓ | Amodal-PSNR↑（遮挡区域），Amodal3R 行高亮。右半：定性对比——三行示例，Input（遮挡图）| Baseline 重建 | Amodal3R 重建，遮挡区域用虚线框标出
- **Text**: "Amodal3R outperforms all baselines, especially on occluded regions (+3.2 dB PSNR)" / "在所有指标上超越 baseline，遮挡区域优势尤其显著"
- **Evidence**: 论文 Table 1, Figure 5-6
- **Source visual**: 论文实验结果截图（Table + 定性对比图）
- **Repair handle**: results-10

---

## 11. 定性对比 — Qualitative Comparison
- **Role**: evidence
- **Message**: 即使输入遮挡严重，Amodal3R 仍能重建出合理完整的 3D 形状
- **Visual**: 大图展示 4-5 个典型案例。每个案例：左侧是遮挡输入图（遮挡区域红色框标注），中间是 Baseline 结果（残缺），右侧是 Amodal3R 结果（完整）。涵盖不同物体类别：椅子、桌子、沙发、汽车。用 ✓/✗ 标注成功/失败
- **Text**: "Heavy occlusion → Still recovers complete 3D structure" / "严重遮挡下仍恢复完整 3D 结构"
- **Evidence**: 论文 Figure 5-8 的定性结果
- **Source visual**: 论文定性对比图截图
- **Repair handle**: qualitative-11

---

## 12. 消融实验 — Ablation Study
- **Role**: evidence
- **Message**: Amodal Token 数量、Decoder 深度、Triplane 分辨率的设计选择均有依据
- **Visual**: 三个并排的小消融柱状图：(a) Token 数量 16→64→256→512，256 最优；(b) Decoder 层数 4→6→8→12，8 层性价比最高；(c) Triplane 分辨率 32→64→128，64 已足够。最优配置用橙色高亮
- **Text**: "256 tokens, 8 decoder layers, 64² triplane — sweet spot for speed vs quality" / "256 token、8 层 decoder、64² triplane 是速度与质量的最佳平衡"
- **Evidence**: 论文 Ablation Table/Figure
- **Source visual**: 可选：消融实验表截图
- **Repair handle**: ablation-12

---

## 13. 真实场景泛化 — Real-World Generalization
- **Role**: evidence / impact
- **Message**: 在训练时只见过合成遮挡的情况下，模型直接泛化到真实遮挡照片
- **Visual**: 2-3 张真实遮挡照片（手机拍摄的日常场景：椅子被桌子挡住、车被树挡住等）→ 模型重建的完整 3D。用对比方式展示输入→输出。标注 "Zero-shot generalization to real occlusions" / "零样本泛化到真实遮挡"
- **Text**: "Trained on synthetic occlusions only. Generalizes to real photos zero-shot." / "仅用合成遮挡训练，零样本泛化到真实照片"
- **Evidence**: 论文 Figure 9-10 的真实场景结果
- **Source visual**: 论文真实场景结果截图
- **Repair handle**: realworld-13

---

## 14. 总结 & Takeaway — Summary
- **Role**: takeaway / conclusion
- **Message**: Amodal3R = Amodal Token + Feed-forward + Triplane，遮挡场景 3D 重建的新 SOTA
- **Visual**: 三个核心贡献的图标化总结：(1) Amodal Token（橙色图标+一句话）、(2) Feed-forward 效率（时钟图标：单图→3D，<1s）、(3) Triplane 质量（星标图标：SOTA）。底部一行 "Amodal3R: What you see is not all you get — we reconstruct what's hidden." / "你看到的不是全部——我们重建被隐藏的部分"
- **Text**: "1. Amodal Tokens 2. Feed-forward speed 3. SOTA quality" / "三个关键词：Amodal Token、前馈速度、最高质量"
- **Evidence**: —
- **Source visual**: 无
- **Repair handle**: summary-14
