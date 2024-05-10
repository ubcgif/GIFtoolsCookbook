.. _invEditOptions_nsem:

.. include:: <isonum.txt>

Edit Options for Natural Source EM (MT and ZTEM)
================================================

.. _invEditOptions_e3dmt_ver1:

E3DMT version 1
---------------

This functionality is responsible for setting all inversion parameters pertaining to the E3DMT version 1 code (*e3dMTinv.exe* and *e3dMTinv_iter.exe*); `see manual <https://e3dmt.readthedocs.io/en/manual_ver1/>`__ . Within the edit options window below, there are 3 tabs:

    - **Basic:** Sets minimum required input for the inversion

    - **Model Options:** Sets starting model, reference model, upper and lower bounds, weighting constraints and trade-off parameter (beta) options

    - **Inversion Parameters:** Sets advanced parameters and tolerances for the inversion

    .. figure:: ../images/e3dmt_ver1.png
        :align: center
        :width: 700


Basic
^^^^^


    - **Observed data:** The user selects one or more data objects from the list provided, allowing for joint inversion of MT and/or ZTEM data. It is important to note that the ordering of the data locations is identical to the ordering of the object selected. To change the ordering of data locations written to file, use the *Shift up* and *Shift down* buttons.


            .. note:: If multiple data objects are used in the inversion, then upon loading predicted data, the data are parsed into several data objects.


    - **Mesh:** OcTree mesh on which a conductivity model is recovered.

    - **Topography:** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active (ALL_ACTIVE). If using reference/starting models where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Background susceptibility model:** Here, the user can specify a background magnetic susceptibility model for the inversion. There are 3 options:

        - **No Sus:** The Earth is considered non-susceptible

        - **Value:** A constant magnetic susceptibility value is assigned to all cells lying below the surface topography

        - **Model:** The user supplies an OcTree model

    - **1D background conductivity model:** The E3DMT version 1 code solves a 1D problem on a background conductivity model and uses the solution to obtain the source term needed for the 3D problem. This is explained in more detail in the `E3DMT version 1 manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#source-term>`__ . Here, the user has two options:

        - **Value:** A constant conductivity value is used for the background conductivity

        - **Model:** A 1D conductivity model is used as the background conductivity. The number of conductivity values defining this model **must** equal the number of underlying mesh cells defining the OcTree mesh in the z-direction; `see manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/inputfiles/forward.html>`__ .


    .. note:: If there is significant topography, computation of the boundary conditions and thus the final 3D solution may not be as accurate. In this case, it is suggested the user model data with E3DMT version 2.


    - **Solver type:** The forward problem can be solved with either a direct solver or an iterative solver. The direct solver requires more memory but is faster. The iterative solver is slower but allows the solution of larger problems.

        - **Iterative:** Uses the BICGstab algorithm.

        - **Direct:** Uses Paradiso


Model Options
^^^^^^^^^^^^^

    - **Beta Cooling Schedule:** Sets the rate of decrease in beta as the algorithm puts increasing emphasis on fitting the data; see :ref:`fundamentals of inversion<Fundamentals_Beta>` or the `E3DMT version 1 manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#cooling-schedule>`__ .

        - **Default:** A default cooling schedule is used.

        - **Custom:** The user sets the following parameters:

            - *beta max:* Starting beta value
            - *beta min:* Final beta value before the algorithm quits (if target misfit not attained)
            - *reduction factor:* a multiplicative constant between (0,1). Sets how much beta is reduced at each iteration

    - **Chi Factor:** Sets the target data misfit for the inversion. A chi-factor of 1 (default value) implies the data misfit is equal to the total number of data observations. 

            .. important:: This code uses a measure of data misfit that is different from the majority of GIF codes. It is recommended the user be familiar with the measure of data misfit; `see manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#e3dmt-version-1>`__ .

    - **Weighting constants:** Sets the weights for smallness and smoothness regularization in x, y and z; see :ref:`fundamentals of inversion <Fundamentals_alphas>`.

        - **Default:** Sets the values of *alpha S*, *alpha E*, *alpha N* and *alpha Z* based on cell dimensions
        - **Alphas:** Sets specific values for *alpha S*, *alpha E*, *alpha N* and *alpha Z*
        - **Lengths:** User sets values *Len E*, *Len N* and *Len Z* which define the values of *alpha X*, *alpha Y* and *alpha Z* relative to *alpha S*. These relationships are given by :math:`L_E = \sqrt{\frac{\alpha_E}{\alpha_S}}`, :math:`L_N = \sqrt{\frac{\alpha_N}{\alpha_S}}` and :math:`L_Z = \sqrt{\frac{\alpha_Z}{\alpha_S}}`.

    - **Additional weights:** Here, the user may specify the implementation of additional cell and/or face weighting; see :ref:`fundamentals of inversion <Fundamentals_WeightingMatrix>`. In this case, the user selects a *GIFweight* object that is defined on the OcTree mesh.

    - **Active model cells:** Here, the user specifies which cells are active during the inversion (allowed to change their value). If all are set to active, then all cells within the surface topography are allowed to change. If an active cells model is used, only the active cells change their value during the inversion; the remaining cells (inactive) are left as the starting model value.

    - **Initial model:** Staring model for the inversion. Can be either a constant value or an OcTree model

    - **Upper bounds:** Upper bounds for the recovered conductivity model.

        - *None:* No upper bounds
        - *Value:* Set a constant upper bound to be applied to all cells.
        - *Model:* An OcTree model that defines the upper bound for each cell individually. Values corresponding to inactive cells in the inversion are ignored.

    - **Lower bounds:**

        - *None:* No lower bounds
        - *Value:* Set a constant lower bound to be applied to all cells.
        - *Model:* An OcTree model that defines the lower bound for each cell individually. Values corresponding to inactive cells in the inversion are ignored.

    - **Reference model:** Reference model for the inversion; see :ref:`fundamentals of inversion <Fundamentals_SmoothInDiff>`.

        - *Value:* Set a constant value for the reference model.
        - *Model:* An OcTree model that defines the reference model.

    - **Update reference model throughout:**

        - *Un-checked:* The reference model remains the same throughout the entire inversion. This option emphasizes preserving structures included in the reference model.
        - *Checked:* Each time beta is updated, the current recovered model is set as the reference model for the next beta value. This results in faster convergence but does not emphasize preserving structures in the original reference model as strongly.

    - **Role in model objective function:** See :ref:`fundamentals of inversion <Fundamentals_SmoothInDiff>`

        - *SMOOTH_MOD:* Reference model only used in smallness term in the model objective function
        - *SMOOTH_MOD_DIF:* Reference model using in the smallness and smoothness terms in the model objective function


Inversion Parameters
^^^^^^^^^^^^^^^^^^^^
    
    - **Newton iteration settings:** Sets stopping criteria for Gauss-Newton iterations; see `E3DMT version 1 manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#gauss-newton-update>`__ . Parameters are:

        - **tol_nl:** stopping criteria based on gradient size (defaul = 0.01)
        - **mindm:** stopping criteria based on size of model perturbation (default = 0.001)
        - **iter_per_beta:** maximum number of Gauss-Newton iterations (default = 3)

    - **IPCG settings:** Sets tolerances for solving the system at each Gauss-Newton iteration using incomplete preconditioned conjugate gradient; see `E3DMT version 1 manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#gauss-newton-solve>`__ . Parameters are:

        **tol_ipcg:** relative tolerance for solution (default = 0.01)
        **max_iter_ipcg:** maximum number of IPCG iterations (20)

    - **Data weighting for joint inversion:** If multiple datasets are being inverted jointly, you may want influence how well the inversion fits each dataset. For more details, see :ref:`fundamentals of inversion <Fundamentals_Joint>`. By default, no data weighting is applied. For E3DMT version 1, options for data weighting are:

        - **Apply weighting to data:** If this box is selected, the user must supply a weighting constant for each of the data objects they selected in the table provided. Enter values of 1 for no weighting.
        - **Weight by number of data:** If this box is not selected, data weighting is defined in the table provided. If selected, each dataset will be weighted based on the number of data it has. 
        

    .. note:: The E3DMT version 1 executable does not have the ability to perform joint inversion directly. To carry out the joint inversion of MT and ZTEM data, the uncertainties are scaled by a constant factor. Although the uncertainties are changed, the target misfit for the inversion (total # data :math:`\times` chi factor) does not. However, the original uncertainties are preserved within the GIFtools framework when plotting misfit maps.

    - **BICG settings:** If solving the forward problem using an iterative solver, these parameters specify the tolerances and stopping criteria for the BiCGstab algorithm.

        - **tol_bicg:** (default = 1e-11)
        - **tol_ipcg_bicg:** (default = 1e-5)
        - **max_it_bicg:** (default 150)
        - **freq_Aphi:** (default = 1e6)



Units
^^^^^

**Inputs:**

    - **Initial model:** OcTree model with conductivity in S/m
    - **Reference model:** Octree model with conductivity in S/m
    - **1D background conductivity:** A 1D model with conductivity in S/m
    - **Susceptibility model:** OcTree model with magnetic susceptibility in SI units
    - **Upper and lower bounds:** Octree model with conductivity in S/m
    - **MT data:** Real and imaginary components of impedance tensor entries (V/A)
    - **ZTEM data:** Real and imaginary components of transfer function entries (unitless)

**Outputs:**

    - **Conductivity model:** OcTree model with conductivity in S/m


.. _invEditOptions_e3dmt_ver2:

E3DMT version 2
---------------

This functionality is responsible for setting all inversion parameters pertaining to the E3DMT version 2 code (*e3dMTinv_ver2.exe*); `see manual <https://e3dmt.readthedocs.io/en/manual_ver2/>`__ . Within the edit options window below, there are 3 tabs:

    - **Basic:** Sets minimum required input for the inversion

    - **Model Options:** Sets starting model, reference model, upper and lower bounds, weighting constraints and trade-off parameter (beta) options

    - **Inversion Parameters:** Sets advanced parameters and tolerances for the inversion

    .. figure:: ../images/e3dmt_ver2.png
        :align: center
        :width: 700


Basic
^^^^^


    - **Observed data:** The user selects either and impedance data or ZTEM data object from the drop-box provided.

    - **Mesh:** OcTree mesh on which a conductivity model is recovered.

    - **Topography:** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active (ALL_ACTIVE). If using reference/starting models where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Background susceptibility model:** Here, the user can specify a background magnetic susceptibility model for the inversion. There are 3 options:

        - **No Sus:** The Earth is considered non-susceptible

        - **Value:** A constant magnetic susceptibility value is assigned to all cells lying below the surface topography

        - **Model:** The user supplies an OcTree model

    - **Background conductivity model:** The E3DMT version 2 code must first compute the source term needed for the 3D problem and can do so in a variety of ways. This is explained in more detail in the `E3DMT version 2 manual <https://e3dmt.readthedocs.io/en/manual_ver2/content/theory.html#source-term>`__ . Here, the user specifies if the source term is computed using a 1D or 3D approach, then supplies the appropriate model. In total, there are 4 options for defining the background conductivity model:

        - **1D + Value:** A 1D background conductivity model is used. This model has a constant conductivity value below the highest surface topography.

        - **1D + Model:** A 1D background conductivity model is used. The number of conductivity values defining this model **must** equal the number of underlying mesh cells defining the OcTree mesh in the z-direction; `see manual <https://e3dmt.readthedocs.io/en/manual_ver2/content/inputfiles/inversion.html>`__ .

        - **3D + Value:** A 3D background conductivity model is used. This model has a constant conductivity value for all cells below the surface topography.

        - **3D + Model:** A 3D background conductivity model is used. The background conductivity model must be defined on the OcTree mesh used to forward model the data.

    .. note:: If surface topography is negligible, the the 1D background model is accurate and computationally efficient. If topography is significant, it is advised that a 3D background model is used.


Model Options
^^^^^^^^^^^^^

    - **Beta Cooling Schedule:** Sets the rate of decrease in beta as the algorithm puts increasing emphasis on fitting the data; see :ref:`fundamentals of inversion<Fundamentals_Beta>` or the `E3DMT version 1 manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#cooling-schedule>`__ .

        - **Default:** A default cooling schedule is used.

        - **Custom:** The user sets the following parameters:

            - *beta max:* Starting beta value
            - *beta min:* Final beta value before the algorithm quits (if target misfit not attained)
            - *reduction factor:* a multiplicative constant between (0,1). Sets how much beta is reduced at each iteration

    - **Chi Factor:** Sets the target data misfit for the inversion. A chi-factor of 1 (default value) implies the data misfit is equal to the total number of data observations. 

    .. important:: This code uses a measure of data misfit that is different from the majority of GIF codes. It is recommended the user be familiar with the measure of data misfit; `see manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#e3dmt-version-1>`__ .

    - **Weighting constants:** Sets the weights for smallness and smoothness regularization in x, y and z; see :ref:`fundamentals of inversion <Fundamentals_alphas>`.

        - **Default:** Sets the values of *alpha S*, *alpha E*, *alpha N* and *alpha Z* based on cell dimensions
        - **Alphas:** Sets specific values for *alpha S*, *alpha E*, *alpha N* and *alpha Z*
        - **Lengths:** User sets values *Len E*, *Len N* and *Len Z* which define the values of *alpha X*, *alpha Y* and *alpha Z* relative to *alpha S*. These relationships are given by :math:`L_E = \sqrt{\frac{\alpha_E}{\alpha_S}}`, :math:`L_N = \sqrt{\frac{\alpha_N}{\alpha_S}}` and :math:`L_Z = \sqrt{\frac{\alpha_Z}{\alpha_S}}`.

    - **Additional weights:** Here, the user may specify the implementation of additional cell and/or face weighting; see :ref:`fundamentals of inversion <Fundamentals_WeightingMatrix>`. In this case, the user selects a *GIFweight* object that is defined on the OcTree mesh.

    - **Active model cells:** Here, the user specifies which cells are active during the inversion (allowed to change their value). If all are set to active, then all cells within the surface topography are allowed to change. If an active cells model is used, only the active cells change their value during the inversion; the remaining cells (inactive) are left as the starting model value.

    - **Initial model:** Staring model for the inversion. Can be either a constant value or an OcTree model

    - **Upper bounds:** Upper bounds for the recovered conductivity model.

        - *None:* No upper bounds
        - *Value:* Set a constant upper bound to be applied to all cells.
        - *Model:* An OcTree model that defines the upper bound for each cell individually. Values corresponding to inactive cells in the inversion are ignored.

    - **Lower bounds:**

        - *None:* No lower bounds
        - *Value:* Set a constant lower bound to be applied to all cells.
        - *Model:* An OcTree model that defines the lower bound for each cell individually. Values corresponding to inactive cells in the inversion are ignored.

    - **Reference model:** Reference model for the inversion; see :ref:`fundamentals of inversion <Fundamentals_SmoothInDiff>`.

        - *Value:* Set a constant value for the reference model.
        - *Model:* An OcTree model that defines the reference model.

    - **Update reference model throughout:**

        - *Un-checked:* The reference model remains the same throughout the entire inversion. This option emphasizes preserving structures included in the reference model.
        - *Checked:* Each time beta is updated, the current recovered model is set as the reference model for the next beta value. This results in faster convergence but does not emphasize preserving structures in the original reference model as strongly.

    - **Role in model objective function:** See :ref:`fundamentals of inversion <Fundamentals_SmoothInDiff>`

        - *SMOOTH_MOD:* Reference model only used in smallness term in the model objective function
        - *SMOOTH_MOD_DIF:* Reference model using in the smallness and smoothness terms in the model objective function


Inversion Parameters
^^^^^^^^^^^^^^^^^^^^
    
    - **Newton iteration settings:** Sets stopping criteria for Gauss-Newton iterations; see `E3DMT version 2 manual <https://e3dmt.readthedocs.io/en/manual_ver2/content/theory.html#gauss-newton-update>`__ . Parameters are:

        - **tol_nl:** stopping criteria based on gradient size (defaul = 0.01)
        - **iter_per_beta:** maximum number of Gauss-Newton iterations (default = 3)

    - **IPCG settings:** Sets tolerances for solving the system at each Gauss-Newton iteration using incomplete preconditioned conjugate gradient; see `E3DMT version 2 manual <https://e3dmt.readthedocs.io/en/manual_ver2/content/theory.html#gauss-newton-solve>`__ . Parameters are:

        - **tol_ipcg:** relative tolerance for solution (default = 0.01)
        - **max_iter_ipcg:** maximum number of IPCG iterations (20)

    - **Data weighting for joint inversion:** If multiple datasets are being inverted jointly, you may want influence how well the inversion fits each dataset. For more details, see :ref:`fundamentals of inversion <Fundamentals_Joint>`. By default, no data weighting is applied. For E3DMT version 1, options for data weighting are:

        - **Apply weighting to data:** If this box is selected, the user must supply a weighting constant for each of the data objects they selected in the table provided. Enter values of 1 for no weighting.
        - **Weight by number of data:** If this box is not selected, data weighting is defined in the table provided. If selected, each dataset will be weighted based on the number of data it has. 
        

    .. note:: The E3DMT version 1 executable does not have the ability to perform joint inversion directly. To carry out the joint inversion of MT and ZTEM data, the uncertainties are scaled by a constant factor. Although the uncertainties are changed, the target misfit for the inversion (total # data :math:`\times` chi factor) does not. However, the original uncertainties are preserved within the GIFtools framework when plotting misfit maps.

    - **Memory settings:** This code factors the forward system at each frequency for repeated use in the inversion algorithm. The user has a choice in where the factorizations are stored:

        - **Store in RAM:** Factorizations are stored in RAM. This option is the fastest, however the user may run into memory limits.
        - **Write to file:** Factorizations are written to files. Larger problems can be solved, however the continual reading and writing of files makes this options slower.



Units
^^^^^

**Inputs:**

    - **Initial model:** OcTree model with conductivity in S/m
    - **Reference model:** Octree model with conductivity in S/m
    - **1D background conductivity:** A 1D model with conductivity in S/m
    - **Susceptibility model:** OcTree model with magnetic susceptibility in SI units
    - **Upper and lower bounds:** Octree model with conductivity in S/m
    - **MT data:** Real and imaginary components of impedance tensor entries (V/A)
    - **ZTEM data:** Real and imaginary components of transfer function entries (unitless)

**Outputs:**

    - **Conductivity model:** OcTree model with conductivity in S/m



