---
tags: [Python Pywinauto]
title: Pywinauto - control_type
created: '2022-08-05T10:30:19.010Z'
modified: '2022-08-05T10:46:13.995Z'
---

# Pywinauto - control_type

**ComboBox**

```python
# ControlType:  UIA_ComboBoxControlTypeId (0xC353)
ComboBox.select(item: str)		# 直接选中
ComboBox.expand()		# 展开
ComboBox.collapse()		# 收回
ComboBox.is_expanded()		# 判断是否展开
ComboBox.is_collapsed()		# 判断是否收回
ComboBox.is_enabled()		# 是否可用
```

**Group**

```python
ControlType:	UIA_GroupControlTypeId (0xC36A)
```
