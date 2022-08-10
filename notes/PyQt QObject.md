---
tags: [PyQt 函数一览, Python]
title: PyQt QObject
created: '2022-08-10T07:52:56.969Z'
modified: '2022-08-10T08:22:54.938Z'
---

# PyQt QObject

## 常用函数

```python
objectName()    # 获取
setObjectName(str)  # 设置

setProperty(name: str, value: str)   # 设置属性
property(name: str) -> Any   # 获取设置过的属性，没找到时返回 None，类似于 dict.get()
dynamicPropertyNames() -> List[QByteArray]   # 返回所有设置过的属性
QByteArray.data().decode() -> str   # QByteArray 可以转换为字符串
# 但是 List[QByteArray]  可以直接识别 str
str in List[QByteArray] 和 List[QByteArray].index(str) 均可使用
```

## 全部函数

```python
['__class__',
 '__delattr__',
 '__dict__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattr__',
 '__getattribute__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__le__',
 '__lt__',
 '__module__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 '__weakref__',
 'blockSignals',
 'childEvent',
 'children',
 'connectNotify',
 'customEvent',
 'deleteLater',
 'destroyed',
 'disconnect',
 'disconnectNotify',
 'dumpObjectInfo',
 'dumpObjectTree',
 'dynamicPropertyNames',
 'event',
 'eventFilter',
 'findChild',
 'findChildren',
 'inherits',
 'installEventFilter',
 'isSignalConnected',
 'isWidgetType',
 'isWindowType',
 'killTimer',
 'metaObject',
 'moveToThread',
 'objectName',    
 'objectNameChanged',
 'parent',
 'property',
 'pyqtConfigure',
 'receivers',
 'removeEventFilter',
 'sender',
 'senderSignalIndex',
 'setObjectName',
 'setParent',
 'setProperty',
 'signalsBlocked',
 'startTimer',
 'staticMetaObject',
 'thread',
 'timerEvent',
 'tr']

```
