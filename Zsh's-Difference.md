# zsh的一些特点

### cd命令

在写代码过程中，会在各个目录之间来回切换，原来用bash时有两点最不爽:

- 对cd命令有TAB补全的功能，但每一级目录都需要按TAB（并且有多个备选项的话需要继续输入才行）还是觉得繁琐，觉得效率不高;
- `pushd/popd/dirs`虽然很有用，但很多时候等你想回到过去的某个目录时，才发现当时忘记`pushd了`

### zsh的改进方法

- 首先，假如`/opt/rubystack-1.9/`下面有`apache2`和`apps`这两个目录，输入`cd /opt/rubystack-1.9/a`然后按TAB的话，首先会补齐为apache2，再按TAB会补齐为apps，不需要象bash下面那样继续输入字母;
- 如果你想进入`/opt/rubystack-1.9/apps/redmine`，那么可以先这样输入 `cd /o/r/a/r` 然后按`TAB`，如果这是唯一匹配，那么zsh会补全为`/opt/rubystack-1.9/apps/redmine，但如果还存在一个/opt/rubystack-1.8/apps/redmine，那zsh就会列出来让你挑选;`
- 如果你现在在`/opt/rubystack-1.9/apps/redmine，`但你想进入`/opt/rubystack-1.8/apps/redmine，可以这样: cd 1.9 1.8 这表示将完整路径上的1.9替换为1.8再使用;`
- 你可以打开`auto_pushd`选项(通过命令`setopt auto_pushd`），这样你通过cd切换目录时，zsh会自动将前一个目录加到栈里，这样你就不会因为忘记pushd而遗憾了;
- bash里面可以`cd -`回到上一个目录（即最后一次调用cd时所在的目录），但zsh里面有`cd -2, cd +3这样的用法，并且在输入cd -之后按TAB能够列出目录名供挑选补全。不过需要注意的是，这里-2并不表示倒数第二次调用cd时的目录，而是倒数第二次通过pushd记录的目录，如 果打开了auto_pushd选项，那么这两个的含义倒是一样的;`
- zsh里面将~这个符号的用法进行了扩展，我们可以用`hash -d www=/var/www/html`定义一个路径别名，然后用`cd ~www`就可以进入到`/var/www/html`了

参考资料: [Refining Linux: ZSH Gem #20: Changing directories the pro's way](http://www.refining-linux.org/archives/55/ZSH-Gem-20-Changing-directories-the-pros-way/)

### a clear history

```
setopt hist_ignore_space
alias cd=" cd"
alias ls=" ls"
```

第一句使得不将以空格开始的命令行记录到历史当中（这在需要在i命令行中明文输入密码时也挺有用，这样不会在历史记录中看到你的密码了）; 
后面两句使得cd/ls这些简单的命令就不记录到历史了，这样用history查看的时候是不是更清晰了？

来自 ： <http://chneukirchen.org/blog/archive/2012/02/10-new-zsh-tricks-you-may-not-know.html>

另一个技巧: 每个目录记录自己的history: <<http://linuxtoy.org/archives/zsh_per_dir_hist.html>>

<http://www.lowlevelmanager.com/2012/05/zsh-history-expansion.html>

### 通配符带子目录

zsh支持更复杂的文件名匹配，不过我大部分我都没去学，只记住了我认为最有用的一个：

```
grep ":project_menu" **/*.erb
```

这个**会搜索所有的子目录，也就避免了用find了（bash下就得借用find了: `find . -name '*.erb | xargs grep ":project_menu"）`

### setopt no_nomatch

这是zsh缺省跟bash不兼容的一个地方。在zsh下，如果你执行`dpkg -l firefox*`，很可能zsh不会列出名字以firefox开头的包，而是告诉你`zsh: no matches found: firefox*`。这是因为zsh缺省情况下始终自己解释这个firefox*，而不会传递给dpkg来解释。

解决这个问题的方法是在~/.zshrc中加入:

```
setopt no_nomatch
```