---
tags: [未分类]
title: Python 获取文件编码
created: '2022-07-22T08:36:20.076Z'
modified: '2022-07-22T08:36:39.088Z'
---

# Python 获取文件编码

```python
import chardet
 
 
# 获取文件编码类型
def get_encoding(file):
    # 二进制方式读取，获取字节数据，检测类型
    with open(file, 'rb') as f:
        data = f.read()
        return chardet.detect(data)['encoding']
 
 
file_name = 'AAAA.txt'
encoding = get_encoding(file_name)
print(encoding)
```
