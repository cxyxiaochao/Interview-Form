# employee-recruitment

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

## Function Introduction（ 功能介绍 ）

A form addition and query created using Vue3+Vite, with an interface completed using the Element plus component, for storing a form submission that requires personal information to be filled in during an interview.
（ 采用 Vue3 + Vite 创建的一个表单新增和查询，运用了 Element-plus 组件完成的界面，在对于面试时需要填写个人信息的一个表单提交的存储。）

## Request using Axios ( 使用axios请求 )

When making a request, there was a cross domain issue, and my solution was to configure a proxy in vitenfig.js to resolve it.
（ 在请求时，产生了跨域问题，我采取的方式是在 vite.config.js 中配置 proxy 解决。 ）

## Welcome everyone to provide valuable opinions and suggestions for changes（ 欢迎大家提出宝贵意见及更改建议 ）

The Element plus of the project did not use on-demand import, but instead imported everything, which may result in a large packaging volume. The original backend has expired and may not be able to provide a backend interface at the moment. I have placed the backend configured fields in the form of txt files in the public folder, and everyone can configure them themselves.
（ 项目的 Element-plus 并没有使用按需引入的方式，而是全部引入，这可能会导致打包体积过大。 原后台过期了，暂时可能还没办法提供后台接口，我将后台配置的字段以 txt 文件的形式放在了 public 文件夹下， 大家可以自行配置。 ）


