
* SublimeREPL，REPL就是read-evaluation-print-loop，解释型语言编译运行的过程）。装了SublimeREPL插件后也支持了编辑器上直接的编译运行和交互，但还是有一些不满的地方。
SublimeREPL提供的功能当中有两个我比较常用的是运行python交互环境和直接运行当前文件，而python自带的IDLE跟人性化的做法是把这两者结合起来，所以我想实现的是对当前的文件运行python的交互环境。

* SublimeREPL 允许你在编辑界面直接运行 Python 解释器。我倾向于在单独的终端窗口用 bpython 来运行，但有时 SublimeREPL 是很有帮助的。 


* Pylinter 这个插件提供了目前我所见到的最好的 pylint 编辑器整合。它自动检查 .py 文件，无论其何时被保存，并且会直接在编辑界面显示 pylint 违规。它还有一个快捷方式来禁用局部的 pylint 检查，通过插入一个 #pylint: 禁用注释。这个插件对于我确实非常有用。 


Anaconda绝对是换到Sublime Text 3后最令我兴奋的插件，没有之一。在Sublime Text 2的时代，为配置一个好用的python开发环境， 我们需要分别安装All Autocomplete,SublimeREPL,Pylinter和PEP8等诸多插件。 Geek就是让一切变得更简单，该插件作者就为了简便，把这些功能集中起来了。 Anaconda把PyFlakes, pep8 和 McCabe以插件的方式集成起来。安装Anaconda后，通过配置即可完成一个良好的Python开发环境。