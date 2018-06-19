<p align="center">
  <a href="javascript:;">
    <img width="100" src="https://raw.githubusercontent.com/iTaster/webpack4-template/master/src/assets/logo.png" alt="logo">
  </a>
</p>
<p align="center">
  <a href="javascript:;" rel="nofollow">
    <img src="https://img.shields.io/badge/node->=6.0.0-brightgreen.svg" alt="node">
  </a>
  <a href="javascript:;" rel="nofollow">
      <img src="https://img.shields.io/badge/npm->=3.0.0-brightgreen.svg" alt="npm">
  </a>
  <a href="javascript:;" rel="nofollow">
      <img src="https://img.shields.io/badge/webpack-4.8.3-brightgreen.svg" alt="webpack">
  </a>
  <a href="https://github.com/vuejs/vue">
    <img src="https://img.shields.io/badge/vue-2.5.16-brightgreen.svg" alt="vue">
  </a>
</p>
   

**索引**

* [概括](#overview)
* [安装](#安装)
* [使用](#使用)
* [更新](#更新)
* [配置](#配置)
* [架构](#架构)
* [已知问题](#已知问题)
* [执照](#执照)

# 概括
### 基于 vue-cli 的 [Webpack4.x 模板](https://github.com/iTaster/webpack4-template).

更新说明

* 2018/6/19 升级webpack, 使用 webpack4 推荐新的插件mini-css-extract-plugin


## 安装
```
＃克隆该项目
git clone https://github.com/iTaster/webpack4-template

# 安装依赖关系
npm install

# 编译开发环境
npm run dev

```
默认自动打开 http://localhost:1988/


## 使用

```
# 编译生产环境
npm run build

# 构建生产环境
npm run build --report
```

## 更新
为确保项目模块后续更新

```
# 检测模块
npm outdated

# 更新模块
npm update

# 删除 node_modules 文件
npm install rimraf -g
rimraf node_modules
```
`npm outdated` 命令会检查你安装的模块，并告诉你哪些模块已经过期了。

具体信息包括该：当前安装的版本（Current）、你应该要更新到的版本（Wanted）以及仓库中最新的版本（Latest）。



## 配置

1. 如果要上传 `dist` 文件夹，删除忽略文件配置(`.gitignore`文件)里 `/dist` 即可。

2. 默认被 `webpack` 编译处理过的资源文件都会存放在 `static` 文件夹下，如果你只想存放在根文件目录下，修改 `config/index.jx` 下的 `build.assetsSubDirectory` 参数留空。但不推荐！这样在打包时候部分图片路径会出错，建议小于10kb的资源和一些svg icon（一般不会改动的东西）放在  `src/assets` 文件夹内，其他的放在 `static` 文件夹里。

3. 默认打包的 `css/js` 文件都带 `source map` ，在开发环境用来调试代码非常有用，但到编译生成环境建议不要，修改 `config/index.js` 文件，把 `build.productionSourceMap` 的值改为：`false` 。

4. 如果代码在服务器上跑不想要地址栏里有 `#/` 需要在 `router/index.js` 把 `mode: 'history'` 注解删除(另需要后端配置，否则页面刷新404)；如果页面需用到锚点跳转到指定位置，把 `scrollBehavior` 注解删除即可。

5. 自带 `autoprefixer` 插件， 在 vue 文件直接写 css 代码会自动添加前缀。

## 架构

在大型单页面开发中推荐以下目录架构：

```bash
src
    ├── README.md
    ├── assets                  // 全局资源目录
    │    ├── images            // 图片
    │    ├── css               // CSS 样式表
    │    └── fonts             // 自定义字体文件
    ├── components              // 公共组件目录
    │    ├── NavMenu.vue
    │    ├── Slider.vue
    │    └── ...
    ├── directives               // 公共指令
    ├── filters                  // 公共过滤器
    ├── i18n                     // 国际化
    │    ├── index.js           // 入口文件
    │    ├── zh.js
    │    └── en.js
    ├── router                   // 路由
    │    └── index.js
    ├── store                    // 状态管理
    │    ├── index.js        
    │    └── ...
    ├── views                    // 页面视图
    │    ├── login
    │    │    ├── index.vue
    │    │    ├── LoginForm.vue
    │    │    └── LoginSocial.vue
    │    ├── home
    │    │    ├── index.vue
    │    │    ├── HomeBanner.vue
    │    │    └── ...
    │    └── ...
    ├── App.vue                // 默认程序入口
    └── main.js
```


优点：

* 假如你想在另一个项目中使用 /login，只需将其复制或移动到 /components 目录下。

* 只要你已经安装了任何扩展依赖(external dependencies)，并且你已经在配置中定义过相同的 loader，那么项目应该能够良好运行。


## 已知问题

* 目前没有

## 贡献

您可以通过提交问题和/或提取请求来为此项目贡献自由。这个项目是测试驱动的，所以请记住，每个变化和新功能都应该包含在测试中

## 执照

该项目在 [MIT](https://github.com/theGC/html-webpack-inline-svg-plugin/blob/master/LICENSE)获得许可。
