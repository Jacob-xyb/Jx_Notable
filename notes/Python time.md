---
tags: [Python, Python 标准库]
title: Python time
created: '2022-07-09T06:35:46.137Z'
modified: '2022-07-12T12:23:02.561Z'
---

# Python time

## 获取时间

### 时间戳(timestamp)

通常来说，时间戳表示的是从**格林威治时间1970年1月1日00:00:00**  (**北京时间1970年01月01日08时00分00秒**)  开始按秒计算的偏移量

`time.time() -> float`

获取当前时间戳，即计算机内部时间值，浮点数, 单位 s

```python
import time
time.time()		# 1655863478.715323
```

### 进程运行时间

`time.perf_counter()`  单位: s

Python3.8 不再支持time.clock

```python
import time
a = time.perf_counter()
time.sleep(3)
b = time.perf_counter()
print(b-a)  # 3.0083799999999883
```

### struct_time

struct_time元组共有9个元素，返回struct_time的函数主要有 `gmtime()` ，`localtime()` 

| 索引（Index） | 属性（Attribute）         | 值（Values）       |
| :------------ | :------------------------ | :----------------- |
| 0             | tm_year（年）             | 比如2011           |
| 1             | tm_mon（月）              | 1 - 12             |
| 2             | tm_mday（日）             | 1 - 31             |
| 3             | tm_hour（时）             | 0 - 23             |
| 4             | tm_min（分）              | 0 - 59             |
| 5             | tm_sec（秒）              | 0 - 61             |
| 6             | tm_wday（weekday）        | 0 - 6（0表示周日） |
| 7             | tm_yday（一年中的第几天） | 1 - 366            |
| 8             | tm_isdst（是否是夏令时）  | 默认为-1           |

#### struct_time()

时间的一个类

```python
class struct_time(tuple):
	...
```

可以通过属性直接获取值

```python
import time

struct_time = time.localtime()
print(struct_time)
# time.struct_time(tm_year=2022, tm_mon=7, tm_mday=12, tm_hour=20, tm_min=20, tm_sec=20, tm_wday=1, tm_yday=193, tm_isdst=0)
print(struct_time.tm_year)  # 2022
print(struct_time.tm_hour)  # 20
```

#### localtime()

`time.localtime([secs])`：将一个时间戳转换为当前时区的struct_time。secs参数未提供，则以当前时间为准。

```python
import time

print(time.localtime())
print(time.localtime(time.time()))

# 输出一致
time.struct_time(tm_year=2022, tm_mon=7, tm_mday=12, tm_hour=19, tm_min=46, tm_sec=25, tm_wday=1, tm_yday=193, tm_isdst=0)
```

#### gmtime()

`time.gmtime([secs])`：和localtime()方法类似，gmtime()方法是将一个时间戳转换为UTC时区（0时区）的struct_time。

#### mktime()

`time.mktime(t)`：将一个struct_time转化为时间戳。

```python
time.mktime(time.localtime())  # 1657626741.0
```

#### asctime()

`time.asctime([t])`：把一个表示时间的元组或者struct_time表示为这种形式：**'Tue Jul 12 19:54:06 2022'**。如果没有参数，将会将time.localtime()作为参数传入。

#### ctime()

`time.ctime([secs])`：把一个时间戳（按秒计算的浮点数）转化为time.asctime()的形式。如果参数未给或者为None的时候，将会默认time.time()为参数。它的作用相当于time.asctime(time.localtime(secs))。

```python
print(time.ctime())
print(time.ctime(time.time()))

# 输出一致
Tue Jul 12 20:00:16 2022
```

#### strftime()

`time.strftime(format[, t])`：把一个代表时间的元组或者struct_time（如由time.localtime()和time.gmtime()返回）转化为格式化的时间字符串。

**如果t未指定，将传入time.localtime()。**

如果元组中任何一个元素越界，ValueError的错误将会被抛出。

|      |                                                              |      |
| :--- | :----------------------------------------------------------- | :--- |
| 格式 | 含义                                                         | 备注 |
| %a   | 本地（locale）简化星期名称                                   |      |
| %A   | 本地完整星期名称                                             |      |
| %b   | 本地简化月份名称                                             |      |
| %B   | 本地完整月份名称                                             |      |
| %c   | 本地相应的日期和时间表示                                     |      |
| %d   | 一个月中的第几天（01 - 31）                                  |      |
| %H   | 一天中的第几个小时（24小时制，00 - 23）                      |      |
| %I   | 第几个小时（12小时制，01 - 12）                              |      |
| %j   | 一年中的第几天（001 - 366）                                  |      |
| %m   | 月份（01 - 12）                                              |      |
| %M   | 分钟数（00 - 59）                                            |      |
| %p   | 本地am或者pm的相应符                                         |      |
| %S   | 秒（00 - 61）                                                |      |
| %U   | 一年中的星期数。（00 - 53星期天是一个星期的开始。）第一个星期天之前的所有天数都放在第0周。 |      |
| %w   | 一个星期中的第几天（0 - 6，0是星期天）                       |      |
| %W   | 和%U基本相同，不同的是%W以星期一为一个星期的开始。           |      |
| %x   | 本地相应日期                                                 |      |
| %X   | 本地相应时间                                                 |      |
| %y   | 去掉世纪的年份（00 - 99）                                    |      |
| %Y   | 完整的年份                                                   |      |
| %Z   | 时区的名字（如果不存在为空字符）                             |      |
| %%   | ‘%’字符                                                      |      |

**备注**：

1. “%p”只有与“%I”配合使用才有效果。
2. 文档中强调确实是0 - 61，而不是59，闰年秒占两秒（汗一个）。
3. 当使用strptime()函数时，只有当在这年中的周数和天数被确定的时候%U和%W才会被计算。

```python
import time

print(time.strftime("%Y-%m-%d %X"))
print(time.strftime("%Y-%m-%d %H:%M:%S"))

# 输出一致
2022-07-12 20:09:30
```

#### strptime()

`time.strptime(string[, format])`：把一个格式化时间字符串转化为struct_time。实际上它和strftime()是逆操作。

```python
print(time.strptime("2022-07-12 20:09:30", "%Y-%m-%d %X"))

# time.struct_time(tm_year=2022, tm_mon=7, tm_mday=12, tm_hour=20, tm_min=9, tm_sec=30, tm_wday=1, tm_yday=193, tm_isdst=-1)
```


