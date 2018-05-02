
# Vue-cli Webpack4.x 模板

1. 如果要上传`dist`文件夹，删除忽略文件配置(`.gitignore`文件)里 `/dist` 即可

2. 默认被 `webpack` 编译处理过的资源文件都会存放在 `static` 文件夹下，如果你只想存放在根文件目录下，修改 `config/index.jx` 下的 `build.assetsSubDirectory` 参数留空。但不推荐！这样在打包时候部分图片路径会出错，建议小于10kb的资源和一些svg icon（一般不会改动的东西）放在  `src/assets` 文件夹内，其他的放在 `static` 文件夹里。

3. 默认打包的 `css/js` 文件都带 `source map` ，为了减小文件体积或者感觉不需要需要，修改 `config/index.js` 文件，把 `build.productionSourceMap` 的值改为：`false` 即可

4. 如果代码在服务器上跑不想要地址栏里有 `#/` 需要在 `router/index.js` 把 `mode: 'history'` 注解删除(另需要后端配置，否则页面刷新404)；如果页面需用到锚点跳转到指定位置，把 `scrollBehavior` 注解删除即可。

5. 输出格式类似 `[name].[chunkhash]` 的要把 `[chunkhash]` 改为 `[hash]` ，否则在 `build` 时候会报错， [Webpack4.2之后不在支持  extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin/issues/763)，作者建议使用 [mini-css-extract-plugin](https://github.com/webpack-contrib/mini-css-extract-plugin)

```bash
    npm install --save-dev mini-css-extract-plugin
```
ps: 安装之后发现在 `build` 的时候报错 =,=

So 不要 `hash` 了，改成 `min` 了，酱编译出来的文件都是 `xx.min.css` / `xx.min.js`   







## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
