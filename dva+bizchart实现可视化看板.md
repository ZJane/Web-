# 环境配置

## 安装 dva-cli

通过 npm 安装 dva-cli 并确保版本是 `0.9.1` 或以上。

```bash
$ npm install dva-cli -g
$ dva -v
dva-cli version 0.9.1
```


## 创建新应用

安装完 dva-cli 之后，就可以在命令行里访问到 `dva` 命令（[不能访问？](http://stackoverflow.com/questions/15054388/global-node-modules-not-installing-correctly-command-not-found)）。现在，你可以通过 `dva new` 创建新应用。

```bash
$ dva new dva-quickstart
```

这会创建 `dva-quickstart` 目录，包含项目初始化目录和文件，并提供开发服务器、构建脚本、数据 mock 服务、代理服务器等功能。

然后我们 `cd` 进入 `dva-quickstart` 目录，并启动开发服务器：

```bash
$ cd dva-quickstart
$ npm start
```

几秒钟后，你会看到以下输出：

```bash
Compiled successfully!

The app is running at:

  http://localhost:8000/

Note that the development build is not optimized.
To create a production build, use npm run build.
```

在浏览器里打开 http://localhost:8000 ，你会看到 dva 的欢迎界面。

## 使用 antd

通过 npm 安装 `antd` 和 `babel-plugin-import` 。`babel-plugin-import` 是用来按需加载 antd 的脚本和样式的，详见 [repo](https://github.com/ant-design/babel-plugin-import) 。

```bash
$ npm install antd babel-plugin-import --save
```

编辑 `.webpackrc`，使 `babel-plugin-import` 插件生效。

```diff
{
+  "extraBabelPlugins": [
+    ["import", { "libraryName": "antd", "libraryDirectory": "es", "style": "css" }]
+  ]
}
```

> 注：dva-cli 基于 roadhog 实现 build 和 dev，更多 `.webpackrc` 的配置详见 [roadhog#配置](https://github.com/sorrycc/roadhog#配置)

## 定义路由

我们要写个应用来先显示产品列表。首先第一步是创建路由，路由可以想象成是组成应用的不同页面。

新建 route component `routes/Products.js`，内容如下：

```javascript
import React from 'react';

const Products = (props) => (
  <h2>List of Products</h2>
);

export default Products;
```

添加路由信息到路由表，编辑 `router.js` :

```diff
+ import Products from './routes/Products';
...
+ <Route path="/products" exact component={Products} />
```

然后在浏览器里打开 http://localhost:8000/#/products ，你应该能看到前面定义的 `<h2>` 标签。

## 安装bizchart
```bash
npm install bizcharts --save
```
安装完成之后，即可使用 import 或 require 进行引用。
## 绘制一个简单的图表
1、在src下新建page/Dashboard/AppAnalysis.js 在该js下声明需要用到的图表


