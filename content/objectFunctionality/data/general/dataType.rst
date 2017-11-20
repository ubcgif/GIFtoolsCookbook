.. _objectDataType:

.. include:: <isonum.txt>


"Data Type" Data Menu
=====================

.. _objectDataHeaders:

Edit data headers
-----------------

Click on desired data object, the menu with its class name (e.g., **MAGdata** for magnetic data) |rarr| **Edit data headers**

.. figure:: ../../../../images/dataGenEdit.png
    :align: center
    :width: 400


.. _objectDataDeleteDataColumns:

Delete data columns
-------------------

Click on desired data object, the menu with its class name (e.g., **MAGdata** for magnetic data) |rarr| **Delete data column(s)**

.. figure:: ../../../../images/dataGenEdit.png
    :align: center
    :width: 400


**NOTE:** Data columns that are used in the :ref:`i/o Headers <objectSetioHeaders>` will not show up on the list of columns eligible for deletion.


.. _objectDataCreateTopo:

Create topography from data
---------------------------

In rare occasions when topography is not given (or in the event of forward modelling gridded data), the user can create a "draped" topography data object at the data locations by clicking on desired data object, the menu with its class name (e.g., **MAGdata** for magnetic data) |rarr| **Create topo**

.. figure:: ../../../../images/dataGenEdit.png
    :align: center
    :width: 400



.. _objectDataCreateMesh:

Create a 3D mesh from data
--------------------------

To create a 3D (tensor) mesh from a given data set, click on desired data object, the menu with its class name (e.g., **FEMdata** for Frequency-domain EM data) |rarr| **Create mesh**

.. figure:: ../../../../images/dataGenEdit.png
    :align: center
    :width: 400


**NOTE:** For EM data, GIFtools will prompt the use for a background resitivity in order to perform "back-of-the-envelope" calculations for skin depth to determine a suggested core region.
 

.. _objectDataExportData:

Export a data object
--------------------

GIFtools will allow the user to export any data object (in GIF format) at any time. The :ref:`i/o headers <objectSetioHeaders>` will need to be set prior to exportation. 

Select data object then menu with the class of the object (e.g., **TEMdata**) |rarr| **Export for [inv]** where ``inv`` is the name of the inversion style (will be GIF formatted)

Below is an example using MAGdata and exporting for MAG3D:

.. figure:: ../../../../images/dataGenEdit.png
    :align: center
    :width: 400


 







