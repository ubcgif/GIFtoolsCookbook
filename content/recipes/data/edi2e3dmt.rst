.. _recipe_data_edi2e3dmt:

.. include:: <isonum.txt>

NSEM: From raw EDI files to GIF formatted data
==============================================

Here we provide a recipe for creating GIF formatted natural source electromagnetic (NSEM) data objects from EDI files. Depending on the forward model/inversion code the user intends to run, additional steps may be required once the data are loaded. The additional steps are explained in the content below.

Loading the data and simple processing
--------------------------------------

    - :ref:`Import data from EDI files <importNSEMData_edi>`: The raw EDI data files contain a combination of impedance, apparent resistivity, phase, ZTEM and other data which can all be loaded. The resulting data object can be an *IMPdata* or *APPdata* object.

    - :ref:`Create different data type (optional) <objectCreateDiffData>`: Let us assume the EDI files contain impedance, apparent resistivity, phase and ZTEM data and that an *IMPdata* (impedance data) object was created upon loading. This functionality can be used to create a *ZTEMdata* or *IMPdata* object if those data are found in the *IMPdata* object.

    - **Correct units:** GIFtools makes assumptions regarding the units of data within EDI files and converts data to standard units used by GIFtools. See :ref:`data units in EDI files <importNSEMData_edi>` and :ref:`GIF data units<sign_units>`.

    - **Correct imaginary and/or phase data:** If the time-dependence (:math:`\pm i\omega t`) differs between the data being loaded and the code being used, then imaginary data and phases must be multiplied by -1 using the :ref:`calculator <objectCalculator>`. The details of this step are explained further for :ref:`MT data<sign_mt_conv>` and :ref:`ZTEM data<sign_ztem_conv>`.

    - :ref:`Set IO headers <objectSetioHeaders>`

    - :ref:`Assign uncertainties <objectAssignUncert>`


.. important::
    Before writing data files and attempting to invert MT data, it **strongly advised** that the data are viewed in terms of apparent resistivity. This information can be used to determine how resistivity changes with respect to depth, determine which frequencies are sensitive to your target and design an appropriate mesh.


Additional Steps
----------------

**Preparing data for E3DMT version 1 code:**

The E3DMT version 1 programing package can forward model and invert both impedance data and ZTEM data. If the previous steps have been done to obtain an *IMPdata* object, impedance data can be forward modeling and/or inverted. However, ZTEM data will require extra steps if a base station is used to measure the Hx and Hy fields. To set up the base station for ZTEM data:

    - :ref:`Set/reset base station and define base station ID column <objectDataTypeZTEM_basestn>`
    - :ref:`Set ZTEM data type <objectDataTypeZTEM_datatype>`
    - :ref:`Check to ensure IO header set for base ID column <objectSetioHeaders>`

Impedance and/or ZTEM data can now be :ref:`exported<objectDataTypeMT_export1>`, forward modeled or inverted.


**Preparing data for E3DMT version 2 code:**

The E3DMT version 2 programing package can forward model and invert either impedance data or ZTEM data. To use this code, the dimensions of all wire and loop receivers measuring fields must first be defined. This can by performing the following steps:

    - For ZTEM data, steps in *"Preparing data for E3DMT version 1 code"* can be used to create a base station, which sets the locations for loop measuring Hx and Hy. If :ref:`ZTEM data type <objectDataTypeZTEM_datatype>` is set to *MTH*, then Hx and Hy measurements happen at the observation locations.
    - **Set/reset receivers from data locations for** :ref:`MT data<objectDataTypeMT_snid>` **or** :ref:`ZTEM data<objectDataTypeZTEM_snid>`
    - :ref:`Check to ensure IO header set for station ID column <objectSetioHeaders>`

Impedance and/or ZTEM data can now be :ref:`exported<objectDataTypeMT_export1>`, forward modeled or inverted.





