.. _objectDataManipulationZTEM:

.. include:: <isonum.txt>

ZTEM Data Manipulation Menu
===========================


.. _objectDataManipulationZTEM_total_divergence:

Compute Total Divergence Columns
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Tipper data are sensitive to lateral changes in electrical conductivity. To represent the tipper data in a way that is directly sensitive to conductive and resistive structures, we can compute the *total divergence parameter* (termed the 'DT'). For both the real and imaginary components, the total divergence parameter is computed by:

.. math::
	DT = \frac{\partial T_{x}}{\partial x} + \frac{\partial T_{y}}{\partial y}

Before and after computing this quantity within the GIFtools framework, there are a few things the user should consider:

	- The data must be represented in UBC-GIF format. That is, X = Northing, Y = Easting and Z +ve downward
	- The UBC-GIF coordinate system also applies when taking derivatives
	- When plotting the total divergence for the real component with GIFtools, you will generally see maxima (positive anomalies) over conductors and minima (negative anomalies) over resistive zones.

This functionality is accessed though:

**Data Manipulation** |rarr| **Calculate** |rarr| **Compute total divergence (DT) columns**

When applying this functionality, GIFtools computes discrete derivatives. It is up to the user to choose the accuracy of the derivatives by setting the spacing between discrete points used in the computation. A default value of 100 is set. We suggest the user choose 1/4 to 1/2 the flight line separation distance. 


.. _objectDataManipulationZTEM_transform:

Transform Data Convention for ZTEM Data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ZTEM data are frequently collected in a data convention that is survey-dependent. This functionality applies the necessary transform to go from the survey-dependent coordinate system to UBC-GIF. The necessary transform can be determined from the ZTEM polarization information provided by the contractor. This functionality can be accessed through:

**Data Manipulation** |rarr| **Coordinates** |rarr| **ZTEM data transformation**

There are 3 considerations when applying the transformation. These are described below.

**Set Flight Bearing:** For each datum, this is the 'along-line' direction. Here, you enter the degrees clockwise from Northing that corresponds to the along-line direction. For UBC-GIF codes, you can think of the along-line direction "X" as being the Northing direction. There are two options:

	- *Constant:* All of the data is defined in the same along-line direction
	- *Column:* If the along-line direction for each datum is provided in a column, it can be applied.

**Define cross-line direction:** UBC-GIF convention defines the cross-line direction "Y" as being 90 degrees clockwise from the along-line direction "X". However, ZTEM data are frequently defined as having a cross-line direction that is 90 degrees counter clockwise from the along-line direction. Here there are two options:

	- *Cross-line direction is 90 degrees CCW from along-line direction:* Need to include this in the transform to go to UBC-GIF convention.
	- *Cross-line direction is 90 degrees CW from along-line direction:* This does not need to be taken into account in the transform.

**Convert Z Direction:** UBC-GIF data convention is Z +ve downward whereas some survey-dependent conventions may use Z +ve upward. For this, there are two options:

	- *Convert from Z +ve up to Z +ve down*
	- *Convention is already Z +ve down*
