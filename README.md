# NLUTOOLS：  NLU 工具包

nlutools 是一系列模型与算法的nlu工具包，提供以下功能：
      1. 切词
      2. 切句
      3. 词向量
      4. 句向量
      5. 语言模型
      6. 实体
  
  >1. 切词
  -
    切词工具提供八种模式，接口函数：```cut（text, mode, pos, cut_all）```,其中```text```为要切词的原始文本；```mode```为分词模式，可选值为字符串类型```'fast', 'accurate'```；
    ```pos```为词性保留选项，可选值为```True、False```，其值为```True```则保留词性，反之则不保留词性； ```cut_all```为切词粒度控制，可选值为```True、False```，其值为```False```则保留不可切分的名词短语，为```True```则不保留。
    
    调用方式为：
    ```
     from nlutools import tools as nlu
     nlu.cut('这是一个能够输出名词短语的分词器，欢迎试用！',mode='fast',pos=True,cut_all=False)
    ```
    
    返回结果：
    ```
    {
        'np': ['名词_短语', '分词器'], 
        'text': '这是一个能够输出名词短语的分词器，欢迎试用！', 
        'items': ['这', '是', '一个', '能够', '输出', '名词', '短语', '的', '分词器', ',', '欢迎', '试用', '!'], 
        'pos': ['r', 'v', 'm', 'v', 'v', 'np', 'np', 'uj', 'np', 'x', 'v', 'vn', 'x']
    }
    ```
  >2. 切句
  - 
    切句工具提供两种模式，接口函数：```getSubSentences(text,mode)```,其中```text```为要切句发原始文本；```mode```为切句模式，可选值为```0、1```，为```0```表示快速模式（规则分句），为```1```则表示精确模式（句法分句）。
    
    调用方式：
    ```
    from nlutools import tools as nlu
    nlu.getSubsentences('我喜欢在春天去观赏桃花，在夏天去欣赏荷花，在秋天去观赏红叶，但更喜欢在冬天去欣赏雪景。',mode=1)
    ```

    返回结果
    ```
    ['我喜欢在春天去观赏桃花', '在夏天去欣赏荷花 在秋天去观赏红叶', '但更喜欢在冬天去欣赏雪景']
    ```
  
  >3. 词向量
  -
    词向量工具提供以下功能：
    1. 获得nlu小组词向量文件，可以根据版本号获取，目前版本号包括：v1.0;默认是下载最新版。获取方式如下：
       ```
       from nlutools import tools as nlu
       nlu.getW2VFile('v1.0','/local/path/')
       ```
    2. 获取到的文件夹下面包含两个文件，一个是词向量文件，一个是字向量文件
    3. 若不想下载词向量文件，可以直接使用一下方式获得词向量：
       ```
       待补充
       ```
  
  >4. 句向量
  -
    ```
    待补充
    ```
    
  >5. 语言模型
  -
    ```
    待补充
    ```
    
  >6. 实体
  -
    ```
    待补充
    ```

