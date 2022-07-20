---
tags: [Python]
title: Python小技巧
created: '2022-07-20T02:26:12.940Z'
modified: '2022-07-20T03:35:36.980Z'
---

# Python小技巧

## 一行代码创建二维数组

```python
arr = [[0] * w for _ in range(h)]
```

## 推导式

- 字典推导式

```python
d = {k: k for k in range(3)}
print(d)  # {0: 0, 1: 1, 2: 2}
```

- 集合推导式

```python
s = {x for x in 'abracadabra' if x not in 'abc'}
print(s)	# {'d', 'r'}
```

## pass 和 ...

pass 是关键字; ... 是 Ellipsis 对象

pass 不能被打印; 

```python
print(...)  # Ellipsis
```

`[[...]]` 代表嵌套列表; `[Ellipsis]` 代表待定容器内变量为 Ellipsis

```python
a = []
a.append(a)
print(a)  # [[...]]

a = [...]
print(a)  # [Ellipsis]
```
