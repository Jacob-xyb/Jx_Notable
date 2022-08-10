---
tags: [Python Pywinauto]
title: Pywinauto - control_type
created: '2022-08-05T10:30:19.010Z'
modified: '2022-08-10T03:05:01.664Z'
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

**CheckBox**

```python
# ControlType:	UIA_CheckBoxControlTypeId (0xC352)
CheckBox.get_toggle_state()		# 获取是否选定状态，返回 0 | 1
```
