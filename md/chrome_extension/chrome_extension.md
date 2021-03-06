title: Chrome Extension
speaker: riskers
prismTheme: dark
url: https://riskers.github.io/share/chrome_extension
js:

- https://www.googletagmanager.com/gtag/js?id=UA-131910384-4
- ./gtag.js

<slide :class="aligncenter">

# Chrome Extension

---

[:fa-home:](https://github.com/riskers/blog)
[:fa-github:](https://github.com/riskers/)
[:fa-weibo:](http://weibo.com/damaoxianjia123)

<slide :class="aligncenter">

- Chrome Extension 能做什么 {:&.fadeIn}
- Chrome Extension 核心
  - background
  - content_scripts
  - inject_scripts
- Chrome 开发概述
  - [manifest.json](https://developer.chrome.com/extensions/manifest)
  - [Chrome Extension API](https://developer.chrome.com/extensions/api_index)
- Chrome Extension VS Chrome App
- Chrome 安全问题

---

<slide>

# Chrome Extension 能做什么

- popup {:&.fadeIn}
- option
- omnibox
- contextMenus
- override

<slide>

# popup - 常用选项

![](https://github-riskers-blog.oss-cn-qingdao.aliyuncs.com/20200327172425.gif)

<slide>

# options - 配置

![](https://github-riskers-blog.oss-cn-qingdao.aliyuncs.com/20200327172409.gif)

<slide>

# omnibox - 搜索栏

![](https://github-riskers-blog.oss-cn-qingdao.aliyuncs.com/20200327172340.gif)

<slide>

# contextMenus - 右键菜单

<slide>

# override - 自定义 Chrome 页面

- history: 浏览历史 {:&.fadeIn}
- newtab: 新 Tab
- bookmarks: 收藏夹

<slide>
# 其他

- [tabs](https://developer.chrome.com/extensions/tabs) {:&.fadeIn}
- [cookies](https://developer.chrome.com/extensions/cookies)
- [storage](https://developer.chrome.com/extensions/storage)
- [webRequest](https://developer.chrome.com/extensions/webRequest)


<slide>

# Chrome Extension 核心

- background 主进程 {:&.fadeIn}
  - 生命周期: 常驻 Chrome 后台
- content_scripts 注入 CSS / JavaScript
  - 控制 DOM
- inject_scripts 注入 CSS / JavaScript?
  - 获取 `window` 变量

<slide>

# 三者通信

![](https://github-riskers-blog.oss-cn-qingdao.aliyuncs.com/20200327172320.png)

<slide>
* background <-> content_scripts: [chrome.runtime.onMessage](https://developer.chrome.com/apps/runtime#event-onMessage) / [chrome.runtime.sendMessage](https://developer.chrome.com/apps/runtime#method-sendMessage)
* content_scripts <-> inject_scripts: [window.postMessage](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/postMessage) / [window.onMessage](https://developer.mozilla.org/zh-CN/docs/Web/API/WindowEventHandlers/onmessage)

<slide>
# 三者权限

|                 | Chrome API | DOM  | window 变量 |
| --------------- | ---------- | ---- | ----------- |
| background      | All        | None | None        |
| content_scripts | not all    | All  | None        |
| inject_scripts  | None       | All  | All         |

---

<slide>

# Chrome Extension VS Chrome App

- 权限不同 (如 FileSystem)
- 展现形式不同

---

<slide>

# Chrome Extension 安全问题

## 无审核，无监控，十分钟上线

<slide>
# Chrome 禁止使用非 web store 下载的扩展

- Windows Chrome 用户自己在 chrome://extension 安装 crx 的方法在 13 年就已经被[禁止](https://blog.chromium.org/2013/11/protecting-windows-users-from-malicious.html)

- Mac Chrome 用户安装 crx 的方法在 15 年也被[禁止](https://blog.chromium.org/2015/05/continuing-to-protect-chrome-users-from.html)

- [inline-install 被禁止](https://blog.chromium.org/2018/06/improving-extension-transparency-for.html)

<slide>

# [permissions_warning](https://developer.chrome.com/apps/permission_warnings#permissions_with_warnings)

<slide>

![提示权限](https://github-riskers-blog.oss-cn-qingdao.aliyuncs.com/20200327172204.png)

<slide>

# 查看源码

- Mac ~/Library/Application\ Support/Google/Chrome/Default/Extensions/{Extension-ID}

---

<slide>
# THANKS

---

<slide>
# Q & A

---
