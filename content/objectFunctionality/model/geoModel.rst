.. _objectFunctionalityGeoModel:

.. include:: <isonum.txt>

Geological Models
=================

.. _objectFunctionalityGeoModelIO:

Set I/O Headers
---------------

This functionality sets the input and output columns for the data defining the geological model. This functionality can be accessed through:

**Geology Model** |rarr| **Geology definition** |rarr| **Set I/O headers**


.. _objectFunctionalityGeoModelRename:

Rename Headers
--------------

This functionality allows the user to rename the headers for the columns which define the geological model. This functionality can be accessed through:

**Geology Model** |rarr| **Geology definition** |rarr| **Set I/O headers**


.. _objectFunctionalityGeoModelEdit:

Edit Geology Definitions
------------------------

This functionality is accessed through:

**Geology Model** |rarr| **Geology definition** |rarr| Edit

For each unit defined in the geological model, this functionality allows the user to set constant value for:

	- The geology ID
	- The mean property value
	- The lower bound for the property value
	- The upper bound for the property value
	- A constant weighting for the cells within each geology
	- Add a comment about the geological unit such as its lithology



.. _objectFunctionalityGeoModelPhysProp:

Create Physical Property Model (GIF Model)
------------------------------------------

This functionality allows the user to create a physical property models (GIF models) from a geological model. This functionality can be accessed through:

**Geology Model** |rarr| **Create model** |rarr| **From property values**

**Requirements:**

	- Values for each geological unit in the geological model must be confirmed
	- The :ref:`I/O headers <objectFunctionalityGeoModelIO>` for each column defining the geological model should confirmed


.. _objectFunctionalityGeoModelActive:

Create Active Model from Units
------------------------------

This functionality allows the user to create an active cells model from a geological model. The user may specify which geological units are active and which are inactive. This functionality can be accessed through:

**Geology Model** |rarr| **Create model** |rarr| **Active model from units**





