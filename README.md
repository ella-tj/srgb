## 搭建KMS服务器激活Windows
```
安装 vlmscd
docker pull mikolatero/vlmcsd
docker run -d -p 1688:1688 --restart=always --name="vlmcsd" mikolatero/vlmcsd

前一个是主机端口，后一个是容器端口

配置 GVLK

没有输入过其它的 key 的跳过这一步. 替换对应系统版本的 key

slmgr /ipk GVLK

配置 KMS 服务器
slmgr /skms ip:port

slmgr /skms jp.262235.xyz:1688

激活
slmgr /ato

# 用kms命令激活office2010

# 管理员CMD进入ospp.vbs所在目录
cd "C:\Program Files (x86)\Microsoft Office\Office14"

# 设置office2010专业增强版激活密钥；
cscript ospp.vbs /inpkey:VYBBJ-TRJPB-QFQRF-QFT4D-H3GVB

# 3个命令分别是设置kms服务器，激活office产品，查看office激活状态；
cscript ospp.vbs /sethst:jp.262235.xyz
cscript ospp.vbs /act
cscript ospp.vbs /dstatus

```
##  CorelDraw不能另存与导出的解决方法
```
CorelDraw不能另存与导出的解决方法

把这个目录删除  C:\Users\vip\AppData\Roaming\Corel\CorelDRAW Graphics Suite X4

CorelDraw有时会出现不能另存与导出的情况，重装CorelDraw也不能解决问题，只有重装系统，再重装CorelDraw才行。

实际上这个问题是由于CorelDraw的工作配置文件出错造成的，删除CorelDraw的配置文件夹，再重新启动一下CorelDraw就行了。

Windows 7 删除这个文件夹：C:\用户\当前用户(如Administrator)\AppData\Roaming\Corel

Windows XP 删除这个文件夹：C:\Documents and Settings\All Users\Application Data\Corel
```

## 解决GitHud上传/下载文件速度慢的问题
```
改hosts

140.82.114.3 github.com
199.232.69.194 github.global.ssl.fastly.net
140.82.114.10 codeload.github.com
199.232.68.133 raw.githubusercontent.com

或

代理
export ALL_PROXY=socks5://127.0.0.1:7070

☞全局代理

# socks5协议，1080端口修改成自己的本地代理端口
git config --global http.proxy socks5://127.0.0.1:1080
git config --global https.proxy socks5://127.0.0.1:1080

# http协议，1081端口修改成自己的本地代理端口
git config --global http.proxy http://127.0.0.1:1081
git config --global https.proxy https://127.0.0.1:1081

☞仅github走本地代理，其他的保持不变

# socks5协议，1080端口修改成自己的本地代理端口
git config --global http.https://github.com.proxy socks5://127.0.0.1:1080
git config --global https.https://github.com.proxy socks5://127.0.0.1:1080

# http协议，1081端口修改成自己的本地代理端口
git config --global http.https://github.com.proxy https://127.0.0.1:1081
git config --global https.https://github.com.proxy https://127.0.0.1:1081

# 查看所有配置
git config -l
# reset 代理设置
git config --global --unset http.proxy
git config --global --unset https.proxy

或导入gitee

```

### Chrome 浏览器离线安装包
https://www.google.cn/chrome/?standalone=1&platform=win64

### 天地图-浙江
http://www.zjditu.cn/map

### 巨硬地图 - Google 卫星地图无偏移版
https://www.juying.co/

### 初窥Scrapy
https://scrapy-chs.readthedocs.io/zh_CN/0.24/intro/overview.html
- Scrapy是一个为了爬取网站数据，提取结构性数据而编写的应用框架。 可以应用在包括数据挖掘，信息处理或存储历史数据等一系列的程序中。

### scrapy学习
https://www.jianshu.com/p/7dee0837b3d2

### Python 3.8.0 中文文档 镜像
- http://srgb.vicp.net/python-zh-cn/

## 清华大学开源软件镜像站  pypi 镜像使用帮助
https://mirrors.tuna.tsinghua.edu.cn/help/pypi/

- 临时使用
	pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package

- 设为默认

```
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 如果您到 pip 默认源的网络连接较差，临时使用本镜像站来升级 pip：

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
```


### 如何在不破坏apt的情况下更新Python 3的替代方案？

- sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7 3

```
update-alternatives: using /usr/bin/python3.7 to provide /usr/bin/python (python) in auto mode

root@orangepizero /u/bin# python -V

Python 3.7.3
```

### linux  chown 改变文件属
- chown -R username:user_group folder

### 改变 WEB文件夹属性为 www-data
- chown -R www-data:www-data  /var/www

### linux笔记(全中文笔记，真是爱学习的好学生)
https://github.com/hongwenjun/linux

### linux  vim bash 脚本学习笔记
https://git.io/vps.us

### Debian 轻量级服务设置脚本 (学习脚本挺好)
https://github.com/Xeoncross/lowendscript

### openwrt-luci-kcp-udp 软件包
https://git.io/openwrt

### Windows udp2raw+kcptun 加速tcp流量 简易工具
https://git.io/winkcp

### 浙江A级景区名单
https://github.com/hongwenjun/zjajq

# git_bash 环境下几个配置文件

# .gitconfig
```
[user]
	email = vip18@gmail.com
	name = vip1

[https]
    proxy = http://127.0.0.1:1080


[alias]
    dog = log --all --decorate --oneline --graph

[gui]
    encoding = utf-8

```

#  .bashrc
```bash
# MINGW64(git_bash) 解决 ping 和 ipconfig 乱码
alias ping='_win_ping() { winpty ping $@ ; }; _win_ping'
alias tcping='_win_tcping() { winpty tcping $@ ; }; _win_tcping'
alias ipconfig='_win_ipconfig() { winpty ipconfig $@ ; }; _win_ipconfig'

alias gcc='_win_gcc() { winpty gcc $@ ; }; _win_gcc'
alias g++='_win_g++() { winpty g++ $@ ; }; _win_g++'
alias cl='_win_cl() { winpty cl $@ ; }; _win_cl'

alias youtube-dl='youtube-dl --proxy 127.0.0.1:1080 '

alias cls='clear'
alias hg="history | sed 's/^[ ]*[0-9]\+[ ]*//' | sort | uniq |grep --color=auto"
alias ssr="http_proxy=http://127.0.0.1:1080 https_proxy=http://127.0.0.1:1080"
alias grep='grep --color=auto'

# 添加 youtube-dl 和 ffmpeg 可执行文件的路径，用 ：分割
PATH=$PATH:/e/mp4:/c/soft/ffmpeg/bin:/c/CodeBlocks/MinGW64/bin:/c/soft/GifCam:/c/Ramdisk:/c/soft/iperf-3.1.3-win64:
```
# .minttyrc
```
BoldAsFont=no
Font=Fixedsys
FontHeight=9
CursorColour=0,255,64
CursorType=block
ThemeFile=windows10
Language=zh_CN
Columns=100
Rows=30
```

# .tmux.conf
```
# https://www.youtube.com/watch?v=xTplsyQaGFs

# tmux 启用鼠标操作
# setw -g mouse
set-option -g history-limit 20000
set-option -g mouse on
bind -n WheelUpPane select-pane -t= \; copy-mode -e \; send-keys -M
bind -n WheelDownPane select-pane -t= \; send-keys -M

```

#  .vimrc
```
" .vimrc   请把本文件 _vimrc 改成 .vimrc 放到 ~目录
" 参见: http://vimdoc.sourceforge.net/htmldoc/options.html 获取更多信息
" 国内 http://blog.csdn.net/luckytanggu/article/details/52045357


set nocompatible  "非兼容模式，使用vim高级特性
" 对于多字节字符支持 (如 CJK 支持):
set fileencodings=ucs-bom,utf-8,cp936,big5,euc-jp,euc-kr,gb18030,latin1
       
set tabstop=4       " 文件中一个 <Tab> 占据的空格数。
 
set shiftwidth=4    " 每一级自动缩进的空格数。
 
set expandtab       " 使用合适数目的空格插入 <Tab>.
                    " 当 '自动缩进' 打开时使用 '>' 和 '<' 命令来用空格缩进
                    " 当 'expandtab' 打开时使用 CTRL-V <Tab> 来插入tab.
 
set smarttab        " 当打开时，行首的 <Tab> 会按照 'shiftwidth' 插入空白
                    " 在其他地方使用 'tabstop'
                    " 一个 <退格> 会删除行首的一个 'shiftwidth' 大小的空格
 
set showcmd         " 在状态栏中显示(部分)命令。

set number          " 显示行号。

set showmatch       " When a bracket is inserted, briefly jump to the matching
                    " one. The jump is only done if the match can be seen on the
                    " screen. The time to show the match can be set with
                    " 'matchtime'.
 
set hlsearch        " 当有一个符合之前搜索的值时，高亮所有匹配
 
set incsearch       " 当输入搜索命令时，离开显示符合与目前输入的模式匹配的内容
 
set ignorecase      " 在搜索中忽略大小写
 
set smartcase       " 如果搜索中有大写字符，忽略 'ignorecase' 选项
 
set backspace=2     " Influences the working of <BS>, <Del>, CTRL-W
                    " and CTRL-U in Insert mode. This is a list of items,
                    " separated by commas. Each item allows a way to backspace
                    " over something.
 
set autoindent      " 当开始新行时复制当前行的缩进
                    " (typing <CR> in Insert mode or when using the "o" or "O"
                    " command).
 
set textwidth=79    " Maximum width of text that is being inserted. A longer
                    " line will be broken after white space to get this width.
 
set formatoptions=c,q,r,t " This is a sequence of letters which describes how
                    " automatic formatting is to be done.
                    "
                    " letter    meaning when present in 'formatoptions'
                    " ------    ---------------------------------------
                    " c         Auto-wrap comments using textwidth, inserting
                    "           the current comment leader automatically.
                    " q         Allow formatting of comments with "gq".
                    " r         Automatically insert the current comment leader
                    "           after hitting <Enter> in Insert mode. 
                    " t         Auto-wrap text using textwidth (does not apply
                    "           to comments)
 
set ruler           " 显示当前光标位置的行号和列号，用逗号分割
 
set background=dark " 当设置为 "dark" 时，Vim 会尝试使用在暗色背景中合适的颜色。
                    " 当设置为 "light" 时，Vim 会尝试使用在亮色背景中合适的颜色。
                    " 其他值是非法的
 
set mouse=a         " 启用鼠标的使用

set paste
set pastetoggle=<F11>  " 快捷键来激活/取消 paste模式  
                       " 使用vim寄存器 "+p  粘贴不用考虑是否自动缩进，是否paste模式，直接原文传递



syntax on
filetype plugin on
au BufRead,BufNewFile *.txt setlocal ft=txt



" C++ 按F5编译运行
map <F5> :call CompileRunGcc()<CR>
func! CompileRunGcc()
    exec "w"
    if &filetype == 'c'
        exec "!g++ % -o %<"
        exec "!time ./%<"
    elseif &filetype == 'cpp'
        exec "!g++ % -o %<"
        exec "!time ./%<"
    elseif &filetype == 'java'
        exec "!javac %"
        exec "!time java %<"
    elseif &filetype == 'sh'
        :!time bash %
    elseif &filetype == 'python'
        exec "!time python %"
    elseif &filetype == 'html'
        exec "!firefox % &"
    elseif &filetype == 'go'
    "        exec "!go build %<"
        exec "!time go run %"
    elseif &filetype == 'mkd'
        exec "!~/.vim/markdown.pl % > %.html &"
        exec "!firefox %.html &"
    endif
endfunc

" C,C++的调试
map <F8> :call Rungdb()<CR>
func! Rungdb()
    exec "w"
    exec "!g++ % -g -o %<"
    exec "!gdb ./%<"
endfunc

" !bash 调用bash
map <F12> :call Runbash()<CR>
func! Runbash()
    exec "!bash"
endfunc

```
