.. _fwdEditOptions_nsem:

.. include:: <isonum.txt>

Edit Options for Natural Source EM (MT and ZTEM)
================================================

.. _fwdEditOptions_e3dmt_ver1:

E3DMT version 1
---------------

This functionality is responsible for setting all forward modeling parameters pertaining to the E3DMT version 1 code (*e3dMTfwd.exe*); `see manual <https://e3dmt.readthedocs.io/en/manual_ver1/>`__ . Within the edit options window below, the user sets the following parameters for the forward modeling:

        .. figure:: ../images/e3dmt_ver1.png
            :align: center
            :width: 500


    - **Locations:** The user selects one or more data objects from the list provided, allowing for simultaneous forward modeling of MT and ZTEM data. It is important to note that the ordering of the data locations is identical to the ordering of the object selected. To change the ordering of data locations written to file, use the *Shift up* and *Shift down* buttons.


            .. note:: If multiple data objects are used to forward modeling data, then upon loaded the output of E3DMT version 1, those data are parsed into several data objects.


    - **Topography (optional):** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active. If using a conductivity model where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Real conductivity model:** This is the required conductivity model for forward modeling natural source EM data.

    - **Imaginary conductivity model (optional):** The user may select another conductivity model to represent the imaginary component of the conductivity at a particular frequency; e.g. this functionality should only be used to predict the response at a single frequency.

    - **1D background conductivity model:** The E3DMT version 1 code solves a 1D problem on a background conductivity model and uses the solution to obtain the source term needed for the 3D problem. This is explained in more detail in the `E3DMT version 1 manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#source-term>`__ . Here, the user has two options:

        - **Value:** A constant conductivity value is used for the background conductivity

        - **Model:** A 1D conductivity model is used as the background conductivity. The number of conductivity values defining this model **must** equal the number of underlying mesh cells defining the OcTree mesh in the z-direction; `see manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/inputfiles/forward.html>`__ .


                .. note:: If there is significant topography, computation of the boundary conditions and thus the final 3D solution may not be as accurate. In this case, it is suggested the user model data with E3DMT version 2.

    - **Susceptibility model:** Here, the user can specify a background magnetic susceptibility model for the forward modeling. There are 3 options:

        - **No Sus:** The Earth is considered non-susceptible

        - **Value:** A constant magnetic susceptibility value is assigned to all cells lying below the surface topography

        - **Model:** The user supplies an OcTree model


    - **Apply:** The values and objects specified are saved to the forward modeling object.


Units
^^^^^

**Inputs:**

    - **Real conductivity model:** OcTree model with conductivity in S/m
    - **Imaginary conductivity model:** Octree model with conductivity in S/m
    - **1D background conductivity:** A 1D model with conductivity in S/m
    - **Susceptibility model:** OcTree model with magnetic susceptibility in SI units

**Outputs:**

    - **MT data:** Real and imaginary components of impedance tensor entries (V/A)
    - **ZTEM data:** Real and imaginary components of transfer function entries (unitless)


.. _fwdEditOptions_e3dmt_ver2:

E3DMT version 2
---------------

This functionality is responsible for setting all forward modeling parameters pertaining to the E3DMT version 2 code (done with *e3dMTinv_ver2.exe*); `see manual <https://e3dmt.readthedocs.io/en/manual_ver2/>`__ . Within the edit options window below, the user sets the following parameters for the forward modeling:

        .. figure:: ../images/e3dmt_ver2.png
            :align: center
            :width: 500


    - **Locations:** The user selects a data object from the drop-down list. If an *IMPdata* object is selected, the code will forward model MT data. If a *ZTEMdata* object is selected, the code will forward model ZTEM data. It will not forward model both simultaneously.

    - **Topography (optional):** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active. If using a conductivity model where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Conductivity model:** This is the required conductivity model for forward modeling natural source EM data.

    - **Background conductivity model:** The E3DMT version 2 code must first compute the source term needed for the 3D problem and can do so in a variety of ways. This is explained in more detail in the `E3DMT version 2 manual <https://e3dmt.readthedocs.io/en/manual_ver2/content/theory.html#source-term>`__ . Here, the user specifies if the source term is computed using a 1D or 3D approach, then supplies the appropriate model. In total, there are 4 options for defining the background conductivity model:

        - **1D + Value:** A 1D background conductivity model is used. This model has a constant conductivity value below the highest surface topography.

        - **1D + Model:** A 1D background conductivity model is used. The number of conductivity values defining this model **must** equal the number of underlying mesh cells defining the OcTree mesh in the z-direction; `see manual <https://e3dmt.readthedocs.io/en/manual_ver2/content/inputfiles/inversion.html>`__ .

        - **3D + Value:** A 3D background conductivity model is used. This model has a constant conductivity value for all cells below the surface topography.

        - **3D + Model:** A 3D background conductivity model is used. The background conductivity model must be defined on the OcTree mesh used to forward model the data.

    .. note:: If surface topography is negligible, the the 1D background model is accurate and computationally efficient. If topography is significant, it is advised that a 3D background model is used.

    - **Apply:** The values and objects specified are saved to the forward modeling object.


Units
^^^^^

**Inputs:**

    - **Conductivity model:** OcTree model with conductivity in S/m
    - **1D background conductivity:** A 1D model with conductivity in S/m
    - **3D background conductivity:** OcTree model with conductivity in S/m

**Outputs:**

    - **MT data:** Real and imaginary components of impedance tensor entries (V/A)
    - **ZTEM data:** Real and imaginary components of transfer function entries (unitless)








