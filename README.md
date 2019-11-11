# golang_workspace
Golang vim IDE for guyu


# install golang
```
brew install go
```

# install Vundle
```
git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
https://github.com/VundleVim/Vundle.vim
```

# edit ~/.vimrc
```
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
```

# 配置语法高亮，在vimrc里面加
```
syntax on
```

# 添加插件，在vimrc的vundle#begin 和 vundle#end中间添加
```
Plugin 'fatih/vim-go'
	
Plugin 'Valloric/YouCompleteMe'
```
# YCM需要编译
```
brew install cmake
cd ~/.vim/bundle/YouCompleteMe
git submodule update --init --recursive
./install.py --clang-completer
!!!报错
    Run Build Command(s):/usr/bin/make cmTC_d3aa3/fast && xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
    
xcode-select --install

CMake Error: The source directory "/Users/rongdongsheng/.vim/bundle/YouCompleteMe/third_party/ycmd/third_party/cregex" does not appear to contain CMakeLists.txt.
rm -rf YouCompleteMe/third_party/ycmd/third_party/cregex 
cd YouCompleteMe/third_party/ycmd/third_party
git submodule update --init --recursive
```

# 补全插件
```
Plugin 'SirVer/ultisnips'
```


# 解决YCM与UltiSnips的快捷键冲突，在vimrc中添加
```
" YCM settings
let g:ycm_key_list_select_completion = ['', '']
let g:ycm_key_list_previous_completion = ['']
let g:ycm_key_invoke_completion = ''
" UltiSnips setting
let g:UltiSnipsExpandTrigger="<Tab>"
let g:UltiSnipsJumpForwardTrigger="<c-j>"
let g:UltiSnipsJumpBackwardTrigger="<c-k>"
```


# 自动格式化，vimrc
```
let g:go_fmt_command = "goimports"
```

# 安装tagbar
```
go get -u github.com/jstemmer/gotags
brew install ctags
```
vimrc添加：
```
Plugin 'Tagbar'
" 设置tagbar的窗口宽度
let g:tagbar_width=30
" 映射Tagbar的快捷键,按F3自动打开
map <F3> :TagbarToggle<CR>
```

let g:go_bin_path = "/usr/local/opt/go@1.13/bin/"



Sorry for flush your configuration...
