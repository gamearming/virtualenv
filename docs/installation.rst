Installation
============

.. warning::

   We advise installing virtualenv-1.9 or greater. Prior to version 1.9, the pip included in virtualenv did not download from PyPI over SSL.
   我們建議安裝是 1.9 或更高版本。之前版本 1.9 pip 列入是沒有下載從 PyPI 通過 SSL。

   我們建議安裝是 1.9 或更高版本。在版本 1.9 之前, 列入是 pip 沒有下載從 PyPI 通過 SSL。

   我們建議安裝 virtualenv-1.9 或更高版本。在版本 1.9 之前，virtualenv 中包含的 pip 沒有通過 SSL 從PyPI下載。

   我們建議安裝_virtualenv-1.9 或更高版本。之前版本 1.9，pip 包含在 _virtualenv 中沒有下載從 PyPI 通過 SSL。


.. warning::

    When using pip to install virtualenv, we advise using pip 1.3 or greater.
    Prior to version 1.3, pip did not download from PyPI over SSL.

.. warning::

    We advise against using easy_install to install virtualenv when using
    setuptools < 0.9.7, because easy_install didn't download from PyPI over SSL
    and was broken in some subtle ways.

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
