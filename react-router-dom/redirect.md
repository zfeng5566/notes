##\<Redirect\>

在应用里，渲染这个\<Redirect>组件将会直接导航到一个新的路由地址，新的路由地址替换当前的history记录，类似服务器端（3XX）重定向操作。
应用场景之一：如果渲染某个路由页面需要做些权限验证，验证失败不能进入该页面，则直接渲染一个\<Redirect>跳转到指定路由地址。

###组件属性配置
#####to:string | object

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

#####push:bool

\<Redirect>组件默认重定向是替换当前URL的，如果你需要新增一个URL保留当前URL,可以设置成 _true_
```jsx
<Redirect push to="/somewhere/else" />
```