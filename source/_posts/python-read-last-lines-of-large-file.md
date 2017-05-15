---
title: 'python: read last lines of large file'
date: 2017-05-03 16:53:15
tags: python
---
用python读取大文件的最后几行。
这是小密圈里一个同学的面试题，我也做了下，做这个题目才发现可以直接loop over file object，而且这种方式是memory efficient, fast.

```
if __name__ == '__main__':
    f=open("xx.log","r")
    count = 0
    loop = True
    while loop:
        f.seek(count,2)
        if len(f.readlines()) < 6:
            count = count-1
        else:
            loop = False
    f.seek(count,2)
    print f.readlines()[1:]
```
