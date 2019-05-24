## \<Redirect\>

在应用里，渲染这个\<Redirect>组件将会直接导航到一个新的路由地址，新的路由地址替换当前的history记录，类似服务器端（3XX）重定向操作。
应用场景之一：如果渲染某个路由页面需要做些权限验证，验证失败不能进入该页面，则直接渲染一个\<Redirect>跳转到指定路由地址。

### 组件属性配置

>* to : string | object
>* push : bool
>* from : string
>* exact : bool
>* strict : bool
##### to:string | object

string：要重定向到的URL,URL必须可以被[path-to-regexp@^1.7.0](https://github.com/pillarjs/path-to-regexp/tree/v1.7.0)正确解析。
```jsx
<Redirect to="/somewhere/else" />
```
object:
```jsx
<Redirect
  to={{
    pathname: "/login",
    search: "?utm=your+face",
    state: { referrer: currentLocation }
  }}
/>
```
*pathname*的值也需要通过[path-to-regexp@^1.7.0](https://github.com/pillarjs/path-to-regexp/tree/v1.7.0)验证

*state参数暂时不理解什么意思，等查阅相关文档后再补*

##### push:bool

\<Redirect>组件默认重定向是替换当前URL的，如果你需要新增一个URL保留当前URL,可以设置成 _true_
```jsx
<Redirect push to="/somewhere/else" />
```
##### from:string

当匹配到from 路径，则重定向到to路径。也可以传url模式匹配项,而且使用  _from_ 属性，必须嵌套在<Switch>组件里,to的地址可以是任意路由地址。
```jsx
<Switch>
  <Redirect from='/old-path' to='/new-path'/>
  <Route path='/new-path' component={Place}/>
</Switch>

// Redirect with matched parameters
<Switch>
  <Redirect from='/users/:id' to='/users/profile/:id'/>
  <Route path='/users/profile/:id' component={Profile}/>
</Switch>
```
##### exact:bool

是否开启完全匹配模式如果开启的话，下面代码只渲染\<Home\>组件，如果不开启，则<Home\>、<NewsFeed\>都渲染。
```jsx
  <Route exact path="/" component={Home}/>
  <Route path="/news" component={NewsFeed}/>
```

##### strict:bool

严格匹配from属性值。
*暂时不理解什么意思*