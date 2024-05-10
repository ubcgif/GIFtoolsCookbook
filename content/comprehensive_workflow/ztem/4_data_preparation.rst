.. _comprehensive_workflow_ztem_4:


Data Preparation
================

Before creating a survey-dependent mesh, writing UBC-GIF formatted data files or inverting, certain steps must be completed. These include:

	- Down-sampling the data to a manageable number of data points
	- Setting the base station (unless Hx and Hy are measured at the same location as Hz)
	- Setting the data type (base station or no base station)
	- Defining the Hx, Hy and Hz receiver loops (only needed for E3DMT v2)

These steps are covered here.

Down-Sampling
^^^^^^^^^^^^^

The sampling rate in the along-line direction is generally much higher than is needed to characterize ZTEM anomalies. Furthermore, 3D EM inversions are generally unable to recover geologically plausible models when the data spacing is less than 2-3 horizontal cell widths; implying you may consider some aspects of mesh design during this step.  The desired station spacing is generally determined by the flight-line separation.  Here, we down-sample the data based on a desired minimum separation.

**Our Approach:**

The flight-line separation for the tutorial dataset is 200 m, indicating we may want to down-sample such that the minimum data separation is 150-200 m. We chose to down-sample the data such that the minimum data spacing was 400 m. This was done so we invert the data on a coarser mesh. If downsampling to a spacing that is larger than the line spacing, smaller-scale features will become less well-constrained by the data. For this step:

	- :ref:`Down-sample based on distance<objectDataDownsample>`


Setting the Base Station
^^^^^^^^^^^^^^^^^^^^^^^^

The horizontal magnetic fields are general measured at a base station. In this case, we must define the base station location. For the tutorial data, the base station is located at Easting = 697523 m, Northing = 6375971 m and elevation = 533 m in UTM zone 12. To carry out this step:

	- :ref:`Set/reset base station<objectDataTypeZTEM_basestn>`


Setting ZTEM Data Type
^^^^^^^^^^^^^^^^^^^^^^

We need to specify if the horizontal fields are measured at a base station or with sensors attached to the aircraft. This is done with the following functionality:

	- :ref:`Set ZTEM data type<objectDataTypeZTEM_datatype>`


Defining Receivers
^^^^^^^^^^^^^^^^^^

E3DMT v1 models the magnetic fields at discrete points whereas E3DMT v2 allows the user to define the receiver loops. If you intend to invert data with E3DMT v2, this step is required. To define the receiver loops, we use the following functionality:

	- :ref:`Set/reset receivers from data locations<objectDataTypeZTEM_snid>`

**Our approach:**

According to the contractor, *Hx* and *Hy* were measured at a base station. The receivers at the base station were circular with a diameter of 0.27 m. *Hz* was measured with a circular loop with a diameter of 7.4 m. Thus we used the following parameters to fill in the fields:

	- **Hx, Hy receiver width: 0.27**
	- **Hx, Hy number of segments: 8**
	- **Hz receiver width: 7.4**
	- **Hz number of segments: 8**
	- **Orientation from Nothing (deg): 0** (since all rotations to UBC-GIF were done already)

.. note:: If any of the loops are square, choose the number of segments to be 4. GIFtools will define the loop as a square with side length equal to the value specified.
