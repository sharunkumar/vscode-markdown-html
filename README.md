## 简介

基于yzane的项目：[vscode-markdown-pdf](https://github.com/yzane/vscode-markdown-pdf)，添加了markdown-it-named-headers，并移除了与之冲突的 markdown-it-anchor。已验证：标题链接和外部链接正常。
生成pdf失败，暂未处理。

~~安装方法（因尚有缺陷，暂未发布到vscode市场。可手动安装）：
~~> // 下载项目
~~> git clone https://github.com/ZhYong10/vscode-markdown-pdf.git <br>
~~> // 进入目录
~~> cd vscode-markdown-pdf <br>
~~> // 安装vscode扩展打包工具 vsce <br>
~~> npm install -g vsce <br>
~~> vsce package // 将会生成markdown-pdf-0.1.8.vsix <br>

1. 下载release：[markdown-pdf.vsix.zip](https://github.com/ZhYong10/vscode-markdown-pdf/releases/download/0.1.8/markdown-pdf-0.1.8.vsix.zip)
2. 在vscode里安装扩展，选择从VSIX安装：markdown-pdf-0.1.8.vsix
3. 在settings.json里，添加用户设置导出格式为html："markdown-pdf.type": "html",
使用时。在vscode打开.md文档，使用命令：Convert Markdown To Pdf。

## 功能描述

1. 只能生成html。
未知的原因，导致生成pdf失败。
临时方案：用chrome打开生成的html，可以打印为pdf。
2. 项目里使用了过时的PhantomJS。功能可用，但正在考虑使用其他方案。

# Markdown PDF

This extension convert Markdown file to pdf, html, png or jpeg file.

## Features

Supports the following features.
* [Syntax highlighting](https://highlightjs.org/static/demo/)
* [emoji](http://www.webpagefx.com/tools/emoji-cheat-sheet/)
* checkbox

## Usage

### Command Palette

1. Open the Markdown file
1. Press `F1` or `Ctrl+Shift+P`
1. Type `pdf` and select `Convert Markdown to PDF`

![demo](https://raw.githubusercontent.com/yzane/vscode-markdown-pdf/master/images/usage1.gif)

### Menu

1. Open the Markdown file
1. Right click and select `Convert Markdown to PDF`

![demo](https://raw.githubusercontent.com/yzane/vscode-markdown-pdf/master/images/usage2.gif)

### Auto convert

1. Add `"markdown-pdf.convertOnSave": true` option to **settings.json**
1. Restart Visual Studio Code
1. Open the Markdown file
1. Auto convert on save

## Extension Settings

[Visual Studio Code User and Workspace Settings](https://code.visualstudio.com/docs/customization/userandworkspace)

1. Select **File > Preferences > UserSettings or Workspace Settings**
1. Find markdown-pdf settings in the **Default Settings**
1. Copy `markdown-pdf.*` settings
1. Paste to the **settings.json**, and change the value

![demo](https://raw.githubusercontent.com/yzane/vscode-markdown-pdf/master/images/settings.gif)

## Options

```javascript
{
	// Enable Auto convert on save
	"markdown-pdf.convertOnSave": false,

	// Excluded file name of convertOnSave option
	"markdown-pdf.convertOnSaveExclude": [
		"^work",
		"work.md$",
		"work|test",
		"[0-9][0-9][0-9][0-9]-work",
		"work\\d"  // \d -> \\d. All '\' need to be written as '\\'.
	],

	// Output Directory
	"markdown-pdf.outputDirectory": "C:\\work",

	// A list of local paths to the stylesheets to use from the markdown-pdf
	"markdown-pdf.styles": [
		"C:\\Users\\<USERNAME>\\Documents\\markdown-pdf.css",  // OK (Windows)
		"C:\Users\<USERNAME>\Documents\markdown-pdf.css",      // N/A. All '\' need to be written as '\\'. (Windows)
		"C:/Users/<USERNAME>/Documents/markdown-pdf.css",      // OK (Windows)
		"/home/<USERNAME>/settings/markdown-pdf.css",          // OK
		".vscode\\markdown-pdf.css",                           // OK. Relative path (Windows)
		".vscode/markdown-pdf.css",                            // OK. Relative path
		"markdown-pdf.css.css"                                 // OK. Relative path
	],

	// Set the style file name. for example: github.css, monokai.css ...
	// fine name list : https://github.com/isagalaev/highlight.js/tree/master/src/styles
	// demo site : https://highlightjs.org/static/demo/
	"markdown-pdf.highlightStyle": "github.css",

	// Enable Syntax highlighting
	"markdown-pdf.highlight": true,

	// Enable line breaks
	"markdown-pdf.breaks": false,

	// Enable emoji. http://www.webpagefx.com/tools/emoji-cheat-sheet/
	"markdown-pdf.emoji": true,

	// Output format: pdf, html, png, jpeg
	"markdown-pdf.type": "pdf",

	// Only used for types png & jpeg
	"markdown-pdf.quality": 90,

	// Page Option. Page size: A3, A4, A5, Legal, Letter, Tabloid
	"markdown-pdf.format": "A4",

	// Page Option. portrait or landscape
	"markdown-pdf.orientation": "portrait",

	// Page Option. Border Top. units: mm, cm, in, px
	"markdown-pdf.border.top": "1.5cm",

	// Page Option. Border bottom. units: mm, cm, in, px
	"markdown-pdf.border.bottom": "1cm",

	// Page Option. Border right. units: mm, cm, in, px
	"markdown-pdf.border.right": "1cm",

	// Page Option. Border left. units: mm, cm, in, px
	"markdown-pdf.border.left": "1cm",

	// Header contents
	"markdown-pdf.header.contents": "",

	// Header height. units: mm, cm, in, px
	"markdown-pdf.header.height": "",

	// Footer contents
	"markdown-pdf.footer.contents": "<div style=\"text-align: center;\">{{page}}/{{pages}}</div>",

	// Footer height. units: mm, cm, in, px
	"markdown-pdf.footer.height": "0.8cm"

}
```


## F.A.Q.

### How can I change emoji size ?

1. Add the following to your stylesheet which was specified in the markdown-pdf.styles.

```css
.emoji {
  height: 2em;
}
```


## [Release Notes](https://github.com/yzane/vscode-markdown-pdf/blob/master/CHANGELOG.md)

### 0.1.7 (2017/04/05)
* Change: Display completion message on status bar [#19](https://github.com/yzane/vscode-markdown-pdf/issues/19)
* Add: markdown-pdf.convertOnSaveExclude option [#16](https://github.com/yzane/vscode-markdown-pdf/issues/16)
* Fix: broken code-blocks [#18](https://github.com/yzane/vscode-markdown-pdf/pull/18)
* Fix: Image path error [#14](https://github.com/yzane/vscode-markdown-pdf/issues/14)
* Update: [markdown.css](https://github.com/Microsoft/vscode/blob/master/extensions/markdown/media/markdown.css) of the vscode
* Update: dependencies packages


## License

MIT


## Special thanks
* [vscode-markdown-pdf](https://github.com/yzane/vscode-markdown-pdf)
* [marcbachmann/node-html-pdf](https://github.com/marcbachmann/node-html-pdf)
* [markdown-it/markdown-it](https://github.com/markdown-it/markdown-it)
* [mcecot/markdown-it-checkbox](https://github.com/mcecot/markdown-it-checkbox)
* [mcecot/markdown-it-named-headers](https://github.com/leff/markdown-it-named-headers)
* [markdown-it/markdown-it-emoji](https://github.com/markdown-it/markdown-it-emoji)
* [HenrikJoreteg/emoji-images](https://github.com/HenrikJoreteg/emoji-images)
* [isagalaev/highlight.js](https://github.com/isagalaev/highlight.js)
* [cheeriojs/cheerio](https://github.com/cheeriojs/cheerio)
* [janl/mustache.js](https://github.com/janl/mustache.js)


and


* [cakebake/markdown-themeable-pdf](https://github.com/cakebake/markdown-themeable-pdf)
