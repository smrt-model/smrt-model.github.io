.. title: Download SMRT
.. slug: download
.. date: 2016-10-02 16:03:55 UTC
.. tags:
.. category:
.. link:
.. description:
.. type: text


This is the first page
======================



Set your system up
-------------------

If you have already downloaded or cloned SMRT on to your system, tutorials to help you run SMRT are available on the :doc:`Getting Started <getstarted>` pages. 

If you have python 2.7, 3.4 or 3.5 installed on your system, skip ahead to **How to get SMRT onto your system**.

Otherwise, you will need to install python on your computer. `Anaconda <https://www.continuum.io/downloads>`_ is recommended to install most of the packages you will need or are likely to find useful. This is an open source distribution for all platforms, free, and community supported. Otherwise, it can be downloaded from `python.org <https://www.python.org/downloads/.>`_ or there are other methods (apt-get, wget, homebrew, macports). Anaconda has built in virtual environments, which can be very useful for installing particular versions of packages (and avoid some problems), but if installed by other methods then it's well worth looking into `virtualenv <http://python-guide-pt-br.readthedocs.io/en/latest/dev/virtualenvs/>`_ or `venv <https://docs.python.org/3/library/venv.html>`_.


Pip
----

SMRT uses a number of packages that are easily available e.g. numpy, scipy to do the hard maths grind behind the scenes. A list of these packages is provided with SMRT in a *requirements.txt* file to ensure that they are available for import on your system. To install them locally you will need the *pip* installer. This is likely to be included with python 2.7+, but **should be updated** (or obtained) e.g. by `these instructions <https://packaging.python.org/installing/>`_. Instructions for using the requirements.txt file are given in **How to get SMRT onto your system** below.


Git
----

SMRT version control is managed with git. Although you can download SMRT, it is far better to clone it so you can easily stay up-to-date with changes, as well as contribute them. `Here are some instructions for installing git <https://www.atlassian.com/git/tutorials/install-git>`_. This `simple guide to using git <http://rogerdudler.github.io/git-guide/>`_ may also be helpful.


How to get SMRT onto your system
--------------------------------

`SMRT is here on github <https://github.com/smrt-model/smrt>`_. You can see the files and download/clone SMRT with the large green button. Alternatively, use a terminal on your computer to navigate to your desired folder, then type:

.. code:: python

    git clone https://github.com/smrt-model/smrt.git

**Please read the Licence (LGPL) and disclaimer** as this governs what you are allowed to do with SMRT! To get ready for using SMRT, you must install the required external packages. To do this you can use the *requirements.txt* file
by typing:

.. code:: python

    pip install -r requirements.txt

It will list the versions of the packages that are being installed to your system. Hopefully this will show no errors, but if you do encounter a problem please visit the Help pages. SMRT should now be ready to use!


Staying up to date
-------------------

If you have cloned SMRT, you can always get the latest version with:

.. code:: python

    git pull
