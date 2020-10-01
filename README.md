# 中山大学物理学院实验报告LaTeX模板

papermodel：论文格式报告模板  
reportmodel：完整实验报告模板

### v1.1 （20200825）
- 将中文字体均设置为了开源字体方正书宋、方正楷体和方正黑体。
- 公式模板修改
- 微调部分注释

---



## 简单指引

关于LaTeX的安装，在非特殊情况下推荐直接安装Tex Live（在macOS上为MacTex）。

- [TeX Live官网](https://tug.org/texlive/)
- [MacTeX官网](https://tug.org/mactex/)

> 安装教程：（比如）[TeX Live 下载及安装说明 | 始终](https://liam.page/texlive/)

如果你从未用过LaTeX进行文章的排版，网上已经有很多优秀的教程。

> 推荐入门教程：[一份其实很短的 LaTeX 入门文档 | 始终](https://liam.page/2014/09/08/latex-introduction/)

安装完Tex Live或者MacTex之后，会自带一个编辑和编译器TeXworks，可以在入门的时候使用，进行简单的学习，但是在实际使用上很不方便。目前比较时髦的配置环境是用微软的 VS Code + 插件 LaTeX Workshop使用，配置十分方便，比笔者之前用的“Sublime Text+Sumatra PDF+Ghostscript+ImageMagick”方便得多，且具体使用起来更加舒服。

![image-20201001150413270](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001150413270.png)

> 配置教程可以参考近期LaTeX工作室的一个直播教程：
>
> - [金秋八月，LaTeX 直播一：LaTeX 安装与基础概念_哔哩哔哩 (゜-゜)つロ 干杯~-bilibili](https://www.bilibili.com/video/BV1Qi4y1g7BL)
> - [LaTeX 安装指南与基础介绍 - LaTeX 直播附带资料 - LaTeX 工作室 - 中国第一个 LaTeX 专业服务网站，学习，模板，开发一应俱全](https://www.latexstudio.net/index/details/index/mid/746.html)

## 中文字体的设置

在这里给出**Windows10**环境下，设置中文字体的一个相对比较完整的流程，以[思源宋体](https://github.com/adobe-fonts/source-han-serif)的安装和使用为例。

### 字体的下载

字体文件的常见格式主要有TrueType (TTF)和OpenType (OTF)等格式的，在各大网站下载的都是可以用的，不管是GitHub下载的开源字体，某些官方网站的商业字体，还是在一些聚合站点上下载的字体。比如说我们进入思源宋体的[GitHub下载主页](https://github.com/adobe-fonts/source-han-serif/tree/release)，在下面这里点击下载链接，

![image-20201001151818925](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001151818925.png)

就会自动下载含有字体文件的压缩包（我点击的是[ExtraLight + Light + Regular + Medium](https://github.com/adobe-fonts/source-han-serif/raw/release/OTF/SourceHanSerifSC_EL-M.zip)），

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001151918472.png" alt="image-20201001151918472" style="zoom: 80%;" />

解压后可以看到一些OTF文件，这就是我们要用的文件，如果你手头上有这样的文件，可以直接拿来用。

![image-20201001152004526](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001152004526.png)

安装字体的方式很简单，右键安装即可；但是需要注意的是，一定要点击“为所有用户安装”

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001152208858.png" alt="image-20201001152208858" style="zoom:80%;" />

如果只点击了“安装”，在Word等软件中可以正常使用这个字体，但是用LaTeX编译的时候会出现无法调用而报错的问题。

---

Windows 10的设置中可以查看自己安装的字体，这个面板可以在设置中进行搜索进入

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001152441720.png" alt="image-20201001152441720" style="zoom:67%;" />

安装成功之后，在“字体设置”页面中搜索应该可以看到这个字体。

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001152556619.png" alt="image-20201001152556619" style="zoom:67%;" />

> 注意，如果通过将字体文件拖放到“字体设置”页面的“添加字体”那个虚线方框中进行字体的安装，并不是为所有用户安装的，不能成功被LaTeX调用。

对于思源宋体这种字体，它是含有多种粗细型号的，都可以在这个面板进行预览和查看。

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001153724376.png" alt="image-20201001153724376" style="zoom:67%;" />

### 查看安装的字体及其代号

上面的在windows设置面板中查看安装的字体，其作用是方便查看字体的预览。并不能给我们在LaTeX调用字体是要用的准确的“代号”。要查看这个代号，我们在命令行（需要用管理员身份运行）中输入

```
fc-list -f "%{family}\n" :lang=zh >d:zhfont.txt
```

系统就会输出一个文件`zhfont.txt`，放在D盘中（当然你可以自己修改路径，更多的信息可以搜索了解）。打开这个文件之后，你就会看到系统中安装的所有中文字体及其代号，都可以在LaTeX中随意调用，当然也包括我们刚刚安装的“思源宋体”，

![image-20201001153748087](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001153748087.png)

所有用逗号`,`隔开的短语，如`Source Han Serif SC`，`思源宋体`，`Source Han Serif SC Medium`，`思源宋体 Medium`，都可以作为后面调用的代号，其中后两者代表“Medium”这个粗细，而前两者实际上代表的是这个字体的默认粗细，即“Regular”，想要调用非默认粗细的话需要注意代号。

安装新字体之后，为了给TeX Live调用，我们刷新一下TeX Live中的字体，在命令行中运行，一般3次就可以了

```
fc-cache -fsv
```

### 使用`xeCJK`宏包调用系统中已安装的字体

我们使用宏包`xeCJK`进行中文字体的设置：

```tex
\usepackage{xeCJK}
```

下面介绍几个常用的命令，更多的玩法网上已经有很多教程。

#### 1. 设置主要文字

首先是对整篇文档主要文字的设置，包括默认字体、加粗字体和斜体字体，

```tex
\setCJKmainfont[ItalicFont=方正楷体简体,BoldFont=FZHei-B01S]{Source Han Serif SC}
```

| 字体     | 对应命令     | 示例字体            |
| -------- | ------------ | ------------------- |
| 默认字体 | -            | Source Han Serif SC |
| 加粗字体 | \textbf{xxx} | FZHei-B01S          |
| 斜体字体 | \textit{XXX} | 方正楷体简体        |

正如上面的示例，我们调用一个字体，既可以用英文代号，也可以用中文代号。下面是一个示例：

```tex
我们对\LaTeX 中\textbf{中文字体}的\textit{设置}进行介绍。
```

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001161913855.png" alt="image-20201001161913855" style="zoom:50%;" />

#### 2. 临时调用某个字体

另外一个常用的命令是临时调用某个字体`\CJKfintspec`：

```tex
{\CJKfontspec{方正楷体简体} 实验时间：2020年9月21日~星期一~下午}
```

> 注意如果是在一大段文字中临时调用字体，一定不能忘记最外面的大括号，否则从这一行起，后面所有的文字都会变成这个字体。

如果嫌上面的命令麻烦，可以使用LaTeX的`\newcommand`自己给调用的字体命名，

```tex
\renewcommand{\songti}{\CJKfontspec{Source Han Serif SC}}%用命令\songti调用思源宋体
\newcommand{\fzkaiti}{\CJKfontspec{方正楷体简体}}%用命令\fzkaiti调用方正楷体简体
```

然后就可以用下面的命令临时调用文字（注意两种方式，最外面的大括号都不能省略），

```tex
使用{\fzkaiti 方正楷体简体}进行书写
```

```
使用{\fzkaiti{方正楷体简体}}进行书写
```

可能有的读者注意到，第一行用的是`\renewcommand`而不是`\newcommand`。这是因为，如果我们引用了`ctex`宏包或者文档类型用的是`ctexart`，我们可以直接用`ctex`宏包自带的字体：

<img src="http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001161128142.png" alt="image-20201001161128142" style="zoom:50%;" />

比如说临时调用隶书这个字体，

```
{\lishu{下面}}是ctex宏包中自带的字体，可以直接使用
```

相应的，我们在自定义字体的时候，就不能和这些字体的命令重名，否则会报错。实际上，我们想进行的操作是替换掉原来的`\songti`命令，故需要用`\renewcommand`。

---

最后给出一个样例代码

```tex
\documentclass[UTF8]{ctexart}
\usepackage{xeCJK}
\setCJKmainfont[ItalicFont=方正楷体简体,BoldFont=FZHei-B01S]{Source Han Serif SC}
\renewcommand{\songti}{\CJKfontspec{Source Han Serif SC}}%用命令\songti调用思源宋体
\newcommand{\fzkaiti}{\CJKfontspec{方正楷体简体}}%用命令\fzkaiti调用方正楷体简体
\begin{document}
    我们对\LaTeX 中\textbf{中文字体}的\textit{设置}进行介绍。\\
    {\lishu 下面}是ctex宏包中自带的字体，可以直接使用；相应得，我们在自定义字体的时候，{\fzkaiti 不能}和这些字体的命令重名。\\
   \begin{tabular}{|lll|}
        \hline 
        \songti 宋体    & SimSun          &\verb|\songti 宋体|   \\
        \kaishu 楷体    & KaiTi           &\verb|\kaishu 楷体|   \\
        \heiti 黑体     & SimHei          &\verb|\heiti 黑体|    \\
        \yahei 微软雅黑  & Microsoft YaHei &\verb|\yahei 微软雅黑| \\
        \fangsong 仿宋  & FangSong        &\verb|\fangsong 仿宋| \\ 
        \youyuan 幼圆   & YouYuan         &\verb|\youyuan 幼圆|  \\
        \lishu 隶书     & LiSu            &\verb|\lishu 隶书|    \\
        \hline 	
    \end{tabular} 	
\end{document}
```

![image-20201001162918360](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001162918360.png)

## 其他常用的工具

### 表格的制作

在LaTeX中制作表格是一件很麻烦的事情，好在我们有一些拓展宏可以实现将excel中的表格转化为代码。在这里我们推荐加载项`Excel2LaTeX`，其官网为[CTAN: Package Excel2LaTeX](https://www.ctan.org/pkg/excel2latex)，下载之后双击就安装到excel里面了

![image-20201001163657343](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001163657343.png)

选中你想转化为代码的表格之后，点选`Convert Table to LaTeX`即可秒速转换为代码，在里面有一些配置，我一般设置如下，

![image-20201001163856974](http://wangfohong-image.oss-cn-shenzhen.aliyuncs.com/img/image-20201001163856974.png)

其中`Booktabs package`是制作三线表的选项，一般都使用这个，但是你的边框线要自己画好，使用三线表也需要引用宏包`booktabs`。