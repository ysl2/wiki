# [study] Research workflow software

| Tool                                                 | Read papers | Write papers | Presentation              |
| ---------------------------------------------------- | ----------- | ------------ | ------------------------- |
| [`git`](https://git-scm.com/)                        | Y           | Y            | Y                         |
| [`nutstore`](https://www.jianguoyun.com/)            | Y           |              | Y                         |
| [`zotero`](https://www.zotero.org/)                  | Y           |              |                           |
| [`obsidian`](https://obsidian.md/)                   | Y           |              |                           |
| [`overleaf`](http://overleaf.com/)                   |             | Y            |                           |
| [`lazyvim`](https://www.lazyvim.org/)                |             | Y (latex)    | Y (mindmap + latex table) |
| [`drawio`](https://draw.io/)                         |             | Y            | Y                         |
| [`tablesgenerator`](https://www.tablesgenerator.com) |             | Y            | Y                         |
| [`wps`](https://www.wps.cn/)                         |             |              | Y (ppt)                   |
| [`tencent-doc`](https://docs.qq.com/)                |             |              | Y (ppt)                   |
| [`mubu`](https://mubu.com/)                          |             |              | Y                         |
| [`mermaidchart`](https://mermaidchart.com)           |             |              | Y                         |

## Read papers

### 需求

- 文献阅读和归档
- 文献笔记+画图+插入图片
- 可丝滑导出笔记+cite到latex

### 解决方案

- 阅读：zotero提供文献归档、阅读标注功能，并且可通过webdav备份
- 笔记：obsidian本身提供完备笔记功能，备份可通过git或者webdav
- 图片：obsidian第三方drawio插件，可画图；自带图片插入功能
- 联动：obsidian对于文件提供url，可链接到zotero
- 导出：zotero第三方插件复制biblatex，然后手动粘贴到obsidian的笔记做链接

### Known issues

- obsidian只提供文件url，不提供文件夹url
- obsidian的drawio插件，左侧工具栏默认折叠，需要手动打开
- obsidian的drawio插件，图片刚创建时无预览，必须切换一下笔记才能展示预览
