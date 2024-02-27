# 🎉 🎉 🎉 Vue3-Mpa 🎉 🎉 🎉

Vue3-Mpa 是一个开箱即用的企业级多页面脚手架，基于 vue3+vite，配备各种工程化工具。

## 特性 🌼

- 支持命令行一键创建子项目，并且可选是否使用 ts
- 支持直接启动指定子项目
- 支持打包指定子项目
- 配置完善的工程化工具，包括 esint、prettier、stulelint、husky、lint-stage、commitlint
- 配置一些基本的插件，例如自动引入 Composition API、打包 size 分析工具、打包压缩工具

## 1.项目结构 📖

```
├── README.md
├── .husky   //git hook钩子
│   ├── commit-msg //规范 commit message 信息
│   └── verify-commit-msg.mjs  //脚本：commitlint 替代方案
├── dist //打包输出目录
├── scripts //存放一些脚本
│   ├── template         //创建子页面的js模版
│   ├── template-ts      //创建子页面的ts模版
│   ├── index.mjs        //创建子页面的脚本
│   └── multiPages.json  //子页面描述说明集合文件
├── src
│   ├── arrets       //公共静态资源
│   ├── components   //公共组件
│   ├── store        //pinia 共享状态存储库
│   ├── utils        //公共方法
│   └── Projects     //多页面文件夹
├── types  //ts 声明文件
├── .env.development   //开发环境-环境变量
├── .env.production    //生产环境-环境变量
├── .eslintrc.cjs      //eslint 配置
├── .gitignore         //git 提交忽略文件
├── .prettierignore    //prettier 忽略文件
├── .prettierrc.js     //prettier 配置
├── .stylelintignore   //stylelint 忽略文件
├── .stylelintrc.js    //stylelint 配置
├── .pnpm-lock.yaml    //锁定项目于一份各个依赖稳定的版本信息
├── .stats.html        //chunck size 分析页面
├── tsconfig.json      //ts 配置
├── tsconfig.node.json //vite在node环境中的 ts 规则
├── vite.config.ts     //vite 配置
├── package.json

```

## 2.如何使用 🔑

### 🪴安装依赖

```
  //全局安装 pnpm
  npm install -g pnpm
  //切换淘宝源
  pnpm config set registry https://registry.npmmirror.com/

  pnpm i
```

### 🪴启动测试页面

```
npm run dev --page=pageone
```

### 🪴创建子项目

执行以下命令：

```js
npm run new:page

// 创建使用ts的子项目：
npm run new:page --ts
```

执行命令后终端提示：请输入要生成的'页面名称:页面描述'、会生成在 /src/Project 目录下  
例如输入：mypage:我的页面  
输入页面信息回车确认后，会在 scripts/multiPages.json 中生成对应的数据，后期如果要删除页面最好删除对应的数据以保持一致

在`multiPages.json`页面中可以查看各个页面的功能，格式如下：

```js
;[
  { chunk: 'pageone', chunkName: '页面1' },
  { chunk: 'pagetwo', chunkName: '页面2' },
  { chunk: 'pagethree', chunkName: '页面3' }
]
```

### 🪴运行指定子项目

```js
npm run dev --page=页面名称
```

配置参数，在命令行上放置--foo bar 设置 foo 配置参数为 bar。 一个 -- 参数(argument)告诉 cli 解析器停止读取 flags.一个 在命令行结尾的--flag 参数(parameter)的值将会是 true。  
然后在 vite.config.ts 中可以获取参数来进行打包对应的项目  
用 process.env.npm_config_page 获取参数

### 🪴打包

> **正式环境打包**

单页面打包：
```js
npm run build --page=页面名称
```
全量打包：
```js
npm run build:all
```

> **测试环境打包**   

单页面打包：
```js
npm run build:test --page=页面名称
```
全量打包：
```js
npm run build:all test
```

## 说在最后 💝

如果本脚手架对你有帮助，希望可以点个 star ⭐️⭐️⭐️ 谢谢 🌹🌹🌹

<img src="https://web-abin.gitee.io/abin-web/assets/qq-code-30f0f86d.jpeg" alt="image.png" width="30%" />
