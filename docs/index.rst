Virtualenv
==========

`網上論壇 <http://groups.google.com/group/python-virtualenv>`_ |
`相關問題 <https://github.com/pypa/virtualenv/issues>`_ |
`Github <https://github.com/pypa/virtualenv>`_ |
`PyPI <https://pypi.python.org/pypi/virtualenv/>`_ |
User IRC: #pypa
Dev IRC: #pypa-dev

介紹
------------
``virtualenv`` 可讓一台機器建立多個虛擬獨立的 Python 環境，而互不影響，

在虛擬獨立環境中 Python 是私有副本，獨立安裝自已的 packages，不會影響到系統共用的 Python。

可以有效的解決：

#. 沒有管理員權限下安裝新套件。
#. 不同應用程式可以使用不同的套件版本。
#. 套件升級不影響其他應用程式。

.. comment: split here

.. toctree::
   :maxdepth: 2

   installation
   userguide
   reference
   development
   changes

.. Warning:: \

   Python 2.6.8/2.7.3/3.1.5/3.2.3 的修正版本中，有個會發生 "import random" 失敗，而無法匯人任何副本名稱 
   "cannot import name urandom" 的錯誤。
   如果您的 ``virtualenv`` 及 Python 2.6/2.7/3.1/3.2 早期版本是建立在 Unix 主機，在升級 Python 時將會發生上 
   述錯誤，那是因為 ``virtualenv`` 使用的是系統 Python 的標準庫，而導致二者版本衝突。
   您可以移除 ``$ENV/bin/python`` 再將 ``virtualenv`` 放到升級後 Python 的相同目錄。


其他文件和連結
-----------------------------
.. _virtualenv 公告:       http://blog.ianbicking.org/2007/10/10/workingenv-is-dead-long-live-virtualenv/
.. _virtualenv 命令:       https://github.com/thisismedium/virtualenv-commands
.. _VirtualenvWrapper:     https://pypi.python.org/pypi/virtualenvwrapper/
.. _Pylons:                http://wiki.pylonshq.com/display/pylonscookbook/Using+a+Virtualenv+Sandbox
.. _Showmedo 教學影片:     http://showmedo.com/videos/video?name=2910000&fromSeriesID=291
.. _IPython:               https://doughellmann.com/blog/2008/02/01/ipython-and-virtualenv/
.. _部落格文章:            https://doughellmann.com/blog/2008/05/01/virtualenvwrapper/
.. _Pew:                   https://pypi.python.org/pypi/pew/
.. _mod_wsgi:              http://code.google.com/p/modwsgi/wiki/VirtualEnvironments
.. _Ian Bicking's:         http://pyvideo.org/video/568/reverse-engineering-ian-bicking--39-s-brain--insi

* `virtualenv 公告`_
* James Gardner 在 `Pylons`_ 寫了一篇如何使用 virtualenv 的教學文章。
* Chris Perkins 錄製一段如何使用 virtualenv 的 `Showmedo 教學影片`_。
* Doug Hellmann 的 virtualenvwrapper 封裝的腳本，可讓您的工作流程與使用 virtualenvs 更加輕鬆。
  他還在 `部落格文章`_ 發表一篇嘗試使用 `IPython`_ 來執行 virtualenv 的範例。
* `Pew`_ 是另一個 virtualenv 的封裝，使用不同的啟動技術。
* virtualenv 如何使用 `mod_wsgi`_。 
* 關於 virtualenv 更多工作流程相關工具的 `virtualenv 命令`_。
* PyCon 2011 年在美國的談話：逆向工程 `Ian Bicking's`_ 的大腦：內部 pip 和 virtualenv。在談話結束之後，
  在看完 pip 和 virtualenv 的談話及如何實現他們的做法，可能有助於您在修正錯誤及解決問題的啟發。

 相關產品的比較與選擇
------------------------------------

以下產品也可以建立多個虛擬獨立的 Python 環境︰

* ``workingenv`` (which I do not suggest you use anymore) is the
  predecessor to this library. It used the main Python interpreter,
  but relied on setting ``$PYTHONPATH`` to activate the environment.
  This causes problems when running Python scripts that aren't part of
  the environment (e.g., a globally installed ``hg`` or ``bzr``). It
  also conflicted a lot with Setuptools.

* `virtual-python
  <http://peak.telecommunity.com/DevCenter/EasyInstall#creating-a-virtual-python>`_
  is also a predecessor to this library. It uses only symlinks, so it
  couldn't work on Windows. It also symlinks over the *entire*
  standard library and global ``site-packages``. As a result, it
  won't see new additions to the global ``site-packages``.

  This script only symlinks a small portion of the standard library
  into the environment, and so on Windows it is feasible to simply
  copy these files over. Also, it creates a new/empty
  ``site-packages`` and also adds the global ``site-packages`` to the
  path, so updates are tracked separately. This script also installs
  Setuptools automatically, saving a step and avoiding the need for
  network access.

* `zc.buildout <http://pypi.python.org/pypi/zc.buildout>`_ doesn't
  create an isolated Python environment in the same style, but
  achieves similar results through a declarative config file that sets
  up scripts with very particular packages. As a declarative system,
  it is somewhat easier to repeat and manage, but more difficult to
  experiment with. ``zc.buildout`` includes the ability to setup
  non-Python systems (e.g., a database server or an Apache instance).

I *strongly* recommend anyone doing application development or
deployment use one of these tools.
