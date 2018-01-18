[原文](https://github.com/css-modules/css-modules/blob/master/docs/pseudo-class-selectors.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 伪类选择器（Pseudo class selectors）

Because css modules works by adding classes to your elements you can easily add pseudo class selectors.

因为css模块是通过向元素添加类来完成工作的，所以您可以轻松地添加伪类选择器。

```css
/* component/text.css */
.text {
  color: #777;
  font-weight: 24px;
}
.text:hover {
  color: #f60;
}
```
``` js
/* component/text.js */
import styles from './text.css';

import React, { Component } from 'react';

export default class Text extends Component {

  render() {
    return (
      <p className={ styles.text }>Text with hover</p>
    );
  }

};
```
