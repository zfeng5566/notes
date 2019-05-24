# history

history接口使用[history](https://github.com/ReactTraining/history)库，主要为了兼容多个运行环境的统一，例如在APP页面，web浏览器，React Native环境等等。

## history 属性

### length ：number

历史记录栈的长度

### action : string
行为，有`PUSH`、`REPLACE`、`POP`。

### location : object
当前的导航位置，有如下属性：
> * pathname - (string) URL路径
> * search - (string) URL查询字符串
> * hash - (string) URL的hash标识串
> * state - (object) 给location 自定义的参数
> 
## history 方法
### push(path, [state])
创建一个新的历史记录，插入到url会话历史记录数组里。

### replace(path, [state])
创建一个新的历史记录，替换当前的url会话记录。

### go(n)
通过当前页面的相对位置从浏览器历史记录( 会话记录 )加载页面。比如：参数为-1的时候为上一页，参数为1的时候为下一页. 当整数参数超出界限时( 译者注:原文为When integerDelta is out of bounds )，例如: 如果当前页为第一页，前面已经没有页面了，我传参的值为-1，那么这个方法没有任何效果也不会报错。调用没有参数的 go() 方法或者不是整数的参数时也没有效果。( 这点与支持字符串作为url参数的IE有点不同)。

### goBack()
回退，相当于go(-1)

### goForward()
前进，相当于go(1)

### block(prompt)
阻止导航行为
