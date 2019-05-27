# \<Router>
一个低阶组件，给其他高阶路由组件提供公共的接口，通常我们的应用应该使用下面的高阶路由组件：
> * <BrowserRouter\>
> * <HashRouter\>
> * <MemeryRouter\>
> * <NativeRouter\>
> * <StaticRouter\>

# \<BrowserRouter>
这是一个采用**HTML5** `history` API (`pushState`,`replaceState`,`popstate`事件)的路由组件。

#### basename : string
给所以应用提供一个基础的前缀路径，`basename`尾部不能加`/`。
```jsx
<BrowserRouter basename="/calendar" />
<Link to="/today"/> // renders <a href="/calendar/today">
```
#### getUserConfirmation : function
第一次进入应用时，执行的函数，用于确认相关信息，给与提示。(无法阻止进入页面)。默认使用`window.confirm`。通常不会用到这个参数。
```jsx
function getConfirmation(message,callback) {
    const allowTransition = window.confirm(message);
    callback(allowTransition);
    
}
<BrowserRouter getUserConfirmation={getConfirmation('欢迎光临',function(){})}>
</BrowserRouter>
```
### forceRefresh : boolean
当为`true`，每次路由的跳转，都会刷新一下页面。*效果如：进入新的路由页面，手动刷新页面*。通常用于浏览器不支持**HTML5 history API**的时候。
```jsx
const supportsHistory = 'pushState' in window.history
<BrowserRouter forceRefresh={!supportsHistory} />
```

### keyLength : number
设置`location.key`的长度。默认为6。(key的作用：当点击同一个链接，每次路由下的`location.key`都会变化，通过`key`的变化来引发组件的渲染。点击同一个链接都会创建新的url访问记录。)

### children : node
要渲染的子组件

# \<HashRouter>
使用`location.hash`机制，来维持UI与URL的同步。用于不支持**HTML5 history API**的浏览器。兼容性高。不支持`location.key`和`location.state`。

### basename : string
同 **\<BowserRouter>** 的`basename`属性。

### getUserConfirmation : function
同 **\<BowserRouter>** 的`basename`属性。

### hashType : string
`location.hash`前缀格式。如下：

> * "slash" : #/sunshine/lollipops 的hash串
> * "noslash" : #sunshine/lollipops 的hash串
> * "hashbang" : #!/sunshine/lollipops 的hash串

# \<MemoryRouter>
用于非浏览器环境下，例如：`React Native`。该组件在运行环境内存中，实例化一套URL历史回话记录机制。可以让UI同该URL保持同步.

### initialEntries : array
用于初始化应用URL访问记录数组。每个访问记录是包含`{ pathname, search, hash, state }`的`location`对象或者`URL`字符串。

### initialIndex : number
`initialEntries`数组的初始化的下标。会话历史记录的索引。
```jsx
<MemoryRouter
  initialEntries={["/one", "/two", { pathname: "/three" }]}
  initialIndex={1}
>
  <App />
</MemoryRouter>
```

### getUserConfirmation : function
同<BowserRouter\>，要配合<Prompt\>使用。

### keyLength: number
同<BowserRouter\>。

### children: node
同<BowserRouter\>。
