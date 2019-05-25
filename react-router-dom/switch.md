# <Switch\>
被<Switch\>组件包裹下，<Route\>和<Redirect\>只会渲染第一个匹配到的组件。
当碰到`/about`路径，下面的三个路由都会渲染，因为每个路由的path都会匹配成功。
```jsx
// /about 路径，三个路由都会渲染。
<Route path="/" component={Home}/>
<Route path="/about" component={About}/>
<Route path="/:user" component={User}/>
```


有时候，我们需要只渲染第一个匹配成功的路由，在这需求下，我们需要使用<Switch\>组件来包裹路由。
```jsx
//只会渲染一个路由。
<Switch>
 <Route exact path="/" component={Home}/>
  <Route path="/about" component={About}/>
  <Route path="/:user" component={User}/>
  <Route component={NoMatch}/>
</Switch>
```
<Switch\>组件的`children`只能<Route\>或<Redirect\>组件。<Route\>的渲染规则是`path`属性与`location`匹配成功，<Redirect\>的渲染规则是`from`属性值与`location`匹配成功。

### location : object
默认情况下，使用当前**历史记录地址**与子路由组件进行匹配，如果传入`location`属性，将使用`location`与子路由组件进行匹配，通常情况下，我们不需要使用这个属性。
