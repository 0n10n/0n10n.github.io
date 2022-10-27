# Linux环境初装的一些基本设置

### VIM
```bash
$ mkdir -p ~/.vim/autoload ~/.vim/plugged ~/.vim/backup ~/.vim/colors 

$ git clone --depth 1 git@github.com:/sheerun/vim-polyglot ~/.vim/pack/plugins/start/vim-polyglot
$ wget https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim -O ~/.vim/autoload/plug.vim
$ wget https://raw.githubusercontent.com/Erichain/vim-monokai-pro/master/colors/monokai_pro.vim -O ~/.vim/colors/monokai_pro.vim 
```

```
#~/.vimrc的内容
set nocompatible
filetype on
filetype plugin on
filetype indent on
set number
set cursorline
set cursorcolumn
call plug#begin()
Plug 'sheerun/vim-polyglot'
call plug#end()
colorscheme monokai_pro
```

### bash color
```bash
#在/etc/bashrc里加入：

alias vi=vim

export LS_COLORS="di=1;36;100:fi=0;37:ln=35;47:so=32;40:pi=33;40:ex=33;40:bd=34;46:cd=34;43:su=0;41:*.tar.gz=95:"
```