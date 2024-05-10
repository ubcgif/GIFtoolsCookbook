.. _objectZTEMDataIndex:

ZTEM Data
=========

ZTEM data can are contained within a Z-axis Tipper EM data object (ZTEMdata). The data columns, properties and functionality associated with these items are as follows:

**Data**

	- **X, Y and Z:** These are columns for the Easting, Northing and vertical position respectively.
	- **Frequency:** The frequency at which each datum was collected.
	- **TZXR, TZXI, TZYR, TZYI:** For apparent resistivity and phase data (APPdata), these columns represent the real and imaginary components of the elements of the transfer function.
	- **Rx station ID:** For the E3DMT version 2 code, each observation location has a set of receivers which is given an ID number. This column contains the station ID numbers for each datum.
	- **Base station ID:** This column contains the base station ID numbers for each datum.

**Properties:**
	
	- :ref:`ZTEM data type <objectDataTypeZTEM_datatype>`: A flag which determines whether a base station is used when modeling ZTEM data


**Functionality:**

    .. toctree::
        :maxdepth: 2

        dataType
        dataManipulation



