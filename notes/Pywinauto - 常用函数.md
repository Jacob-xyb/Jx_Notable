---
tags: [Python, Python Pywinauto]
title: Pywinauto - 常用函数
created: '2022-08-05T10:22:50.761Z'
modified: '2022-08-12T02:32:58.265Z'
---

# Pywinauto - 常用函数

## 直接调用

```python
ctrl.rectangle()        # 获取控件坐标
#  <self.left, self.top, self.right, self.bottom>
```

### 控件鼠标调用

```python
ctrl.click_input()

def click_input(
    self,
    button = "left",
    coords = (None, None),
    button_down = True,
    button_up = True,
    double = False,
    wheel_dist = 0,
    use_log = True,
    pressed = "",
    absolute = False,
    key_down = True,
    key_up = True):

def wheel_mouse_input(self, coords = (None, None), wheel_dist = 1, pressed =""):
    """Do mouse wheel"""
    self.click_input(button='wheel', coords=coords, wheel_dist=wheel_dist, pressed=pressed)
    return self

button = 'left','right','move','wheel'

```

## 间接调用
