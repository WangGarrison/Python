# 正则表达式

正则表达式(Regular Expression)：正则表达式是一个特殊的字符序列（<font color='red'>**包括普通字符（例如，a 到 z 之间的字母）和特殊字符（称为"元字符"））**</font>，==它描述了一种字符串匹配的模式（pattern），可以用来检查一个串是否含有某种子串、将匹配的子串替换或者从某个串中取出符合某个条件的子串等==

例如：

- **runoo+b**，可以匹配 runoob、runooob、runoooooob 等，+ 号代表前面的字符必须至少出现一次（1次或多次）
- **runoo\*b**，可以匹配 runob、runoob、runoooooob 等，* 号代表前面的字符可以不出现，也可以出现一次或者多次（0次、或1次、或多次）
- **colou?r** 可以匹配 color 或者 colour，? 问号代表前面的字符最多只可以出现一次（0次、或1次）

# 正则表达式中的特殊字符

特殊字符，就是一些有特殊含义的字符，如上面说的 **runoo\*b** 中的 *****，简单的说就是表示任何字符串的意思。如果要查找字符串中的 ***** 符号，则需要对 ***** 进行转义，反斜杠 \

| 字符  | 描述                                                         |
| :---- | :----------------------------------------------------------- |
| *     | 匹配前面的子表达式==零次或多次==。例如，zo* 能匹配 "z" 以及 "zoo"。* 等价于{0,}。 |
| +     | 匹配前面的子表达式==一次或多次==。例如，'zo+' 能匹配 "zo" 以及 "zoo"，但不能匹配 "z"。+ 等价于 {1,}。 |
| ?     | 匹配前面的子表达式==零次或一次==。例如，"do(es)?" 可以匹配 "do" 、 "does" 中的 "does" 、 "doxy" 中的 "do" 。? 等价于 {0,1}。 |
| {n}   | n 是一个非负整数。==匹配确定的 n 次==。例如，'o{2}' 不能匹配 "Bob" 中的 'o'，但是能匹配 "food" 中的两个 o。 |
| {n,}  | n 是一个非负整数。==至少匹配n 次==。例如，'o{2,}' 不能匹配 "Bob" 中的 'o'，但能匹配 "foooood" 中的所有 o。'o{1,}' 等价于 'o+'。'o{0,}' 则等价于 'o*'。 |
| {n,m} | m 和 n 均为非负整数，其中n <= m。==最少匹配 n 次且最多匹配 m 次==。例如，"o{1,3}" 将匹配 "fooooood" 中的前三个 o。'o{0,1}' 等价于 'o?'。请注意在逗号和两个数之间不能有空格。 |

**其他特殊字符：**

| 特别字符 | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| $        | 匹配输入字符串的结尾位置。如果设置了 RegExp 对象的 Multiline 属性，则 $ 也匹配 '\n' 或 '\r' |
| ( )      | 标记一个子表达式的开始和结束位置。子表达式可以获取供以后使用 |
| .        | 匹配除换行符 \n 之外的任何单字符                             |
| [        | 标记一个中括号表达式的开始                                   |
| \        | 将下一个字符标记为或特殊字符、或原义字符、或向后引用、或八进制转义符。 |
| ^        | 匹配输入字符串的开始位置，除非在方括号表达式中使用，当该符号在方括号表达式中使用时，表示不接受该方括号表达式中的字符集合。要匹配 ^ 字符本身，请使用 \^。 |
| {        | 标记限定符表达式的开始                                       |
| \|       | 指明两项之间的一个选择                                       |

# 正则表达式语法

```python
^[0-9]+abc$
```

- `^` 为匹配输入字符串的开始为之
- `[0-9]+` 匹配一个或者多个数字`[0-9]` 匹配单个数字，`+` 表示匹配一个或者多个

- 写用户注册表单时，只允许用户名包含字符、数字、下划线和连接字符(-)，并设置用户名的长度，我们就可以使用以下正则表达式来设定：

  <img align='left' src="img/Python%EF%BC%9A%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F.img/image-20211221123347835.png" alt="image-20211221123347835" style="zoom: 33%;" />

| 字符   | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| [ABC]  | 匹配 **[...]** 中的所有字符，例如 **[aeiou]** 匹配字符串 "google runoob taobao" 中所有的 e o u a 字母。![img](https://www.runoob.com/wp-content/uploads/2014/03/E691DDE1-E5CB-4EA8-8D16-759BD0D2B09D.jpg) |
| [^ABC] | 匹配除了 **[...]** 中字符的所有字符，例如 **[^aeiou]** 匹配字符串 "google runoob taobao" 中除了 e o u a 字母的所有字母。![img](https://www.runoob.com/wp-content/uploads/2014/03/ED971D92-30F4-4768-A2C7-02A84A3A9DEB.jpg) |
| [A-Z]  | [A-Z] 表示一个区间，匹配所有大写字母，[a-z] 表示所有小写字母。![img](https://www.runoob.com/wp-content/uploads/2014/03/C5E357BD-65E3-4EB3-9D80-10D096F19287.jpg) |
| .      | 匹配除换行符（\n、\r）之外的任何单个字符，相等于 [^\n\r]。![img](https://www.runoob.com/wp-content/uploads/2014/03/0FD7E77D-38A7-43BC-B51A-7DBA23A77756.jpg) |
| [\s\S] | 匹配所有。\s 是匹配所有空白符，包括换行，\S 非空白符，不包括换行。![img](https://www.runoob.com/wp-content/uploads/2014/03/47CA6C59-64CF-433A-909E-1E342349A4E0.jpg) |
| \w     | 匹配字母、数字、下划线。等价于 [A-Za-z0-9_]![img](img/Python%EF%BC%9A%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F.img/F35A5971-3519-4CAE-8BEC-9DE8F4A55257.jpg) |

# Python中正则表达式的使用

re模块

re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()就返回none。

==re.match(pattern, str, flags=0)==：匹配成功re.match方法返回一个匹配的对象，否则返回None。

- pattern：匹配的正则表达式
- str：要匹配的字符串
- flags：标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等

代码示例如下：

```python
import re

print(re.match('www', 'www.wanggarrison.com').span())  # 在起始位置匹配
print(re.match('com', 'www.wanggarrison.com'))  # 不在起始位置匹配
```

输出结果如下：

```python
(0, 3)
None
```

==re.search(pattern, string, flags =0)==：扫描整个字符串并返回第一个成功的匹配

```python
import re
 
print(re.search('www', 'www.runoob.com').span())  # (0, 3)
print(re.search('com', 'www.runoob.com').span())  # (11, 14)
```

**re.match与re.search的区别：**re.match 只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None，而 re.search 匹配整个字符串，直到找到一个匹配。



