.. _fwdEditOptions_fdem:

.. include:: <isonum.txt>

Edit Options for Frequency Domain EM
====================================

.. _fwdEditOptions_e3d_ver1:

E3D version 1
-------------

This functionality is responsible for setting all forward modeling parameters pertaining to the E3D version 1 code (*e3d.exe*); `see manual <https://e3d.readthedocs.io/en/e3d/>`__ . Within the edit options window below, the user sets the following parameters for the forward modeling:

        .. figure:: ../images/e3d_v1.png
            :align: center
            :width: 700


    - **Locations:** The user selects an *FEMdata* object from the dropdown menu.

    - **Topography (optional):** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active. If using a conductivity model where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Conductivity model:** This is the required conductivity model for forward modeling the data.

    - **Background susceptibility model:** Here, the user can specify a background magnetic susceptibility model for the forward modeling. There are 3 options:

        - **No Sus:** The Earth is considered non-susceptible

        - **Value:** A constant magnetic susceptibility value is assigned to all cells lying below the surface topography (*not currently implemented*)

        - **Model:** The user supplies an OcTree model


    - **Model total field or secondary field:**

        - **Total field:** the data output by the forward modeling is the total field.

        - **Secondary (analytic):** the code will forward model the secondary field. It will do this by computing the total field for the *conductivity model* provided, then subtracting the analytic total field using the homogeneous *background conductivity* provided. To subtract the free-space primary field, let the background conductivity be 1e-8 S/m.

        - **Secondary (numeric):** the code will forward model the secondary field. It will do this by computing the total field for the *conductivity model* provided, then subtracting the numerically computed total field using the homogeneous *background conductivity* provided. To subtract the free-space primary field, let the background conductivity be 1e-8 S/m.

    - **Solver Options:** The forward problem can be solver using the direct Pardiso solver or the BiCG iterative solver. The parameters for the accuracy of the iterative solver are described in the `E3D v1 manual <https://e3d.readthedocs.io/en/e3d/content/inputfiles/inversion.html#e3d-input-inv-ln19>`__ .


Units
^^^^^

**Inputs:**

    - **Conductivity model:** Octree model with conductivity in S/m
    - **Susceptibility model:** OcTree model with magnetic susceptibility in SI units

**Outputs:**

    - Either **total field** or **secondary field** data in A/m


.. _fwdEditOptions_e3d_ver2:

E3D version 2 (and version 2 tiled)
-----------------------------------

This functionality is responsible for setting all forward modeling parameters pertaining to the E3D version 2 code (done with *e3d_v2.exe*) and the E3D version 2 tiled code (done with *e3d_v2_tiled.exe*); see `E3D v2 manual <https://e3d.readthedocs.io/en/e3d_v2/>`__ or see `E3D v2 tiled manual <https://e3d.readthedocs.io/en/e3d_v2_tiled/>`__ . Within the edit options window below, the user sets the following parameters for the forward modeling:

        .. figure:: ../images/e3d_v2.png
            :align: center
            :width: 700


    - **Locations:** The user selects an *FEM3Dsounding* object from the dropdown menu.

    - **Topography (optional):** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active. If using a conductivity model where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Conductivity model:** This is the required conductivity model for forward modeling the data.

    - **Background susceptibility model:** Here, the user can specify a background magnetic susceptibility model for the forward modeling. There are 3 options:

        - **No Sus:** The Earth is considered non-susceptible

        - **Value:** A constant magnetic susceptibility value is assigned to all cells lying below the surface topography (*not currently implemented*)

        - **Model:** The user supplies an OcTree model


    - **Model total field or secondary field:**

        - **Total field:** the data output by the forward modeling is the total field.

        - **Secondary (analytic):** the code will forward model the secondary field. It will do this by computing the total field for the *conductivity model* provided, then subtracting the analytic total field using the homogeneous *background conductivity* provided. To subtract the free-space primary field, let the background conductivity be 1e-8 S/m.

        - **Secondary (numeric):** the code will forward model the secondary field. It will do this by computing the total field for the *conductivity model* provided, then subtracting the numerically computed total field using the homogeneous *background conductivity* provided. To subtract the free-space primary field, let the background conductivity be 1e-8 S/m.

    - **Solver Options:** The forward problem can be solver using the direct Pardiso solver or the BiCG iterative solver. The parameters for the accuracy of the iterative solver are described in the `E3D v1 manual <https://e3d.readthedocs.io/en/e3d/content/inputfiles/inversion.html>`__ .

    - **Mesh tiles file:** If you are using the tiled code, this space is used to set the filepath to the local meshes (or tiles)


Units
^^^^^

**Inputs:**

    - **Conductivity model:** Octree model with conductivity in S/m
    - **Susceptibility model:** OcTree model with magnetic susceptibility in SI units

**Outputs:**

    - Either **total field** or **secondary field** data in A/m








