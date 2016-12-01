---
layout: post
title: "Learning Python 028 获取命令行参数"
date: 2016-12-02 02:07:35 +0800
comments: true
sharing: true
categories: [python]
tags: [python3, python2, 命令行, 参数, args]
---

---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python2.7.10 或者 python 3.5.0

---

> 本博文对Python2和Python3都适用。


----------



```python
import optparse

def main():
    parser = optparse.OptionParser('usage%prog ' +\
                                   '-f <zipfile> -d <dictionary>')
    parser.add_option('-f', dest='zname', type='string',\
                      help='specify zip file')
    parser.add_option('-d', dest='dname', type='string',\
                      help='specify dictionary file')
    (options, args) = parser.parse_args()
    if (options.zname == None) | (options.dname == None):
        print(parser.usage)
        exit(0)
        pass
    else:
        zname = options.zname
        dname = options.dname
        dlist = dname.split(',')
        pass
    print('zname is ', zname)
    print('dname is ', dname)
    print('dlist is ', dlist)
    pass

if __name__ == '__main__':
    main()
    pass
```

Python3 的运行结果：

```
>python learningpython28.py -f aobo  -d sir,patty,re
zname is  aobo
dname is  sir,patty,re
dlist is  ['sir', 'patty', 're']
```

Python2 的运行结果：

```
>C:\Python27\python.exe learningpython28.py -f aobo -d sir,patty,re
('zname is ', 'aobo')
('dname is ', 'sir,patty,re')
('dlist is ', ['sir', 'patty', 're'])
```

下面这个几个命令运行的效果是一样的：（Python2 和 Python3 运行的效果都一样）

```
>python learningpython28.py -h
>python learningpython28.py --h
>python learningpython28.py --help
>python learningpython28.py -help
```

运行结果：

```
Usage: usagelearningpython28.py -f <zipfile> -d <dictionary>

Options:
  -h, --help  show this help message and exit
  -f ZNAME    specify zip file
  -d DNAME    specify dictionary file

```
