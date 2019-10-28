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

什么时候适合使用 TS

## 逐步升级

js -> ts
