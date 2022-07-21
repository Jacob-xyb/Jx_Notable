---
tags: [Python, Python 基础数据类型]
title: 集合 set
created: '2022-07-21T07:32:12.561Z'
modified: '2022-07-21T07:33:00.544Z'
---

# 集合 set

## 集合运算

```python
a = set('abracadabra')
b = set('alacazam')
# 集合是无序的
print(a)	# {'b', 'c', 'd', 'a', 'r'}
print(b)	# {'m', 'c', 'z', 'l', 'a'}

# a有 b没有
print(a - b)	# {'b', 'd', 'r'}
# a 或 b 有
print(a | b)	# {'l', 'm', 'b', 'c', 'z', 'd', 'a', 'r'}
# a 和 b 都有
print(a & b)	# {'c', 'a'}
# a b 不同时有
print(a ^ b)	# {'b', 'm', 'z', 'l', 'd', 'r'}
```
