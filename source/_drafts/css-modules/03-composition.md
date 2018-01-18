[原文](https://github.com/css-modules/css-modules/blob/master/docs/composition.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 组合（Composition）

It's possible to compose selectors.

我们可以组合使用选择器。

``` css
.className {
  color: green;
  background: red;
}

.otherClassName {
  composes: className;
  color: yellow;
}
```
