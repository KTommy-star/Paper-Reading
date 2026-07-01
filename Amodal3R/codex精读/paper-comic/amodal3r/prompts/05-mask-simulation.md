【类型】数据流程图
【风格】paper-figure
【语言】中文
【主题】Amodal3R 的遮挡模拟与多视角一致 mask
【画幅】16:9 横版

【视觉结构】
- 左半部分：训练阶段随机 2D 遮挡，展示线条、椭圆、矩形叠加到渲染图上。
- 右半部分：评估阶段 3D-consistent mask，展示 mesh triangle random-walk 选中连续区域，再渲染成多个视角一致遮挡。
- 中间用分隔线标注 Training vs Evaluation。

【要标注的短文字】
- 随机 2D 遮挡
- 线 / 椭圆 / 矩形
- 3D 一致遮挡
- mesh random-walk
- 多视角一致

【颜色限制】
- 白底，训练侧用蓝色，评估侧用青绿 + 橙色。

【禁止】
- 不要复杂真实渲染，使用清晰矢量感图解。
