---
tags: [Python, Python Pywinauto]
title: Pywinauto 调试
created: '2022-08-07T05:16:47.198Z'
modified: '2022-08-16T03:27:33.293Z'
---

# Pywinauto 调试

## coonect

connect 最常用的两个参数是: `process` 和 `path`

但是临时调试时，`process` 反而是最方便快捷的连接方式

```python
import pywinauto
app = pywinauto.application.Application(backend="uia").connect(process=29928)
win = app.top_window()
```

```
process_id = win.process_id()
```
