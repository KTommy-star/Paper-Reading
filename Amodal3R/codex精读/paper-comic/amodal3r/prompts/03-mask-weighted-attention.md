【类型】机制细节图
【风格】paper-figure
【语言】中文
【主题】Mask-weighted Cross-Attention 如何让模型关注可见区域
【画幅】16:9 横版

【视觉结构】
- 左侧：DINO patch grid，部分 patch 是目标可见区域，部分是遮挡/背景。
- 中间：visible ratio c_vis 形成一条权重向量，用蓝色深浅表示权重大小。
- 右侧：attention heatmap，低可见 patch 权重被压低，可见 patch 权重被增强。
- 底部：简短公式 callout，用清晰排版展示 A_ij proportional to c_vis,j exp(S_ij)。

【要标注的短文字】
- 图像 patch
- 可见权重
- 注意力重加权
- 忽略遮挡
- 读取可靠特征

【颜色限制】
- 白底，蓝色 heatmap，少量橙色用于被遮挡 patch。

【禁止】
- 不要长公式推导，不要密密麻麻矩阵。
- 不要生成假论文截图。
