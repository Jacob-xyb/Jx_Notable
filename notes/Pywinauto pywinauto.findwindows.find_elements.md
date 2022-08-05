---
tags: [Python Pywinauto]
title: Pywinauto pywinauto.findwindows.find_elements
created: '2022-08-05T10:29:10.978Z'
modified: '2022-08-05T11:00:25.805Z'
---

# Pywinauto pywinauto.findwindows.find_elements

## Inspect 对应字段

```python
pywinauto.findwindows.find_elements(class_name=None, class_name_re=None, parent=None, process=None, title=None, title_re=None, top_level_only=True, visible_only=True, enabled_only=False, best_match=None, handle=None, ctrl_index=None, found_index=None, predicate_func=None, active_only=False, control_id=None, control_type=None, auto_id=None, framework_id=None, backend=None, depth=None)
```

```python
# 函数参数        # Inspect字段        # 函数获取
class_name        ClassName           ctrl.class_name()
title             Name                ctrl.window_text()
auto_id           AutomationId        ctrl.automation_id()
framework_id      FrameworkId         ctrl.element_info.framework_id
control_type      ControlType         ctrl._control_types[0]                
```


## 官方文档

```python
pywinauto.findwindows.find_elements(class_name=None, class_name_re=None, parent=None, process=None, title=None, title_re=None, top_level_only=True, visible_only=True, enabled_only=False, best_match=None, handle=None, ctrl_index=None, found_index=None, predicate_func=None, active_only=False, control_id=None, control_type=None, auto_id=None, framework_id=None, backend=None, depth=None)
```

WARNING! Direct usage of this function is not recommended! It’s a very low level API. Better use Application and WindowSpecification objects described in the Getting Started Guide.

Possible values are:

- **class_name** Elements with this window class

  Inspect 中的 **ClassName**

- **class_name_re** Elements whose class matches this regular expression

- **parent** Elements that are children of this

- **process** Elements running in this process

  这个基本不用，每次启动进程都会变化

- **title** Elements with this text

  Inspect 中的 **Name** 属性

- **title_re** Elements whose text matches this regular expression

- **top_level_only** Top level elements only (default=**True**)

- **visible_only** Visible elements only (default=**True**)

- **enabled_only** Enabled elements only (default=False)

- **best_match** Elements with a title similar to this

- **handle** The handle of the element to return

- **ctrl_index** The index of the child element to return

- **found_index** The index of the filtered out child element to return

- **predicate_func** A user provided hook for a custom element validation

- **active_only** Active elements only (default=False)

- **control_id** Elements with this control id

- **control_type** Elements with this control type (string; for UIAutomation elements)

- **auto_id** Elements with this automation id (for UIAutomation elements)

  Inspect 中的 **AutomationId**

- **framework_id** Elements with this framework id (for UIAutomation elements)

- **backend** Back-end name to use while searching (default=None means current active backend)
