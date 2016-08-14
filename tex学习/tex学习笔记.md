### 空白距离
- latex将空格和制表符视为相同的空白距离，多个连续的空白字符视为一个空白字符
- 每行开始的空格将被忽略，而单一的回车被视为一个空格
- 使用空行来结束段落，两行文本中的空行标志上一段的结束和下一段的开始

### 特殊字符
> # $ % ^ & _ { } ~ \
> \\是一个断行的命令

### latex命令
- latex命令是大小写敏感的
	- 以反斜杠 \ 开始，加上只包含字母字符组成，命令后的空格符，数字或其他非字母字符标志该命令的结束。
	- 由反斜杠 \ 和一特殊字符组成
- latex命令将忽略后面的空格，如果希望得到会面的一个空格，可以在命令后面加上{}和一个空格
- 许多命令需要一个参数，其使用一对大括号{}括起来，放在命令的后面。
- 也有一些命令支持方括号的可选参数

### 注释
- 遇到 % 时，将忽略其后的该行文本，分行符以及下一行开始的空白符
- % 也可以用来分割不允许有空格或分行的较长输入文本
- 如果需要较长的注释，可以使用verbatim宏集所提供的comment环境。
	> \usepackage{verbatim}
	> \begin{comment}
	> ........
	> \end{comment}

### 源文件结构
- 每个latex文档必须以如下命令开始，这个命令指定了所写文档的类别
	> \documentclass{...}
- 接下来可以使用
	> \usepackage{...}
	> \usepackage{...}
	> ...........
	> \begin{document}

- \documentclass 和 \begin{document}之间的区域称作导言区
- 使用 \end{document}来结束文档

### 文档类
- article：科技期刊，短报告，程序文档，邀请涵
- report：多章节的长报告，短篇的书籍，博士论文
- book：书籍
- slides：排版幻灯片

### 宏包
- 使用宏包增强基本的latex的功能

### 页面式样
- latex支持三种预定的页眉，页脚格式，称为页面式样。

### 大型文档
- 当处理大型文档时，可以将源文件分成几个部分，latex有两条命令来处理
	> 在文档的正文中使用 \include{filename}
	> 在文档的导言区，使用 \includeonly{filename1,filename2....}

### 特殊字符和符号
- 引号：用两个单引号
- 省略号：\ldots
- 支持使用国际语言
	> 使用宏包babel完成
	> \usepackage[language]{babel}

### 标题，章和节
- 对于article风格的文档，有下列命令
	> \section{...}
	> \subsection{...}
	> \subsubsection{...}
	> \paragraph{...}
	> \subparagraph{...}
- 对于report和book风格的文档，还有如下两个命令
	> \part{...}
	> \chapter{...}
- 命令 \tableofcontents提取节的标题和页码
- 整篇文档的标题由命令 \maketitle 产生
	> 标题的内容必须在调用 \maketitle 之前，由\title{...},\author{...}和可选的\date{...}定义

### 脚注
- 利用 \footnote{footnote text}
- 脚注命令总是置于其指向的单词或句子的后面

### 强调
- \underline{text} 下划线
- \emph{text} 斜体

### 环境
> \begin{environment} text \end{environment}
- itemize环境用于简单的列表
- enumerate环境用于带序号的列表
- description环境用于带描述的列表
- flushleft和flushright环境分别产生靠左排序和靠右排序的段落，center环境产生居中的文本
- quote环境用于引用
- 位于 \begin{verbatim} 和 \end{verbatim}之间的文本将直接打印，包括所有的断行和空白，不执行任何latex命令

### 表格
- tabular环境用来排印表格
	> \begin{tabular} {table spec}
	> {table spec} 定义了表格的样式，用l产生左对齐的列，r产生右对齐的列，c产生中间对齐的列，p{width}产生相应的宽度，| 产生铅直表线
	> 用 & 跳入下一列，用 \\ 开始新的一行，用 \hline 插入水平表线
	> 用 \cline{j-i}可添加部分表线，其中j和i分别表示表线的起始列和终止列的序号

### 浮动体
- 对于在当前排不下的任何一个图片或表格，其解决办法是把他们浮动到下一页面，于此同时当前页面用正文文本填充。
- latex提供了两个浮动体环境，一个用于图片，一个用于表格
- 包围于环境figure或环境table中的任何材料都被视为浮动内容

### 保护脆弱命令
- \protect 命令保护紧跟其右侧的命令，连它的参量也 不惠及，过多的\protect 并不碍事


## 数学公式

### 基本知识
- 段落中的数学表达式应该置于 \( 和\),或者 $ 和 $,或者 \begin{math} 和 \end{math}之间
- 对于较大的公式，可以放在 \begin{displaymath} 和 \end{displaymath}之间
- 对于需要编号的公式，使用equation环境来达到目的，其中 \label 和 \ref 对公式加以引用
- 数学模式下：
	> 空格和分行都将被忽略
	> 不允许有空行，每个公式只能有一个段落
	> 每个字符都将被看着是一个变量名并以此来排版，可以使用命令 \textrm{...}来输入文本

### 数学模式中的分组
- 命令只对其后的第一个字符其作用，如果对多个字符起作用，需要使用{}括起来

### 建立数学公式模块
- 小写希腊字符，可以使用 \alpha,\beta,大写的可以使用 \Gamma,\Delta
- 指数和下标可以使用 ^ 和 _ 来实现


## 特殊功能

### 包含EPS图形

### 参考文献

### 索引

### 定制页眉和页脚

### 下载并安装latex宏包
