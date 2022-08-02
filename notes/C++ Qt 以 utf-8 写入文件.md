---
title: C++ Qt 以 utf-8 写入文件
created: '2022-07-29T02:31:43.974Z'
modified: '2022-08-02T05:43:51.726Z'
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

# C++ Qt 以 UTF-8-BOM 写入文件

最近项目中需要批量修改源代码的编码格式，原编码格式有很多种，有UTF-8、UTF-8-Bom、GB2312、GBK等，需要统一修改为UTF-8-BOM格式，源代码有很多，分在几十个文件夹下，每个文件夹里又有很多个子文件夹。

电脑不能连网，只有Qt开发环境，于是写了个简易脚本处理解决了。解决方案比较简单，写个dfs遍历出指定文件夹下所有文件挨个转换，首先获取原文件的编码格式，转换并存储，然后写入原文件进行覆盖。这里以UTF-8-BOM为例，如果想统一转成其他格式，只需要改写入文件的编码格式即可。

开发过程遇到了几个预想之外的问题，主要问题在于QTextCodec::codecForName的参数是QByteArray或char *，开始想构造个QStringList，循环遍历一遍，挨个转成QByteArray去匹配，但是始终有问题，会存在不匹配的情况，开始以为是QString转成QByteArray的接口有问题，于是把toLatin1()、toLocal8Bit()、toUtf8挨个都试了一遍，还是不行。然后就构造了QList<QByteArray>发现也不行，构造了char *数组也不行。最后没办法只能放弃参数调用，直接拿字符串当参数。

```cpp
// 获取字符串text原编码格式，如果转换成果则记录在str里
bool testTurnBtn::judgeIsInvalid(int id, const QByteArray &text, QString &str)
{
    QTextCodec::ConverterState state;
 
    QTextCodec *codec;
    if (id == 0)    // 匹配每种编码，如有新编码追加即可
        codec = QTextCodec::codecForName("UTF-8");
    else if (id == 1)
        codec = QTextCodec::codecForName("GB2312");
    else if (id == 2)
        codec = QTextCodec::codecForName("GBK");
    else
        return false;
 
    str = codec->toUnicode(text.constData(), text.size(), &state);
 
    if (state.invalidChars == 0)
        return true;
    else
        return false;
}
 
// 将fileName文件转换成UTF-8-BOM格式
void testTurnBtn::transferFilesToUtf8Bom(QString fileName)
{
    // 读文件内容
    QFile file(fileName);
    if (!file.open(QIODevice::ReadOnly | QIODevice::Text))
        return;
 
    QByteArray text = file.readAll();
    file.close();
 
    // 转换内容
    QString content;
    bool isSuccess = false;
    for (int i = 0; i < 3; ++i)     // 内置的编码格式，暂设3
    {
        if (judgeIsInvalid(i, text, content))
        {
            isSuccess = true;
            break;
        }
    }
    if (isSuccess)
        qDebug() << "Transfer Success:\t" << fileName;
    else
    {
        qDebug() << "Transfer Failed:\t" << fileName;
        return;
    }
 
    // 写入文件
    QFile fileOut(fileName);
    if (!fileOut.open(QIODevice::WriteOnly | QIODevice::Text | QIODevice::Truncate))
        return;
 
    QTextStream out(&fileOut);
    out.setGenerateByteOrderMark(true);     // 设置编码带Bom
    out.setCodec("UTF-8");
    out << content;
    fileOut.close();
}
 
// 递归遍历每个子文件夹
void testTurnBtn::dfsRequireFiles(QString path)
{
    QDir dir(path);
    QFileInfoList file_list = dir.entryInfoList(QDir::Files | QDir::Hidden | QDir::NoSymLinks);  // 获取文件列表
    QFileInfoList folder_list = dir.entryInfoList(QDir::Dirs | QDir::NoDotAndDotDot);  // 获取文件夹里列表
 
    for (int i = 0; i < file_list.size(); i++)
    {
        QString name = file_list.at(i).fileName();
        transferFilesToUtf8Bom(name);
    }
 
    for (int i = 0; i != folder_list.size(); i++)
    {
        QString name = folder_list.at(i).absoluteFilePath();
        dfsRequireFiles(name);
    }
}
```
