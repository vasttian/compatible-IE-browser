# compatible-IE-browser

## Some compatible with IE browser


#### 下面是基于 Vue，相应的可以移植到其他框架。

1. IE 中 Array 不支持 find 和 findIndex 方法
  现在的处理方法是：直接在项目的入口文件（`main.js`）中引入 (`import './utils/compatible-ie';`) `compatible-ie.js` 文件,
  在检测到数组的原型链（`Array.prototype`）上没有 find 和 findIndex 方法时，添加这两个方法。

2. IE 中 Promise 未定义 `'Promise' is undefined`
  在IE中报错 `Vuex requires a Promise polyfill in this browser`
  这里使用的是 [babel-polyfill](https://www.babeljs.cn/docs/usage/polyfill/)
  ```shell
  npm install -S babel-polyfill
  ```
  >因为这是一个 polyfill （它需要在你的源代码之前运行），我们需要让它成为一个 dependency, 而不是一个 devDependency.
  ~~PS: 其实 devDependency 也行~~

    需要在应用入口顶部通过 require 将 polyfill 引入进来。`require("babel-polyfill");`
    使用 ES6 的 `import` 语法，需要在入口顶部通过 import 将 polyfill 引入，以确保它能够最先加载：`import "babel-polyfill";`
    在 `webpack.base.config.js` 中，将 `babel-polyfill` 加到 entry 数组中:
```javascript
  module.exports = {
    entry: {
      app: [
        'babel-polyfill',
        './src/main.js'
      ]
    },
  };
```
