搭建vim环境
########################

本章主要介绍如何搭建属于自己的vim，以及vim使用命令，vim的命令使用不区分系统。
   
.. caution::  
    vim源码可以从云服务器上下载，也可以从github上下载，云服务器上的不保证最新，github上的工程会保持更新

- windos系统上搭建vim_
- linux系统上搭建vim_
- vim模式_
- vim常用命令_
- vim一些不常用命令行命令_
- map使用方法_
- vim自定义快捷方式_

.. _windows_vim_use:

windos系统上搭建vim
**************************

#. 获取vim源码
    github项目，保持更新 `github获取地址`_ 
    
    另外提供通过云服务器方式获取，但是不保持更新，需要请点击: `下载wondows系统vim`_，密码:``jlmz``

#. 获取到源码后解压到D盘根目录

    .. important:: 
        安装路径不能有空格或者是中文，不然在使用cscope的时候会有问题，我默认装在D盘根目录

#. 借助 `RightMenuMgr`_ 生成右击打开vim快捷方式

    .. figure:: ../images/env_vim/RightMenuMgr.png
        :width: 500px
        :align: center

#. 添加vim环境变量

    .. figure:: ../images/env_vim/vim环境变量.jpg
        :width: 500px
        :align: center

.. _linux_vim_use:

linux系统上搭建vim
**************************

vim安装
==================

#. 拷贝/230common/minzong/vim到home目录下，并改名成 ``.vim``

#. 拷贝/230common/minzong/vimrc到home目录下，并改名成 ``.vimrc``

vim模式
============

#. Normal Mode
    也就是最一般的普通模式，默认进入vim之后，处于这种模式。
#. Visual Mode
    一般译作可视模式，在这种模式下选定一些字符、行、多列。在普通模式下，可以按v进入。
#. Insert Mode
    插入模式，其实就是指处在编辑输入的状态。普通模式下，可以按i进入。
#. Select Mode
    选择模式。用鼠标拖选区域的时候，就进入了选择模式。和可视模式不同的是，在这个模式下，选择完了高亮区域后，敲任何按键就直接输入并替换选择的文本了。和windows下的编辑器选定编辑的效果一致。普通模式下，可以按gh进入。
#. Command-Line/Ex Mode
    命令行模式和Ex模式。两者略有不同，普通模式下按冒号(:)进入Command-Line模式，可以输入各种命令，使用vim的各种强大功能。普通模式下按Q进入Ex模式，其实就是多行的Command-Line模式。

vim常用命令
===================

    .. figure:: ../images/env_vim/vim命令1.jpg
        :width: 500px
        :align: center

    .. figure:: ../images/env_vim/vim命令2.jpg
        :width: 500px
        :align: center

vim一些不常用命令行命令
============================

    .. code-block::

        :set nonu                 #不显示行号
        :ccl                      #关闭quickfix窗口
        :%s/目标/替换为/g          #当前文件不询问直接替换
        :%s/目标/替换为/gc         #当前文件询问替换
        :%s/\<目标\>/替换为/gc     #当前文件询问并整词匹配替换
        :bdelete x                #关闭x号buffer
        :ls                       #显示当前buffers
        :set paste                #进入全格式粘贴模式，shift+insert全格式粘贴
        :set nopaste              #取消全格式粘贴模式
        常规模式下 gd 可以跳转到局部变量定义处

        :g/str1/s//str2/g         #底行模式字符串替换

        hlsearch操作:
            :set hlsearch  高亮所有匹配的字符串
            :nohlsearch 临时关闭
            :set nohlsearch 彻底关闭，只有重新:set hlsearch才可以高亮搜索
            
        vimgrep操作
            " vimgrep /匹配模式/[g][j] 要搜索的文件/范围
            " g: 表示是否把每一行的多个匹配结果都加入
            " j: 表示是否搜索完后定位到第一个匹配的位置
            " vimgrep /pattern/%  在当前打开文件中查找
            " vimgrep /pattern/ *   在当前目录下查找所有
            " vimgrep /pattern/ **   在当前目录及其子目录下查找所有
            " vimgrep /pattern/ *.c  查找当前目录下所有的.c文件
            " vimgrep /pattern/ **/*  只查找子目录

map使用方法
=================
参考博文: `【Vim】使用map自定义快捷键`_


vim自定义快捷方式
====================

.. code-block::

    F9：常规模式下 quickfix 跳转快捷键，上一个要寻找的目标
    F10：常规模式下 quickfix 跳转快捷键，下一个要寻找的目标
    \ev：查看vimrc文件
    \es：查看sync文件
    {  ：{}/()括号匹配
    *  ：高亮光标所在关键字
    ;// ：tComment 插件注释重映射
    F4：打开/关闭paste功能
    F1：打开/关闭quickfix窗口
    F3：跳转到报错代码处
    xtime：插入模式下 输入当前系统时间
    

.. _`RightMenuMgr`: https://wws.lanzoui.com/iluuDrr6sve
.. _`下载wondows系统vim`: https://wws.lanzoui.com/iSpBYroz99e
.. _`【Vim】使用map自定义快捷键`: https://www.jianshu.com/p/8ae25a680ed7
.. _`github获取地址`: https://github.com/zhangminzong-jieli/Vim_8_1.git