.. _comprehensive_workflow_mt_ztem_3:

MT Data Preparation and Uncertainties
=====================================

.. note:: The steps for preparaing and assigning uncertainties to ZTEM and MT data do not necessarily need to be done in a specific order. Here, we have chosen to start with the MT data.


MT measurements provide comprehensive EM information by measuring multiple data components at frequencies spanning many orders of magnitude (mHz to kHz). Unfortunately, MT data collection is very time consuming and is rarely collected at more than a few dozen stations. ZTEM data can be collected efficiently over large areas. However, ZTEM data are collected over a much smaller range of frequencies (generally between 30 Hz and 720 Hz).  As a result, ZTEM data is generally used to provide limited information over a large area. And MT data is used to provide high quality information for specific purposes. Examples include:

    - using a spaced out set of MT stations characterize the regional geology
    - using a more localized cluster of MT station to better characterize a geological target
    - using higher frequency MT data to characterize the near-surface/overburden


For independent MT inversion, a standard approach for assigning uncertainties and preparing MT data was covered in the Cloncurry MT comprehensive workflow.
We strongly urge the reader to be familiar with this material. For reference, visit:

    - :ref:`Preparing MT data <comprehensive_workflow_mt_3>`

    - :ref:`Assigning uncertainties to MT data <comprehensive_workflow_mt_4>`



Data Preparation
----------------

Frequency-Based Extraction
^^^^^^^^^^^^^^^^^^^^^^^^^^

The intended purpose for collecting the MT data and the computational resources available will determine which frequencies are extracted and used in our joint MT-ZTEM inversion.
When looking forward to mesh design and joint inversion, we must consider the following:

    1. The collective range of frequencies contained within the MT and ZTEM data being inverted should not exceed 3 orders of magnitude. This ensures the smallest cells in the mesh can adequately model the highest frequency. And ensures we can create a large enough mesh to adequately model the lowest frequency. Since ZTEM data are collected between (30 Hz and 720 Hz), there is only a certain range of frequencies at which MT data can be used in a joint inversion.
    
    2. The inversion algorithm must store a factorization for every unique frequency. And since MT and ZTEM systems don't collect data at identical frequencies, the computational resources required for joint MT-ZTEM inversion can be quite large. We are therefore limited in the number of MT data frequencies that can be used in our joint inversion.


Using GIFtools, we perform the frequency-based extraction:

    - :ref:`Frequency-based extraction of data<objectTimeFreqExtract>`


**Our approach:**

For the tutorial data, we extracted MT data at 5 logarithmically spaced frequencies (8 Hz, 24 Hz, 80 Hz, 256 Hz and 756 Hz); which created the data object *mt_data_5freq*. Accoding to the :ref:`apparent resistivity sounding curves <comprehensive_workflow_mt_ztem_2_mt_interp>`, this range of frequencies appears to be sensitive to the nearer-surface conductive region and the background geology.



Defining Receivers
^^^^^^^^^^^^^^^^^^

Presently, E3DMT v2 is considered the superior code for inverting natural-source EM data. To use this code, we must define the receivers:

    - :ref:`Set/reset receivers from data locations<objectDataTypeMT_snid>`

We define the receivers on our frequency-extracted data object (*mt_data_5freq* in our case).

**Our approach:**

According to the contractor, the electric field dipoles had lengths of 100 m. Receivers measuring the magnetic fields were much smaller than the cell dimensions being used to model the fields. If the contractor does not provide you with the coil receiver's dimensions, you may choose a value such as 1 m or 4 m. We used the following parameters to fill the fields:

    - **Hx, Hy receiver width: 2 m**
    - **Hx, Hy number of segments: 4**
    - **Ex, Ey receiver length: 100 m**
    - **Ex, Ey number of segments: 3**
    - **Orientation from Nothing (deg): 0** (since data are defined Northing-Easting-Down)
    - **Ex (Northing) shift:** 0 m Easting and 50 m Northing
    - **Ey (Easting) shift:** 50 m Easting and 0 m Northing

.. note:: If the loop receivers are square, choose the number of segments to be 4. GIFtools will define the loop as a square with side length equal to the value specified.



Assigning Uncertainties
-----------------------

    - Use the :ref:`GUI for applying frequency-dependent uncertainties <objectAssignUncertGUI>`.

**Off-Diagonal Impedances (ZXYR, ZXYI, ZYXR and ZYXI):**

For off-diagonal impedance components, we applied both a percent and a floor. For all components and for all frequencies, the percent uncertainty was 5%. Choosing a floor was more involved. Similar to the approach in the :ref:`Cloncurry MT comprehensive workflow <comprehensive_workflow_mt_4>`, the floor uncertainty at each frequency was computed according to:

.. math::
    \varepsilon (f) = \sqrt{2\pi \mu f (0.5 \Omega m)}

This resulted in floor uncertainties of roughly 0.0055, 0.01, 0.018, 0.032 and 0.055 V/A. Essentially, the floor uncertainties ensure we do not try to fit large localized fluctuations in high conductivity regions at the expense of properly fitting resistive structures.


**Diagonal Impedances (ZXXR, ZXXI, ZYYR and ZYYI):**

For diagonal impedance components, we applied a floor uncertainty equal to 5% the maximum amplitude. This was done separately for each component and for each frequency.
    