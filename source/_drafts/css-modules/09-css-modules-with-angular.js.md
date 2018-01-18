[原文](https://github.com/css-modules/css-modules/blob/master/docs/css-modules-with-angular.js.md)

<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 使用angular.js的CSS模块（CSS Modules with Angular.js）

```css
.bacon { /* ... */ }
.pancakes { /* ... */ }
```

```js
import styles from "./component.css"

class MyController {
    constructor($scope) {
        $scope.styles = styles;
    }
}

angular.module('myApp').controller('MyController', ['$scope', MyController])
```

```html
<div ng-app="myApp">
    <div ng-controller="MyController">
        <header class="{{styles.bacon + ' ' + styles.pancakes}}">
            <h1 class="{{styles.pancakes}}">pancakes (2-way binding)</h1>
            <h1 ng-class="styles.bacon">bacon</h1>
            <!-- ... -->
        </header>
    </div>
</div>
```

---

## 使用angular.js 1.5 组件的CSS模块（CSS Modules with angular.js 1.5 component）

```css
.content { /* ... */ }
.bacon { /* ... */ }
.pancakes { /* ... */ }
```

```js
import angular from 'angular'
import styles from './index.css'

const template = `
    <div class="${styles.content}">                   
        <div class="${styles.pancakes}">pancakes</div>
        <div ng-class="'${styles.bacon}'">bacon</div>
    </div>
`;

angular
    .module('app', [])
    .component('myComponent', {
        template
    });
```

This needs expansion/revision by someone who really knows angular. Maybe that's you!

这部分内容需要真正了解angular的人来扩展和修改。也许就是您！

- [ ] Angular 2.0 syntax

- [ ] Angular 2.0 语法
