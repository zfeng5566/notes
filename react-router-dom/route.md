# \<Route>

这是一个经常用到的组件，非常重要。基础用法是：当location匹配到 **path** 属性值，就会渲染响应组件UI到\<Route>里。\<Route>包含如下属性：

> * **component** : \<Component>
> * **render** : function
> * **children** : function
> * **path** : string | string[]
> * **exact** : boolean
> * **strict** : boolean
> * **location** : object
> * **sensitive** : boolean

## \<Route> 渲染方式

### \<Route> 有三种渲染方式
> * **\<Route component\>**
> * **\<Route render>**
> * **\<Route children>**

每种方式使用不同的情况，多数情况下 我们只用**component**属性即可。这三种渲染方式都会给**渲染组件**或**渲染函数** 传递三个属性
> * **match**
> * **location**
> * **history**

------

#### component:\<Component> | function
当location匹配到**path**，则渲染**component**组件,如下：
```jsx
<Route path="/user/:username" component={User} />;

function User({ match }) {
  return <h1>Hello {match.params.username}!</h1>;
}
```
component可以是一个内联函数，每次render渲染，component都会创建新的组件。这意味着每次渲染旧组件卸载，新组件渲染，而不是组件更新。我们应该避免使用这种写法。

#### render : function

render只接受函数,不同于component函数渲染方式，render不会引起重复卸载和创建组件。render接受一个函数返回的组件，这意味着我们可以在这个函数里，做一些逻辑判断处理,返回不同的组件。
```jsx
<Route path="/home" render={(props) => <div>Home</div>}/>
<Route path="/user" render={(props) => 
true 
? 
<div>Home</div>
:
<div>User</div>
}/>

```

#### children : function

children只接受函数,无论**path**是否匹配都会渲染组件。渲染时，children函数接受match,history,location三个参数作为props传入。如果不匹配**match**为 `null`,如果匹配则为`object`。
```jsx
<div>
    <Route path='/' exact component={Index}></Route>
    <Route path='/about/'  component={About}></Route>
   
    <Route path='/abc' children={
        (props)=>{
            console.log(props);
            return <Child/>
        }
    }></Route>
</div>
```

#### path : string | string[ ]

任何通过[path-to-regexp@^1.7.0](https://github.com/pillarjs/path-to-regexp/tree/v1.7.0)验证的**字符串**或**字符串集合**。匹配成功则渲染路由下的组件。

```jsx
<Route path={["/users/:id", "/profile/:id"]} component={User} />
//或
<Route path="/users/:id" component={User} />
```
#### exact : boolean
当为`true`的时候，`path`属性必须完全匹配`location.pathname`，才会渲染组件。

| path | location.pathname | exact|matchs?|
| ---- | -----             | ---- | ----  |
|/one  | \/one/two         | true | no    |
|/one  | \/one/two         | false| yes   |

#### strict : boolean

是否匹配尾斜杠`/`,当为`true`时,如果`path`末尾带着`/`,`location.pathname`末尾 无`/`且没有多余的片段，就会匹配失败，其它情况匹配成功。

| path  | location.pathname | strict|matchs?|
| ----  | ----------------- | ----  | ----  |
| /one/ | \/one/two         | true  | yes   |
| /one  | \/one/            | true  | yes   |
| /one/ | \/one             | true  | no    |

#### sensitive : boolean

大小写是否敏感,`true`则大小写敏感。`false`忽略大小写。默认为`false`。
