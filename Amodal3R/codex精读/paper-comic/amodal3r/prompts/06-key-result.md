【类型】结果对比图
【风格】paper-figure
【语言】中文
【主题】Amodal3R 为什么优于两阶段 pipeline
【画幅】16:9 横版

【视觉结构】
- 左侧：Two-stage pipeline，Occluded input -> 2D completion -> 3D reconstruction，箭头中标出 error propagation 和 multi-view inconsistency。
- 右侧：Amodal3R，Occluded input + masks -> 3D latent reasoning -> complete 3D asset。
- 底部：三个关键指标数字卡片：GSO FID 30.64 vs 58.82；GSO 4-view FID 26.27 vs 60.37；Toys4K FID 23.45 vs 43.05。

【要标注的短文字】
- 两阶段
- 错误传播
- 视角不一致
- 一阶段 3D 补全
- 更低 FID

【颜色限制】
- 左侧用灰色和红色警示，右侧用蓝色和绿色积极高亮。

【禁止】
- 不要生成完整密集表格，只放 3 个大数字。
