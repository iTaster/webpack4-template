
# Vue-cli Webpack4.x 模板

如果要上传`dist`文件夹，删除忽略文件配置(`.gitignore`文件)里 `/dist` 即可

默认被 `webpack` 编译处理过的资源文件都会存放在 `static` 文件夹下，如果你只想存放在根文件目录下，修改 `config/index.jx` 下的 `build.assetsSubDirectory` 参数留空，

输出格式类似 `[name].[chunkhash]` 的要把 `[chunkhash]` 改为 `[hash]` ，否则在 `build` 时候会报错， [Webpack4.2之后不在支持  extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin/issues/763)，作者建议使用 [mini-css-extract-plugin](https://github.com/webpack-contrib/mini-css-extract-plugin)

```bash
    npm install --save-dev mini-css-extract-plugin
```


**webpack.config.js**

```js
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
module.exports = {
  plugins: [
    new MiniCssExtractPlugin({
      // Options similar to the same options in webpackOptions.output
      // both options are optional
      filename: "[name].css",
      chunkFilename: "[id].css"
    })
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          MiniCssExtractPlugin.loader,
          "css-loader"
        ]
      }
    ]
  }
}
```

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
