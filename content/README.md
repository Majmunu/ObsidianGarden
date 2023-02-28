---
obsidianUIMode: preview
progress: 正在进行
title: README
updated: 2022-06-09 10:00
---
## 💡引言
This Vault  contains the basic functions of Obsidian and has built-in common Obsidian plugins.
Notice：You need to open this vault with [Obsidian](https://obsidian.md/)

---
> **Example-lite 库删除了大量辅助插件都是一些非必须插件，如果实际用到根据需要安装即可**

本[Examples库](https://github.com/cumany/Blue-topaz-examples)由Cuman建立，Tips教程由[BT主题](https://github.com/whyt-byte/Blue-Topaz_Obsidian-css)作者3F撰写。
本库是一个包含Obsidian基本功能的入门库，并内置了Obsidian的常用插件。
需要用[Obsidian](https://obsidian.md/)软件打开本库即可。
特别感谢@Johnny @Lillianwho  @lavi @成雙酱 @锋华 提供的教程和创作思路。
如果有问题或者建议 请加入Topaz社区[Topaz QQ群](https://jq.qq.com/?_wv=1027&k=TWGhXs40)  [Obsidian频道](https://qun.qq.com/qqweb/qunpro/share?_wv=3&_wwv=128&inviteCode=zHpby&from=246610&biz=ka)
## 🎞视频教程
<https://space.bilibili.com/1970226/channel/series>
## 👉后续更新 请关注
- [Examples库](https://github.com/cumany/Blue-topaz-examples)
- [Blue topaz 主题用法示例 - 飞书文档 (feishu.cn)](https://kknwfe6755.feishu.cn/docs/doccn67RYLVN4IQZiJTwviIdnog)

另外推荐鸟姐的Homepage 也是很棒的风格
[Rainbell129/Obsidian-Homepage: A dashboard for your obsidian vault. (github.com)](https://github.com/Rainbell129/Obsidian-Homepage)
## 🚩更新日志


## 主题内置的cssclass样式表  
```expander
path: 77-Example usage:
^|文件名称|cssclass|用法|
^|---|---|	---|
|[[$filename]]|$frontmatter:cssclass|$frontmatter:usage|
```
 
|文件名称|cssclass|用法|
|---|---|	---|
|[[电影观看清单-状态控制（dvjs）]]|cards|对dataview表格渲染成卡片视图|
|[[电影观看清单（dv）]]|cards|对dataview表格渲染成卡片视图|
|[[多彩高亮（三种语法）]]|colorful-highlight|实时预览模式下正确显示多彩高亮|
|[[各类列表和彩虹大纲线]]|noscroll|隐藏当前页面滚动条|
|[[全宽显示-表格测试]]|fullwidth|缩减栏宽开启下，控制页面全宽显示|
|[[四象限表格]]|matrix|四象限表格样式|
|[[图书阅读清单-状态控制(dvjs)]]|cards|对dataview表格渲染成卡片视图|
|[[图书阅读清单(dv)]]|cards|对dataview表格渲染成卡片视图|
|[[涂黑和挖空效果（三种语法）]]|cloze|实时预览模式下正确显示涂黑和挖空效果|
|[[伪看板-yaml声明]]|kanban|伪看板的样式，无序列表四分栏|
|[[预览隐藏frontmatter]]|noyaml|预览状态不显示frontmatter区域|
|[[Callout环绕布局、缩进效果示例]]|fullwidth|callout实现文章环绕，全文缩进效果|
|[[code-wrap【代码块自动换行】]]|code-wrap|代码块自动换行|
|[[Image-grid【图片自适应】]]|img-grid|图片自适应分布|
|[[inline-list【行内列表】]]|inline-list|图片和列表混排|
 
<-->

| cssclass    | role                                                               |
| ----------- | ------------------------------------------------------------------ |
| code-wrap   | code-block-auto-wrap                                               |
| img-grid    | image adaptive distribution                                        |
| inline-list | images and lists mixed                                             |
| kanban      | pseudo-kanban style, unordered list of four columns                |
| fullwidth   | reduce column width on, control the full width of the page display |
| noscroll    | hide the current page scrollbar                                    |
| matrix      | four-quadrant table style                                          |
| cards       | rendering-dataview-tables-to-cards-view                            |
| cards       | rendering-dataview-tables-to-cards-view                            |
| noyaml      | preview state does not show the frontmatter area                   |


## 主题内置的ad样式表
ad样式使用方法参考
[[分栏效果示例#前置条件]]
[[分栏效果示例#AD样式效果]]

| Admonition类型 | 解释             | 使用        |
| ------------ | -------------- | --------- |
| blank        | 全透明框           | ad-blank  |
| def          | definition 定义  | ad-def    |
| thm          | theorem 定理     | ad-thm    |
| lem          | lemma 引理       | ad-lem    |
| cor          | corollary 推论   | ad-cor    |
| pro          | proposition 命题 | ad-pro    |
| hibox        | 自动隐藏框          | ad-hibox  |
| col2         | 内容分左右两栏        | ad-col2   |
| kanban       | 伪看板 无序列表并列     | ad-kanban |
| flex         | 自适应元素分栏        | ad-flex   |
## Javascript作用
> 88-Template\script

| 名称                 | 功能                             | 调用js的功能             |
| ------------------ | ------------------------------ | ------------------- |
| bookfromdouban.js  | 根据url从豆瓣获取图书数据                 | Quickadd-宏-豆瓣读书     |
| changeSticky.js    | 快捷修改home.md中的四个便签内容            | Quickadd-宏-添加首页便签   |
| colorclock.js      | 彩色时钟js                         | 已通过react组件实现，此js已弃用 |
| fetchhomepage.js   | 获取主页中的联网数据(OB启动后加载)            | quickadd-宏-Home工作区  |
| movies.js          | 从IMDB获取电影数据                    | quickadd-宏-电影卡片     |
| notice.js          | 生成自定义边栏提示                      | quickadd-宏-生成notice |
| refreshhomepage.js | 重载主页数据，重新获取联网数据                | quickadd-宏-重新获取主页数据 |
| getrandomImage.js  | 随机获取99-Attachment\banner文件夹的图片 | tp-日记模板获取banner     |
| getweather.js      | 获取天气数据                         | tp-日记模板获取天气         |
## ❓ 常见问题
1. 如何获取指定地区的天气？
		主页天气代码默认根据ip地址自动获取，如果手动指定`https://i.tianqi.com/?c=code&id=34&bdc=%23&icon=4&site=14&py=chongqing` chongqing改为你想要的城市拼音即可。
2. 如何更换字体？
   示例库默认配置的主字体为[[LXGWWenKai-Light.ttf]]  代码块字体为[[JetBrainsMono-Regular.ttf]]  可以自行安装，即可自动识别。
	如果要安装其他字体，打开 style settings设置，2.2.1字体设置，主字体里填写**字体名称**即可。注意如果字体名称有空格需要用单引号括起来。
		字体需要安装到系统里才会成功调用，比如win系统安装后显示的**字体名称**才是真正的字体名称。
		![[Pasted image 20220119151051.png]] ^d0e999
3. 如何更换Ob背景图？
		打开 style settings设置，1.2.1工作页面背景，开启背景，并在custom theme light(亮色主题使用)或者custom theme dark(暗色主题使用)里设置壁纸路径.壁纸路径需要使用类似格式url("app://local/XXXXX)设置本地图片。
		比如windows图片路径置
		url(app://local/D:/Documents/XXXX.jpg")
		mac系统图片路径设置 url("app://local/Users/XXXX .jpg")
4. 工作区页面背景跟笔记背景的区别?
		工作区页面背景是指整个OB界面背景，笔记背景仅仅是当前md文档的背景。两者不冲突可以同时设置，当然这样背景也就叠加一起了。如果只需要整个OB是一个背景图，笔记背景关闭即可。
5. 主页的歌曲和每日一言如何更新？
		点击主页的topaz图片 或者侧边栏的重载主页 都可以重新获取最新的歌曲和一言。重新获取后如何没有显示出来，点击刷新主页即可。
		![[Pasted image 20220119152758.png]]
6. 备忘录Memos 无法启动打开？
		开启核心插件日记，并指定日记文件夹位置。
7. 主页加载部分数据没有显示全？
		如果时钟不动或者主页没有显示全。手动点一下刷新主页即可。
8. 带按钮的常用工具侧边栏如何实现？
		其实就是`88-template/常用工具`笔记文档，打开后拖动文档标题前的图标到侧边栏即可。
9. 示例库目前有五十多个插件，实在太多了，想保持示例库主要功能的话需要几个插件
		示例库真正需要的核心插件并不多，大部分都是为了Ob使用更方便的辅助类插件，可以根据自己需要开启。
		如果想体验最精简版本的示例库很简单。
		按图修改[[FastStart-StartupScript]] ![[Pasted image 20220315145116.png|500]]  即可启动最低示例库运行插件配置。
		启动后启动ob只需要100ms
		![[Pasted image 20220315144725.png|300]]
10. 侧边栏悬浮memos 无法打开有错误提示？
			需要先`ctrl+p` ==>`打开其他库`，然后选择示例库“20-diary”文件夹，打开一次之后，这个悬浮按钮就自动生效。详情看[[Obsidian 库中库玩法#实现]]
11. 为什么在style setting下切换配色没什么效果？
	![[Pasted image 20220429154332.png]]
	注意2.1 里面的颜色设置 是不是有自定义颜色。这里的自定义颜色设置优先级比较高，建议把里面的颜色设置都恢复成默认就可以了。
12. 如何取消开启ob自动加载主页，我想打开ob出现上次关闭时的笔记？
	打开quickadd设置，宏管理 关闭home工作区的 启动加载选项。
	![[Pasted image 20220523110336.png]]
13. 如何移植动画版天气到自己的主页？并获取指定城市天气？
    直接复制"文字版天气加图标"注释之间的内容，并copy"88-Template/script/dv_weatherSvg.js"   启用【天气】weather.css 样式片段就移植成功了。设置指定地区天气，需要在quickadd宏home工作区中如图设置即可。![[Pasted image 20220531101243.png|400]]
14. 如何移植动画猫到自己的主页中？
    跟多彩时钟一样，动画猫也是react组件生成的。需要首先安装react_component插件，并copy`\88-Template\ReactJS\react_cat.md`  这样动画猫代码就生效了。
    
## 捐赠
如果你觉得不错，这个示例库对你使用ob有帮助，可以支持我一下。
![image|inl|350](https://user-images.githubusercontent.com/42957010/172568261-8a732d3d-303a-4367-993e-23c3efbf62a8.png) ![[Pasted image 20220608162248.png|inl|350]]
