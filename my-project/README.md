# my-project

Vueのコンポーネント同士の関係をイメージで示したのが下図。

![component-relation](assets/image_2020-09-09-13-50-54.png)

## メモ

このプロジェクトは`@vue/cli: 4.5.4`を使って、以下のコマンドで生成したもの。

```sh
vue create my-project
```

## `style`について

Vueに記述する`<style>`は、`<style scoped>`と書くことで他のコンポーネントにCSSが波及しないようにできる。また、`<style lang="scss">`と書くことでSCSSの文法で書ける。

SCSSを使う場合は、以下のコマンドを実行してから`yarn serve`すればおｋ。

```sh
yarn add sass-loader node-sass
```

### `props`とは

親コンポーネントから状態を受け取るインターフェース。以下の記述は、親コンポーネントから`msg`というプロパティを受け取るという意味。

```html
<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
```

これは、`HellowWorld.vue`の`template`の中で`{{ msg }}`として展開されている。

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
....
```

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
