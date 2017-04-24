.. title: SMRT: Snow Microwave Radiative Transfer model
.. slug: index
.. date: 2016-10-02 16:03:55 UTC
.. tags:
.. category:
.. link:
.. description:
.. type: text


This is the first page
======================

hello!!!SMRT is an active / passive microwave radiative transfer model for multilayer snow. It was developed with `European Space Agency <http://www.esa.int/>`_ support in order to investigate the representation of the snow microstructure, as this was shown to be the main difference between scattering coefficient models by `Löwe and Picard (2015) <http://www.the-cryosphere.net/9/2101/2015/>`_. Other factors, such as the radiative transfer solver, are also important `(Pan et al., 2016) <http://ieeexplore.ieee.org/abstract/document/7323820/>`_. At present, five different analytical microstructure models are available within SMRT. In the future it should be possible to use the correlation function determined from micro-CT samples. There are three electromagnetic models, and one (multi-angular) radiative transfer solver. Whilst there is plenty to get started with, there are more theoretical advances that can be made. SMRT is intended to be a community model - all are welcome to use it, and to contribute to its development! 


Modules
--------

SMRT is modular, so allows easy intercomparisons between different modelling approaches in a plug-and-play way e.g. use the same microstructure model but different electromagnetic models or to use a multi-flux vs a 6-flux radiative transfer scheme. There are three main steps to set up SMRT: 1) construct a snowpack (either from field data or snowpack model), 2) configure an active or passive sensor and 3) select the model assumptions. The model is then run on the snowpack, for the given sensor characteristics.

.. image:: /images/SMRT.png
    :height: 500 px
    :alt: modular illustration of the SMRT model. Snow microstructure is in the centre, and SMRT modules placed around the edge.
    :align: right
..    :scale: 30
..     :height: 100
..    :width: 200

Module categories available for use in SMRT are:

    * Microstructure model
    * Electromagnetic model
    * Radiative transfer solver
    * Substrate (optional)
    * Atmosphere (optional)
    * Interlayer reflectivity (optional)
    * Permittivity (optional)

These have structured inputs and outputs, so it is easy to add modules, but also have flexibility to incorporate any specific module-dependent parameters. SMRT has autoimport of the modules - as long as new modules are placed in the correct folders, they are available for immediate use. At present the electromagnetic modules included are suitable for 10-40GHz microwave frequencies, but the model framework allows this to be extended. See the model documentation for more details on SMRT development.


Other features
--------------
SMRT is written in python (2.7, 3.4, 3.5), and `hosted on github <https://github.com/smrt-model/smrt>`_ under git version control. There is a *nose* testing framework to ensure continuity and consistency between platforms and as development progresses. Wrappers are included for MEMLS and HUT models for comparisons of SMRT with these historically important models e.g. see this notebook about `memls_legacy <memls_legacy>`_.


