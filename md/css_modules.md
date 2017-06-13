title: CSS Modules 介绍以及在项目中的使用
speaker: riskers
transition: move
theme: dark
date: 2017年4月26日

[slide]

# CSS Modules

## 重峦

[<i class="fa fa-home"></i>](https://github.com/riskers/blog)
[<i class="fa fa-github"></i>](https://github.com/riskers/)
[<i class="fa fa-weibo"></i>](http://weibo.com/damaoxianjia123)

****************************************************************************************************************

[slide]

# What

[CSS Modules](https://github.com/css-modules/css-modules)：使用JS管理CSS依赖，学习成本几乎为零，完美搭配 webpack / React 。

****************************************************************************************************************

[slide]

# Trouble

****************************************************************************************************************

[slide]

## 全局污染

```css
.container {
  .title {
    & > span {

    }
  }
  .content {
    p {

    }
    .side {

    }
  }
}
```

****************************************************************************************************************

[slide]

## 命名混乱

```css
/*小A*/
.container {}
.container-header {}
.container-footer {}

/*小B*/
.container2 {}
.container2-header {}
.container2-footer {}
```

****************************************************************************************************************

[slide]

## less

```html
<section class="abc-container">
  <h1 class="title">this is title</h1>
  <div class="content">
    <p>this is <span class="bar">content</span></p>
  </div>
</section>
```

```less
.abc-container {
  .title {
    color: red;
    font-size: 14px;
  }
  .content {
    margin: 20px;
    .bar {
      color: blue;
      font-size: 20px;
    }
  }
}
```

  [note]
  这是我们现在的less写法，我们使用命名空间来确保样式不会冲突。随着这个页面越来越复杂，就变成了这样：
  [/note]

  [note]
  这样，一个 less 就会上百行，后期也并不好维护。其实，我们这么写只是为了解决样式冲突问题而已，而这一点 CSS Modules 早就完美解决了。
  [/note]


****************************************************************************************************************

[slide]

## CSS Modules

```js
import styles from './style.css'

class Demo extends React.Component {
  render() {
    return (
      <section>
        <h1 className={styles.title}>this is title</h1>
        <div className={styles.content}>
          <p>this is <span className={styles.bar}>content</span></p>
        </div>
      </section>
    )
  }
}
```

```css
/* style.css */
.title {
  color: red;
  font-size: 14px;
}
.content {
  margin: 20px;
}
.bar {
  color: blue;
  font-size: 20px;
}
```

****************************************************************************************************************

[slide]

![react渲染后的DOM](/img/css_modules/d1.png)

  [note]
  解决了什么问题？
  不必再有类似 `abc-container` 的命名空间了，这个页面和别的页面样式绝不会冲突，哪怕class名字是一样的！
  [/note]

****************************************************************************************************************

[slide]

# theory


  [note]
  为什么绝对不会冲突？现在来介绍一下 CSS Modules 的原理
  [/note]


****************************************************************************************************************

[slide]

## webpack config

webpack 的 [css-loader](https://github.com/webpack-contrib/css-loader) 的 `localIdentName` 配置项:

```js
module: {
  rules: [
    {
      test: /\.css$/,
      use: [
        'style-loader',
        'css-loader?modules&localIdentName=[name]__[local]-[hash:base64:5]'
      ]
    }
  ]
}
```

![styles对象](/img/css_modules/d2.png)

  [note]
  modules: 开启 CSS Modules
  localIdentName: 具体生成规则，name、local在加hash保证绝对不会冲突
  [/note]

****************************************************************************************************************

[slide]

# Use

  [note]
  CSS Module 很简单，几乎是零成本。
  [/note]

********

[slide]

## 作用域

```css
.title {
  color: red;
}

:global(.title) {
  color: green;
}

:global {
  .title {}
}
```

  [note]
  凡是这样声明的 `.title` ，都不会被编译成哈希字符串。
  [/note]

****************************************************************************************************************

[slide]

## 样式复用

```css
.className {
  color: green;
  background: red;
}

.otherClassName {
  composes: className;
  color: yellow;
}
```

||

```css
.otherClassName {
  background: red;
  color: yellow;
}
```

****************************************************************************************************************

[slide]

## 引入其他文件样式

```css
.otherClassName {
  composes: className from "./style.css";
}
```

****************************************************************************************************************

[slide]

以上是 CSS Modules 的所有功能，具体可看官方[demo](https://css-modules.github.io/webpack-demo/)

****************************************************************************************************************

[slide]

## 变量（结合 postcss）

* postcss-loader
* postcss-modules-values

****************************************************************************************************************

[slide]

1. 根目录新建 postcss.config.js

  ```js
  module.exports = {
    plugins: [
      require('postcss-modules-values')
    ]
  }
  ```

2. webpack.config.js

  ```js
  {
    test: /\.css$/,
    use: [
      'style-loader',
      'css-loader?modules&localIdentName=[name]__[local]-[hash:base64:5]&importLoaders=1',
      'postcss-loader'
    ]
  }
  ```

> importLoaders 必须设置，具体见 css-loader 的文档

[note]
因为 CSS Modules 设计得及其简单，所以一些功能可以用 postcss 实现
[/note]

[note]
postcss 等同于 JS 中的 babel，是用标准的CSS语法转译为 CSS
less/sass 等同与 JS 中的 coffee，是用自己的语法转译为 CSS
[/note]

****************************************************************************************************************

[slide]

```css
@value xxx: #c1c3c4;

.title {
  color: xxx;
}
.content {
  color: xxx;
}
```

```js
// CSS、JS变量共享，这是 CSS Modules 独有的功能
import styles from './style.css';
console.log(styles.xxx) ; //#c1c3c4
```

****************************************************************************************************************

[slide]

# 在 React 使用 CSS Modules

****************************************************************************************************************

[slide]

```js
import styles from './style.css'

class Demo extends React.Component {
  render() {
    return (
      <section>
        <h1 className={styles.title}>this is title</h1>
        <div className={styles.content}>
          <p>this is <span className={styles.bar}>content</span></p>
        </div>
      </section>
    )
  }
}
```

****************************************************************************************************************

[slide]

为了避免太多的 `style.`，使用 babel 插件 [react-css-modules](https://github.com/gajus/babel-plugin-react-css-modules):

```js
// .babelrc
{
  "plugins": [
    ["react-css-modules",
      {
        "generateScopedName":"[local]___[hash:base64:5]"
      }
    ]
  ]
}
```

****************************************************************************************************************

[slide]

```js
import './style.css'

class Demo extends React.Component {
  render() {
    return (
      <section>
        <h1 styleName="title">this is title</h1>
        <div styleName="content">
          <p>this is <span styleName="bar">content</span></p>
        </div>
      </section>
    )
  }
}
```


****************************************************************************************************************

[slide]

# Q & A

****************************************************************************************************************

[slide]

# THANKS