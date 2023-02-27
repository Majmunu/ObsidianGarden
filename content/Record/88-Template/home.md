---
banner: "https://api.dujin.org/bing/1920.php"
cssclass: fullwidth,noyaml,noscroll,myhome
obsidianUIMode: preview
---



````ad-tip
title:常用工具
collapse: open
`button-textools`  `button-emoji` `button-table`  `button-carbon`

````


ad-icon
<svg xmlns="http://www.w3.org/2000/svg" aria-label="Calendar" role="img" viewBox="0 0 512 512">
  <path d="M512 455c0 32-25 57-57 57H57c-32 0-57-25-57-57V128c0-31 25-57 57-57h398c32 0 57 26 57 57z" fill="#e0e7ec"></path>
  <path d="M484 0h-47c2 4 4 9 4 14a28 28 0 1 1-53-14H124c3 4 4 9 4 14A28 28 0 1 1 75 0H28C13 0 0 13 0 28v157h512V28c0-15-13-28-28-28z" fill="#cf5659"></path>
 <g fill="#f3aab9">
        <circle cx="462" cy="136" r="14"/>
        <circle cx=```"462" cy="94" r="14"/>
        <circle cx="419" cy="136" r="14"/>
        <circle cx="419" cy="94" r="14"/>
        <circle cx="376" cy="136" r="14"/>
        <circle cx="376" cy="94" r="14"/>
      </g>
  <text id="month" x="32" y="164" fill="#fff" font-family="-apple-system, BlinkMacSystemFont, 'Noto Sans', 'Noto Sans CJK SC', 'Microsoft YaHei', 微软雅黑, sans-serif, 'Segoe UI', Roboto, 'Helvetica Neue', Arial" font-size="122px" style="text-anchor: left"><%+ tp.date.now("MMMM").toUpperCase() %>
  </text>
  <text id="day" x="256" y="400" fill="#333" font-family="-apple-system, BlinkMacSystemFont, 'Noto Sans', 'Noto Sans CJK SC', 'Microsoft YaHei', 微软雅黑, sans-serif, 'Segoe UI', Roboto, 'Helvetica Neue', Arial" font-size="256px" style="text-anchor: middle"><%+ tp.date.now("D") %>
  </text>
  <text id="weekday" x="256" y="480" fill="#66757f" font-family="-apple-system, BlinkMacSystemFont, 'Noto Sans', 'Noto Sans CJK SC', 'Microsoft YaHei', 微软雅黑, sans-serif, 'Segoe UI', Roboto, 'Helvetica Neue', Arial" font-size="64px" style="text-anchor: middle"><%+ tp.date.now("dddd") %>
  </text>
</svg>
```
%%便签板块%%
%%可通过侧边栏主页便签按钮快捷更改便签内容%%
---

````ad-flex
%%notice1%%
> [!stickies3]
> #### 倒计时
>> 今年已过去 <%+* tR+= moment().diff(tp.date.now("YYYY-1-1"), "days") %> 天
>> 
>> 距春节还有<%+* let edate = moment("2022-02-01", "yyyy-MM-DD"); let from = moment().startOf('day'); edate.diff(from, "days") >= 0 ? tR += edate.diff(from, "days") : tR += edate.add(1, "year").diff(from, "days") %> 天

%%notice2%%
> [!stickies3|blue]
>```dataviewjs
async function removeMarkdown (text) {
let excludeComments= true;
let excludeCode= true; 
let plaintext = text;
if (excludeComments) {plaintext = plaintext.replace(/<!--.*?-->/sg, "").replace(/%%.*?%%/sg, "");}
if (excludeCode) {plaintext = plaintext.replace(/```([\s\S]*)```[\s]*/g, "");}plaintext = plaintext.replace(/`\$?=[^`]+`/g, "").replace(/^---\n.*?\n---\n/s, "").replace(/!?\[(.+)\]\(.+\)/g, "$1").replace(/\*|_|\[\[|\]\]|\||==|~~|---|#|> |`/g, ""); return plaintext;}
async function getradomnote (files) {
const random = Math.floor(Math.random() * (files.length - 1));
const randomNote = files[random];
dv.paragraph(randomNote.link);
const sampleTFile = app.vault.getAbstractFileByPath(randomNote.path);
const contents = await app.vault.cachedRead(sampleTFile); 
return contents;}
let reg=/[\u4e00-\u9fa5]/
let nofold = '!"88-Template" and !"99-Attachment" and !"50-Inbox" and !"20-Diary"';
let files = dv.pages(nofold).file;
let content =await getradomnote(files);
let clean= await removeMarkdown(content);
let lines = clean?.split("\n").filter(line => line.match(reg));
const randomline = Math.floor(Math.random() * (lines.length - 1));
lines = lines[randomline]?.replace(/(\r|\n|#|-|\*|\t|\>)/gi,"").substr(0,80) + '...';
dv.span(lines);
>```

%%notice3%%
> [!stickies3|pink]
> #### 每日一句
> ```dataviewjs
 let history = Object.assign(JSON.parse(await app.vault.adapter.read(".obsidian/.diary-stats")));
 let today = moment().format("YYYY-MM-DD");
 if (history.hasOwnProperty(today))
 {
 let quotes=history[today].quotes;
 dv.el("blockquote", quotes);
 }
> ```

%%notice4%%
> [!stickies3|green]
> ### 💌
> 开启美好的一天
````

---

````ad-flex
```ad-note
title: 🤔 快速导航
color: 178,155,64
> “Quick Access”
-  `button-richeng`

-  `button-kanban`

- `button-suibi2`

- `button-renwu2`

- 📆 `$= '[[日记统计#'+ moment().format("YYYY-MM") +'|当月日记]]'`

```
```ad-note
title: 😏 功能
color: 99,188,76
> “Common actions”
- Ⓜ️ [生成MOC](obsidian://advanced-uri?commandid=templater-obsidian%253A88-Template%252Ftp_foldermoc-Include-subfolders.md)

- 📚 [豆瓣读书](obsidian://advanced-uri?commandid=quickadd%253Achoice%253A19402f67-f691-4b0f-9975-f8203e74be96)

- 🎞️ [豆瓣电影](obsidian://advanced-uri?commandid=quickadd%253Achoice%253Aaabcb6ad-5faa-45fb-a713-deddc27bc384)

- 💠 [[随机显示文档中的图片和文字|随机漫游]]

```

```ad-note
title: 🥰 阅读笔记
color: 178,22,164
> “Media”

- 💬 [[微信读书清单|微信阅读]]

- 📑 [[图书阅读清单(dv)|图书馆]]

- 👁 [[电影看板]]

- 🛹[[可以编辑的dv表格|资料维护]]

```
```ad-note
title: 🤩 帮助教程
color: 139,65,06
> “Tutorials”

- 🚩 [Cuman的B站](https://b23.tv/2Uqt2dn)

- 🥑 [[🥑Blue Topaz Themes Tips|主题TIPS]]

- 🇲🇩 [[MarkDown教程 Obsidian版 2022.4.22|MD超级教程]]

- [[🔑Dataview教程]]

- 💾 [[77-Example|示例库]]

```
````



![[从这开始#MOC 另一种样式]]

![[从这开始#最近编辑]]

![[通过下拉框检索文件示例]]

![[项目追踪（完成的字数和任务）#选择需要跟踪的项目]]

---
