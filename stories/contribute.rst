.. title: Contribute to SMRT Development
.. slug: contribute
.. date: 2016-10-02 16:03:55 UTC
.. tags:
.. category:
.. link:
.. description:
.. type: text


This is the first page
======================


Please see the Developers Guide (add link)


.. image:: /images/smrtstructure.png
    :height: 300 px
    :align: right

Structure of SMRT
------------------


SMRT is based on object-oriented programming e.g. the snowpack is an object, so is the sensor (radiometer or scatterometer). This makes it easy to interface modules. The image on the right illustrates the structure of SMRT. Users will be interested mainly in the inputs and outputs shown in green and have no need to look at the internal mechanics of the model. Modules of interest to the science developers are shown in yellow. Changing these changes the scientific assumptions used in the model. *Please make changes to these, add new things and feed your work back into SMRT*. Items shown in blue form the backbone of SMRT and do not contribute to the science. SMRT allows flexible inputs so there should never be any need to touch these. Changes to the core modules may break SMRT, so please contact us if you wish to make changes to them.

.. container:: clearer

    .. image :: /images/spacer.png


Make new modules
----------------

Have a play! The easiest way to start is to take an existing file e.g. ``iba.py`` and copy it *in the same folder*. You can then make changes to your new file. As long as the outputs are of the same format and there is no problem with the code (see **Testing** below) then you should be able to use your module with no additional installation steps. For example, to switch from ``IBA`` to ``YOURNEWTHEORY`` electromagnetic module, you can just use the new file name in place of 'iba' e.g.

.. code :: python

    ibamodel = make_model("iba", "dort")
    newmodel = make_model("yournewtheory", "dort")

    # To run the new model on your scatterometer object and your snowpack object
    newmodel.run(yourscatterometer, yoursnowpack)

Documenting your code
---------------------

SMRT uses `Sphinx in-code documentation <http://www.sphinx-doc.org/en/stable/>`_. Provided they are in the correct format, comments will be formatted and included in the documentation. For modules contributed to SMRT, this will be automatic (via a remotely hosted repository and webhooks). To generate the documentation locally on your system, ``pip install Sphinx`` (if it isn't already installed) then:

.. code:: python

    cd smrt/doc
    make fullhtml

You can then see the documentation in the ``smrt/doc/build/html/`` folder. Note that there are currently some issues with the Windows-Ubuntu OS.

Testing
--------

We use the ``nose`` testing framework. Please write tests to check your code performs as you expect it to. Tests for a module are stored in the same folder and given the name ``test_yourmodulename.py``.

.. code:: python

    nosetests

will automatically discover the tests in your file and run them. Running ``nosetests`` in the main smrt folder will run all tests in its subfolders. See `nose <http://nose.readthedocs.io/en/latest/>`_ for more information. It's also worth looking at the `tox package <https://tox.readthedocs.io/en/latest/>`_ for testing on all supported versions of python, and the `tissue package <https://pypi.python.org/pypi/tissue/>`_ for ensuring PEP008 style compliance.


Contributing your modules
--------------------------

Commit changes to your local repository (`a simple guide to git <http://git.huit.harvard.edu/guide/>`_). Once you are satisfied your module behaves as you expect, or if you have improvements to make to existing modules, please `submit a pull request <https://help.github.com/articles/creating-a-pull-request/>`_ to the SMRT repository.


Contributors
-------------

SMRT was originally developed as part of an ESA-funded project. Consortium members for this project are: G. Picard, M. Sandells, H. Löwe, M. Dumont, R. Essery, N. Floury, A. Kontu, J. Lemmetyinen, C. Mätzler, S. Morin and A. Wiesmann

Contributors to the git repository will be posted here in the future!
