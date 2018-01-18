[原文](https://github.com/css-modules/css-modules)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# CSS模块（CSS Modules）

A CSS Module is a CSS file in which all class names and animation names are scoped locally by default. All URLs (`url(...)`) and `@imports` are in module request format (`./xxx` and `../xxx` means relative, `xxx` and `xxx/yyy` means in modules folder, i. e. in `node_modules`).

CSS模块是一个CSS文件，其中所有的类名称和动画名称都默认在本地的范围内。所有的URL(`url(...)`)和`@imports`都是模块请求格式（`./xxx`和`../xxx`表示相对定位，`xxx`和`xxx/yyy`表示模块内的文件夹，即在`node_modules`中）。

CSS Modules compile to a low-level interchange format called ICSS or [Interoperable CSS](https://github.com/css-modules/icss), but are written like normal CSS files:

CSS模块会编译成一个称为ICSS或[可交互操作的CSS](https://github.com/css-modules/icss)的低级可变格式，但是写起来就像像普通的CSS文件一样：

``` css
/* style.css */
.className {
  color: green;
}
```

When importing the CSS Module from a JS Module, it exports an object with all mappings from local names to global names.

当从一个JS模块中引入CSS模块时，它会导出一个包含从本地名称到全局名称的全部映射的对象。

``` js
import styles from "./style.css";
// import { className } from "./style.css";

element.innerHTML = '<div class="' + styles.className + '">';
```

## 命名（Naming）

For local class names camelCase naming is recommended, but not enforced.

对于本地类而言，建议使用驼峰命名法，但不强制使用。

> This is recommended because the common alternative, kebab-casing may cause unexpected behavior when trying to access style.class-name as a dot notation. You can still work around kebab-case with bracket notation (eg. `style['class-name']`) but `style.className` is cleaner.

> 这是推荐的方法，因为当尝试使用点获取类名，就像style.class-name时，使用常见的替代方法短横线隔开的方式可能会造成意想不到的结果。您仍然可以使用括号（例如`style ['class-name']`）来解决短横线隔开的方式，但是使用style.className会更清晰一些。

## 例外（Exceptions)

`:global` switches to global scope for the current selector respective identifier. `:global(.xxx)` respective `@keyframes :global(xxx)` declares the stuff in parenthesis in the global scope.

`:global`表示将当前选择器的作用域扩大到全局作用域相应的标识符。`:global(.xxx)`中的`@keyframes:global(xxx)`会在全局范围内声明括号中的内容。

Similarly, `:local` and `:local(...)` for local scope.

相似的，`:local`和`:local(...)`表示本地作用域。

If the selector is switched into global mode, global mode is also activated for the rules. (This allows us to make `animation: abc;` local.)

如果选择器切换到全局模式，那全局模式的规则也会起作用。（这里允许我们用`animation: abc;`来使规则本地化）

Example: `.localA :global .global-b .global-c :local(.localD.localE) .global-d`

例子：`.localA :global .global-b .global-c :local(.localD.localE) .global-d`

## 组成结构（Composition）

It's possible to compose selectors.

它允许结合选择器使用。

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

There can be multiple `composes` rules, but `composes` rules must be before other rules. Extending works only for local-scoped selectors and only if the selector is a single class name. When a class name composes another class name, the CSS Module exports both class names for the local class. This can add up to multiple class names.

这里有多个`compose`规则，但是`compose`规则必须在其他规则之前声明。当选择器是本地范围内，并选择器只是一个类名的情况下才会扩展项目。当一个类名结合另一个类名时，CSS模块会为本地类导出两个类名。这里也可以添加多个类名称。

It's possible to compose multiple classes with `composes: classNameA classNameB;`.

我们可以使用`composes: classNameA classNameB;`来结合多个类。

## 依赖（Dependencies）

### 与其他文件结合（Composing from other files）

It's possible to compose class names from other CSS Modules.

我们可以结合其他的CSS模块中的类名。 

``` css
.otherClassName {
  composes: className from "./style.css";
}
```

Note that when composing multiple classes from different files the order of appliance is undefined. Make sure to not define different values for the same property in multiple class names from different files when they are composed in a single class.

请注意，从不同文件组合多个类时，应用的顺序是不确定的。当在一个类中组合不同的文件时，请确保不要为多个类名中的相同属性定义不同的值。

Note that composing should not form a circular dependency. Elsewise it's undefined whether properties of a rule override properties of a composed rule. The module system may emit an error.

还请注意，当我们组合时要避免形成循环依赖。否则，它不确定一个规则的属性是否会覆盖组合规则的属性。从而导致模块系统报错。

Best if classes do a single thing and dependencies are hierarchic.

最好的情况就是类只做一件事，并且依赖是可以分级的。

### 结合全局作用域的类名（Composing from global class names）

It's possible to compose from global class names.

我们可以通过global来使用全局作用域下的类名。

```css
.otherClassName {
  composes: globalClassName from global;
}
```

## 预处理器的用法（Usage with preprocessors）

Preprocessors can make it easy to define a block global or local.

预处理器可以让定义一个全局块元素或者本地块元素变得更简单。

例如使用less.js（i. e. with less.js）

``` less
:global {
  .global-class-name {
    color: green;
  }
}
```

## 为什么？（Why?）

modular and reusable CSS!

* No more conflicts.
* Explicit dependencies.
* No global scope.

为了生成模块化和可重用性的CSS!

* 没有更多的冲突
* 明确的依赖关系
* 没有全局作用域

## 例子（Examples）

* [css-modules/webpack-demo](https://github.com/css-modules/webpack-demo)
* [outpunk/postcss-modules-example](https://github.com/outpunk/postcss-modules-example)
* [主题化（Theming）](docs/theming.md)
* [css-modules/browserify-demo](https://github.com/css-modules/browserify-demo)
* [x-team/starting-css-modules](https://github.com/x-team/starting-css-modules)

## 历史（History）

* 04/2015: `placeholders` feature in css-loader (webpack) allows local scoped selectors (later renamed to `local scope`) by @sokra
* 05/2015: `postcss-local-scope` enables `local scope` by default (see [blog post](https://medium.com/seek-ui-engineering/the-end-of-global-css-90d2a4a06284)) by @markdalgleish
* 05/2015: `extends` feature in css-loader allow to compose local or imported class names by @sokra
* 05/2015: First CSS Modules spec document and github organization with @sokra, @markdalgleish and @geelen
* 06/2015: `extends` renamed to `composes`
* 06/2015: PostCSS transformations to transform CSS Modules into an intermediate format (ICSS)
* 06/2015: Spec for ICSS as common implementation format for multiple module systems by @geelen
* 06/2015: Implementation for jspm by @geelen and @guybedford
* 06/2015: Implementation for browserify by @joshwnj, @joshgillies and @markdalgleish
* 06/2015: webpack's css-loader implementation  updated to latest spec by @sokra


* 04/2015: 由@sokra提出在CSS加载器（webpack）中的`placeholders`允许使用本地作用域的选择器（之后重命名为`local scope`）
* 05/2015: 由@markdalgleish提出`postcss-local-scope`默认启用`local scope`（详情请见[blog post](https://medium.com/seek-ui-engineering/the-end-of-global-css-90d2a4a06284)）
* 05/2015: 由@sokra提出在CSS加载器中`extend`特性允许组合本地或者导入的类名
* 05/2015: 由@sokra, @markdalgleish和@geelen首先提出了CSS模块规范文档和github项目
* 06/2015: 将`extend`重命名为`composes`
* 06/2015: 通过使用PostCSS转换的方式将CSS模块转换为中间格式（ICSS）
* 06/2015：由@geelen提出将ICSS作为多模块系统作为通用的实现格式的规范文档
* 06/2015：由@geelen和@guybedford实现jspm
* 06/2015: 由@joshwnj, @joshgillies和@markdalgleish执行browserify
* 06/2015: 由@sokra将webpack的CSS加载器更新为最新的规范标准

## 实施（Implementations）

### webpack

Webpack's [css-loader](https://github.com/webpack/css-loader) in module mode replaces every local-scoped identifier with a global unique name (hashed from module name and local identifier by default) and exports the used identifier.

在模块模式中，webpack的[CSS加载器](https://github.com/webpack/css-loader)通过使用全局唯一的名称（默认情况下从模块名称和本地标识符的角度考虑名称）替换每个本地作用域标识符，并导出正在使用的标识符。

Extending adds the source class name(s) to the exports.

将源类的名称扩展添加到导出的类名称里面。

Extending from other modules first imports the other module and then adds the class name(s) to the exports.

首先从其他模块的扩展导入到另一个模块，然后将类名添加到导出模块里面。

### 服务端和静态网站（Server-side and static websites）

[PostCSS-Modules](https://github.com/outpunk/postcss-modules) allows to use CSS Modules for static builds and the server side with Ruby, PHP or any other language or framework.

[PostCSS-Modules](https://github.com/outpunk/postcss-modules)运行我们为使用CSS模块进行静态构建，服务器端选择使用Ruby，PHP或任何其他语言或框架。
