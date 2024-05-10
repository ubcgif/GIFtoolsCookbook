.. _objectDataManipulationMT:

.. include:: <isonum.txt>

MT Data Manipulation Menu
=========================

.. _objectDataManipulationMT_rotate:

Rotate impedance tensors
^^^^^^^^^^^^^^^^^^^^^^^^

This functionality is used to rotate the impedance tensor in the case that the primary direction (X) does not lie along the Northing. This functionality can be accessed through:

    - **Data manipulation** |rarr| **Calculate** |rarr| **Rotate impedance tensor**

The user will enter the amount of degrees clockwise they would like to rotate the impedance tensor data. For example, let us assume the data are defined such that X is towards the Northwest and Y is towards the Northeast. If we enter a value of **45**, the impedance tensor data will be rotated to UBC-GIF convention (X = Northing and Y = Easting); assume that Z is +ve downward.


.. _objectDataManipulationMT_IMP2APP:

Convert between impedance data and apparent resistivity and phase data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This functionality either:

    - generates apparent resistivity and phase data from impedance data, or
    - generates impedance data from apparent resistivity and phase data

This functionality can be accessed through:

    - **Data manipulation** |rarr| **Create new item** |rarr| **Convert to apparent resistivity and phase data (APPdata)**
    - **Data manipulation** |rarr| **Create new item** |rarr| **Convert to impedance data (IMPdata)**

Some things to note about this functionality:

    - A new data object is created when this functionality is used
    - To compute :math:`\rho_{xy}` and :math:`\phi_{xy}` from Re[ :math:`\! Z_{xy} \!` ] and Im[ :math:`\! Z_{xy} \!` ], you must set the associated data headers. Some goes for the reverse operation.
    - This functionality works regardless of whether data use a time-dependency of :math:`e^{i\omega t}` or :math:`e^{-i\omega t}`.

