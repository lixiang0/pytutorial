#### search() vs. match()

两者的操作都是匹配到第一个需要匹配的字段。区别在于re.search()是全字符匹配，而re.match()只匹配字符串的开头部分。
并且在re.MULTILINE模式下出现换行操作的情况，match操作不会匹配包括中间的行开头字段，而search会。示例：
```
import re
a='abca'
re.match('c',a)#匹配失败
re.search('c',a)#匹配成功
a='a\b\c\nd\n'
re.match('c',a)#匹配失败
re.search('c',a)#匹配成功
```

