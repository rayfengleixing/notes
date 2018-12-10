# [vim中显示windows或者dos的换行符^M](http://blog.chinaunix.net/uid-14214482-id-3220695.html)

linux下，如果需要在vim中查看^M，需要使用如下命令：e ++ff=unix % 。



有时候，我们在 Linux 中打开曾在 Win 中编辑过的文件时，会在行尾看到 ^M 字符。虽然，这并不影响什么，但心里面还是有点不痛快。如果想要删除这些 ^M 字符，可以使用 Vim 来轻松搞定它。

在 Vim 的命令模式中输入 :%s/^M$//g 后，回车即会自动删除该文件中的所有 ^M 字符。

^M 注意要用 Ctrl + V Ctrl + M 来输入。