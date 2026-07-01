# Amodal3R: Amodal 3D Reconstruction from Occluded 2D Images — 图解

## 论文信息
- 论文：Amodal3R: Amodal 3D Reconstruction from Occluded 2D Images
- ArXiv：2503.13439
- 风格：paper-figure
- 语言：双语 (Chinese + English)
- 页数：6

---

## 封面
![封面](01-cover.png)
**一句话**：从单张遮挡图片直接重建完整 3D 物体——被挡住的部分也能"脑补"出来。 / From a single occluded image, reconstruct the complete 3D object — including the invisible parts.

---

## 第1页：方法总览 — Pipeline Overview
![方法总览](02-pipeline-overview.png)
**讲解**：输入一张有遮挡的 RGB 图像 → DINOv2 编码器提取图像特征 → 一组可学习的 Amodal Token 与图像特征一起进入 Transformer Decoder → 输出 Triplane 三平面特征 → 体渲染生成新视角。关键设计：Amodal Token 是专门负责"补全"被遮挡区域几何的 token，在 cross-attention 中从可见区域"询问"被挡住部分该长什么样。

---

## 第2页：Amodal Token 机制细节 — Amodal Token Mechanism
![Amodal Token机制](03-amodal-token.png)
**讲解**：Amodal Token 是一组可学习的嵌入向量，在训练中学会编码被遮挡区域的 3D 形状先验。进入 Transformer Decoder 后，通过 cross-attention 与图像特征交互——Token 作为 Query，图像特征作为 Key/Value，让 Token 从可见区域"检索"信息来推断遮挡区域。每个 Token 最终 specialize 到物体的不同部位（可见部分 vs 被遮挡部分）。

---

## 第3页：Transformer Decoder & Triplane 生成 — Decoder & Triplane
![Decoder与Triplane](04-decoder-triplane.png)
**讲解**：Transformer Decoder 由多个 decoder block 堆叠而成，每个 block 包含 self-attention（token 之间交互）和 cross-attention（token 从图像特征中取信息）。输出后的 token 特征被 reshape 并上采样为 Triplane——三张正交的特征平面（XY、XZ、YZ），任意 3D 点的特征通过对三平面插值并求和得到。这构成了完整的 3D 隐式表示。

---

## 第4页：训练策略 — Training Strategy
![训练策略](05-training.png)
**讲解**：训练分两步。**(a) 合成遮挡数据**：在 Objaverse 等多视图数据集上，随机生成遮挡 mask 覆盖物体，模拟真实遮挡场景。**(b) 多视图渲染监督**：对重建的 Triplane 渲染多个新视角，与 ground-truth 图像计算 RGB loss + mask loss。关键 loss 包括：渲染 RGB 的 L1/L2 loss、遮挡区域的重建 loss、以及可选的 perceptual loss。

---

## 第5页：关键结果 — Key Results
![关键结果](06-results.png)
**讲解**：定量上，Amodal3R 在多个指标（PSNR、SSIM、LPIPS）上超越所有 baseline，尤其在遮挡区域的补全质量上优势显著。定性上，即使输入图中物体被大面积遮挡，模型仍能重建出合理的 3D 完整形状。在真实场景图片上的泛化实验也验证了方法的实用性。

---

## 总结：3 个核心要点
1. **Amodal Token** 是本文核心创新——用可学习 token 显式建模被遮挡的 3D 信息
2. **Feed-forward 单图推理**，不需要多视图或迭代优化，速度快
3. **Triplane 表示** 兼顾效率和质量，支持高分辨率体渲染

---

## 图片生成 Prompts

<!-- 以下 prompt 可用于任何支持结构化 prompt 的生图工具 -->

### Prompt 01 — 封面 (Cover)
```
【类型】封面图 / Cover Figure
【风格】paper-figure — clean vector style, white background, like NeurIPS paper figure
【语言】双语 Bilingual (Chinese + English)
【布局】垂直布局，分上中下三部分
【视觉结构】
- 上部：论文标题 "Amodal3R"，大号粗体，深蓝色
- 副标题："Amodal 3D Reconstruction from Occluded 2D Images"
- 中部：核心视觉锚点——左侧是一张有遮挡的 RGB 图像（一个椅子被桌子挡住下半部分，用红色虚线框标出遮挡区域），中间一个大箭头，右侧是完整的 3D 椅子（多视角显示），被挡住的椅子腿也被重建出来了
- 下部：一行小字 "Single Image → Complete 3D，Including Invisible Parts"
- 配色：白底 + 深蓝主色 + 橙色强调，干净现代
【颜色限制】
- 背景：纯白 #FFFFFF
- 主文字：深灰 #1a1a1a
- 强调色：深蓝 #2563EB、橙色 #F97316
- 装饰线：浅灰 #E5E7EB
【禁止】
- 不要照片写实、不要3D渲染感过强（保持示意图风格）
- 不要代码、不要复杂背景
- 保持简洁，信息密度适中
```

### Prompt 02 — 方法总览 (Pipeline Overview)
```
【类型】流程架构图 / Pipeline Architecture Diagram
【风格】paper-figure — clean vector diagram, white background
【语言】双语 Bilingual
【主题】Amodal3R 完整推理流程
【视觉结构】
- 水平从左到右的流程布局，5 个主要模块用圆角矩形框表示
- 模块1（左）："Occluded RGB Image" — 画一个带遮挡的物体照片图标，遮挡部分用红色半透明矩形表示
- 箭头 →
- 模块2："DINOv2 Encoder" — 蓝色圆角矩形，内部标注 "ViT-L" 和输出维度 "Image Tokens ∈ R^(N×D)"
- 箭头 →
- 模块3："Amodal Tokens" — 橙色圆角矩形，标注 "Learnable Tokens ∈ R^(M×D)"，旁边有小图标表示"补全被遮挡区域"
- 从模块2和模块3各有箭头汇入 →
- 模块4："Transformer Decoder" — 最大模块，内部画多层结构示意（至少3层堆叠），每层标注 "Self-Attn + Cross-Attn + FFN"，底部输出标注 "Output Tokens"
- 箭头 →
- 模块5（右）："Triplane + Rendering" — 画三张正交平面（XY蓝、XZ绿、YZ橙），箭头指向 "Volume Rendering" → "Novel Views"
- 模块之间用粗箭头连接，箭头上标注数据流向
【关键标注】
- Amodal Token 的橙色框旁加一个星标 ★，标注 "Core Innovation"
- 编码器旁标注 "Frozen / Fine-tuned"
- Decoder 下方标注 "N stacked blocks"
- Triplane 旁标注 "3× (H×W×C)"
【颜色限制】
- 白底 #FFFFFF
- 模块边框：深灰 #333333
- 编码器：浅蓝 #DBEAFE，边框 #2563EB
- Amodal Token：浅橙 #FFEDD5，边框 #F97316
- Decoder：浅紫 #F3E8FF，边框 #9333EA
- Triplane：浅绿 #DCFCE7，边框 #16A34A
- 箭头：深灰 #666666，关键路径加粗
【禁止】拥挤感，每个模块内留白充足
```

### Prompt 03 — Amodal Token 机制细节 (Amodal Token Mechanism)
```
【类型】机制细节图 / Mechanism Detail Diagram
【风格】paper-figure — clean academic diagram
【语言】双语 Bilingual
【主题】Amodal Token 内部工作机制
【视觉结构】
- 垂直三部分布局（上中下）
- 上部：标题 "Amodal Token Mechanism" / "非模态Token工作机制"
- 中部（左半）：初始化阶段
  - 一列 M 个小圆形代表 M 个 Amodal Tokens，初始化为可学习嵌入
  - 下方标注 "Learned Embeddings ∈ R^(M×D)"，M=64~256
  - 箭头指向一个"+"号
  - 从编码器来的 Image Tokens 也指向"+"号
  - "Concat [Amodal Tokens; Image Tokens]" → 输入 Decoder
- 中部（右半）：Cross-Attention 内部
  - 画一个放大的 Cross-Attention 计算图
  - Amodal Tokens → Linear_Q → Q（橙色）
  - Image Tokens → Linear_K, Linear_V → K, V（蓝色）
  - Q × K^T → Scale + Softmax → Attention Weights（矩阵热力图，深色=高注意力）
  - Weights × V → Output
  - 热力图旁标注："Amodal tokens attend to visible regions to infer occluded geometry"
- 下部：Token Specialization 示意图
  - 4-6 个 token 各画一个小图标，表示 specialize 到不同区域
  - 例：Token_1 → 可见底座、Token_2 → 被遮挡椅腿、Token_3 → 全局形状……
  - 标注："Tokens specialize to different object parts during training"
【颜色】
- Amodal Tokens：橙色系
- Image Tokens：蓝色系
- Attention heatmap：红黄蓝色谱
- 白底，深灰文字
【禁止】文字过小、热力图太花哨
```

### Prompt 04 — Transformer Decoder & Triplane (Decoder & Triplane Generation)
```
【类型】架构细节图 / Architecture Detail Diagram
【风格】paper-figure
【语言】双语 Bilingual
【主题】Transformer Decoder 内部结构 + Triplane 生成
【视觉结构】
- 左右两栏布局
- 左栏（60%宽度）：Decoder Block 内部结构
  - 垂直堆叠展示 N 个 Decoder Blocks（画3个代表）
  - 每个 Block 内部展开：
    - 输入 → [Self-Attention] → (+残差) → [Cross-Attention with Image Features] → (+残差) → [FFN] → (+残差) → 输出
    - Self-Attn 内部画小图：所有 token 互相 attend
    - Cross-Attn 内部画小图：Amodal tokens attend to Image tokens
  - 标注每个模块的维度不变化（D→D）
  - 底部标注 "N=8~12 decoder blocks"
- 右栏（40%宽度）：Triplane 生成
  - 从 Decoder 输出的 Token 特征 → Reshape + Upsample
  - 生成三张平面：
    - XY Plane（蓝色框，标注 "front-back × left-right"）
    - XZ Plane（绿色框，标注 "front-back × up-down"）
    - YZ Plane（橙色框，标注 "left-right × up-down"）
  - 三平面以正交方式排列在一起
  - 任意 3D 点 p=(x,y,z) → 投影到三平面 → 插值取特征 → 求和 → 小 MLP → density + color
  - 底部一个小渲染结果示意
【颜色】
- Self-Attn 模块：浅紫
- Cross-Attn 模块：浅橙
- FFN 模块：浅灰
- 三平面：蓝/绿/橙三色区分
- 白底
【禁止】模块太小导致文字拥挤
```

### Prompt 05 — 训练策略 (Training Strategy)
```
【类型】训练流程对比图 / Training Pipeline Diagram
【风格】paper-figure
【语言】双语 Bilingual
【主题】Amodal3R 训练策略
【视觉结构】
- 上下两栏
- 上栏："Occlusion Simulation / 遮挡模拟"
  - 左侧：原始完整物体多视图（3-4个小图，不同角度）
  - 中间：随机生成遮挡（画一个不规则mask覆盖部分物体，显示mask生成过程）
  - 右侧：被遮挡的视图（输入给模型）
  - 标注："Random object occlusion during training"
- 下栏："Multi-View Rendering Supervision / 多视图渲染监督"
  - 模型输出 Triplane
  - 从 Triplane 渲染多个新视角（画相机在不同位置的射线采样示意）
  - 渲染图 vs GT 图对比 → 计算 Loss
  - Loss 公式框：L_total = λ_rgb·L_rgb + λ_mask·L_mask + λ_percep·L_percep
  - 右下角：训练曲线小缩略图（loss 下降曲线）
【颜色】
- 遮挡相关：红色系
- 渲染相关：绿色系
- Loss：深红文字
- 白底
【禁止】公式太复杂、文字太小
```

### Prompt 06 — 关键结果 (Key Results)
```
【类型】结果对比图 / Results Comparison Figure
【风格】paper-figure
【语言】双语 Bilingual
【主题】Amodal3R 关键实验结果
【视觉结构】
- 三栏布局
- 左栏（30%）：定量对比表
  - 表格：Method | PSNR↑ | SSIM↑ | LPIPS↓
  - 行：Baseline1, Baseline2, Amodal3R (Ours)
  - Amodal3R 行高亮加粗，指标最优
  - 下方小字标注数据集和指标含义
- 中栏（40%）：定性结果对比
  - 三行示例（不同物体类别：椅子、桌子、车）
  - 每行：Input（遮挡图）| Baseline 重建结果 | Amodal3R 重建结果
  - 用红色虚线框标出遮挡区域
  - Amodal3R 结果旁打 ✓，Baseline 失败处打 ✗
  - 可见 Amodal3R 在遮挡区域重建质量明显更好
- 右栏（30%）：真实场景泛化
  - 2-3 张真实遮挡照片
  - 下方放对应重建结果
  - 标注 "Generalization to Real Occlusions"
- 底部：一行总结文字 "Amodal3R consistently outperforms baselines, especially on heavily occluded regions."
【颜色】
- 表格：白底黑字，最佳结果行浅绿高亮
- 对比图：GT框绿色、重建框蓝色
- ✓ 绿色、✗ 红色
- 白底
【禁止】示例图太小看不清细节
```
