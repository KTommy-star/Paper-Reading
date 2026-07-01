# Amodal3R - Paper Deck Analysis

## 主题与受众

- 主题：Amodal3R 如何从遮挡 2D 图像直接重建完整 3D 资产。
- 受众：计算机视觉方向组会、reading group、3D generation 研究者。
- 场景：10 页中文技术汇报，目标是在 8-12 分钟内讲清楚问题、方法、关键机制和实验结论。

## 一句话主张

Amodal3R 把遮挡补全从 2D amodal completion pipeline 改写为 3D latent space 中的条件生成问题，通过 visible mask 和 occlusion mask 引导 TRELLIS-based diffusion model 直接恢复完整 3D geometry 与 appearance。

## 必须讲清楚的核心点

1. 两阶段 `2D completion -> 3D reconstruction` 的根本问题是 2D 补全缺少 3D 几何约束，多视角时还会不一致。
2. Amodal3R 基于 TRELLIS，在每个 transformer block 中加入 mask-weighted cross-attention 和 occlusion-aware attention。
3. `M_vis` 与 `M_occ` 的作用不同：前者约束从哪里读取可靠图像特征，后者指明哪里是被遮挡但可能需要补全的区域。
4. 训练使用 synthetic 3D assets 与随机遮挡，评估包含 GSO、Toys4K、Replica 和 in-the-wild images。
5. 关键实验显示 Amodal3R 在渲染质量、语义一致性和 3D 几何指标上均显著优于两阶段 baseline。

## 推荐页数与风格

- 推荐页数：10
- 风格：journal-minimal
- 语言：中文
- 真实素材：允许使用论文 Figure/Table 局部截图，但本轮先以生图重绘式 slide 为主，避免直接复刻论文图。
