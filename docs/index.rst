Virtualenv
==========

`Mailing list <http://groups.google.com/group/python-virtualenv>`_ |
`Issues <https://github.com/pypa/virtualenv/issues>`_ |
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

.. warning::

Python 2.6.8/2.7.3/3.1.5/3.2.3 修正版本中，有個會發生 "import random" 失敗，而無法匯人任何副本名稱 "cannot import name urandom" 
如果您的 virtualenv 是建立在 Unix 主機的 Python 2.6/2.7/3.1/3.2 早期版本，在升級 Python 時將會發生上述錯誤。
那是因為 virtualenv 使用的是系統 Python 的標準庫，而導致二者版本衝突。
您可以移除 ``$ENV/bin/python`` 再將 virtualenv 放到升級後 Python 的相同目錄。

Other Documentation and Links
-----------------------------

* `Blog announcement of virtualenv`__.

  .. __: http://blog.ianbicking.org/2007/10/10/workingenv-is-dead-long-live-virtualenv/

* James Gardner has written a tutorial on using `virtualenv with
  Pylons
  <http://wiki.pylonshq.com/display/pylonscookbook/Using+a+Virtualenv+Sandbox>`_.

* Chris Perkins created a `showmedo video including virtualenv
  <http://showmedo.com/videos/video?name=2910000&fromSeriesID=291>`_.

* Doug Hellmann's `virtualenvwrapper`_ is a useful set of scripts to make
  your workflow with many virtualenvs even easier. `His initial blog post on it`__.
  He also wrote `an example of using virtualenv to try IPython`__.

  .. _virtualenvwrapper: https://pypi.python.org/pypi/virtualenvwrapper/
  .. __: https://doughellmann.com/blog/2008/05/01/virtualenvwrapper/
  .. __: https://doughellmann.com/blog/2008/02/01/ipython-and-virtualenv/

* `Pew`_ is another wrapper for virtualenv that makes use of a different
  activation technique.

  .. _Pew: https://pypi.python.org/pypi/pew/

* `Using virtualenv with mod_wsgi
  <http://code.google.com/p/modwsgi/wiki/VirtualEnvironments>`_.

* `virtualenv commands
  <https://github.com/thisismedium/virtualenv-commands>`_ for some more
  workflow-related tools around virtualenv.

* PyCon US 2011 talk: `Reverse-engineering Ian Bicking's brain: inside pip and virtualenv
  <http://pyvideo.org/video/568/reverse-engineering-ian-bicking--39-s-brain--insi>`_.
  By the end of the talk, you'll have a good idea exactly how pip
  and virtualenv do their magic, and where to go looking in the source
  for particular behaviors or bug fixes.

Compare & Contrast with Alternatives
------------------------------------

There are several alternatives that create isolated environments:

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
