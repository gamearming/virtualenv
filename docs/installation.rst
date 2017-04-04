安裝說明
============

.. warning:: 
  我們建議安裝 virtualenv-1.9 或更高版本，virtualenv 1.9 以前版本含 pip 都無法通過 SSL 到 PyPI 下載。

.. warning::    
  當使用 pip 來安裝 virtualenv 時，建議使用 pip 1.3 或更高版本，pip 1.3 以前版本，無法通過 SSL 到 PyPI 下載。

.. warning::
   使用 setuptools 0.9.7 以前版本，建議不要使用 easy_install 來安裝 virtualenv，它無法通過 SSL 到 PyPI 下載，可能會因未知原因造成中斷下載。

To install globally with `pip` (if you have pip 1.3 or greater installed globally):

::

 $ [sudo] pip install virtualenv

Or to get the latest unreleased dev version:

::

 $ [sudo] pip install https://github.com/pypa/virtualenv/tarball/develop


To install version X.X globally from source:

::

 $ curl -O https://pypi.python.org/packages/source/v/virtualenv/virtualenv-X.X.tar.gz
 $ tar xvfz virtualenv-X.X.tar.gz
 $ cd virtualenv-X.X
 $ [sudo] python setup.py install


To *use* locally from source:

::

 $ curl -O https://pypi.python.org/packages/source/v/virtualenv/virtualenv-X.X.tar.gz
 $ tar xvfz virtualenv-X.X.tar.gz
 $ cd virtualenv-X.X
 $ python virtualenv.py myVE

.. note::

    The ``virtualenv.py`` script is *not* supported if run without the
    necessary pip/setuptools/virtualenv distributions available locally. All
    of the installation methods above include a ``virtualenv_support``
    directory alongside ``virtualenv.py`` which contains a complete set of
    pip and setuptools distributions, and so are fully supported.
