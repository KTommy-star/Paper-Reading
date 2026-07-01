# Amodal3R - paper-comic 图解推荐方案

## 论文信息

- 论文：Amodal3R: Amodal 3D Reconstruction from Occluded 2D Images
- 本地 PDF：`/Users/kongsanjin/Desktop/Paper-Reading/Amodal3R_2503.13439.pdf`
- 当前状态：已完成论文阅读和图解内容拆分，等待你确认后再生成图片。

## 我建议生成 6 张图

1. 封面图：一句话贡献 + 视觉锚点
   - 表达：从被遮挡的 2D 图像直接恢复完整 3D 资产。
   - 画面：左侧是被遮挡物体，右侧是完整 3D asset，中间用“3D latent reasoning”连接。

2. 方法总览图：Amodal3R 输入到输出
   - 表达：输入图像 + point prompts，经 2D segmenter 得到 visible mask 和 occlusion mask，再进入 TRELLIS-based 3D generator。
   - 必须画清楚：`c_dino`、`c_vis`、`c_occ` 三条条件分支如何进入模型。

3. 核心机制 A：Mask-weighted Cross-Attention
   - 表达：让模型只从目标可见区域读取可靠图像特征。
   - 画面：DINO patch tokens 上叠加 visible ratio，attention heatmap 中遮挡和背景 patch 权重被压低。
   - 关键公式：`A_ij = c_vis,j exp(S_ij) / sum_k c_vis,k exp(S_ik)`。

4. 核心机制 B：Occlusion-aware Attention Layer
   - 表达：区分“背景空白”和“被遮挡但可能存在目标”的区域。
   - 画面：一个不可见区域被拆成 background 与 occluder，两条路径对应不同补全逻辑。

5. 遮挡数据与多视角一致性
   - 表达：训练用随机 2D occlusion，评估用 3D-consistent mask。
   - 画面：随机线条/椭圆/矩形遮挡 vs mesh triangle random-walk 生成的多视角一致遮挡。

6. 关键结果图：为什么优于两阶段 pipeline
   - 表达：`2D completion + 3D reconstruction` 会因 2D 补全不一致而误导 3D；Amodal3R 直接在 3D latent space 完成补全。
   - 画面：左侧 baseline 断裂/不一致，右侧 Amodal3R 几何完整、纹理连续。

## 可选缩减方案

- 只生成 1 张：方法总览图
- 生成 3 张：方法总览 + 两个 attention 机制
- 生成 6 张：按上面的完整推荐

## 需要你确认

1. 语言：中文 / English / 双语
2. 风格：`sketchnote` / `paper-figure`
3. 范围：1 张总览 / 3 张机制 / 6 张完整推荐
4. 用途：论文阅读笔记 / README 首图 / 组会展示 / 小红书或公众号配图

我的默认推荐：中文，`paper-figure`，生成 6 张，适合论文阅读笔记和组会展示。
