.. _importWeights:

.. include:: <isonum.txt>

Import weights
==============

Under **Import** |rarr| **Weights**, the user can import cell and face weights used to control the inversion.
See the :ref:`Fundamentals of inversion <Fundamentals_WeightingMatrix>` for more details about the role of weighting matrices.

.. figure:: ../../../images/importMesh.png
    :align: center
    :width: 400

.. _importAllWeights:

Import full weights file
------------------------



**Import** |rarr| **Weights** |rarr| **Full weight file**




.. _importFaceWeights:

Import only face weights
------------------------



**Import** |rarr| **Weights** |rarr| **Only faces**


.. _importSensWeights:

Import Sensitivity as Weights
-----------------------------

**Import** |rarr| **Weights** |rarr| **Sensitivity as weights**

This option allows to create :ref:`cell and face weights <Fundamentals_WeightingMatrix>` based on the ``sensitivity.txt`` file generated for example by ``DCINV2D`` and ``DCINV3D``.

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

