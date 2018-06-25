# compatible-IE-browser

## Some compatible with IE browser


#### 下面是基于 Vue，相应的可以移植到其他框架。

1. IE 中 Array 不支持 find 和 findIndex 方法
  现在的处理方法是：直接在项目的入口文件（`main.js`）中引入 (`import './utils/compatible-ie';`) `compatible-ie.js` 文件,
  在检测到数组的原型链（`Array.prototype`）上没有 find 和 findIndex 方法时，添加这两个方法。

