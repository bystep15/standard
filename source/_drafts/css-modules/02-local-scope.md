[原文](https://github.com/css-modules/css-modules/blob/master/docs/local-scope.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# CSS模块-本地作用域（CSS Modules — Local Scope）

The first and most fundamental feature of CSS Modules is that class selectors, by default, are local. So, if you write:

CSS模块中第一个也是最基本的特点是类选择器，通常，它们是本地的，如果您写：

```css
.backdrop {}
.prompt {}
.pullquote {}
```

the classes `backdrop`, `field` & `pullquote` are local to that file. That means they don't pollute the global namespace, so you're free to use any name you like. You compile them by importing or requiring them in your JS file. These examples will be using React syntax, but of course it's not tied to React in any particular way.

`backdrop`, `field` 和 `pullquote`类都是本地的文件。这意味着它们不会污染全局命名空间，所以您可以随意使用任何您喜欢的名字。您可以通过导入或在您的JS文件中引用它们来编译这些类。这些例子使用的是React的语法，但是当然它不以任何特定的方式与React绑定。

```js
import styles from "./style.css"

const Component = props => {
  return (
    <div className={styles.backdrop}>
      <div className={styles.prompt}>
      </div>
      <div className={styles.pullquote}>
      </div>
   </div>
  )
}
```
