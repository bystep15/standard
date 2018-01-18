[原文](https://github.com/css-modules/css-modules/blob/master/docs/get-started.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 设置CSS模块（Setting up CSS Modules）

CSS Modules works by compiling individual CSS files into both CSS and data. The CSS output is normal, global CSS, which can be injected directly into the browser or concatenated together and written to a file for production use. The data is used to map the human-readable names you've used in the files to the globally-safe output CSS.

CSS模块的工作原理是将各个CSS文件编译为CSS和数据。CSS输出是正常的全局CSS，它可以直接注入到浏览器中，也可以和其他CSS一起写入文件以供开发使用。其中数据用于将您在文件中使用的具有可读性的名称映射到全局中安全的CSS文件中。

There are currently 4 ways to integrate CSS Modules into your project. You should look to each of these projects for more detailed setup instructions. 

目前有4种方法将CSS模块集成到您的项目中。你可以看看这些项目中更详细的设置说明。

### Webpack

The [css-loader](https://github.com/webpack/css-loader) has CSS Modules built-in. Simply activate it by using the `?modules` flag. We maintain an example project using this at [css-modules/webpack-demo](https://github.com/css-modules/webpack-demo).

[CSS加载器](https://github.com/webpack/css-loader)内置了CSS模块。只需简单的使用`?modules`标签就可以激活它。[css-modules/webpack-demo](https://github.com/css-modules/webpack-demo)是我们维护的一个示例项目。

### Browserify

The plugin [css-modulesify](https://github.com/css-modules/css-modulesify) gives your Browserify build the ability to `require` a CSS file and compile it as a CSS Module. For an example project using this setup, check out [css-modules/browserify-demo](https://github.com/css-modules/browserify-demo).

[css-modulesify](https://github.com/css-modules/css-modulesify)插件可以使您的Browserify有构建成`require`的CSS文件能力并可以将其编译为CSS模块。 请点击[css-modules/browserify-demo](https://github.com/css-modules/browserify-demo)查看示例项目。

### JSPM

The experimental JSPM loader [jspm-loader-css-modules](https://github.com/geelen/jspm-loader-css-modules) adds CSS Modules support to SystemJS & JSPM. There's a simple project using this at [css-modules/jspm-demo](https://github.com/css-modules/jspm-demo).
 
试验性的JSPM加载器[jspm-loader-css-modules](https://github.com/geelen/jspm-loader-css-modules)为SystemJS和JSPM提供了了CSS的模块支持。在[css-modules/jspm-demo](https://github.com/css-modules/jspm-demo)中有一个简单的项目。

### NodeJS

The [css-modules-require-hook](https://github.com/css-modules/css-modules-require-hook) works similarly to the Browserify plugin, but patches NodeJS's `require` to interpret CSS files as CSS Modules. This gives complete flexibility in how the output is handled, ideal for server-side rendering.

[css-modules-require-hook](https://github.com/css-modules/css-modules-require-hook)与Browserify插件的工作方式类似，但是所需的NodeJS的`require`会将CSS文件编译为CSS模块。这为输出处理CSS提供了非常大的灵活性，是服务器端渲染的理想选择。

## 语言整合（Language integrations)

### React

If you're using React, CSS Modules is a great fit. [react-css-modules](https://github.com/gajus/react-css-modules) adds a `CSSModules` higher-order component or `@CSSModules` annotation for better integrating CSS Modules & React.

如果您在使用React，那么使用React的CSS模块会非常适合。[react-css-modules](https://github.com/gajus/react-css-modules)添加`CSSModules`的高级组件或`@CSSModules`注释，以便可以更好地集成CSS模块和React。

### Deku

If you're using Deku, CSS Modules is an awesome fit. [deku-css-modules](https://github.com/StevenIseki/deku-css-modules) allows for easy integration of CSS Modules & Deku.

如果您在使用Deku，那么Deku的CSS模块是一个很好的选择。[deku-css-modules](https://github.com/StevenIseki/deku-css-modules)允许我们更好的继承CSS模块和Deku。
