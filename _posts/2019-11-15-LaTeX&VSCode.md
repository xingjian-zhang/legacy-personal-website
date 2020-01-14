---
layout:     post
title:      如何轻松愉快地使用LaTeX
subtitle:   使用VSCode及众多扩展编写.tex文件
date:       2019-11-15
author:     JIM
header-img: img/post-bg-coffee.jpg
catalog: true
tags:
    - LaTeX
    - VSCode
    - 排版
    - 报告
---
# LaTeX × VSCode

第一篇blog 献给LaTeX和VS Code

最近241/215/260/...各种地方需要用到LaTeX肝报告，之前一直用的*Texmaker*，没觉得有多不好，直到受余祖指点，开始上手VSCode，前者完全被碾压。以前只是感觉VSCode写代码还可以，没想到用来写LaTeX体验也可以**这么好**，再次深刻地感受到：一个好的编辑器，能极大地提升我们学习工作的**效率**和**体验**。

有好几个朋友来问为啥VS Code好用，所以开个帖子在这，希望能总结一下使用心得，配置方法等等，也许能帮到大家。此外，写这个贴子也是想锻炼一下自己做TC的能力。欢迎评论指正~

## 帖子目的

* 介绍VS Code编辑LaTeX的特性

## 适用对象

* 无LaTeX基础的小白
* 有一定LaTeX基础的Texmaker用户
* Windows/Mac用户


P.S. 很有可能以后还会尝试一些别的LaTeX编辑器，如果有感觉更好的也会在这个贴子下更新。

## *TODO list*：
 - [ ] 快速加粗/斜体=>如何在文本两端快速添加代码
 - [ ] 一些有用的小工具
 - [ ] 如何利用Git管理LaTeX project

---

# 简介

这部分介绍LaTeX，Texmaker，VS Code，如果有所了解可以直接跳过。


## LaTeX

首先介绍一下**LaTeX**：

> **LaTeX** ，是一种基于[TeX](https://zh.wikipedia.org/wiki/TeX)的排版系统，由美国计算机科学家[莱斯利·兰伯特](https://zh.wikipedia.org/wiki/%E8%8E%B1%E6%96%AF%E5%88%A9%C2%B7%E5%85%B0%E4%BC%AF%E7%89%B9)在20世纪80年代初期开发，利用这种格式系统的处理，即使用户没有排版和程序设计的知识也可以充分发挥由TeX所提供的强大功能，不必一一亲自去设计或校对，能在几天，甚至几小时内生成很多具有书籍质量的印刷品。对于生成复杂表格和数学公式，这一点表现得尤为突出。因此它非常适用于生成高印刷质量的科技和数学、物理文档。这个系统同样适用于生成从简单的信件到完整书籍的所有其他种类的文档。
(原文链接：https://zh.wikipedia.org/wiki/LaTeX)

由此，简单总结一下LaTeX的优点：

* 基本无需排版
* 便于编辑公式
* 减少重复工作
* 后期修改方便

LaTeX的缺点：

* 上手没Word这种编辑器快（真要入门也很快）
* 复杂公式/表格的编辑常常要借助第三方软件/网站
* 仔细想想上面俩也不算缺点

身在JI，个人觉得**LaTeX是迟早要学的**，而且学习收益>>学习成本，用熟了之后效率很顶，虽然制造的是~~学术垃圾~~普通报告，但是看起来就专业很多。
LaTeX入门教程很多，在网上对着教程写个两份report就算上手了，这里就不放链接了，毕竟这篇帖子主要讲的是怎么用VS Code加快肝report的速度。

接下来介绍一下*Texmaker*和*VSCode*

## Texmaker
---
官网：[https://www.xm1math.net/texmaker/](https://www.xm1math.net/texmaker/)

> **Texmaker** 是一款跨平台的开源LaTeX编辑器，它界面干净并集成有PDF阅读器。
（原文链接：[https://zh.wikipedia.org/wiki/Texmaker](https://zh.wikipedia.org/wiki/Texmaker)）

照例总结一下优缺点，欢迎补充

优点：
* 轻量化
* 基本不需要额外的配置 装了就能用
* 有一些帮助编辑的功能（拼写检查，pdf分屏等等）
* 符号插入很方便（边上keymap）

缺点：
* 上古界面 颜控忍无可忍
* 很多关键词没有代码补全，需要手敲
* 功能都比较基础

## Visual Studio Code（for LaTeX）

官网：[https://code.visualstudio.com/](https://code.visualstudio.com/)

> **Visual Studio Code** （简称 **VS Code** ）是一个由微软开发，同时支持Windows 、 Linux和macOS等操作系统且开放源代码的代码编辑器，它支持[测试](https://zh.wikipedia.org/wiki/%E8%B0%83%E8%AF%95)，并内置了[Git 版本控制](https://zh.wikipedia.org/wiki/Git)功能，同时也具有开发环境功能，例如代码补全（类似于 [IntelliSense](https://zh.wikipedia.org/w/index.php?title=IntelliSense&action=edit&redlink=1)）、代码片段和[代码重构](https://zh.wikipedia.org/wiki/%E4%BB%A3%E7%A0%81%E9%87%8D%E6%9E%84)等，该编辑器支持用户个性化配置，例如改变主题颜色、键盘快捷方式等各种属性和参数，同时还在编辑器中内置了扩展程序管理的功能。
（原文链接：https://zh.wikipedia.org/wiki/Visual_Studio_Code）

优点：
* 可安装各种功能强大的扩展程序
光扩展的优点就很多了，之后慢慢讲
* 快捷编辑（代码块，缩写等等）
* 自定义主题/配色方案（高颜值）
* 交互界面比较人性化
* 配置各种个性化编辑偏好

缺点：
* 各种扩展功能很多，但比较难找到相应的demo和handbook
* 一些扩展有奇奇怪怪的bug
目前还没发现什么大的缺点

下面两张图分别是用Texmaker和VSCode打开一篇.tex文档编辑时的场景。

Texmaker:![Texmaker](https://img-blog.csdnimg.cn/20191031215034697.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)
VS Code:
![VS Code](https://img-blog.csdnimg.cn/20191031215129536.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70) 
可以看出，两者都能够显示structure，pdf等关键信息，在这一方面上，VS Code并没能体现出它的优势，不过界面的确是好看很多了。那么VS Code的优势在哪里呢？
注意看第二张图，当把光标移动到一个equation环境时，这个equation的预览出现了，这就是扩展程序的功能，很多很杂，但都十分实用，接下来我将分点介绍一些对写报告十分实用的功能。
P.S. 这份DPF就是215lab2的manual，绝无HC用意，侵删。

---

# 配置

前面写了一大堆很主观的体验，现在展示一下VS Code中LaTeX开发环境的配置。
这里默认已配置好VS Code和Texlive，如果没有，直接去[VSC官网下载](https://code.visualstudio.com/)，[Texlive下载](https://tug.org/texlive/)。

打开VS Code，进入屏幕左侧Extension界面，搜索并install, enable以下几个插件：

<img src="https://img-blog.csdnimg.cn/2019103121542070.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70" width="70%" />

↑随手打开一个.tex文档，可以看到左侧tool bar出现了“TEX”，代码也被高亮显示了。

再配置一下编译工具，我们就可以开始愉快地使用VS Code来写report了。
打开VS Code settings，进入到User的setting.json文件里。（这里是保存VS Code全局设置的地方，相对应的Workspace里也有一个setting.json，用来保存针对单个项目的设置。优先级：workspace > user > system default）

![配置](https://img-blog.csdnimg.cn/20191031215442398.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

打开setting.json之后，把这段代码粘贴进去
```json
"latex-workshop.latex.tools": [
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "%DOC%"
            ]
        },
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
              "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
      {
        "name": "PDFLaTeX",
        "tools": [
          "pdflatex"
        ]
        },
      {
        "name": "XeLaTeX",
        "tools": [
          "xelatex"
        ]
      },
      {
        "name": "latexmk",
        "tools": [
          "latexmk"
        ]
      },
      {
        "name": "BibTeX",
        "tools": [
          "bibtex"
        ]
      },
      {
        "name": "pdflatex -> bibtex -> pdflatex*2",
        "tools": [
          "pdflatex",
          "bibtex",
          "pdflatex",
          "pdflatex"
        ]
      },
      {
        "name": "xelatex -> bibtex -> xelatex*2",
        "tools": [
          "xelatex",
          "bibtex",
          "xelatex",
          "xelatex"
        ]
      }
  ],
```
当然可以根据自己需要调整编译方式，参考[https://zhuanlan.zhihu.com/p/38178015](https://zhuanlan.zhihu.com/p/38178015)。

File->Save, 再随便打开一个.tex 文档，点击TEX扩展，可以看到左侧的TEX tool bar中出现了我们设置好的各种build recipe。

<img src="https://img-blog.csdnimg.cn/20191031215509462.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70" width="30%" />

点击“Build LaTeX project”，或者指定一种recipe来构建文档，再点“View LaTeX PDF”，我们就可以看到PDF预览了。分屏后，再次构建，PDF也会自动更新。此外，点击下方的“Structure”就可以看到文档结构，和Texmaker一样。

![pdf预览](https://img-blog.csdnimg.cn/20191031215605898.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

到目前为止，我们基本可以使用VS Code来写报告了。别的不说，至少这界面让人看起来就舒服很多，生产力也就上去了。:call_me_hand::call_me_hand::call_me_hand: VS Code的高亮当然也可以自己去配（Setting->Color Theme）图中用的是Monokai。

在这些之外，我们还可以自定义配置：
* PDF阅读器（目前我用的还是VS Code集成的，准备有空搞一搞SumatraPDF，据说支持latex-pdf正反向搜索）
* 一些其他扩展（比如TODO highlight）

---

# 【重点】实用功能

这一部分主要讲VS Code是怎么**直接提升LaTeX的编辑效率**的，包括以下内容
1. 特殊符号输入
2. 自定义代码块/快捷键
3. 代码缩进
4. 双向查找
5. 快速插入图片

## 特殊符号输入

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031215852474.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

LaTeX workshop集成的Snippet Panel包含了所有基本的特殊符号，在LaTeX tool bar中点击“Snippet Panel”即可唤出。相比texmaker，这个面板还包含了**检索**功能：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031215901779.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

除了特殊符号外，Snippet Panel还包含了[Tikz](https://en.wikipedia.org/wiki/PGF/TikZ)的快捷插入，用于绘制各种矢量图，在此不做赘述。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031215912582.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

我们还可以自定义**键盘快捷方式**来快速调出Snippet Panel：左下角齿轮->Keyboard Shortcuts，搜索latex snippet，设置快捷键。我习惯设置成<kbd>ctrl</kbd>+<kbd>S</kbd>+<kbd>P</kbd>，保存设置后退出，按下<kbd>ctrl</kbd>+<kbd>S</kbd>+<kbd>P</kbd>，召出Snippet Board，方便！

## 自定义代码块/快捷键

LaTeX language support等扩展程序内置了LaTeX的代码补全，比方说我们输入来新建一个enumerate环境：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019103122001492.gif)

除去正文瞎输的一些文字，整个过程就没敲几下键盘。
注意到几个细节：
* 换行时，自动出现了新的\item，这是LaTeX workshop的特性
* 按Tab时，自动切换到下一个位置，免去鼠标/键盘移动，这是VS Code代码块快速切换的特性
* 字符下面出现波浪线提示~~强调事实~~拼写错误，这是扩展Spell Checker的特性

只是创建一个环境，就得到了多个扩展的帮助，这效率就很顶:call_me_hand:

再来一个插入figure的demo，注意光标每次位置的切换：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031220049359.gif)

注意这里我们插入的是ACM规范的图片

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031220109357.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

输入figure，我们会发现提示框里面有很多补全，有的有重复（之前安装的三个插件有些补全是相似的），后面再研究一下怎么避免这个问题。不过，由于每次补全都会默认首选上次使用的补全，所以影响也不是很大。

那么补全都有哪些呢？由于这些扩展程序都是在GitHub上开源的，我们可以直接通过源码看到都有哪些代码块，以LaTeX language support为例：[传送门](https://github.com/sabertazimi/LaTeX-snippets/blob/master/snippets/snippets.json)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019103122012722.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70)

扩展程序给出的代码补全非常丰富，但是，我们每个人都有自己的代码习惯，也有自己常用的一些代码块，我们也可以通过**设置User Snippets**的方式来自定义编辑代码块。

方法：齿轮->User Snippets->latex->latex.json
根据文档的指导，我们可以自己创建属于自己的代码块：
```json
    // Place your snippets for latex here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	// "Print to console": {
	// 	"prefix": "log",
	// 	"body": [
	// 		"console.log('$1');",
	// 		"$2"
	// 	],
	// 	"description": "Log output to console"
	// }
```
按照这个格式编写即可，$1 $2 ... $n是按Tab后光标依次出现的位置，$0表示最后一次出现的位置。注意：输入字符串的特殊符号需要转义，比如'\\newline'需要写为‘\\\\newline’。

我们以引用图片为例，说明怎么编写自己的代码块
```json
	"Figure reference":{
		"prefix": "figref",    //在文档中输入figref即可选择此代码块
		"body":[
			"Fig.\\ref{fig:$1}$0"
		],
		"description": "Refer to a figure"    //在候选框中可以看到对此代码块的描述
	},
```
当我们输入figref时，就可以插入这个迷你代码块了。
```tex
Fig.\ref{fig:}
```

## 代码缩进

代码缩进有助于我们的文档条理清晰，对于洁癖来说，看到一堆乱七八糟的代码很难有好心情。所幸VS Code本身就有editor formatter的功能，我们只需要安装特定的formatter扩展就行。
如果你不想安装什么特别的formatter，latex workshop里自带的formatter一般就可以满足你的需求。配置方法就是在settings.json里粘贴一下代码：
```json
"[latex]": {
    "editor.defaultFormatter": "James-Yu.latex-workshop"
  },
```
展示一下效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019103122023031.gif)

使用方法：
1. 直接<kbd> Shift </kbd>+<kbd> Alt </kbd>+<kbd> F</kbd>

2. <kbd> Ctrl </kbd>+<kbd> P </kbd> 召出命令窗，输入“>Format document”并选择
3. 鼠标右键 -> format document
爽。

## 查找内容

最后再说一下这个latex-pdf双向搜索= =
整了一个小时终于整出来了！！不过是真的好用，哭了，配置代码直接在下面分享给大家
首先[下载并安装SumatraPDF](https://www.sumatrapdfreader.org/download-free-pdf-viewer.html)，记住路径。
猜测一下，有的小伙伴就要问了，要这个SumatraPDF有什么用呢？不是已经有集成的pdf阅读器了吗？
原因：SumatraPDF轻量却**功能完备**，且支持**双向搜索**！

然后我们需要把latex workshop自带的pdf阅读器给改成Sumatra PDF，这一步要注意了，按网上的方法一个个试我基本没有成功，最后还是自己摸索出来的。

我们把以下配置信息粘贴到settings.json里，注意看一下有没有和上下文冲突的重复设置，有的话需要把以前的覆盖掉。
```json
  "latex-workshop.view.pdf.external.viewer.command": "C:\\Program Files\\SumatraPDF\\SumatraPDF.exe",    // 改成SumatraPDF的路径, 注意转义符
  "latex-workshop.view.pdf.external.synctex.command": "C:\\Program Files\\SumatraPDF\\SumatraPDF.exe",    // 同上
  "latex-workshop.view.pdf.external.synctex.args": [
    "-forward-search",
    "%TEX%",
    "%LINE%",
    "%PDF%"
  ],
```
**注意：** 请把两个文件路径改成自己安装的SumatraPDF的执行路径！

由于这个配置文本是我自己写的，虽然我的电脑设置成功运行，也许在别的环境下设置不通过，此情况可参考[https://zhuanlan.zhihu.com/p/38178015](https://zhuanlan.zhihu.com/p/38178015)

现在我们就可以使用latex->pdf查找了，赶紧试一下~
方法：
1. 点击<kbd> Ctrl </kbd>+<kbd> Alt </kbd>+<kbd> J </kbd>
2. 点击左侧tool bar中的 “SyncTex from cursor”

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031220336282.gif)

而反向搜索要在SumatraPDF中设置，打开SumatraPDF->设置->选项->设置反向搜索命令行

<img src="https://img-blog.csdnimg.cn/20191031220413195.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70" width="50%" />

删掉默认的命令，替换为
```
"C:\Users\10907\AppData\Local\Programs\Microsoft VS Code\Code.exe"  -g "%f:%l"    //将前面的执行路径设置为VS Code的exe文件
```
**注意：** 第一个引号内要填写VS Code的可执行文件的路径，嫌找麻烦的话，直接右键VS Code，点击属性，复制里面的目标路径。

<img src="https://img-blog.csdnimg.cn/20191031220438653.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70" width="50%" />

点击确定，大功告成！

我们来试一下效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031220500555.gif)

**爽到**，谁用谁知道！

然而，这个功能就有个**小bug**，如果我们直接在VS Code里打开SumatraPDF，也就是点击View LaTeX PDF，再双击PDF界面，VS Code竟然啥反应都么得！这是为什么呢？

我上LaTeX workshop扩展的[Github主页](https://github.com/James-Yu/LaTeX-Workshop)上查了一下，发现有这么一个issue： [Synctex inverse search doesn't work half the time (and How I got forward search to work for SumatraPDF) #637](https://github.com/James-Yu/LaTeX-Workshop/issues/637)。作者 **[James-Yu](https://github.com/James-Yu)**这样解释：
> The external program was executed using child_process, which, as its name implies, opens the viewer as a child process in vscode. This can explain all your observations.
However, there is no work-around on the extension side. You may try using CMD.exe someviewer.exe instead of its current form.
All in all, external viewer support is unfortunately a second-class citizen in the context, and there is no obvious and universal solution to your problem.

大致意思就是说VS Code开的SumatraPDF只是作为一个子进程，无法使用反向查找，那么解决方法是什么呢？

**在VS Code外启动SumatraPDF**，SumatraPDF就不再作为一个子进程被启动了~ 这么做听起来有点麻烦，但毕竟反向查找真的能节约很多时间，算是值了。这么做再次测试一波，发现反向查找被成功触发了。

## 快速插入图片

首先感谢@zbm，介绍了如何**从剪切板直接向LaTeX中插入图片**。

先上demo：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191031220521736.gif)
（↑ 截图后，在LaTeX中创建图片environment，并直接把复制好的图片插入进来，注意到在粘贴图片的时候，剪贴板中的图片被保存在了当前路径下，且直接以时间命名防止重复）

实现这个功能，我们需要安装扩展：Paste Image

<img src="https://img-blog.csdnimg.cn/20191031220537530.png" width="50%" />

**注意：** 这个扩展默认的图片粘贴快捷键是<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>V</kbd>，而不是<kbd>Ctrl</kbd>+<kbd>V</kbd>。

如果我们使用Windows自带的截图工具（如demo所示），截图后会自动把图片保存到剪贴板里，无缝衔接上了这个扩展。考虑到我们写报告时经常需要截图，这个功能是非常方便的！



---


# 结语

那么到此为止，VS Code的优点已经介绍的差不多了。值得一提的是，这些实用特性只是我接触 VS Code × LaTeX 这个奇妙组合三天之内发现的，可以想象以后还能找到许多有用的功能，我也会在本帖更新。

**开始题外话：**

<img src="https://img-blog.csdnimg.cn/20191031222734725.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDAwOTU5OQ==,size_16,color_FFFFFF,t_70" width="40%" />

余祖所言的费曼学习法属实好用，如果不是开了坑督促自己研究VS Code，我八成需要一学期才能零零散散把这LaTeX环境配置好。

爆肝三天写这个blog也是希望向大一小朋友介绍LaTeX的重要性，希望小朋友们能少受点某些课（懂得都懂）的折磨（大朋友们也是，有些苦吃得有价值，有些苦个人认为是完全没必要吃的）。毕竟如果不在某些课程上减负，我们能做的就是把手上的刀换把好的，再磨快点。

:vulcan_salute: