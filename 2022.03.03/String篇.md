## String篇

> 先假设定义一个字符串
>
> let string = ‘hello world’；
>
> let searchString = ‘wo’;

1.string.length---获取字符串长度string.length(会记入空格，从1开始计数)



2.获取指定字符串的位置

a)  string.indexOf(searchString) ---头向尾找  也可以用于值集合的数组，也类似于数组的findIndex方法

b)  string.lastIndexOf(searchString) ---尾向头找

> 结果不同：除开是否有“last”之外影响两者结果的决定因素为第二个参数，第二个参数可选，为数字，表示从数字指定的位置从头向尾找还是尾向头找

(c) string.search(pattern) ---返回符合规则字符/串的位置，没找到返回-1；

(d) 另外用于类似的，只不过不是返回位置，而是返回布尔值，第二个参数同indexOf和lastindexOf,表示从那个位置开始判断。

>  i.     string.startWith(“XXXX”)        ii.     string.endWith(“XXXX”) 可用于判断后缀



3.正则匹配

a)  let pattern = /   /;  ---pattern代表正则表达式

b)  pattern.exec(string) ---等同于string.match(pattern)

c)  pattern.test(string) ---检测字符串中是否存在某个约定规则的字符串 返回true / false

d)  补充string.search(pattern),返回符合规则字符/串的位置，没找到返回-1；更像是indexOf和lastIndexOf的升级版



4.string.charAt ---获取指定位置的字符string.charAt(数字)，数字代表指定的位置



5.字符串截取 --- 字符串提取多个字符，指定其实位置，返回这段位置的字符串，用slice或者subString，或者substr。



6.分割字符串为数组 ---字符串根据特定符号分割为数组，用split('特定符号')



7.字符串拼接 ---使用concat或者“+”号，不影响原字符串，返回一个新的字符串供使用。



8.清除字符串首尾空格

> a)  清除首空格string.strimLeft()或者string.trimStart()
>
> b)  清除尾空格string.strimRight()或者string.trimEnd ()

9.字符串复制 ---string.repeat(数字)，数字表示复制多少次

> 扩展：指定内容和长度的复制
>
> a)  string.padStart(指定包括原来的最终长度，‘填充的内容’)
>
> b)  string.padEnd(指定包括原来的最终长度，‘填充的内容’)
>
> c)  两者分别表示在字符串前面或者后面复制加入什么内容直到达到指定的最终长度

10.字符串替换

>   a)  指定内容替换：string.replace(‘指定被替换的内容’,’指定替换上去的内容’)，之替换从左至右匹配到的第一个内容
>
>   b)  指定规则替换：string.replace(pattern,”指定替换上去的内容”)，此可以实现替换多个，取决于pattern的正则怎么写。一般正则指定是全局的话那么       就是替换全部的指定内容了。

11.特性（由此可见很多情况下两者有些时候是可以互相转换的，部分语法是可以共用的，通过特定的方法）

>   a)   String原型上有@@interator方法，故可以使用for let of来遍历出其中的每一个字符
>
>   b)   String原型上有@@interator方法，字符串转化为数组[…string]或者Array.from(string)



12.大小写转换 ---string.toLowerCase() && string.toUpperCase()