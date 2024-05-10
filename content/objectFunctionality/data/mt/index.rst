.. _objectMTDataIndex:

MT Data
=======

MT data can be contained either within an impedance data object (IMPdata) or an apparent resistivity and phases data object (APPdata). The data columns and functionality associated with these items are as follows:

**Data:**

	- **X, Y and Z:** These are columns for the Easting, Northing and vertical position respectively.
	- **Frequency:** The frequency at which each datum was collected.
	- **ZXXR, ZXXI, ZXYR, ZXYI, ZYXR, ZYXI, ZYYR, ZYYI:** For impedance data (IMPdata), these columns represent the real and imaginary components of impedance tensor elements.
	- **RHOXX, RHOXY, RHOYX, RHOYY:** For apparent resistivity and phase data (APPdata), these columns represent the apparent resistivities for impedance tensor elements.
	- **PHSXX, PHSXY, PHSYX, PHSXX:** For apparent resistivity and phase data (APPdata), these columns represent the phases for impedance tensor elements.
	- **Rx station ID:** For the E3DMT version 2 code, each observation location has a set of receivers which is given an ID number. This column contains the station ID numbers for each datum.


**Functionality:**

    .. toctree::
        :maxdepth: 2

        dataType
        dataManipulation



