---
layout: post
title: "Building an application with Nuxt"
tags: vueJs Nuxt Bootstrap
date: 2018-02-18
published: true
---

[Nuxt](https://nuxtjs.org/) is a wrapper of vueJs that allows to quickly bootstrapping web aplication using convention over configuration.

## Install vue-cli

```bash
yarn global add vue-cli
```

## Create a nuxt project

Using vue-cli, it is easy to bootrap a nuxt projectµµ.

```bash
vue init nuxt-community/starter-template  <project-name>
```

Build the project

```bash
yarn
```

You can run it using

```bash
yarn run dev
```

## bootstrap-vue

```
yarn add bootstrap-vue
```

Add bootstrap-vue in the module section of `nuxt.config.js`.
```javascript
  modules: [
    'bootstrap-vue/nuxt'
    ]
```

## CSS style

Install sass support

```
yarn add node-sass sass-loader --dev
```

Create a sass file `/assets/css/main.scss`

Configure the page to be loaded globally in the css section of `nuxt.config.js`.

```javascript
  css: [
    '@/assets/css/main.scss'
  ]
```


                                                                        

