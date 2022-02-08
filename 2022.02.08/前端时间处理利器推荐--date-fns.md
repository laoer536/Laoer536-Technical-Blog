前端时间处理利器推荐--date-fns

在开发本博客项目中，原来每篇文章时间戳显示的是发布的具体时间，我认为这个不够直观和贴近，于是想到了处理为相对时间，然而我是个懒人，用原生JS的Date去处理或许不够方便，于是我想有没有一种功能强大、且轻量的时间处理库呢？几经捣鼓，我发现了它，date-fns。

**前端时间处理相关库**

[Moment.js 中文网 (momentjs.cn)](http://momentjs.cn/)

[Day.js · 中文文档 - 2kB 大小的 JavaScript 时间日期库 (gitee.io)](https://dayjs.gitee.io/zh-CN/)

[date-fns - modern JavaScript date utility library](https://date-fns.org/)

在使用时对比：`Moment.js`功能强大，但重。`Day.js`轻但功能上有所欠缺。`date-fns`轻并且提供了很多时间处理方法，支持按需导入，Nice！



`date-fns`特点：

API数量多,全面,健壮: 数量高达180+
模块化: 使用的时候引入自己需要的API即可,轻便
不可变性和纯粹性: API都是纯函数
支持TS
支持国际化



**如何使用**

安装

```
# 安装
# 使用npm
npm install --save date-fns

# 或使用yarn
yarn add date-fns
```



引入`date-fns`方法

```js
//还有很多实用方法
import {
  differenceInMinutes,
  parseISO,
  format,    
} from "date-fns";
```



使用

1.日期格式化

```js
const formatDate = format(new Date(), "yyyyMMdd_HHmm") 
```

2.时间字符串转Date

```js
const myDate = parseISO(article.createdAt as string);
const date = parseISO('1990-12-17'); // Mon Dec 17 1990 00:00:00 GMT+0800 (中国标准时间)
```

3.获取相对时间

```js
const differenceMinutes = differenceInMinutes(new Date(),parseISO(article.createdAt as string)); //得到相差的分钟数
const tomorrow = addDays(new Date(), 1); // 明天,其它的方法类似,如: addHours / addMinutes 等 以add开头 对应之后的时间
const yesterday = subDays(new Date(), 1); // 昨天, 其它的方法类似,如: subYears / subMonths 等 以sub开头 对应之前的时间
```

4.判断当前时间是否满足条件

```js
const day = new Date();
console.log(isToday(day)); // 结果为: true

const date = new Date();
console.log(isYesterday(date)); //结果false

//另外还有isTomorrow()
```

5.其他

探索中...



感谢阅读，如有错误欢迎评论说明。谢谢😄