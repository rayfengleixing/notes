# ubuntu vim使用solarized主题教程

```vim
...   .vimrc
plug 'altercation/vim-colors-solarized'

syntax enable
let g:solarized_termcolors=256
colorscheme solarized

if has("gui_running)
	set background=light
else
	set background=dark
endif

... vim
:PluginInstall
```

