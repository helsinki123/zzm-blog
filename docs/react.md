```
这样带来的好处是显而易见的：“高度聚合，可阅读性提升”。伴随而来的便是 “效率提升，bug变少”。

vue中大部分场景是不需要用render函数的,还是用模板更简洁直观.

函数式组件无状态，无this实例

总结一下吧，我们平时开发还是多用temlate因为直观简洁，各种指令用着很方便，
等你觉得用template写出的代码看着很冗余，或者想自己控制渲染逻辑比如循环，判断等等时可以考虑用JSX。
另外推荐大家多用函数式组件提高性能。

 styled-components是为React或者类似组件化框架提供 标签+样式 的组合

memo
const MyComponent = React.memo(function MyComponent(props) {
  /* 使用 props 渲染 */
});
以此通过记忆组件渲染结果的方式来提高组件的性能表现。这意味着在这种情况下，React 将跳过渲染组件的操作并直接复用最近一次渲染的结果

react路由使用 https://www.jianshu.com/p/8954e9fb0c7e

 useEffect, useState？？withModel

React Suspense让我们轻松定义延迟加载的组件
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
在<OtherComponent />外面使用Suspense标签，并在fallback中声明OtherComponent加载完成前做的事，即可优化整个页面的交互
```
