---
tags: [Python, Python Pywinauto]
title: Pywinauto - control_type
created: '2022-08-05T10:30:19.010Z'
modified: '2022-08-16T11:26:43.711Z'
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

**Table**

```python
# ControlType:	UIA_TableControlTypeId (0xC374)
Table.item_count()		# 获取表格的行数
Table.column_count()	# 获取表格的列数
```

**Tree**

```python
getattr(Tree.iface_grid, "CurrentRowCount")
getattr(Tree.iface_grid, "CurrentColumnCount")
```

**Edit**

```python
# ControlType:	UIA_EditControlTypeId (0xC354)
Edit.set_edit_text('')
Edit.set_text('')		# .set_text() == .set_edit_text()
Edit.get_value() -> str		# 返回 Edit 的值
```

