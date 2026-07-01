【类型】方法总览图
【风格】paper-figure
【语言】中文
【主题】Amodal3R 输入到输出整体架构
【画幅】16:9 横版

【视觉结构】
- 从左到右 5 个分区：输入、2D 分割、特征与 mask、Amodal3R transformer、3D 输出。
- 输入区：image + point prompts。
- 分割区：SAM-like segmenter 输出 Visible Mask 和 Occlusion Mask。
- 条件区：DINOv2 tokens c_dino、visible weights c_vis、occlusion weights c_occ 三条并行流。
- 模型区：TRELLIS-based 3D diffusion block，内部有 mask-weighted cross-attention 与 occlusion-aware attention 两个高亮模块。
- 输出区：complete 3D asset。

【要标注的短文字】
- 输入图像
- 可见 mask
- 遮挡 mask
- DINOv2
- Mask-weighted attention
- Occlusion-aware layer
- 完整 3D

【颜色限制】
- 白底，深灰线条
- 蓝色高亮可见分支，橙色高亮遮挡分支

【禁止】
- 不要照抄论文 Figure 2；要重新组织，更清晰、更适合传播。
- 不要写长句，标签要短。
