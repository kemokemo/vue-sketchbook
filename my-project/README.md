# my-project

[Software Design 2020年9月号](https://gihyo.jp/magazine/SD/archive/2020/202009)の特集記事を見ながら写経するプロジェクト。レッツVue.js！

## メモ

### components

Vueのコンポーネント同士の関係をイメージで示したのが下図。

![component-relation](assets/image_2020-09-09-13-50-54.png)

このプロジェクトは`@vue/cli: 4.5.4`を使って、以下のコマンドで生成したもの。

```sh
vue create my-project
```

## `style`を適用する、適用範囲を制御する

Vueに記述する`<style>`は、`<style scoped>`と書くことで他のコンポーネントにCSSが波及しないようにできる。また、`<style lang="scss">`と書くことでSCSSの文法で書ける。

SCSSを使う場合は、以下のコマンドを実行してから`yarn serve`すればおｋ。

```sh
yarn add sass-loader node-sass
```

### `props`で親コンポーネントから値をもらう

親コンポーネントから状態を受け取るインターフェース。以下の記述は、親コンポーネントから`msg`というプロパティを受け取るという意味。`props`は親から受け取るだけの一方的なもので、コンポーネント内で書き換えてはならない。

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

### `emit`で親コンポーネントにイベントを飛ばす

子コンポーネントから`methods`プロパティで`$emit()`を使って、親コンポーネントにイベントを送る。第1引数がイベント名（イベントを購読する親コンポーネントで使う）。

```html
<script>
....
    methods: {
      increment(){
        this.count++;
        this.$emit("emitUp", {name: this.name, counted: this.count})
      }
    },
....
</scirpt>
```

親コンポーネントでは、`@{イベント名}`を使ってイベントを購読する。以下の例では、イベント`emitUp`が発火される度に`getEvent()`メソッドを実行する。カッコ`()`を省略してメソッド名だけ書いたことで、イベントの中身である`{name: this.name, counted: this.count}`がメソッドに渡される。

```html
<Counter name="Counter 1" :initCount="5" @emitUp="getEvent" />
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
