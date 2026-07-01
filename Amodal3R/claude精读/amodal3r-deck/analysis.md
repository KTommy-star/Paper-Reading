# Amodal3R — Paper Deck Analysis

## 论文信息
- 标题：Amodal3R: Amodal 3D Reconstruction from Occluded 2D Images
- ArXiv：2503.13439
- 类型：3D Computer Vision, Amodal Reconstruction

## 1 句话主张
从单张遮挡图片直接推理完整 3D 物体——用可学习的 Amodal Token 显式建模被遮挡区域的几何补全。

## 3-5 个核心点
1. **问题**：遮挡是真实场景中 3D 理解的本质难题，传统方法需要多视图或完整标注
2. **Amodal Token**：核心创新——一组可学习 token，通过 cross-attention 从可见区域推理被遮挡的 3D 几何
3. **Feed-forward 架构**：单图输入 → DINOv2 编码 → Transformer Decoder → Triplane → 体渲染，无需迭代
4. **训练**：合成遮挡 + 多视图渲染监督，泛化到真实遮挡场景
5. **结果**：在遮挡区域重建质量上大幅超越 baseline

## 推荐
- 页数：14 页
- 风格：journal-minimal（学术汇报，像 Nature/IEEE 论文图）
- 语言：双语（中英文双语标注）
- 用途：组会汇报 + 个人理解
- 真实素材：第 5 页插入论文方法架构截图，第 10 页插入实验结果表/图
