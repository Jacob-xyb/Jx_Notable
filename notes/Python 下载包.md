---
tags: [Python, Python 下载]
title: Python 下载包
created: '2022-07-07T14:42:11.023Z'
modified: '2022-07-25T01:11:04.100Z'
---

# Python 下载包

## pip 下载包到本地

```python
pip download xlrd==1.2.0		# 下载到当前文件夹下
pip download -r .\requirements.txt		# 依据requirements.txt 下载到当前文件夹下
pip download -d d:\lib -r .\requirements.txt		# 指定文件下载whl
```

## pip 下载加速

```python
https://pypi.tuna.tsinghua.edu.cn/simple		# 清华大学
https://pypi.douban.com/simple					# 豆瓣(douban) 
https://pypi.mirrors.ustc.edu.cn/simple/		# 中国科技大学 
http://mirrors.aliyun.com/pypi/simple/			# 阿里云 
http://pypi.mirrors.ustc.edu.cn/simple/			# 中国科学技术大学
```


