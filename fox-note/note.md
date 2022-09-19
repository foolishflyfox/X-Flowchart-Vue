# 代码阅读笔记

## 根目录

### vue.config.js

参考：[Vue CLI服务](https://cli.vuejs.org/zh/guide/cli-service.html#%E4%BD%BF%E7%94%A8%E5%91%BD%E4%BB%A4)

在一个 Vue CLI 项目中，`@vue/cli-service` 安装了一个名为 `vue-cli-service` 的命令。你可以在 npm scripts 中以 `vue-cli-service`，或者从终端中以 `node_modules/.bin/vue-cli-service serve` 访问这个命令。

这是你使用默认 preset 的项目的 `package.json`:
```json
  "scripts": {
    "serve": "vue-cli-service serve",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint"
  },
```
可以通过 npm 或者 yarn 调用这些 script: 

```sh
npm run serve
# OR
yarn serve
```
也可以使用 npx 直接调用：
```
npx vue-cli-service serve
```

#### serve 用法

`vue-cli-service serve [options] [entry]`。vue-cli-service 命令会启动一个开发服务器(基于 webpack-dev-server)并附带一个开箱即用的模块热加载(hot-module-replacement)。

- options
    - `--open`: 在服务器启动时打开浏览器
    - `--copy`: 在服务器启动时将 URL 复制到剪切板
    - `--mode`: 指定环境模式，默认为 development
    - `--host`: 指定 host，默认值为 0.0.0.0
    - `--port`: 指定 port, 默认值为 8080，如果端口被占用则递增找到没被占用的端口
    - `--https`: 使用 https，默认为 false

除了通过命令行参数，也可以使用 vue.cnofig.js 里面的 devServer 字段配置开发服务器。例如：
```js
module.exports = defineConfig({
  devServer: {
    port: 2020,
    open: true
  }
})
```
命令行参数 `[entry]` 将被指定为唯一入口(默认值为 `src/main.js`)，TypeScript 项目则为 `src/main.ts`。尝试使用 `[entry]` 覆盖 `config.pages` 中的 entry 可能发生错误。

#### build 用法

`vue-cli-service build [options] [entry|pattern]`。

选项：

- `--mode`: 指定环境模式，默认为 `production`
- `--dest`: 指定输出目录，默认为 `dist`
- `--modern`: 面向现代浏览器带自动回退地构建应用
- `--target`: app | lib | wc | wc-asyncj(默认值: app)
- `--name`: 库或 Web Components 模式下的名字 (默认值：package.json 中的 "name" 字段或入口文件名)
- `--no-clean`: 在构建项目之前不清除目标目录的内容

### .prettierrc

json 格式文件，例如下面的一个配置：

```json
{
  "tabWidth": 2,
  "useTabs": false,
  "singleQuote": true,
  "semi": false,
  "trailingComma": "none"
}
```

-`"tabWidth": 2`: 表示 tab 用 2 个空格替代
-`"useTabs": false`: 表示不适用 tab
-`"singleQuote": true`: 表示使用单引号
-`"semi": false`: 表示不自动添加多余是分号
-`"trailingComma": "none`: 表示不自动添加多余的逗号
