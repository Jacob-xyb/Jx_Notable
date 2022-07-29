---
title: C++ Qt 以 utf-8 写入文件
created: '2022-07-29T02:31:43.974Z'
modified: '2022-07-29T02:32:45.899Z'
---

# C++ Qt 以 utf-8 写入文件

```cpp
QTextCodec::setCodecForLocale(QTextCodec::codecForName("UTF-8"));
QFile file(filePath);
if (!file.open(QIODevice::WriteOnly))
{
    VUtils::showMessageBoxError("");
    return;
}
QTextStream stream(&file);
stream.setCodec("UTF-8");
stream << "file,";
QTextCodec* utf8 = QTextCodec::codecForName("UTF-8");
stream << utf8->toUnicode(name.toLocal8Bit().data());
```
