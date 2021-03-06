Virtualenv
==========
 `網上論壇`_ | `相關問題`_ | `Github`_ | `PyPI`_ | User IRC: #pypa | Dev IRC: #pypa-dev

介紹
------------
``virtualenv`` 可讓一台機器建立多個虛擬獨立的 `Python`_ 環境，而互不影響。

在虛擬獨立環境中 `Python`_ 是私有副本，獨立安裝自已的 packages，不會影響到系統共用的 `Python`_。

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

.. Warning::

   `Python`_ 2.6.8/2.7.3/3.1.5/3.2.3 的修正版本中，有個會發生 "import random" 失敗，而無法匯人任何副本名稱
   "cannot import name urandom" 的錯誤。

   如果您的 ``virtualenv`` 及 `Python`_ 2.6/2.7/3.1/3.2 早期版本是建立在 Unix 主機，在升級 `Python`_ 時將會發生上
   述錯誤，那是因為 ``virtualenv`` 使用的是系統 `Python`_ 的標準庫，而導致二者版本衝突。

   您可以移除 ``$ENV/bin/Python`` 再將 ``virtualenv`` 放到升級後 `Python`_ 的相同目錄。

其他文件和連結
-----------------------------

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
以下產品也可以建立多個虛擬獨立的 `Python`_ 環境︰

* ``workingenv`` 是這個程式庫的前身。主要是使用 `Python`_ 解譯器，必須設定 $PYTHON_PATH 環境變數來啟動，當執行不在環境變數的 `Python`_ 腳本，
  例如: globally 安裝的 ``hg`` 或 ``bzr``，會導致問題且與 `Setuptools`_ 衝突很多。（不建議再使用）

* `virtual-python`_ 也是這個程式庫的前身。
  使用符號連結，因此無法在 Windows 上工作，也在 entire 標準程式庫和全區的 'site_packages' 符號連結，因此看不到 'site_packages' 新增的內容。

  該腳本僅將標準程式庫的小部分符號連結到環境中，Windows 等只需複製這些文件即可。此外它會建立一個空或新的 ``site-packages``，
  並將全區 ``site-packages`` 新增到路徑中，以便更新追蹤。該腳本會自動安裝 `Setuptools`_ 避免了網路下載。

* `zc.buildout`_ 不會以相同的樣式建立獨立的 `Python`_ 環境，而是通過設定檔聲明，指定套裝軟體的腳本來實現類似的結果。

  作為一個聲明系統，重複和管理更容易，但更難的是測試。

  ``zc.buildout`` 包括安裝非 `Python`_ 系統 （例如: 資料庫伺服器或 Apache） 的功能 。

我強烈建議一定要使用以上工具之一來開發或部署應用程式。

.. _Python:                https://www.python.org/
.. _相關問題:              https://github.com/pypa/virtualenv/issues
.. _Github:                https://github.com/pypa/virtualenv
.. _virtualenv 命令:       https://github.com/thisismedium/virtualenv-commands
.. _IPython:               https://doughellmann.com/blog/2008/02/01/ipython-and-virtualenv/
.. _部落格文章:            https://doughellmann.com/blog/2008/05/01/virtualenvwrapper/
.. _PyPI:                  https://pypi.python.org/pypi/virtualenv/
.. _Pew:                   https://pypi.python.org/pypi/pew/
.. _VirtualenvWrapper:     https://pypi.python.org/pypi/virtualenvwrapper/
.. _setuptools:            https://pypi.python.org/pypi/setuptools
.. _網上論壇:              http://groups.google.com/group/python-virtualenv
.. _mod_wsgi:              http://code.google.com/p/modwsgi/wiki/VirtualEnvironments
.. _virtualenv 公告:       http://blog.ianbicking.org/2007/10/10/workingenv-is-dead-long-live-virtualenv/
.. _Pylons:                http://wiki.pylonshq.com/display/pylonscookbook/Using+a+Virtualenv+Sandbox
.. _Showmedo 教學影片:     http://showmedo.com/videos/video?name=2910000&fromSeriesID=291
.. _zc.buildout:           http://pypi.python.org/pypi/zc.buildout
.. _Ian Bicking's:         http://pyvideo.org/video/568/reverse-engineering-ian-bicking--39-s-brain--insi
.. _virtual-python:        http://peak.telecommunity.com/DevCenter/EasyInstall#creating-a-virtual-python
