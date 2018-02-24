生成pdf失败，暂未处理。

项目使用方法（因尚有缺陷，暂未发布到vscode市场。可手动安装）：

> // 下载项目
> git clone https://github.com/ZhYong10/vscode-markdown-html.git <br>
> // 进入目录
> cd vscode-markdown-html <br>
> // 安装vscode扩展打包工具 vsce <br>
> npm install -g vsce <br>
> vsce package // 将会生成markdown-pdf-0.1.8.vsix <br>

## 功能描述

1. 只能生成html。
未知的原因，导致生成pdf失败。
临时方案：用chrome打开生成的html，可以打印为pdf。

2. 项目里使用了过时的PhantomJS。功能可用，但正在考虑使用其他方案。
