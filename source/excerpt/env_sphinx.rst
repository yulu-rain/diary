sphinx文档系统使用
########################

本章主要介绍sphinx文档系统的构建以及reStructuredText 语法
   
安装各类必要工具
********************

#. 安装Git
    下载路径：https://git-scm.com/download/win 

    .. note::

        安装完成后，用Windows Terminal测试 : ``git --version`` （注意： ``是双--线`` ）

#. 安装python
    下载路径：https://www.python.org/downloads/  

    安装完python后需要添加环境变量，如下所示：

    .. figure:: ../images/env_sphinx/env_path.jpg
        :width: 500px
        :align: center

    .. note::

        安装完成后，用Windows Terminal测试 : ``python -V`` 和 ``pip3 --version`` （注意： ``是双--线`` ）

#. 安装sphinx
    ``pip3 install sphinx doc8 sphinx-autobuild``

在本地目录中初始化Sphinx项目
*****************************
    进入对应文件夹目录，同时按住“shift + 右击”，选择“在此处打开命令窗口”，在命令行里输入： ``sphinx-quickstart``

    填写必要的项目信息，初始化成功，其中第一个选项，可以选择yes，使目录保持各自独立，有source和build两个文件夹。

    .. note::

        该步骤是为了生成新的工程，如果有现成工程，此步骤可以省略
    
    获取svn工程: https://192.168.8.109:9001/svn/sphinx-firmware2

工程安装sphinx_rtd_theme主题
******************************
    如果没有安装sphinx_rtd_theme主题，命令行输入: ``pip install sphinx_rtd_theme``

    配置工程的conf.py文件添加： ``html_theme = ‘sphinx_rtd_theme’``

reStructuredText 与 Sphinx
*****************************
    什么是reStructuredText 与 Sphinx？ 

    reStructuredText（RST、ReST或reST）是一种用于文本数据的文件格式，主要用于 Python 编程语言社区的技术文档。它是Python Doc-SIG（Documentation Special Interest Group）的 Docutils 项目的一部分，旨在为 Python 创建一组类似于 Java 的 Javadoc 或 Perl 的 Plain Old Documentation（pod）的工具。Docutils 可以从 Python 程序中提取注释和信息，并将它们格式化为各种形式的程序文档。从这个意义上说，reStructuredText是一种轻量级标记语言，其设计目的是：

    （a）文档处理软件（如Docutils）可以处理它 

    （b）读和写 Python 源代码的程序员很容易读它 

    Sphinx是从reStructuredText文档生成HTML / PDF的工具。

使用VS code编辑文档
**********************
    参考文章：https://www.cnblogs.com/clwydjgs/p/10078065.html

    .. note::

        用vs code打开工程的时候，会提示安装一些插件，统一点击安装即可，在vs code可以直接预览效果 

    .. figure:: ../images/env_sphinx/display.jpg
        :width: 500px
        :align: center

    如果需要预览功能，一定要按照如下步骤：

    .. figure:: ../images/env_sphinx/chajian.jpg
        :width: 500px
        :align: center

    点击后会在工程生成一个 ``.vscode`` 文件夹

    .. figure:: ../images/env_sphinx/chajian1.jpg
        :width: 500px
        :align: center

    预览后会在 ``source`` 目录下生成 ``_build`` 文件夹，该文件夹是临时文件，不要纳入版本管理

    .. figure:: ../images/env_sphinx/chajian2.jpg
        :width: 500px
        :align: center

兼容markdown语法
*******************
    在命令行输入以下命令安装插件：

    ``pip install breathe``

    ``pip install myst_parser``

    相关配置请查看： `markdown插件配置`_ 

    .. note::
        安装完插件想要添加对应的插件，是在对应的工程的conf.py文件里添加

    .. figure:: ../images/env_sphinx/chajian3.jpg
        :width: 500px
        :align: center


doxygen安装与配置
**********************
#. `下载doxygen安装包`_ , 提取码： ``jlmz``
#. 配置环境变量，把doxygen.exe所在路径添加到系统环境变量中

    .. figure:: ../images/env_sphinx/doxygen_env.jpg
        :width: 500px
        :align: center

    配置成功后可以通过 ``set path`` 查看是否设置成功

    .. figure:: ../images/env_sphinx/doxygen_env1.jpg
        :width: 500px
        :align: center

#. 用 ``doxygen config.doxyfile.in`` 命令生成相关文件，默认输出到 ``source\doxygen_out`` ，如果没有config.doxyfile.in文件，则要用 ``doxygen -g config.doxyfile.in`` 命令生成默认配置文件 ``config.doxyfile.in``

#. 添加输入文件路径
    .. figure:: ../images/env_sphinx/doxygen_env2.jpg
        :width: 500px
        :align: center

#. doxygen生成注释相关格式请参考 ``c_template.c`` 、 ``c_template.h`` 文件，请点击下载： `c_template模板`_

reStructuredText语法
************************

#. 注释代码

    ``.. + 空格``

#. 创建目录树
    代码：

    .. figure:: ../images/env_sphinx/toctree_code.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/toctree_effect.png
        :width: 500px
        :align: center

#. 创建全局跳转

    .. code-block::

        :ref:`advanced_train`
        advanced_train为某个文件的标签，其格式为.. _advanced_train:

    点击跳转处：

    .. figure:: ../images/env_sphinx/goble_jump.png
            :width: 500px
            :align: center

    跳转处（也就是说该tag在哪里就会跳到对应的地方）:

    .. figure:: ../images/env_sphinx/goble_jump1.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/goble_jump2.png
        :width: 500px
        :align: center

#. 创建全局跳转

    .. code-block::

        - 硬件及硬件工具准备_
  
        硬件及硬件工具准备
        *************

    效果：

        .. figure:: ../images/env_sphinx/tmp_jump.png
            :width: 500px
            :align: center

#. 创建超链接

    .. code-block::

        - 通过  `超链接`_  创建超链接文字，如：
     
        所有的杰理开源项目均维护在 `Github仓库`_ 和 `Gitee仓库`_

        - 关联超链接，注意..后面有空格，如：

        .. _`Github仓库`: https://github.com/Jieli-Tech

    效果：

    .. figure:: ../images/env_sphinx/link.png
            :width: 500px
            :align: center

#. 创建表格

    代码：

    .. figure:: ../images/env_sphinx/table.png
            :width: 500px
            :align: center

    效果：

    .. figure:: ../images/env_sphinx/table1.png
            :width: 500px
            :align: center

    代码：

    .. figure:: ../images/env_sphinx/table2.png
            :width: 500px
            :align: center

    效果：

    .. figure:: ../images/env_sphinx/table3.png
            :width: 500px
            :align: center

#. 插入图片

    .. figure:: ../images/env_sphinx/pic.png
        :width: 500px
        :align: center

#. 文字面前显示.
    ``需要加.文字前加-``

#. 添加note

    .. figure:: ../images/env_sphinx/note.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/note1.png
        :width: 500px
        :align: center

#. 添加caution

    .. figure:: ../images/env_sphinx/caution.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/caution1.png
        :width: 500px
        :align: center

#. 添加important

    .. figure:: ../images/env_sphinx/important.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/important1.png
        :width: 500px
        :align: center

#. 添加序号

    .. figure:: ../images/env_sphinx/num.png
        :width: 500px
        :align: center

    效果:

    .. figure:: ../images/env_sphinx/num1.png
        :width: 500px
        :align: center

#. 代码格式输出

    .. figure:: ../images/env_sphinx/code.png
        :width: 500px
        :align: center

    效果:

    .. figure:: ../images/env_sphinx/code1.png
        :width: 500px
        :align: center


#. 标题

    一级标题：

    .. figure:: ../images/env_sphinx/title.png
        :width: 500px
        :align: center

    二级标题：

    .. figure:: ../images/env_sphinx/title1.png
        :width: 500px
        :align: center

    三级标题：

    .. figure:: ../images/env_sphinx/title2.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/title3.png
        :width: 500px
        :align: center


#. 红色字体显示

    .. figure:: ../images/env_sphinx/redtxt.png
        :width: 500px
        :align: center

    效果：

    .. figure:: ../images/env_sphinx/redtxt1.png
        :width: 500px
        :align: center

.. _`markdown插件配置`: https://www.sphinx-doc.org/en/master/usage/markdown.html
.. _`下载doxygen安装包`: https://pan.baidu.com/share/init?surl=VBIX4Bgk5Ulq6c1dl5-ymg
.. _`c_template模板`: https://wws.lanzoui.com/iZXqRrya27a
