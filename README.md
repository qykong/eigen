## 推荐
1. 为已知商家所售商品寻找关联商品。
  - 数据：所有用户浏览记录中相关商品的信息（商品名），以及商家所售商品的信息（商品名）
  - 实现：为每个商品创建词向量，再计算目标商家所售商品信息的词向量与所有商品词向量间cosine相似度。取前k个相似的商品
2. 预测下个月购买相似商品的概率
  - 数据：所有用户的行为记录
  - 模型：logistics regression
  - 训练：取训练集为$(X_{ij}, Y_{j+1})$其中i表示第i个用户，j表示月份，X为对k个相似商品的浏览记录，Y为是否购买了目标商品。即通过当月用户对上一步中得出的k个相似商品的浏览记录（浏览、推荐、收藏），来预测下个月购买目标商品的概率。通过logistics regression在训练集上的训练即可得到用于预测的模型。
  - 预测：用当前月所有用户对k个相似商品的行为记录，通过训练所得模型即可得到购买概率。
3. 对商户所售所有商品重复1、2步，为每个用户取平均概率，再进行排序，即可获得前n个对该商户有价值的用户。