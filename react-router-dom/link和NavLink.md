# <Link\>
为你的应用提供声明式，无障碍导航。

> * to : string | object
> * replace : boolean
> * innerRef : function | RefObject
> * to : string | object
> * to : string | object

### to : string | object
跳转到指定路径。
字符串形式：可以包含`pathname`、`search`、`hash`参数.
```jsx
<Link to="/courses?sort=name#type=abc" />
```
object对象形式可以包含上述三个参数还可以包含`state`参数。
```jsx
<Link
  to={{
    pathname: "/courses",
    search: "?sort=name",
    hash: "#the-hash",
    state: { fromDashboard: true }
  }}
/>
```

### replace : boolean
当为`true`时，新的url地址替换当前的url地址。否则就会创建新的url地址。

#\<NavLink>
一种高级版本的 **\<Link>** 组件，有激活配置属性，与当前url地址相同时，会激活`activeClassName`和`activeStyle`配置的属性。我们可以添加激活样式。

### activeClassName : string
当激活时，应用的样式名，默认样式名为`active`。
```jsx
<NavLink to="/faq" activeClassName="selected">
  FAQs
</NavLink>
```

### activeStyle : object
当激活时，应用的内联样式属性。
```jsx
<NavLink
  to="/faq"
  activeStyle={{
    fontWeight: "bold",
    color: "red"
  }}
>
  FAQs
</NavLink>
```

### exact : boolean
当为`true`时，必须完全匹配url，才会启动激活状态。
```jsx
<NavLink exact to="/profile">
  Profile
</NavLink>
```
### strict : boolean
当为`true`时，在确定是否匹配当前URL时，将考虑路径名尾部斜杠。即组件路径尾部斜杠也参与校验是否匹配。

### isActive : function
用于创建自定义激活状态是否启动。当函数返回`true`启动组件状态。
```jsx
const oddEvent = (match, location) => {
  if (!match) {
    return false
  }
  const eventID = parseInt(match.params.eventID)
  return !isNaN(eventID) && eventID % 2 === 1
}

<NavLink
  to="/events/123"
  isActive={oddEvent}
>Event 123</NavLink>
```

### aria-current : string
在激活状态下`aria-current`属性使用的值，默认为`page`。可选项为`page` `step` `location` `date` `time` `true`。



