【类型】机制细节图
【风格】paper-figure
【语言】中文
【主题】Occlusion-aware Attention Layer 区分背景和遮挡区域
【画幅】16:9 横版

【视觉结构】
- 左侧：一张目标物体被遮挡的示意图，分成三类区域：可见目标、遮挡物、背景。
- 中间：三个 mask token groups：visible、occluder、background。
- 右侧：3D latent block 中第二个 cross-attention layer，专门读取 occlusion mask。
- 最右：补全后的隐藏几何区域与可见区域自然连接。

【要标注的短文字】
- 可见目标
- 遮挡物
- 背景
- 遮挡感知层
- 推理隐藏部分

【颜色限制】
- 蓝色表示可见目标，橙色表示遮挡物，浅灰表示背景。

【禁止】
- 不要把所有不可见区域都画成同一种颜色。
- 不要漫画人物或对话框。
