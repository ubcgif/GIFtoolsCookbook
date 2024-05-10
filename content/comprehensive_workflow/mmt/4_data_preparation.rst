.. _comprehensive_workflow_mmt_4:


Data Preparation
================

Before creating a survey-dependent mesh, writing UBC-GIF formatted data files or inverting, certain steps must be completed. These include:

    - Down-sampling the data to a manageable number of data points
    - Setting the location of the base station that measures Ex and Ey
    - Defining the Ex, Ey, Hx and Hy receivers

These steps are covered here.

Down-Sampling
^^^^^^^^^^^^^

The sampling rate in the along-line direction is generally much higher than is needed to characterize MobileMT anomalies. Furthermore, 3D EM inversions can have trouble converging to a geologically plausible model when the data spacing is less than 2-3 horizontal cell widths; unless the measured fields are sufficiently smooth. As a result, you may consider some aspects of mesh design during this step. The desired station spacing is generally determined by the flight-line separation. Here, we down-sample the data based on a desired minimum separation.

**Our Approach:**

The flight-line separation for the tutorial dataset is 200 m. For a cursory inversion, we may choose to downsample to a minimum station spacing of 200 m.
Here, we chose to down-sample the data to a minimum spacing of 125 m. The observed data were fairly smooth and we wanted to accurately characterize the anomalies observed at the highest frequencies. For this step, we use:

    - :ref:`Down-sample based on distance<objectDataDownsample>`


Setting the Base Station Location
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The horizontal electric fields are measured at a surface base station. Here, we must define the base station location. For the tutorial data, the base station is located at Easting = 490276 m, Northing = 5421761 m and elevation = 290 m. To carry out this step:

    - :ref:`Set/reset base station<objectDataTypeZTEM_basestn>`


Defining Receivers
^^^^^^^^^^^^^^^^^^

E3DMT v2 requires the user to define the receivers used to measure electric and magnetic fields. To define the receivers, we use the following functionality:

    - :ref:`Set/reset receivers from data locations<objectDataTypeMT_snid>`

**Our approach:**

We were not provided with the dimensions of the receiver loops measuring magnetic fields. For MobileMT, it is generally safe to assume the dimensions of the receiver loops are much smaller than the minimum cell size of the mesh we will create. In this case, we set the width of the receiver loops measuring magnetic fields to 1 m, and made the loops square by defining the number of segments as 4. The lengths of the dipole receivers measuring electric fields were 100 m. Because MobileMT data are computed by taking the determinant of the admittance tensor, the choice in orientation should be redundant, and so it is left as 0 degrees.

    - **Hx, Hy receiver width: 1**
    - **Hx, Hy number of segments: 4**
    - **Ex, Ey dipole length: 100**
    - **Ex, Ey number of segments: 1**
    - **Orientation from Nothing (deg): 0**
