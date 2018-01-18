[原文](https://github.com/css-modules/css-modules/blob/master/docs/values-variables.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 导出值变量（Exporting values variables)

You can export values with css modules similar to using variables in less or sass.

您可以像在less或者sass使用变量一样，用css模块导出值。

Just ensure you are using postcss and the [postcss-modules-values](https://github.com/css-modules/postcss-modules-values) plugin

确保您在使用postcss和[postcss-modules-values](https://github.com/css-modules/postcss-modules-values) 插件

现在，您可以设置您的值/变量（Now you set up your values/variables）

**colors.css**

```css
@value blue: #0c77f8;
@value red: #ff0000;
@value green: #aaf200;
```

then import them into your components css module

然后在您的css模块组件中导入它们

**demo.css**

```css
/* import your colors... */
@value colors: "./colors.css";
@value blue, red, green from colors;

.button {
  color: blue;
  display: inline-block;
}
```

## 使用webpack.config对postcss-modules-values进行设置的例子（Example webpack.config for postcss-modules-values）

```js
var path = require('path');
var webpack = require('webpack');
var ExtractTextPlugin = require('extract-text-webpack-plugin');
var values = require('postcss-modules-values');

module.exports = {
  entry: ['./src/index'],
  output: {
    filename: 'bundle.js',
    path: path.join(__dirname, 'public'),
    publicPath: '/public/'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test: /\.css$/, loader: ExtractTextPlugin.extract('style-loader', 'css-loader?modules&importLoaders=1&localIdentName=[name]__[local]___[hash:base64:5]!postcss-loader') }
    ]
  },
  postcss: [
    values
  ],
  plugins: [
    new ExtractTextPlugin('style.css', { allChunks: true })
  ]

};
```
