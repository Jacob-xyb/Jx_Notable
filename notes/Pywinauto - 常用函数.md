---
tags: [Python, Python Pywinauto]
title: Pywinauto - 常用函数
created: '2022-08-05T10:22:50.761Z'
modified: '2022-08-12T06:55:45.209Z'
---

# Pywinauto - 常用函数

## 直接调用

```python
#  <self.left, self.top, self.right, self.bottom>
ctrl.legacy_properties()    # 获取私有属性的字典 .get('key') 获取值
ctrl.rectangle()        # 获取控件坐标
    coord = list(ctrl.rectangle().mid_point())
ctrl.capture_as_image()     # 截图控件
ctrl.get_properties()       # 获取属性
ctrl.draw_outline(colour='green', thickness=2,..)   # 突显控件
ctrl.descendants()      # 返回所有满足条件的子控件
ctrl.children()         # 返回一层中所有满足条件的子控件
ctrl.children_texts()
ctrl.print_ctrl_ids(deep=None)
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
