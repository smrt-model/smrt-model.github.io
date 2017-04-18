.. title: Getting started with SMRT
.. slug: getstarted
.. date: 2016-10-02 16:03:55 UTC
.. tags:
.. category:
.. link:
.. description:
.. type: text
.. pretty_url: False


This is the first page
======================


Run some tests
--------------

A great way to check SMRT is working ok is to run the automated tests. If the *nose* package is not in your system you will need to

.. code:: python

    pip install nose

Make sure you are in the smrt directory, then type

.. code:: python

    nosetests

Hopefully this will tell you that it is all **OK**! If SMRT is not working as expected, please let us know on the Help page.


A simple example
----------------

This simple script sets up a simple, one-layer snowpack with exponential microstructure. The Improved Born Approximation (iba) and Discrete Ordinates Radiative Transfer model (DORT) are used to simulate the AMSR-E 37V channel:

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

The result should be ``267.73`` K. To adapt this to multiple layers, extend the size of the snowpack parameter arrays (e.g. below should give a brightness temperature of ``228.45`` K if used in place of the snowpack above)

.. code:: python

    thickness = [1, 99]
    corr_length = [5e-5, 3e-4]
    temperature = [270, 260]
    density = [320, 350]


.. note::

    * Layer numbers are from the top to the bottom i.e. first in the array is the top.
    * SI units are always used: metres, Kelvin, kilograms, Hertz.
    * Different parameters are needed for each microstructure model. See documentation for details

Tutorials
-----------

There are many ways in which to use SMRT. A great place to start is with the `tutorials <https://esaproject.smrt-model.science/shownotebooks/browse/smrtnotebooks/tutorial>`_



