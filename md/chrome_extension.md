title: Chrome Extension
speaker: riskers
transition: move
theme: dark
date: 2018年8月24日


[slide]
# Chrome Extension

[<i class="fa fa-home"></i>](https://github.com/riskers/blog)
[<i class="fa fa-github"></i>](https://github.com/riskers/)
[<i class="fa fa-weibo"></i>](http://weibo.com/damaoxianjia123)

[slide]
* Chrome Extension 能做什么 (manifest.json)
* Chrome Extension 的开发概念

****************************************************************************************************************

[slide]
# Chrome Extension 能做什么 (manifest.json)

<!-- 每一个都会推荐插件 -->

* browser_action
  * 图标
  * tooltip
  * badge
* popup
* omnibox
* context
* option
* override
  * history
  * newtab
  * bookmarks

****************************************************************************************************************

[slide]
# Chrome Extension 的核心概念

* background 主进程
* content_scripts 注入脚本
* inject_scripts

****************************************************************************************************************

[slide]
# Chrome Extension 常用 API
* storage
* i18n
* webRequest
* tabs

****************************************************************************************************************

[slide]
# Chrome Extension 其他
* 调试
* 打包
* 发布

****************************************************************************************************************

[slide]
# Chrome Extension VS Chrome App

* 权限不同
* 展现形式不同

****************************************************************************************************************

[slide]
# Chrome Extension 安全

None

无审核，无监控，十分钟上线

****************************************************************************************************************

[slide]

[permissions_warning](https://developer.chrome.com/apps/permission_warnings#permissions_with_warnings)

![提示权限](/img/chrome_extension/a_lot_of_warnings.png)

****************************************************************************************************************

[slide]

Chrome 禁止使用非 web store 下载的扩展

* Windows Chrome 用户自己在 chrome://extension 安装 crx 的方法在 13 年就已经被[禁止](https://blog.chromium.org/2013/11/protecting-windows-users-from-malicious.html)。

* Mac Chrome 用户安装 crx 的方法在 15 年也被[禁止](https://blog.chromium.org/2015/05/continuing-to-protect-chrome-users-from.html)

* [inline-install 被禁止](https://blog.chromium.org/2018/06/improving-extension-transparency-for.html)

****************************************************************************************************************

[slide]

远远不够

* Firefox 扩展正式发布前会经过严格审核（人工）
* Edge 目前还不开放扩展的自由提交，上架的扩展都是官方挑选出的合作方开发的

****************************************************************************************************************

[slide]
# THANKS

****************************************************************************************************************

[slide]
# Q & A

****************************************************************************************************************