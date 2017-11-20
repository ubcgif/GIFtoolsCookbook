.. _objectMagDataManipulation:

.. include:: <isonum.txt>

Data Manipulation for Magnetic Data
===================================

.. _objectEditFieldParam:

Edit inducing magnetic field parameters
---------------------------------------

The inducing field (inclination, declination, and field strength) is vital to properly creating a sensitivity matrix in inversion and forward modelling. This is only performed on a magnetic data object (MAGdata).

Select the object and the menu **Data manipulation** |rarr| **Edit field params**

.. figure:: ../../../../images/uncert.png
    :align: center
    :width: 400


 
.. _objectRemoveIGRF:

Remove the IGRF from magnetic data
----------------------------------

To remove the IGRF value from a magnetic data set, the i/o header for the data must be set. Click on the data item of interest and use the menu:

**Data manipulation** |rarr| **Calculate** |rarr| **Subtract IGRF value**

.. figure:: ../../../../images/dataCalculate.png
    :align: center
    :width: 400

**NOTE 1:** A separate way of removing the IGRF would be through the :ref:`Constant calculator <objectConstantCalculator>`. 




