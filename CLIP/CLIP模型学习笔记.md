# CLIP模型学习笔记

##### 采用对比方式，图像采用vit结构编码，文本使用bert编码，实现视觉和语言的多模态融合

![image-20250826144324447](C:\Users\24540\AppData\Roaming\Typora\typora-user-images\image-20250826144324447.png)

### CLS token结构：

背景：原本的图像数据格式是[Height,Width,Channel]，但是这种方式不是Transformer所能接受的，所欲需要一个Embedding层，对原始的图片数据进行变换。

##### vit划分patch原理：

本文将输入的图片尺寸为(224×224)按照16×16大小的Patch进行划分。其中（224×224）/（16×16）=196，因此我们会得到196个patches。到这里我们可以知道每一个Patches数据的shape为[16, 16, 3]。为了满足Transformer的需求，在这里，对每个Patch进行投影变化，映射到一维向量中。即完成如下转化。[16, 16, 3]->[768]，那么这样一来，就将原始的[224, 224, 3]转化为[196, 768

##### cls token原理：

输入Transformer Encoder之前，需要加上一个东西叫做[class]token（专门用于分类操作），这是一个可训练的参数，数据格式和其他token保持一致，均为向量。

### image encode原理

图像编码使用vit编码结构，将图片划分为多个patch，然后使用transfomer结构编码提取特征，最终获得特征表达。

### text encode原理

文本编辑使用BERT编码结构，使用transformer结构编码提取特征，最终获得特征表达。

### 文本位置编码

将位置编码嵌入，实际是x加上位置信息

### 文本特殊结构

self.text_projection特殊结构，该结构若使用将进一步将文本特征表达进行变换，该变换的self.text_projection是可学习参数，代码如下：

```python
self.text_projection = nn.Parameter(torch.empty(transformer_width, embed_dim))
```

