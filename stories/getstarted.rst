.. title: Getting started with SMRT
.. slug: getstarted
.. date: 2018-01-09
.. tags:
.. category:
.. link:
.. description:
.. type: text
.. pretty_url: False



The following procedure explains how to get SMRT running on your personal computer.


Step 1. Install Python and dependencies
-----------------------------------------

SMRT is developed with the highest stable version of Python but also work with python 2.7 series and 3.4 or higher. `Anaconda <https://www.anaconda.com/distribution/>`_ is the recommended distribution to get Python as it contains numerous packages needed for scientific computations and analysis. This is an open source distribution available for Linux, Windows and MacOS. Alternatively, you can install Python with the main package manager of your system (e.g. apt-get on Debian/Ubuntu, rpm on Fedora, homebrew on MacOS, ...) or visit `<https://wwww.python.org/>`_ for more information.

To keep your system clean we recommend to create a virtual environment for the following installation either via `conda create <https://conda.io/docs/user-guide/tasks/manage-environments.html>`_ or `virtualenv <https://virtualenv.pypa.io/en/stable/>`_.

The main python packages to install are: `numpy <http://www.numpy.org/>`_, `scipy <https://www.scipy.org>`_, `pandas <https://pandas.pydata.org/>`_, `xarray <http://xarray.pydata.org/en/stable/>`_ and `six <https://pypi.python.org/pypi/six>`_. With the Anaconda distribution, use the Anaconda navigator or the conda command:

.. code:: bash

    conda install numpy scipy xarray pandas six

Using pip, it is similar:

.. code:: bash

    pip install numpy scipy xarray pandas six


In addition, it is likely you will want to plot graph with for instance `matplotlib <https://matplotlib.org/>`_, `bokeh <https://bokeh.pydata.org/>`_ or `plot.ly <https://plot.ly/python/>`_.

To download and keep up-to-date SMRT, it is recommended to use the version control software `Git <https://git-scm.com/>`_ that can be installed using the package manager of your system. `Here are some instructions for installing git <https://www.atlassian.com/git/tutorials/install-git>`_. This `simple guide to using git <http://rogerdudler.github.io/git-guide/>`_ may also be helpful but the two needed commands are given below.


Step 2. Get SMRT code
----------------------

SMRT code is hosted on `github <https://github.com/smrt-model/smrt>`_. To get the code clone the repository with:

.. code:: bash

    git clone https://github.com/smrt-model/smrt.git

Alternatively, download directly the code with the large green button on `github <https://github.com/smrt-model/smrt>`_.

**Please note the Licence (LGPL) and disclaimer** as this governs what you are allowed to do with SMRT! To get ready for using SMRT, you must install the required external packages.

Because SMRT is not formally installed in your system, it is necessary to inform Python where the code is. Under Linux, this is done by using the following command (in every terminal or better to put in ~/.bashrc file)

.. code:: bash

    export PYTHONPATH=$PYTHONPATH:/the/full/path/to/smrt

where /the/full/path/to/smrt is the SMRT top directory, i.e. the directory that contains README.md, requirements.txt, etc.


Step 3. A first example
-------------------------

This simple script sets up a simple, one-layer snowpack with exponential microstructure. The Improved Born Approximation (IBA) and Discrete Ordinates Radiative Transfer model (DORT) are used to simulate the AMSR-E 37V channel:

.. code:: python

    from smrt import make_snowpack, make_model, sensor_list

    # prepare inputs
    thickness = [100]
    corr_length = [5e-5]
    temperature = [270]
    density = [320]

    # create the snowpack
    snowpack = make_snowpack(thickness=thickness,
                             microstructure_model="exponential",
                             density=density,
                             temperature=temperature,
                             corr_length=corr_length)

    # create the sensor
    radiometer = sensor_list.amsre('37V')

    # create the model
    m = make_model("iba", "dort")

    # run the model
    result = m.run(radiometer, snowpack)

    # outputs
    print(result.TbV())

Copy this code into a new file called "first-smrt.py" somewhere on your filesystem (generally **NOT** in the smrt directory) and execute the code with the python command or by clicking on the file depending on your system:

.. code:: bash

    python first-smrt.py

If you get an ImportError, it is likely that python does not find the smrt directory. Check that $PYTHONPATH is properly set.

The result of this computation should be ``268.04`` K. To adapt this to multiple layers, extend the size of the snowpack parameter arrays (e.g. below should give a brightness temperature of ``228.45`` K if used in place of the snowpack above)

.. code:: python

    thickness = [1, 99]
    corr_length = [5e-5, 3e-4]
    temperature = [270, 260]
    density = [320, 350]


.. note::

    * Layer numbers are from the top to the bottom i.e. first in the list is the top.
    * SI units are always used: metres, Kelvin, kilograms, Hertz.
    * Different parameters are needed for each microstructure model. See documentation for details

Last Recommendations: Staying up to date
-------------------------------------------

If you have cloned SMRT with git, you don't need to use clone again to get the last version, just move to the smrt directory and execute:

.. code:: bash

    git pull

We recommend to always get the latest version as we constantly correct bugs and improve the code. See git documentation how to revert to a past version.

Going further with the tutorials
-----------------------------------

There are many ways in which to use SMRT. Here's a list of examples:

#. `Sensitivity study with a list of snowpacks <../sensitivity_study/index.html>`_
#. `Use wrapper to call MEMLS <../memls_legacy/index.html>`_
#. `Figure in the GMD paper <https://github.com/smrt-model/smrt1paper>`_



