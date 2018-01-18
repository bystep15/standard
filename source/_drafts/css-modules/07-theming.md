[原文](https://github.com/css-modules/css-modules/blob/master/docs/theming.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 主题化（Theming）

Instead of importing a style in the component, the component can take a style as property. This way different themes can be used. The user can even define custom themes.

不像在组件中导入样式一样，组件可以将样式看作是一个属性。这样可以使用不同的主题。用户甚至还可以自定义主题样式。

``` css
/* component/theme-a.css */
.outer { background: green; }
.inner { color: blue; }
```

``` css
/* component/theme-b.css */
.outer { background: red; }
.inner { color: yellow; }
```

``` js
/* component/index.js */
export default class Component {
  constructor(theme) {
    this.theme = theme;
  }
  render() {
    var theme = this.theme;
    return '<div class="' + theme.outer + '">' +
      '<div class="' + theme.inner + '">' +
      '</div></div>';
  }
}
```

``` js
/* application */
import themeA from "component/theme-a.css";
import themeB from "component/theme-b.css";
import customTheme from "./custom-theme.css";

import Component from "component";

// use the Component
new Component(themeA);
new Component(themeB);
new Component(customTheme);
```
