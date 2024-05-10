.. _objectWeightsObjects:

.. include:: <isonum.txt>

Weights
=======

Here we describe the general functionality for *GIFweight* objects.


.. _objectWeightsObjects_setModel:

Set Model
---------

For a given *GIFweight* object, the user may want to change the cell or face weights. This done through 'Set Model':

**Weighting functions** |rarr| **Set Model** |rarr| **Cell Weighting**

**Weighting functions** |rarr| **Set Model** |rarr| **Face Weighting**

This action will make a copy of the *GIFmodel* or *FACEmodel* selected, place it within the items contained in the *GIFweight* object,
then set the new cell/face weights as a property of the *GIFweight* object. The user must make sure that the *GIFmodel* or *FACEmodel*
is consistent with the mesh size and dimensions associated with the weights object.


.. _objectWeightsObjects_Export:

Export Weights
--------------

This functionality will write out separate files containing the cell and the face weights. This functionality is accessed as follows:

**Weighting functions** |rarr| **Export**

If desired, the user could select any of the models within the *GIFweight* object and export them independently.