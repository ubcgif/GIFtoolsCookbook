.. _comprehensive_workflow_mt_ztem_4:


ZTEM Data Preparation and Uncertainties
=======================================

A standard approach for assigning uncertainties and preparing ZTEM data was covered in the Dufferin Lake ZTEM comprehensive workflow and we will use the same approach here. We strongly urge the reader to be familiar with this material before continuing. For reference, visit:

    - :ref:`Assigning uncertainties to ZTEM data <comprehensive_workflow_ztem_3>`

    - :ref:`Preparing ZTEM data <comprehensive_workflow_ztem_4>`


Uncertainties
-------------

Whereas the maximum amplitude of the in-phase data was roughly 0.5 for all frequencies, the maximum amplitude of the quadrature data was closer to 0.25; the amplitude of the maximum anomaly decreased somewhat at the highest frequencies.
For simplicity, we chose to add uncertainties of 0.025 to all in-phase data and uncertainties of 0.0125 to all quadrature data.
This was roughly 5 % the maximum anomaly amplitude for most components and frequencies; for the 720 Hz data it's more like 8 %. Despite being a quick way to assign uncertainties, we may end up over-fitting certain frequencies and/or components at the expense of others. To apply uncertainties:

    - Use the :ref:`GUI for applying frequency-dependent uncertainties <objectAssignUncertGUI>`.


.. _comprehensive_workflow_mt_ztem_4_preparation:

Data Preparation
----------------

Down-Sampling
^^^^^^^^^^^^^

ZTEM data at 720 Hz is frequently poor quality and is not used in the inversion. In our case, the 720 Hz data appears to be good quality and will be inverted.

The flight-line separation for the tutorial dataset is 200 m, indicating we may want to down-sample such that the minimum data separation is roughly 200 m.
However, we chose to down-sample the data such that the minimum data spacing was 400 m. This was done to invert the data on a coarser mesh, allowing the inversion to be run on a single 64 GB node. For this step:

    - :ref:`Down-sample based on distance<objectDataDownsample>`

which created the data object *ztem_data_ds400m*.


Setting the Base Station
^^^^^^^^^^^^^^^^^^^^^^^^

The horizontal magnetic fields are general measured at a base station. In GIFtools, we must define the base station location.
For the tutorial data, the base station is located at Easting = 545905 m, Northing = 3623156 m and elevation = 1063 m in UTM zone 12.
To carry out this step:

    - :ref:`Set/reset base station<objectDataTypeZTEM_basestn>` to the downsampled data.


Setting ZTEM Data Type
^^^^^^^^^^^^^^^^^^^^^^

We need to specify if the horizontal fields are measured at a base station or using sensors attached to the aircraft. This is done with the following functionality:

    - :ref:`Set ZTEM data type<objectDataTypeZTEM_datatype>` to the downsampled data.


Defining Receivers
^^^^^^^^^^^^^^^^^^

Presently, E3DMT v2 is considered the superior code for inverting natural-source EM data. To use this code, we must define the receivers:

    - :ref:`Set/reset receivers from data locations<objectDataTypeZTEM_snid>`

**Our approach:**

According to the contractor, *Hx* and *Hy* were measured at a base station. The receivers at the base station were square and had a side length of 3.04 m. *Hz* was measured with a circular loop with a diameter of 7.4 m. Thus we used the following parameters to fill in the fields:

    - **Hx, Hy receiver width: 3.04**
    - **Hx, Hy number of segments: 4**
    - **Hz receiver width: 7.4**
    - **Hz number of segments: 8**
    - **Orientation from Nothing (deg): 0** (since all rotations to UBC-GIF were done already)

.. note:: If any of the loops are square, choose the number of segments to be 4. GIFtools will define the loop as a square with side length equal to the value specified.
