---
tags: [未分类, Python, Python 三方库]
title: Python yaml
created: '2022-07-08T06:17:02.338Z'
modified: '2022-07-08T08:26:57.985Z'
---

# Python yaml

`pip install pyyaml`

```python'
import yaml

def get_yaml_data(yaml_file):
    print("*****获取yaml数据*****")
    with open(yaml_file, encoding='utf-8')as file:
        content = file.read()
        print(content)
        print(type(content))

        print("\n*****转换yaml数据为字典或列表*****")
        # 设置Loader=yaml.FullLoader忽略YAMLLoadWarning警告
        data = yaml.load(content, Loader=yaml.FullLoader)
        print(data)
        print(type(data))
        print(data.get('my'))  # 类型为字典 <class 'dict'>
　　　　# print(data[0]["model"]) # 若类型为列表 <class 'list'>

if __name__ == "__main__":
    get_yaml_data("config.yaml")
```
