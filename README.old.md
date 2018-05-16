
# Vue-cli Webpack4.x 模板

1. 如果要上传`dist`文件夹，删除忽略文件配置(`.gitignore`文件)里 `/dist` 即可

2. 默认被 `webpack` 编译处理过的资源文件都会存放在 `static` 文件夹下，如果你只想存放在根文件目录下，修改 `config/index.jx` 下的 `build.assetsSubDirectory` 参数留空。但不推荐！这样在打包时候部分图片路径会出错，建议小于10kb的资源和一些svg icon（一般不会改动的东西）放在  `src/assets` 文件夹内，其他的放在 `static` 文件夹里。

3. 默认打包的 `css/js` 文件都带 `source map` ，在开发环境用来调试代码非常有用，但到编译生成环境建议不要，修改 `config/index.js` 文件，把 `build.productionSourceMap` 的值改为：`false` 。

4. 如果代码在服务器上跑不想要地址栏里有 `#/` 需要在 `router/index.js` 把 `mode: 'history'` 注解删除(另需要后端配置，否则页面刷新404)；如果页面需用到锚点跳转到指定位置，把 `scrollBehavior` 注解删除即可。

5. 输出格式类似 `[name].[chunkhash]` 的要把 `[chunkhash]` 改为 `[hash]` ，否则在 `build` 时候会报错， [Webpack4.2之后不在支持  extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin/issues/763)，作者建议使用 [mini-css-extract-plugin](https://github.com/webpack-contrib/mini-css-extract-plugin)

```bash
    npm install --save-dev mini-css-extract-plugin
```
ps: 安装之后发现在 `build` 的时候报错 =,=

So 不要 `hash` 了，改成 `min` 了，酱编译出来的文件都是 `xx.min.css` / `xx.min.js`   



## Build Setup

``` bash
# 安装依赖
npm install

# 检测模块
npm outdated

# 更新模块
npm update

# 编译开发环境
npm run dev

# 编译生产环境
npm run build

# 构建生产环境
npm run build --report
```
注解：<sup>1</sup>这个命令会检查你安装的模块，并告诉你哪些模块已经过期了，有了新的版本。具体的信息则包括该模块你当前安装的版本（Current）、你应该要更新到的版本（Wanted）以及仓库中最新的版本（Latest）。如果发现标红的建议更新到最新版本。


## Other
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
在大型单页面开发中推荐使用上面目录结构，why?

假如你想在另一个项目中使用 /login，只需将其复制或移动到 /components 目录下。只要你已经安装了任何扩展依赖(external dependencies)，并且你已经在配置中定义过相同的 loader，那么项目应该能够良好运行。

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
