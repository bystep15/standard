[原文](https://github.com/css-modules/css-modules/blob/master/docs/import-multiple-css-modules.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 在一个组件中导入多个CSS模块（Import multiple css modules into a component）

You can import multiple css modules into a component or function using `Object.assign`
For example if you import a button css modules to your Demo component, add this to the components default styles.

您可以使用`Object.assign`将多个css模块导入到一个组件或者函数中。例如，如果您要将一个按钮的CSS模块导入到您的示例组件中，请将其导入到组件的默认样式中。

```js
let styles = {}
import demo from './Demo.css'
import fancyButton from 'css-fancy-button'
Object.assign(styles, fancyButton, demo)
```

You can even import css modules installed from npm. e.g. [pure-css](https://github.com/StevenIseki/pure-css)

您甚至可以从npm通过安装像[pure-css](https://github.com/StevenIseki/pure-css)这样的组件导入CSS模块。

```sh
npm install pure-css --save-dev
```

Then in your component... start using pure css styles.

然后在您的组件中，开始使用pure-css的样式。

```js
import { buttons, grids } from 'pure-css'
```

A full example of a demo component with 2 css modules imported.

一个导入两个css模块的示例组件的完整的例子。

```jsx
import React from 'react'
let styles = {}
import demo from './Demo.css'
import fancyButton from 'css-fancy-button'
Object.assign(styles, fancyButton, demo)

function Demo( props) {

    const { route } = props;

    return (
    	<div className={styles.demo}>
    		<button className={styles.fancyButton}>press me</button>
       	</div>
    );
}

export default Demo
```
