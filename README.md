# NLUTOOLS: NLU 工具包

nlutools 是一系列模型与算法的nlu工具包，提供以下功能：

1. 切词
2. 切句
3. 词向量
4. 句向量
5. 语言模型
6. 实体
7. 情感分析

## 切词

切词工具暂时提供四种模式，接口函数：cut(text, mode, pos, cut_all)

其中

* text 为要切词的原始文本

* mode 为分词模式，可选值为字符串类型'fast', 'accurate'，其中accurate模式暂时不可用，正在改进中

* pos为词性保留选项，可选值为True、False，其值为True则保留词性，反之则不保留词性

* cut_all为切词粒度控制，可选值为True、False，其值为False则全部保留名词短语，为True则只保留不可切分的名词短语

调用方式为：

```python
from nlutools import tools as nlu
nlu.cut('这是一个能够输出名词短语的分词器，欢迎试用！', pos=True, cut_all=False, mode='fast')
```

返回结果：

```json
{
    'np': ['名词_短语', '分词器'], 
    'text': '这是一个能够输出名词短语的分词器，欢迎试用！', 
    'items': ['这', '是', '一个', '能够', '输出', '名词', '短语', '的', '分词器', ',', '欢迎', '试用', '!'], 
    'pos': ['r', 'v', 'm', 'v', 'v', 'np', 'np', 'uj', 'np', 'x', 'v', 'vn', 'x']
}
```

## 切句

切句工具提供两种模式，接口函数：getSubSentences(text,mode)

其中

* text 为需要进行切句的原始文本

* mode 为切句模式，可选值为 0、1 ，为 0 表示快速模式（规则分句），为 1 则表示精确模式（句法分句）

调用方式：

```python
from nlutools import tools as nlu
nlu.getSubSentences('我喜欢在春天去观赏桃花，在夏天去欣赏荷花，在秋天去观赏红叶，但更喜欢在冬天去欣赏雪景。', mode=1)
```

返回结果：

```json
['我喜欢在春天去观赏桃花', '在夏天去欣赏荷花 在秋天去观赏红叶', '但更喜欢在冬天去欣赏雪景']
```

## 词向量

词向量工具提供以下功能：

1. 获得nlu小组词向量文件，可以根据版本号获取，目前版本号包括：v1.0

   默认是下载最新版。获取到的文件夹下面包含两个文件，一个是词向量文件，一个是字向量文件。

   获取方式如下:

    ```python
    from nlutools import tools as nlu
    nlu.getW2VFile('v1.0', '/local/path/')
    ```

2. 若不想下载词向量文件，可以直接使用一下方式获得词向量：

    ```python
    from nlutools import tools as nlu
    nlu.getWordVec('深度学习')
    # 或者传入多个词
    nlu.getWordVec(['深度学习', '机器学习'])
    ```

3. 获取词向量相似的词:

    ```python
    from nlutools import tools as nlu
    nlu.getMostSimiWords('深度学习', 10)  # 10表示最多返回10个最相似的词
    # 或者传入多个词
    nlu.getMostSimiWords(['深度学习', '机器学习'], 10)
    ```
  
## 句向量

将不同长度的句子转换为固定大小的向量表示

调用方式：

```python
from nlutools import tools as nlu
nlu.getSentenceVec(['主要负责机器学习算法的研究', '训练模型、编写代码、以及其他一些工作'])
```

返回结果：

```json
{
    'dimention': 300,  # 维度
    'veclist': [[0.01, ...,0.56],[0.89,...,-0.08]]
}
```

## 语言模型

待补充

## 实体

待补充

## 情感分析

返回句子的情感极性，暂时支持正向和负向情感

参数说明：

* prob 值为False，不返回预测句子的情感预测得分，只返回情感类别（pos或者neg）；值为True，则都返回。

调用方式：

```python
from nlutools import tools as nlu
nlu.predictEmotion(['这家公司很棒'，'这家公司很糟糕'], prob=False)
```

返回结果：

```json
{
    'text': ['这家公司很棒','这家公司很糟糕'],
    'labels': ['pos','neg']
}
```
