.. _invEditOptions_dcip:

.. include:: <isonum.txt>

Edit Options for DCIP Inversion Objects
***************************************

.. _invEditOptions_dcip2d:

DCIP2D
======

This functionality is responsible for setting all inversion parameters pertaining to the "DC2Dinversion" and "IP2Dinversion" codes; see `DCIP2D online manual <http://dcip2d.readthedocs.io/en/latest/index.html>`__ . The edit options window is comprised of 2 tabs:

    - **Basic:** Sets minimum required input for the inversion

    - **Advanced:** Sets advanced parameters for the inversion, including: the solver, regularization, weights and hard constraints


.. figure:: ../images/dcip2d.png
    :align: center
    :width: 700

    Basic (left), advanced parameters 1 (middle) and advanced parameters 2 (right) tabs.


Units
-----

**Inputs:**

	- **Observed DC data:** observed voltage, normalized by the transmitter current (i.e. :math:`\Delta V/ \! I` )
	- **Observed IP data:** apparent intrinsic chargeabilities (i.e. :math:`\eta_a \in [0,1]`)
	- **Reference/background conductivity model:** S/m
	- **Reference chargeability model:** intrinsic chargeabilities (i.e. :math:`\eta_a \in [0,1]`)

**Outputs:**

	- **Recovered conductivity model:** S/m
	- **Recovered chargeability model:** intrinsic chargeabilities (i.e. :math:`\eta \in [0,1]`)

Basic
-----

	- **Mesh:** mesh for the recovered model

		- **Default (DC only):** The cell size, core region and padding are set automatically based on the electrode spacings and locations. This option will output a mesh object.
		- **Semi-default (DC only):** The user specifies the minimum number of cells between electrodes (*default* = 4) and the aspect ratio (*default* = 2). The aspect ratio is the vertical dimensions of the cells divided by the horizontal width. This options will output a mesh object.
		- **Object:** a mesh object is provided. Reference models, starting models and bound models must all exist on this mesh. For IP inversion, the mesh from the DC inversion must be used.

	- **Observed data:**

		- For DC inversion, the data are the observed voltage, normalized by the transmitter current (i.e. :math:`\Delta V/ \! I` ).
		- For IP inversion, the data are the apparent intrinsic chargeabilities where :math:`\eta_a \in [0,1]`.
		- Data format:
			- **Surface Data Format (recommended)**: Use this data format if the electrodes are at the surface. The Z-values will be excluded from the output data file and the forward modeling code will take care of projecting them at the surface. This avoid the risk of having electrodes in the air or underground.
			- **General Data Format**: Use this option if any electrode is underground. The Z-values are specified in the output data file.

	- **Topography:**

	    - *Default:* Sets topography assuming all electrode are located on the Earth's surface
	    - *Value:* Set the surface to the specified elevation value
	    - *Object:* A 2D topography data object

	- **Conductivity Model (IP inversion only):** Constant value or conductivity model object. Reference and starting models are set in the advanced parameters tab.


Advanced (Parameter 1)
----------------------

**Trade-off parameter:** The inversion choses the optimum trade-off parameter based on the :ref:`chi factor <Fundamentals_Beta_Discrepancy>`.

	- **Chi factor**: sets the target data misfit for the inversion (*default* = 1). :math:`target = C.F. \times \# \, data`.
	- **Max number of iterations:** maximum number of iterations to find optimum trade-off parameter (*default* = 50).

**Inverse solver:** Sets the solver used to determine the model update direction.

	- **SVD:** Singular value decomposition
	- **CG:** Conjugate gradient solver. The user may specify the number of conjugate gradient iterations (*default* = 10) and the accuracy of the solve (*default* = 0.01).

**Length scales:** Sets the weights for smallness and smoothness regularization in x and z; for relevant equations `see manual <http://dcip2d.readthedocs.io/en/latest/content/backgroundtheory.html#equation-intMOF>`__ .

	- **Default:** Sets the values of *alpha S*, *alpha X* and *alpha Z* based on cell dimensions
	- **Alphas:** Sets specific values for *alpha S*, *alpha X* and *alpha Z*
	- **Lengths:** User sets values *Len E* and *Len Z* which define the values of *alpha X* and *alpha Z* relative to *alpha S*. These relationships are given by :math:`L_x = \sqrt{\frac{\alpha_x}{\alpha_s}}` and :math:`L_z = \sqrt{\frac{\alpha_z}{\alpha_s}}`.

**Bounds:** Here, the user specified the lower and upper bounds for the inverted physical property values. For both lower and upper bounds, the user may choose from the following options:

	- **None:** No bounds
	- **Value:** A constant value applied to all cells
	- **Object:** A model object containing a distinct bound value for every cell

**Output files:** Here, the user controls the number of output files. They may choose to output every iteration of the inversion or just the final result

**Wave:** To solve the 2D forward problem, the problem must be solved in the wave domain. *N* specifies the number of log-distribution waves numbers used between *Min* and *Max*. The default is set to: *N* = 13, *Min* = 2.5e-4 and *Max* = 1.

**Huber norm:** Here, the user specifies the norm for the data misfit. For description of the data misfit see the `DCIP2D manual <http://dcip2d.readthedocs.io/en/latest/content/backgroundtheory.html#equation-phid>`__ .

	- **Default data misfit:** the data misfit is defined by an :math:`L_2 \!` -norm
	- **Huber norm:** the data misfit is defined by the Huber norm and the user may specify the Huber constant (:math:`c`).


Advanced (Parameter 2)
----------------------

**Model objective function norm:** Here, the user specifies the norm for the smallness and smoothness in X and Z. Background information regarding the model objective function norm and relevant parameters can be found within the `DCIP2D manual <http://dcip2d.readthedocs.io/en/latest/content/backgroundtheory.html#equation-intMOF>`__

	- **Default norm:** an :math:`L_2 \!`-norm is used for the smallness and smoothness terms
	- **Ekblom norm (CG solver only):** The Ekblom norm can be used to recover more compact and blockier models. For each term in the model objective function, the user specifies the parameters :math:`\epsilon` and :math:`\rho`.

**Reference model:** Here, the user specifies the reference model used in the inversion. There are 3 choices:

	- **Default:** no reference model is used
	- **Value:** a constant reference model is used
	- **Object:** the user specifies a model object as the reference model


**Role in the model objective function:** Here, the user chooses from the following 2 options in the case a reference model is used:

	- **SMALLEST MODEL ONLY:** The reference model is only used in the smallness term. The inversion attempts to preserve the structures found in the reference model.
	- **ALL DERIVATIVES:** The reference model is used in the smallness and smoothness terms. The inversion attempts to preserve the structures and gradients found the in the reference model.


**Initial model:** The user specifies the starting model. There are 3 choices:

	- **Default:** the best-fitting half spaced is used as a starting model
	- **Value:** a constant reference model is used
	- **Object:** the user specifies a model object as the reference model


.. _invDCIP3DCreateSensWeights:

**Weighting functions:** Here, the user may choose not to include additional model weights (**none**) or include face/model weights using a weights object or sensitivity-based weighting. (see section :ref:`Import sensitivity as weights <importSensWeights>`).
	- **no weighting**: no weight is applied
	- **Sensitivity weighting**: If this latest option is chosen, the program will be called a first time to compute the sensitivity matrix. GIFtools will then automatically load the sensitivity, compute the weight and launch the full inversion (see :ref:`fundamentals section <sensW_for_dcip_demo>`).
		- On cells center: the sensitivity weights are applied to the smallness term
		- On faces: the sensitivity weights are applied on the gradient terms.
		- threshold: apply a threshold to the sensitivity weights
	- **Choose weighting GIFmodel**: select a GIFmodel to use as weights



**DCinversion** |rarr| **Discrete Topo/Weights** |rarr| **Create Sensitivity Weights**

.. math::
	\mathbf{w_s} = \mathbf{J}_{approx} / max(\mathbf{J}_{approx}) + \delta

.. math::
	\mathbf{w_x} = \mathbf{A}_c^{f_x}\mathbf{w_s}

.. math::
	\mathbf{w_y} = \mathbf{A}_c^{f_y}\mathbf{w_s}

.. math::
	\mathbf{w_z} = \mathbf{A}_c^{f_z}\mathbf{w_s}

where :math:`\mathbf{w_s}`, :math:`\mathbf{w_s}`, :math:`\mathbf{w_s}` and
:math:`\mathbf{w_s}` are the cell-center and cell-face weights,
:math:`\mathbf{J}_{approx}` are the values from the ``sensitivity.txt`` file,
values from :math:`\delta` is a user-defined threhold parameter ([DEFAULT=1e-2]) and :math:`\mathbf{A}_c^{f_x}, \mathbf{A}_c^{f_y},
\mathbf{A}_c^{f_z}` are averaging operators taking the cell-center values to the respective faces.

**Active cells:** If all cells are updated during the inversion, set as **null**. If an active cells model is supplied, only the cells which are set as active will be updated during the inversion. The values of the remaining cells are determined by the starting model.



.. _invEditOptions_dcip3d:

DCIP3D v5.5
===========

.. figure:: ../images/dc3d.png
    :align: center
    :width: 700

    Inversion parameters tab (left), Models and constraints tab (right).

Functionality specific to the ``DCIPinversion`` object


Inversion Parameters Tab
------------------------

**Mesh:** The 3D tensor mesh file used in the DC or IP inversion

**Observed Data:** a *DC3Ddata* or *IP3Ddata* object

**Data format:** the *surface* and *general* buttons are used to set whether the output observed data file is formatted as surface data or in general format (usually borehole).

**Topography:**

	- **TOPOdata:** An xyz *TOPOdata* object. If you leave as *null*, the topography will correspond to the top of your mesh.

	- **ACTIVEmodel:** An *ACTIVEmodel* object that defines which cells are above and below the surface topography.

	- **IDX file:** File path to an idx file. This is a special file which can be used to define topography for the DCIP3D coding package.

**Conductivity model (IP inversion only):** Define a constant value for all Earth cells or provide a GIFmodel.

**Wavelet parameters:** Define parameters for the wavelet compression for the sensitivity matrix. For more on these parameters, see the `DCIP3D v5.5 manual <https://dcip3d.readthedocs.io/en/latest/content/runprog/dcinv.html#parameter-definitions>`__ .

**Vector memory:** Specifies how solution vectors are to be stored in the computer’s memory. For more on these parameters, see the `DCIP3D v5.5 manual <https://dcip3d.readthedocs.io/en/latest/content/runprog/dcinv.html#parameter-definitions>`__ .

**Forward problem - Solver tolerance:** Sets the relative tolerance for the accuracy of the solution of the forward problem.

Models and Constraints Tab
--------------------------

**Inversion Mode:** Either use the discrepancy principle to choose the optimum trade-off parameter or fix the trade-off parameter for the optimization. For more on these parameters, see the `DCIP3D v5.5 manual <https://dcip3d.readthedocs.io/en/latest/content/runprog/dcinv.html#parameter-definitions>`__ .

**Sensitivity Matrix:** The *Default* option is selected if the user must form the sensitivity matrix for the problem. If you have done an inversion with the same data and mesh, you can use the *already exists* option to set the file path to the sensitivity matrix binary file.

**Weighting:** Sets the weights for smallness and smoothness regularization in x, y and z; for relevant equations :ref:`fundamentals of inversion <Fundamentals_alphas>`

	- **Default:** Sets the values of *alpha S*, *alpha X*, *alpha Y* and *alpha Z* based on cell dimensions
	- **Alphas:** Sets specific values for *alpha S*, *alpha X*, *alpha Y* and *alpha Z*
	- **Lengths:** User sets values *Len E*, *Len N* and *Len Z* which define the values of *alpha X*, *alpha Y* and *alpha Z* relative to *alpha S*.

**Weights object:**

	- *No weighting:* select if you have not created sensitivity weighting yet or if no weighting is being applied.

	- *Weights object:* A GIFweights object that represents sensitivity weights or an additional weights object. Note that when creating sensitivity weights, you can multiply this weights object by the sensitivity weights.

**Active cells:** An *ACTIVEmodel* which denotes active cells in the inversion. If *null*, the active cells are determined by the topography.

**Initial model:**

	- *Value:* A constant background value

	- *Object:* GIFmodel object

	- *Default:* best-fitting halfspace


**Reference model:**

	- *Value:* A constant background value

	- *Object:* GIFmodel object

	- *Default:* best-fitting halfspace

**Role in model objective function:** To see the difference between *SMOOTH_MOD* and *SMOOTH_MOD_DIF* , see the :ref:`fundamentals of inversion <Fundamentals_SmoothInDiff>` .


.. _invEditOptions_dcipoctree:

DCIP Octree
===========

.. important:: This manual contains the documentation for DCIP octree package releases beginning on 2020-05-08. This version of the package is **compatible with GIFtools v2.31 and later**. If using an earlier version of GIFtools, everything is essentially the same except for the *independent smallness weights* option.


.. figure:: ../images/dcipoctree.png
    :align: center
    :width: 700

    Basic (left), model options (middle) and advanced parameters (right) tabs.


Basic
-----


    - **Data file format:**

        - *Surface:* All electrodes are projected to the discrete surface topography. This setting uses the surface file format and ignores the elevation columns for the electrodes.

        - *General:* Elevation columns for the electrodes must be set. Here, any electrodes lying above the discrete surface topography are projected downward while all other electrodes are left in their original positions. This necessary when borehole data are included.

    - **Observed data:** The user selects a *DC3Ddata* or *IP3Ddata* object from the drop-down list.

    - **Mesh:** OcTree mesh on which a conductivity/chargeability model is recovered. 

    - **Topography:** The user may define the surface topography using an *ACTIVEmodel* object or set all cells as active (ALL_ACTIVE). If using reference/starting models where air cells are defined as 1e-8 S/m, merely set all topography cells to active. If an *ACTIVEmodel* is used to define the underground cells, all cells in the air are automatically assigned a value of 1e-8 S/m.

    - **Background conductivity (IP only):** For IP inversion, the user must define a background conductivity model. Either a constant value for all cells below the surface topography or a *GIFmodel*.



Model Options
-------------

    - **Beta Cooling Schedule:** Sets the rate of decrease in beta as the algorithm puts increasing emphasis on fitting the data; see :ref:`fundamentals of inversion<Fundamentals_Beta>`.

        - **Default:** A default cooling schedule is used.

        - **Custom:** The user sets the following parameters:

            - *beta max:* Starting beta value
            - *beta min:* Final beta value before the algorithm quits (if target misfit not attained)
            - *reduction factor:* a multiplicative constant between (0,1). Sets how much beta is reduced at each iteration

    - **Chi Factor:** Sets the target data misfit for the inversion. A chi-factor of 1 (default value) implies the data misfit is equal to the total number of data observations.

    - **Weighting constants:** Sets the weights for smallness and smoothness regularization in x, y and z; see :ref:`fundamentals of inversion <Fundamentals_alphas>`.

        - **Default:** Sets the values of *alpha S*, *alpha E*, *alpha N* and *alpha Z* based on cell dimensions
        - **Alphas:** Sets specific values for *alpha S*, *alpha E*, *alpha N* and *alpha Z*
        - **Lengths:** User sets values *Len E*, *Len N* and *Len Z* which define the values of *alpha X*, *alpha Y* and *alpha Z* relative to *alpha S*. These relationships are given by :math:`L_E = \sqrt{\frac{\alpha_E}{\alpha_S}}`, :math:`L_N = \sqrt{\frac{\alpha_N}{\alpha_S}}` and :math:`L_Z = \sqrt{\frac{\alpha_Z}{\alpha_S}}`.

    - **Cell and interface weights:** Here, the user may specify the implementation of cell and/or face weighting; see :ref:`fundamentals of inversion <Fundamentals_WeightingMatrix>`. In this case, the user selects a *GIFweight* object that is defined on the OcTree mesh.

    - **Independent smallness weights:** Standard cell weights are applied in both the smallness and smoothness terms. This functionality allows the user to include independent cell weights only to the smallness term. The user will choose a *GIFweight* object whose cell weights are to be applied. If you have a *GIFmodel* that you would like to use as independent smallness weights, first :ref:`use octree mesh to create weights object <objectMeshCreateWeights>`, then click the newly created *GIFweights* object and use :ref:`set model <objectWeightsObjects_setModel>`.

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


Advanced Parameters
-------------------
    
    - **Newton iteration settings:** Sets stopping criteria for Gauss-Newton iterations; see `DCIPoctree manual <https://dcipoctree.readthedocs.io/en/latest/content/theory.html#chart>`__ . Parameters are:

        - **tol_nl:** stopping criteria based on gradient size (defaul = 0.01)
        - **mindm:** stopping criteria based on size of model perturbation (default = 0.001)
        - **iter_per_beta:** maximum number of Gauss-Newton iterations (default = 3)

    - **IPCG settings:** Sets tolerances for solving the system at each Gauss-Newton iteration using incomplete preconditioned conjugate gradient; see `DCIPoctree manual <https://dcipoctree.readthedocs.io/en/latest/content/theory.html#chart>`__ . Parameters are:

        - **tol_ipcg:** relative tolerance for solution (default = 0.01)
        - **max_iter_ipcg:** maximum number of IPCG iterations (20)
