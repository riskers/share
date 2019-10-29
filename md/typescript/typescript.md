title: 移动端页面适配方案
speaker: riskers
theme: tomorrow
url: https://riskers.github.io/share/flexible
js:

- https://www.googletagmanager.com/gtag/js?id=UA-131910384-4
- ./gtag.js

<slide :class="aligncenter">

# TypeScript

## JavaScript that scales

![](./img/logo.png)TypeScript = JavaScript + Type

:::note
可见 TypeScript 的关键在 Type (类型) 上

------

<slide>

## 强类型和弱类型

* 使之强制数据类型定义的语言，没有强制类型转化前，不允许两种不同类型的变量相互操作
* 数据类型可以被忽略的语言

<slide>

## 动态语言和静态语言

????

------

<slide>

## TypeScript 类型系统

2012.10 ~ Now

-----

<slide>

## 类型声明

```ts
{值}: 类型
```

## 基础类型

```ts
const n: number = 6; // Number
const hasDone: boolean = false; // Boolean
const text: string = "abc"; // String

const list: number[] = [1, 2, 3]; // Array
const x: [string, number];  // Tuple
enum Color {Red, Green, Blue};  // Enum

function log(msg: string): void {  // Void
  console.log(msg)
}

class Person {} // Class
```


## 高级类型

```ts
type fooType = string | number;
```

> 等等等等很多很多

## 泛型

```ts
class Queue<T> {
  private data: T[] = [];
  push = (item: T) => {
    this.data.push(item)
  }
  pop = (): T|undefined => {
    this.data.shift()
  }
}

const q = new Queue<number>();
q.push(0)
q.push("a") // Error
```


## 使用 TypeScript 的好处

* 代码提示

![]()

* 不用看文档

* 将低级错误暴露在编译期


![]()

> 基本就是静态类型语言对动态类型语言的好处

----

动态类型一时爽,
代码重构火葬场!


https://barretlee.github.io/ppt/TypeScript%20%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F.pdf

为什么要存在 TS?

> 如果你对 JS 很熟，那么你已经会了 TS 80%，剩下的 20% 是类型系统和下面我要讲的东西。
>
> TS 的哲学: 在某些功能是它独创，比如它的 class 和 namespace / module，但是在 ECMAScript 2015 出来之后向 JS 靠拢，JS 没有进 stage4 的功能它不会实现(optional chaining)，JS 已经实现的它也实现的被废弃(namespace / module 现在只在声明类型的时候用)

> 然后讲讲 tc39 / babel /

## Why

介绍生态:

ECMAScript -> babel -> TS

> 什么是标准？
> W3C

> 什么是宿主？
> Chrome / Node

> babel 为什么存在?
> 前端编译器

> TS 为什么存在
> 和 babel 不冲突

## What

一大段的语法介绍

## types

> 各个开源项目要么是直接用 TS 开发的
>
> 要么是 JS 写的，但是提供了 @types .d.ts

https://ts.xcatliu.com/basics/declaration-files#fa-bu-sheng-ming-wen-jian

## 编写 .d.ts

- declare namepsace
- declare module

https://stackblitz.com/edit/typescript-cxc1vo

---

TS namespace vs module ?

typescript 已经有模块系统了，为什么还需要 namespace？ - Trotyl Yu 的回答 - 知乎
https://www.zhihu.com/question/65676593/answer/242421102

https://tasaid.com/blog/2019022017450863.html
https://tasaid.com/blog/20171102225101.html#module-exports

https://codesandbox.io/s/confident-noether-9rbsc

namespace 和 module 都是过时的产物，很少有项目使用了，都是 ES6

look this: https://ts.xcatliu.com/basics/declaration-files#declare-var

--

> 怎么组织业务代码中 interface / type
> 外面有人用就 export 出去

```ts
export interface IAbc {}
```

---

---

## VSCode 中使用 TS

https://gist.github.com/riskers/0bb7b9fcea5747c21d1d195566c29fbf

## When

什么时候适合使用 TS ?

大型项目、多人协作、长期迭代维护

活动页什么的就没必要了，太折腾

## 逐步升级

js -> ts
