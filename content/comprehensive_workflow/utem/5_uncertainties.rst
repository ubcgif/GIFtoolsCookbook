.. _comprehensive_workflow_utem_5:

Assigning Uncertainties
=======================

A standardized strategy for assigning uncertainties to surface UTEM data prior to inversion has not been established.
Here, we discuss the ways uncertainties could be applied to surface UTEM data, and how it might impact the inversion result.
The role of uncertainties in geophysical inversion is presented in the :ref:`fundamentals of inversion <Fundamentals_Uncertainties>`.
When assigning uncertainties, we want to ensure we fit the anomaly and not the background.
We also want to ensure we fit each component and time channel equally.

Uncertainties on Secondary Fields
---------------------------------

For this approach, we assume the primary field has been accounted for exactly.
Regardless of whether secondary field or total field data are being inverted, we expect the uncertainties on our data to depend on the amplitude of the secondary field. For each unique transmitter loop, time channel and directional component, we apply a floor and a percent uncertainty based on the amplitude of secondary field data.

.. important:: If uncertainties are computed using total field data, we would have very large uncertainties proximal to transmitter loops and we would under-fit in this region. If the primary field has not been accounted for exactly, there will be erroneous signatures and proximal to the transmitter loops which are likely to result in the recovery of erroneous structures.

The percent uncertainty (1\% - 10\%) helps account for survey geometry by fitting anomalies in all regions of the survey region equally. E.g. conductors proximal to transmitter loops experience a stronger excitation than similar conductors located further away. If a percent uncertainty is not
applied, the inversion may over-fit the proximal conductors at the expense of fitting similar conductors lying further away. Generally, the same percent uncertainty can be applied for all data. Since the magnitudes of TEM anomalies vary over multiple orders of magnitude over the range of time channels measured, percent uncertainties are one way to ensure data at all time channels are fit evenly.

The floor uncertainty for each transmitter, time channel and directional component is some fraction (0.01 - 0.1) of the largest amplitude value. 
The floor value ensures we fit anomalies and not the background. The floor uncertainty is another approach for fitting the data evenly across all time channels. E.g. if a large floor were used for all time channels, smaller late time signatures could be under-fit and larger early time signatures could be over fit. Floor uncertainties also help to stabilize the inversion when data have zero crossings.
Although the process is somewhat labour intensive, it is nonetheless important to assign a floor separately for each transmitter, time channels and directional component. 

To apply uncertainties:

    - Use the :ref:`GUI for applying time-dependent uncertainties <objectAssignUncertGUI>`.

Uncertainties on Primary Reduced Data
-------------------------------------

One could also apply uncertainties based on primary reduced data. This approach naturally accounts for survey geometry by taking into account the geometry of the primary field. For each unique transmitter loop, time channel and field component, we assign a floor value based on the largest anomaly in
the primary reduced data. These floors are then multiplied by the absolute value of the primary field to obtain
uncertainties for secondary field data. I.e.:

.. math::
	\varepsilon = | \vec{B}_0 | \, floor


Because the primary field is largest near the transmitter loops, the uncertainties on secondary field data will also
be largest near the transmitter loops.

To apply uncertainties:

    - Use the :ref:`GUI for applying time-dependent uncertainties <objectAssignUncertGUI>` on the primary reduced column.
    - Use the :ref:`column calculator <objectCalculator>` to convert to uncertainties on secondary fields.

Uncertainties for Tutorial Data
-------------------------------

We chose to assign uncertainties based directly on the secondary fields. For all transmitters, time channels and
components, a floor of 0.02 times the largest amplitude was applied. A percent uncertainty of 10 \% was applied.

