安裝說明
============
.. warning:: 
#. 建議安裝 virtualenv-1.9 或更高版本，virtualenv 1.9 以前版本含 pip 都無法通過 SSL 到 PyPI 下載。
#. 當使用 pip 來安裝 virtualenv 時，建議使用 pip 1.3 或更高版本，1.3 以前的版本，無法通過 SSL 到 PyPI 下載。
#. 使用 setuptools 0.9.7 以前版本，請不要使用 easy_install 來安裝 virtualenv，它無法通過 SSL 到 PyPI 下載，可能會因未知原因造成中斷下載。

使用 'pip' 全域安裝 (pip 必須是 1.3 或更高版本)：

::

 $ [sudo] pip install virtualenv
 
  或者取得未發行的 dev 最新的版本：

::

 $ [sudo] pip install https://github.com/pypa/virtualenv/tarball/develop

若要安裝版本 X.X *全域原始碼*︰

::

 $ curl -O https://pypi.python.org/packages/source/v/virtualenv/virtualenv-X.X.tar.gz
 $ tar xvfz virtualenv-X.X.tar.gz
 $ cd virtualenv-X.X
 $ [sudo] python setup.py install

使用*本地原始碼*︰

::

 $ curl -O https://pypi.python.org/packages/source/v/virtualenv/virtualenv-X.X.tar.gz
 $ tar xvfz virtualenv-X.X.tar.gz
 $ cd virtualenv-X.X
 $ python virtualenv.py myVE

.. note::    
    ``virtualenv.py`` 腳本執行時，本地必須有 pip/setuptools/virtualenv 發佈版本，否則無法安裝。 
    
    上述的安裝方法都必須包含完整的 pip 和 setuptools 發佈版本及 ``virtualenv_support`` 目錄才能使用 ``virtualenv.py`` 腳本安裝。


    
    
