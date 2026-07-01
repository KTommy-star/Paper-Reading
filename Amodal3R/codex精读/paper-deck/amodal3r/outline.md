# Amodal3R - 10 Page Deck Outline

## 01. Amodal3R
- Role: cover
- Message: 从遮挡 2D 图像直接恢复完整 3D 资产。
- Visual: 被遮挡输入、3D latent reasoning、完整 3D asset 三段式。
- Text: Amodal3R / 遮挡输入到完整 3D
- Evidence: Figure 1 concept.
- Source visual: None; generated as original slide visual.
- Repair handle: cover visual triptych.

## 02. 问题在哪里
- Role: problem
- Message: 真实世界物体常被遮挡，而普通 image-to-3D 默认目标完整可见。
- Visual: 完整可见输入 vs 遮挡输入，输出分别稳定与破碎。
- Text: 遮挡是常态 / 普通重建会缺失
- Evidence: Introduction motivation.
- Source visual: None.
- Repair handle: two-column problem comparison.

## 03. 两阶段为何失败
- Role: motivation
- Message: 2D amodal completion 的错误会传播到 3D，多视角还会不一致。
- Visual: Two-stage pipeline with red error arrows.
- Text: 2D 补全 / 错误传播 / 视角不一致
- Evidence: Sec. 1 and Sec. 4.2.
- Source visual: None.
- Repair handle: pipeline failure slide.

## 04. 方法总览
- Role: method-overview
- Message: Amodal3R 把 visible mask 和 occlusion mask 直接注入 3D generator。
- Visual: Input image + masks + DINOv2 + two attention modules + 3D asset.
- Text: 可见 mask / 遮挡 mask / 3D 生成
- Evidence: Figure 2.
- Source visual: Figure 2 concept, remixed.
- Repair handle: main architecture slide.

## 05. 可见区域注意力
- Role: mechanism-detail
- Message: visible mask 调制 cross-attention，让模型读取可靠图像区域。
- Visual: patch grid, c_vis vector, attention heatmap, short formula.
- Text: 可见权重 / 可靠特征
- Evidence: Eq. (2), Eq. (3).
- Source visual: None.
- Repair handle: mask-weighted attention slide.

## 06. 遮挡感知层
- Role: mechanism-detail
- Message: occlusion mask 区分背景与遮挡物，指导隐藏几何补全。
- Visual: three-region mask and second cross-attention block.
- Text: 背景 / 遮挡物 / 隐藏部分
- Evidence: Sec. 3.2.
- Source visual: None.
- Repair handle: occlusion-aware attention slide.

## 07. 数据与遮挡模拟
- Role: method
- Message: synthetic 3D data 加随机遮挡支撑训练，3D-consistent masks 支撑多视角评估。
- Visual: random 2D masks and mesh random-walk masks.
- Text: 随机遮挡 / 3D 一致遮挡
- Evidence: Sec. 3.3 and Appendix A.
- Source visual: Figure 4 concept.
- Repair handle: data simulation slide.

## 08. 关键实验
- Role: evidence
- Message: Amodal3R 在 GSO 和 Toys4K 显著优于两阶段 baseline。
- Visual: three large metric cards with exact FID comparisons.
- Text: GSO / Toys4K / FID 更低
- Evidence: Table 1 and Table 2.
- Source visual: Table values remixed as metric cards.
- Repair handle: quantitative evidence slide.

## 09. 消融说明什么
- Role: evidence
- Message: mask-weighted attention 与 occlusion-aware layer 互补。
- Visual: four-column ablation comparison.
- Text: naive / only Mvis / only Mocc / full
- Evidence: Table 3 and Figure 7.
- Source visual: Table 3 concept.
- Repair handle: ablation slide.

## 10. 结论与局限
- Role: takeaway
- Message: 遮挡不是图像缺口，而是 3D 生成条件；但方法仍受数据、mask 和可控性限制。
- Visual: left takeaways, right limitations.
- Text: 核心结论 / 局限
- Evidence: Conclusion and Appendix C.6.
- Source visual: None.
- Repair handle: takeaway slide.
