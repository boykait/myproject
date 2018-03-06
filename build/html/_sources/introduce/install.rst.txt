begining
=======================================

打造基于RTD+Sphinx+GitHub的个人博客空间
---------------------------------------

:时间: 2018年01月7日

.. note::

	目的，之前国内的CSDN博客网站上写过一些篇不痛不痒的技术文章，后来没了兴致，主要是觉得该网站内容太多显得太繁杂且充斥着各种广告，想找一个比较简洁的地方记录点东西，经过一番度娘，找到了这个比较好的方案，记录一下，大家有需要也可以做参考。

前提条件
--------

 - git基本操作
 - ``reStructuredText`` 语法
 - 最重要的是要有一台电脑(一般配置即可)
 
步骤简介
--------

 - 申请RTD和GitHub账号
 - 下载并安装Python3+(推荐用3.5或3.6吧，自带pip安装数据源)

安装python和Sphinx
------------------

- python软件比较好安装，除了要将其add to classpath外，其他一路默认即可，安装好后，使用cmd下执行python命令查看安装结果：

::

	C:\Users\Administrator>python
	Python 3.5.3 (v3.5.3:1880cb95a742, Jan 16 2017, 16:02:32) [MSC v.1900 64 bit (AM
	D64)] on win32
	Type "help", "copyright", "credits" or "license" for more information.

- 安装好python后，进行Sphinx的安装，过程也很简单，执行命令“easy_install -U Sphinx”，一般不出意外，十分钟左右安装成功。

::

	==========================================================================
	WARNING: The C extension could not be compiled, speedups are not enabled.
	Failure information, if any, is above.
	Retrying the build without the C extension now.

	==========================================================================
	WARNING: The C extension could not be compiled, speedups are not enabled.
	Plain-Python installation succeeded.
	==========================================================================
	creating d:\program files\python\python35\lib\site-packages\markupsafe-1.0-py3.5
	.egg
	Extracting markupsafe-1.0-py3.5.egg to d:\program files\python\python35\lib\site
	-packages
	Adding markupsafe 1.0 to easy-install.pth file

	Installed d:\program files\python\python35\lib\site-packages\markupsafe-1.0-py3.
	5.egg
	Finished processing dependencies for Sphinx

建立Sphinx工程
--------------

- 使用sphinx自带的配置工具sphinx-quickstart，我提前创建的目录 D:\mygithub\blog,具体详细配置大家随意，满足自己需求即可:

::

	D:\mygithub>
	D:\mygithub>sphinx-quickstart
	Welcome to the Sphinx 1.6.5 quickstart utility.

	Please enter values for the following settings (just press Enter to
	accept a default value, if one is given in brackets).

	Enter the root path for documentation.
	> Root path for the documentation [.]:

	You have two options for placing the build directory for Sphinx output.
	Either, you use a directory "_build" within the root path, or you separate
	"source" and "build" directories within the root path.
	> Separate source and build directories (y/n) [n]: y

	Inside the root directory, two more directories will be created; "_templates"
	for custom HTML templates and "_static" for custom stylesheets and other static
	files. You can enter another prefix (such as ".") to replace the underscore.
	> Name prefix for templates and static dir [_]:

	The project name will occur in several places in the built documentation.
	> Project name: blog
	> Author name(s): boyka

	Sphinx has the notion of a "version" and a "release" for the
	software. Each version can have multiple releases. For example, for
	Python the version is something like 2.5 or 3.0, while the release is
	something like 2.5.1 or 3.0a1.  If you don't need this dual structure,
	just set both to the same value.
	> Project version []: 1.0.1
	> Project release [1.0.1]:

	If the documents are to be written in a language other than English,
	you can select a language here by its language code. Sphinx will then
	translate text that it generates into that language.

	For a list of supported codes, see
	http://sphinx-doc.org/config.html#confval-language.
	> Project language [en]:

	The file name suffix for source files. Commonly, this is either ".txt"
	or ".rst".  Only files with this suffix are considered documents.
	> Source file suffix [.rst]:

	One document is special in that it is considered the top node of the
	"contents tree", that is, it is the root of the hierarchical structure
	of the documents. Normally, this is "index", but if your "index"
	document is a custom template, you can also set this to another filename.
	> Name of your master document (without suffix) [index]:

	Sphinx can also add configuration for epub output:
	> Do you want to use the epub builder (y/n) [n]: y

	Please indicate if you want to use one of the following Sphinx extensions:
	> autodoc: automatically insert docstrings from modules (y/n) [n]: y
	> doctest: automatically test code snippets in doctest blocks (y/n) [n]:
	> intersphinx: link between Sphinx documentation of different projects (y/n) [n]
	:
	> todo: write "todo" entries that can be shown or hidden on build (y/n) [n]:
	> coverage: checks for documentation coverage (y/n) [n]:
	> imgmath: include math, rendered as PNG or SVG images (y/n) [n]: y
	> mathjax: include math, rendered in the browser by MathJax (y/n) [n]: y
	Note: imgmath and mathjax cannot be enabled at the same time.
	imgmath has been deselected.
	> ifconfig: conditional inclusion of content based on config values (y/n) [n]:
	> viewcode: include links to the source code of documented Python objects (y/n)
	[n]: y
	> githubpages: create .nojekyll file to publish the document on GitHub pages (y/
	n) [n]: y

	A Makefile and a Windows command file can be generated for you so that you
	only have to run e.g. `make html' instead of invoking sphinx-build
	directly.
	> Create Makefile? (y/n) [y]: y
	> Create Windows command file? (y/n) [y]: y

	Creating file .\source\conf.py.
	Creating file .\source\index.rst.
	Creating file .\Makefile.
	Creating file .\make.bat.

	Finished: An initial directory structure has been created.

	You should now populate your master file .\source\index.rst and create other doc
	umentation
	source files. Use the Makefile to build the docs, like so:
	   make builder
	where "builder" is one of the supported builders, e.g. html, latex or linkcheck.


- 执行完毕后，会得到如下的几个文件：

::

	build      运行make命令后，生成的文件都在这个目录里面
	source     放置文档的源文件
	make.bat   批处理命令
	makefile


- 执行一把 make html，生成静态站点项目,可以通过浏览器(用chrome或Firefox,开发人员必备)瞅瞅，是有点不太入眼，后期再更改它的风格：

::

	D:\mygithub\blog>make html
	Running Sphinx v1.6.5
	making output directory...
	loading pickled environment... not yet created
	building [mo]: targets for 0 po files that are out of date
	building [html]: targets for 1 source files that are out of date
	updating environment: 1 added, 0 changed, 0 removed
	reading sources... [100%] index
	looking for now-outdated files... none found
	pickling environment... done
	checking consistency... done
	preparing documents... done
	writing output... [100%] index
	generating indices... genindex
	writing additional pages... search
	copying static files... done
	copying extra files... done
	dumping search index in English (code: en) ... done
	dumping object inventory... done
	build succeeded.

	Build finished. The HTML pages are in build\html.


创建项目推送到GitHub远端master分支
----------------------------------

- 关于GitHub和ReadTheDocs的注册不用多说吧，就和注册淘宝账号一样简单。
- 建一个GitHub库: https://github.com/gxw255613/myproject.git
- 下载 `git工具 <https://git-scm.com/download/win>`_ 并安装。
- 打开blog项目目录第一层路径，空白处右键鼠标>git bush here,开始执行一系类git操作(ps: 我也终于有了至高无上的master权限了,happy ^^)。

::

 - $ git init
 - $ git add .
 - $ git commit -m 'blog start'
 - $ git remote add origin https://github.com/gxw255613/myproject.git
 - $ git push origin master


导入到 ReadtheDocs
------------------

- 启用GitHub的代码更新通知服务，选择对应的仓库，然后依次点击 Setting => Integrations & Service => Add service => ReadTheDocs
- 到 ReadtheDocs import 这个仓库，导入成功后，点击阅读文档，便可看到 Web 效果了

- 如果在更新主题的时候遇到这个问题,就按照提示执行"ip install sphinx\_rtd\_theme"吧：

::

	D:\mygithub\blog>make html
	Running Sphinx v1.6.5
	loading pickled environment... done

	Theme error:
	sphinx_rtd_theme is no longer a hard dependency since version 1.4.0. Please inst
	all it manually.(pip install sphinx_rtd_theme)

	D:\mygithub\blog>pip install sphinx_rtd_theme


- 以后写点东西的步骤应该变成了::

	- 写reStructuredText语法的文章
	- copy文档到本地blog>source对应的目录下
	- 更新index.rst
	- 执行make html
	- 执行git add\commit\push\(merge)操作
  
- 好像有点复杂，管它呢，后期到时候看能不能再搞一个自动化的东西来一键执行。


资源附录
--------

- `sphinx中文介绍 <http://zh-sphinx-doc.readthedocs.io/en/latest/tutorial.html#id3>`_ 

.. warning::

    试一试吧，超级好使，轻松写美文
