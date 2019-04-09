OpenCV中的Haar分类器 = 类Haar特征 + 积分图方法 + AdaBoost + 级联

Viola-Jones分类器算法要点： 
1． 使用类Haar输入特征：对矩形图像区域的和或差进行阈值化； 
2． 积分图像技术加速了矩形图像区域的45度旋转的值的计算，这个图像结构被用来加速类Haar输入特征的计算。 
3． 使用Adaboost来创建二分类问题（人脸与非人脸）的分类器节点（高通过率，低拒绝率）。 
4． 把分类器节点组成筛选式级联（在筛选式级联里，一个节点是Adaboost类型的一组分类器）。换句话说：第一组分类器是最优，能通过包含物体的图像区域，同时允许一些不包含物体的图像通过；第二组分类器次优分类器，也有较低的拒绝率；以此类推。只要图像通过了整个级联，则认为里面有物体。这保证了级联的运行速度可以很快，因为它一般可以在前几步就可以拒绝不包含物体的图像区域，而不必走完整个级联。

在VJ之前识别率就很高了，亮点不在识别率，而在识别效率。一是用Haar特征， 计算简单，又引入积分图技术进行加速。二是使用AdaBoost将很容易构造出的弱分类器组合成强分类器。三是使用级联cascade策略将构造这些强分类器的退化决策树，使不满足的区域直接被排除，大大提高计算效率。

## 机器学习

pandas库 	缺失值，数据转换，重复值（不需要去重）

**sklearn库** 	python中机器学习算法库，对于特征的处理提供了强大的接口，必须先安装numpy和pandas

| scikit-learn 包含的算法       |
| ----------------------------- |
| classification 分类           |
| Regression 回归               |
| Clustering 聚类               |
| Dimensionality reduction 降维 |
| Model selection 模型选择      |
| Preprocession 特征工程        |

结构：特征值 + 目标值

#### 数据的特征工程

**特征工程**：是将原始数据转化为更好地代表预测模型的潜在问题的特征的过程，从而提高了对未知数据的预测准确性。

**特征抽取**：文本、字符串、字典类型的数据转化为数字

* 字典特征抽取：对字典数据进行特征值化。（`sklearn.feature_extraction.DictVectorizer`)

  DictVectorizer(sparse=True,...)

  1. **Dictvectorizer.fit_transform(X) **

  ​	X：字典或包含字典的迭代器

  ​	返回值：返回sparse矩阵

  2. Dictvectorizer.inverse_transform(X)

  ​	X：array数组或sparse矩阵

  ​	返回值：转换之前的数据格式

  3. Dictvectorizer.get_feature_names(X) 

  ​	返回类别名称

  4. Dictvectorizer.transform(X)

  ​	按照原先的标准转换

* 文本特征提取：对文本数据进行特征值化。（`sklearn.feature_extraction.text.CountVectorizer`）

  **文本分类、情感分析**

  CountVectorizer()

  1. **CountVectorizer.fit_transform(X)**

     X：文本或包含文本字符串的可迭代对象

     返回值：返回sparse矩阵

  2. CountVectorizer.inverse_transform(X)

     X：array数组或sparse矩阵

     返回值：返回sparse矩阵

  3. CountVectorizer.get_feature_names(X)

     返回值：单词列表

```python
import jieba
jieba.cut("我是一个程序员")
# 返回值：词语生成器，弥补中文无空格无法把词语分开的缺陷
```


* 流程：

   1. 实例化类CountVectorizer

   2. 调用fit_transform方法输入数据并转换

      注意返回格式，利用toarray()进行sparse矩阵转换为array数组。
