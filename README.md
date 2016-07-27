### 1. 规范说明

此规范为参考规范，意在提高代码的规范性和可维护性 。不全是硬性要求，统一团队编码规范和风格。让所有代码都是有规可循的，并且能够得到沉淀，减少重复劳动。
#### 1.1  结构说明
```
-- 项目结构

----|---- CSS文件结构

----|---- JS文件结构
```

### 2. 书写规范
#### 2.1 样式与内容分离
##### 2.1.1 项目结构
```
 |---- index.html             入口页    
 |---- js/                    JS //具体见JS细化结构                 
 |---- css/                   CSS //具体见CSS细化结构
 ```
##### 2.1.2 重构步骤约定
1. index.html 全部样式附着于 class="xxx" 注： 此时文件中不包含任何一个 id="xxx"
2. 为上一步书写 CSS style[至此重构完成]
3. 开始书写js交互文件，使用 ID 和 Class 定位被操作句柄
向 index.html 中需要的地方添加 id="xxx" 及 data-xxx="xxx"
[至此交互效果完成]

##### 2.1.3 命名规范
- 文件及文件夹: 全部英文小写字母+数字或连接符"- , _ "，不可出现其他字符
如：../css/style.css, jquery.1.x.x.js
- 文件：调用 /libs 文件需包含版本号，压缩文件需包含min关键词，其他插件则可不包含
如：/libs/jquery.1.9.1.js /libs/modernizr-1.7.min.js fileuploader.js plugins.js
- ID: 匈牙利命名法 & 小駝峰式命名法
如：firstName topBoxList footerCopyright
- Class: [减号连接符]
如：top-item main-box box-list-item-1
- 尽量使用语义明确的单词命名，避免 left bottom 等方位性的词语
##### 2.1.4 格式&编码
- 文本文件： .xxx UTF-8_(无BOM)_ 编码
- 图片文件： .png (PNG-24) .jpg (压缩率8-12)
- 动态图片： .gif
- 压缩文件： .tar.gz .zip
#### 2.2 CSS 细化规范

##### 2.2.1 CSS 文件结构
```
--- ../css/
 |---- css/libs/reset.css                  CSS reset文件
 |---- … … 
 |---- css/images/                         主 CSS-sprite  图片     
 |---- css/style.css                       主 CSS 样式表
 |---- … … 
 |---- css/images/xxx/sprite.png           xxx 的 CSS-sprite 图片
 |---- css/xxx-style.css                   xxx 的 样式表
 ```
##### 2.2.2 CSS(含Less) 文件结构
```
--- ../css/
 |---- css/libs/reset.less            CSS reset文件
 |---- css/libs/elements.less         Less 函数复用文件
 |---- … … 
 |---- css/images/                         主 CSS-sprite 图片     
 |---- css/style.less                      主样式Less
 |---- css/style.css                       less -> css 自动生成
 |---- … … 
 |---- css/images/xxx/sprite.png           xxx 的 CSS-sprite 图片
 |---- css/xxx-style.less                  xxx 的 Less
 |---- css/xxx-style.css                   less -> css 自动生成
 ```
##### 2.2.3 使用Less
在 .less文件头部引入 reset.less & elements.less，之后调用如下属性传参即可，具体使用说明见 -> Lesselements 官方文档

```
@import "libs/reset.less";  
@import "libs/elements.less";

.gradient
.bw-gradient
.bordered
.drop-shadow
.rounded
.border-radius
.opacity
.transition-duration
.rotation
.scale
.transition
.inner-shadow
.box-shadow
.columns
.translate
```
##### 2.2.4 CSS reset
CSS reset 文件使用：reset.css 或 reset.less

reset文件用于重设各个浏览器的默认样式方案，解决其引起的耦合问题。
也可使用 .clearfix 清除浮动
##### 2.2.5 CSS 注释格式约定
```
/*
@name: Drop Down Menu
@description: Style of top bar drop down menu.
@require: reset.css
@author: Andy Huang(andyahung@geekpark.net)
*/
```
其中，@require为可选项

- CSS换行制表：使用 2 <del>或4</del> 个空格，而非[Tab]
- 书写格式：
 CSS名称+冒号+属性
如：`.box1 {float:left;}`

建议保留{左侧空格，字体名用'包含  

如：`.box1,.box2,.box3 {font-family:Courier,'Courier New';}`

避免中文，或使用转义，推荐前者

如：`font-family: "Microsoft YaHei"; font-family:\5fae\8f6f\96c5\9ed1;`

##### 2.2.6 CSS各属性的排列顺序：不做硬性要求
如：以下2种顺序均可

```
.box {
  /* 顺序1 */
  background: none repeat scroll 0 0 transparent;
  bottom: 11px;
  position: relative;
  width: 22px;
  z-index: 33;
}
.box {
  /* 顺序2 */
  z-index: 33;
  width: 22px;
  bottom: 11px;
  background: transparent none repeat scroll 0 0 ;
  position: relative;
}
2.2.7 CSS嵌套规则
/* 推荐嵌套层级 */
.ui-icon-rarr{}
.ui-icon-larr{}
.ui-title{}
.ui-nav .ui-list{}
.ui-table .ui-list{}

/* 不推荐 */
.ui-icon-rarr{}
.ui-icon-larr{}
.ui-title{}
.ui-list{}
.ui-nav{}
```
##### 2.2.8 CSS格式化
勿格式化，保留下面这种格式，增加可读性和可维护性，后期后台程序(如：PHP/Python)会将CSS压缩成 一行 输出：
```
.box{
  /* 勿格式化，增加可读性 */
  background: none repeat scroll 0 0 transparent;
  bottom: 11px;
  position: relative;
  width: 22px;
  z-index: 33;
}
```

#### 2.3 XHTML 细化规范
##### 2.3.1 HTML 注释格式约定
```
`<!--`
`@name: Drop Down Menu`
`@description: Style of top bar drop down menu.`
`@author: Andy Huang(andyahung@geekpark.net)`
`-->`

`<div id="header">`
    `<div class="xxx">`
        `<span>HTML行内注释格式</span>`
    `</div>`
`</div><!-- #header end-->`
```
- HTML换行缩进：采用 2 空格
##### 2.3.2 HTML嵌套规则

```
/* 推荐嵌套层级 */
  <ul class="ui-nav">
    <li class="ui-nav-item"> some text
      <ul class="ui-nav-item-child">
        <li> some text
          <ul class="ui-list">
            <li class="ui-list-item"> some text</li>
          </ul
        ...
       </ul>
    </li>
    <li
    ...
  </ul>
  ```
##### 2.3.4 * 第一行统一使用HTML5标准：<!DOCTYPE html>

```
`<!DOCTYPE html>`
`<html dir="ltr" lang="zh-CN">`
`<head>`
`  <meta charset="utf-8" />`
`  <title>极客公园 | 创新者社区</title>`


```


##### 2.3.5 Meta 的使用：（需要根据具体需求按需选择）可参看：[cool-head](https://github.com/hzlzh/cool-head)

```
`  <meta name="keywords" content="xxxx, xxx, xxxxx" />`
`  <meta name="description" content="xxxxxxxxxxxxxxxxxxxx" />`
`  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>`
`<meta http-equiv="Cache-Control" content="max-age=7200" />`
`<meta name="viewport" content="width=device-width, initial-scale=1.0"/>`
`<link rel="alternate" type="application/rss+xml" title="RSS 2.0" href="http://feeds.geekpark.net/" />`
`<link rel="shortcut icon" href="favicon.ico">`
`<link rel="apple-touch-icon" href="/apple-touch-icon.png">`

`<script type="text/javascript" src="/js/xxx.js"></script>`
`<link rel="stylesheet" href="/css/xxx.css">`

`<script type="text/javascript">`
    //Google 统计代码 的位置在离</head>最近的位置
`</script>`
`</head>`
`</html>`
```

- `<img>`标签默认缺省格式：`<img src="xxx.png" alt="缺省时文字" />` 避免出现src="" 问题
- `<a>`标签缺省格式：`<a href="###" title="链接名称">xxx</>` 注：target="_blank" 根据需求决定
-`<a>`标签预留链接占位符使用###，参见：a标签占位符问题
- 所有标签需要符合XHTML标准闭合
- 一律统一标签结尾斜杠的书写形式：`<br />` `<hr />` 注意之间空格
- 避免使用已过时标签，如：`<b>` `<u>` `<i>` 而用 `<strong>` `<em>`等代替
- 使用data-xxx来添加自定义数据，如：`<input data-xxx="yyy"/>`
- 避免使用style="xxx:xxx;"的内联样式表
- 特殊符号使用参考HTML 符号实体
#### 2.4 JS 细化规范
##### 2.4.1 JS 文件结构

```
---/js/
|---- /libs/plugin-1/       使用到的js插件1  
|---- /libs/plugin-2/       使用到的js插件2  
|---- /libs/plugin-3/       使用到的js插件3  
|---- script.js             单独书写的js  
|---- plugins.js            调用的plugins汇总  
|---- juqery-1.9.x.min.js   调用jq库文件
```
- JS 换行缩进：采用 4 空格
- 结束行需添加分号;
- jQuery变量要求首字符为 $, 私有变量:首字符为_; 尽量避免全局变量.
- 避免使用 eval()，setTimeOut使用调用函数，考虑重绘，回流 操作对页面影响 参看：reflows，repaints
- JS调试使用console.log()及console.dir()进行，避免使用弹出框，线上版- 需要注释所有调试代码
- JS压缩混淆工具: JS Compressor 如果使用了压缩，需要留 name-src.js在同路径供今后修改使用
##### 2.4.2 jQuery Call
```
`<!-- Grab Google CDN jQuery. fall back to local if necessary -->  `
`<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>  `
`<script>!window.jQuery && document.write('<script src="js/jquery-1.7.2.min.js"><\/script>')</script>`
```
##### 2.4.3 jQuery Plugin
- IE对HTML5标签支持，以及浏览器特性检测：Modernizr & html5shiv
- <del>IE6 PNG 图片支持：DD_belatedPNG</del>
- 定制&统一 浏览器的滚动条样式：jquery-scroll & Lionbars
- hover提示效果文字：bootstrap-tooltips & tipsy
- 滚动条跟随nav效果：bootstrap-scrollspy
- 提示冒泡文字：grumble.js
- 导航栏过渡效果：lavalamp
- 移动设备的滚动效果：iscroll 4
- Mac OS Lion 风格的滚动条：Lionbars
- 弹性SlideShow：kwicks for jQuery
- 瀑布流：isotope
- 抖动效果：jQ shake
- LightBox：fancyBox
- KenDo UI：KenDo UI
- textarea自适应高度：elastic
- 提示区域 & 提示层：noty
- 浮动话题泡：jQuery grumble
- 旋转进度：jQuery Knob
##### 2.4.4 JSON格式规范
参考JSON Style Guide翻译，原版：Google JSON Style Guide

- HTML 细化规范
- HTML head部分的结构参看：cool-head (摘取必要内容即可)
- css 文件置于都 头部
- jQuery 及 Google Analytics引用置于 头部
- 其他效果js及统计代码 文件置于 尾部
- HTML 代码尽量过一遍HTML5 验证
- HTML 占位图片使用 temp.im & placehold.us 图片服务
#### 2.5 Responsive Web 规范
从设计之处就坚持"Mobile First"的理念，在重构页面的时候要灵活采取响应式的解决方案。

##### 2.5.1 响应式实现途径
* 设置 meta viewport 属性

```
`<meta name="viewport" content="width=device-width, initial-scale=1" />`
```

- 引入不同尺寸设备的样式表

```
`<link rel="stylesheet" type="text/css" href="style.css" media="screen, handheld" />`
`<link rel="stylesheet" type="text/css" href="enhanced.css" media="screen  and (min-width: 40.5em)" />`
`<!--[if (lt IE 9)&(!IEMobile)]>`
`<link rel="stylesheet" type="text/css" href="enhanced.css" />`
`<![endif]-->`
```

* 使用 CSS Media Queries 方法

```
@media screen and (max-width: 40.5em) {
  .product-img {
    width: auto;
    float: none;
  }
}
@media screen and (max-width: 480px) {
}
```

* JS控制导航栏在 resize 事件 触发后的可见性，如：

```
$(w).resize(function(){ //Update dimensions on resize
  sw = document.documentElement.clientWidth;
  sh = document.documentElement.clientHeight;
  checkMobile();
});
//Check if Mobile
function checkMobile() {
  mobile = (sw > breakpoint) ? false : true;
  if (!mobile) { //If Not Mobile
    $('[role="tabpanel"],#nav,#search').show(); //Show full navigation and search
  } else { //Hide 
    if(!$('#nav-anchors a').hasClass('active')) {
      $('#nav,#search').hide(); //Hide full navigation and search
    }
  }
}
```

##### 2.5.2 响应式解决方案
* 弹性图片

```
img {
  max-width: 100%;
  height: auto;
  width: auto\9; /* ie8 */
}
```

* 自适应嵌入媒体

```
.video embed, .video object, .video iframe {
  width: 100%;
  height: auto;
}
```

* 禁用iPhone字体自适应功能：

```

html {
  -webkit-text-size-adjust: none;
}
```

* 让 IE 9 以下的IE版本支持响应式：

```
`<!--[if lt IE 9]>`
  `<script src="http://css3-mediaqueries-js.googlecode.com/svn/trunk/css3-mediaqueries.js"></script>`
`<![endif]-->`
```
#### 2.6 Newletter 制作规范
- CSS只可使用 内联样式表 ，如：style="margin:0;"
- 设计之初遵循： 图上无文本，文本后无底纹 的规则
- 使用 MailChimp HTML Email CSS Fix 参看下文链接
- 引入 CSS Reset for HTML Email 参看下文链接
- 使用Table布局而非DIV
- 所有图片使用IMG标签，如：<img style="style="display:block" "src="" />
- 可以适当使用占位符spacer.gif
- 多用<br />换行而非<p>
- 整体最佳宽度为：550-600px
- 不使用Javascript
- 正式发送给用户之前，多次测试
- 更多细节参考下面链接：
- 12 Killer Tips and Tricks for Building HTML Email

#### 2.7 生产力工具推荐
##### 2.7.1 for Mac OS
for more app detial check -> IUSETHIS

###### 2.7.1.1 前端相关工具(Mac)
- 编辑器：Sublime Text 2 / TextMate 2 / Vim / Intellij IDEA
- 命令行：iTerm2
- 浏览器调试环境：Chrome / Firefox + Firebug
- 移动设备调试环境：Mozilla Fennec
- 兼容性测试：VirtualBox + Win XP（IE 8）
- 版本控制工具：GitHub for Mac / Versions / SourceTree
- FTP工具：Filezilla / ForkLift
- HTTP抓包及Post/Get模拟：Charles
- PHP集成环境：XAMPP for Mac / MAMP
- SQL数据库管理：Sequel Pro
- 标注工具：Mark Man / xScope
- 取色拾色器： Frank DeLoupe / Sip / Snip / xScope
- MarkDown编辑器：Mou
- 浏览器免刷新开发环境：LiveReLoad / CodeKit
- CSS Sprite切图工具：SpriteRight
- Less -> CSS 编译：CodeKit / LiveReLoad / Less
- 配色方案工具：ColorSchemer Studio
- 多浏览器Cookie管理：Cookie
- 图片素材收集：Sparkbox / Pixa
###### 2.7.1.2 其他效率工具
- 快速启动及切换app：Alfred
- 剪切板历史记录：Alfred(Fretures -> Clipboard)
- 笔记：Evernote
- 轻量级GTD：Clear
- 压缩解压：The Unarchiver / Keka / iPack
- 语言文档和快捷词扩展：Dash
- 时间中断提醒：BreakTime
2.7.2.1 前端相关工具(Windows)
- 编辑器：Sublime Text 2 / Vim / Intellij IDEA
- 命令行：Putty
- 浏览器调试环境：Chrome / Firefox
- 移动设备调试环境：Chrome Remote USB Debugging
- 版本控制：Subversion / Github for Windows
- FTP工具：Filezilla
- 抓包工具：Fiddler2
- MarkDown：MarkdownPad Mou
- 浏览器免刷新开发环境：LiveReLoad / F5
- Less、sass-> CSS编译：less.org(nodejs环境下编译)
- Haml -> Html编译：haml.info(Gem下编译)
- 响应式设计查看工具：Firefox Responsive Design View
###### 2.7.2.2 其他效率工具(Windows)
- 笔记：Evernote
- 压缩解压：7z
##### 2.7.3 其他收集
- Firefox 扩展收藏集 -> Firefox Add-ons collections
- Chrome 扩展 -> 待添加
- Sublime Text 2 技巧 -> ST2 资源技巧汇总
#### 2.8 相关技巧
- Wiki page index

- 各浏览器的缓存清除方法
- 测试技巧Gmail 添加词缀 .+ 获得多个邮件的方法
- 关于Mac Win Linux跨系统传文件，文件名乱码的解决方案
- 技术团队"路由代理"解决方案和使用须知
#### 2.9 参考数据
涉及到 设计->重构->兼容性->测试 时可参考各浏览器的占用情况
-- updated: 2013/02 - 2013/04 via Google Analytics of GeekPark

<table>
<tbody valign="top"><tr>
<th align="center">总浏览器分布</th>
<th align="center">IE版本分布</th>
<th align="center">移动设备分布</th>
<th align="center">屏幕解决方案</th>
</tr>
<tr>
<td align="left">
<table>
<tbody><tr>
<th align="left">类别</th>
<th align="right">占有率</th>
</tr>
<tr>
<td align="left">Chrome</td>
<td align="right">40.39%</td>
</tr>
<tr>
<td align="left">Internet Explorer</td>
<td align="right">24.86%</td>
</tr>
<tr>
<td align="left">Safari & Safari (in-app)</td>
<td align="right">16.05%</td>
</tr>
<tr>
<td align="left">Android Browser</td>
<td align="right">10.57%</td>
</tr>
<tr>
<td align="left">Firefox</td>
<td align="right">5.99%</td>
</tr>
<tr>
<td align="left">Opera</td>
<td align="right">0.69%</td>
</tr>
<tr>
<td align="left">Opera Mini</td>
<td align="right">0.37%</td>
</tr>
<tr>
<td align="left">Mozilla Compatible Agent</td>
<td align="right">0.14%</td>
</tr>
<tr>
<td align="left">Maxthon</td>
<td align="right">0.13%</td>
</tr>
</tbody></table>
</td>
<td align="right">
<table>
<tbody><tr>
<th align="left">版本号</th>
<th align="right">占有率</th>
</tr>
<tr>
<td align="left">IE 8</td>
<td align="right">60.97%</td>
</tr>
<tr>
<td align="left">IE 9</td>
<td align="right">17.11%</td>
</tr>
<tr>
<td align="left">IE 7</td>
<td align="right">8.39%</td>
</tr>
<tr>
<td align="left">IE 6</td>
<td align="right">7.63%</td>
</tr>
<tr>
<td align="left">IE 10</td>
<td align="right">5.87%</td>
</tr>
<tr>
<td align="left">IE 4</td>
<td align="right">0.02%</td>
</tr>
</tbody></table>
</td>
<td align="right">
<table>
<tbody><tr>
<th align="left">移动平台</th>
<th align="right">占有率</th>
</tr>
<tr>
<td align="left">iOS</td>
<td align="right">50.39%</td>
</tr>
<tr>
<td align="left">Android</td>
<td align="right">48.05%</td>
</tr>
<tr>
<td align="left">Windows Phone</td>
<td align="right">0.96%</td>
</tr>
<tr>
<td align="left">Nokia</td>
<td align="right">0.33%</td>
</tr>
</tbody></table>
</td>
<td align="right">
<table>
<tbody><tr>
<th align="left">PC & Mac屏幕分辨率</th>
<th align="right">占有率</th>
</tr>
<tr>
<td align="left">1366x768</td>
<td align="right">21.55%</td>
</tr>
<tr>
<td align="left">1440x900</td>
<td align="right">12.70%</td>
</tr>
<tr>
<td align="left">1280x800</td>
<td align="right">9.60%</td>
</tr>
<tr>
<td align="left">1280x1024</td>
<td align="right">6.68%</td>
</tr>
<tr>
<td align="left">320x480</td>
<td align="right">6.38%</td>
</tr>
<tr>
<td align="left">1920x1080</td>
<td align="right">6.27%</td>
</tr>
</tbody></table>
</td>
</tr>
</tbody></table>

###使用团队
此规范基于 MIT License 开源，持续更新维护中，可 Star 或 Fork 本项来形成你的规范，请以 创建[issues] 的方式反馈，或发起Pull Request

文／PHP开发者（简书作者）
原文链接：http://www.jianshu.com/p/66f066126f5f
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。
