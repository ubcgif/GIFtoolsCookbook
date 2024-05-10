.. _objectEMDataIndex:

EM Data
=======


    .. toctree::
        :maxdepth: 2

        dataType
        dataManipulation



There are 6 main types of EM data that can be created in GIFtools.

- :ref:`FEM1Dsounding and TEM1Dsounding <objectEMDataIndex_EM1Dsounding>`
- :ref:`FEMdata <objectEMDataIndex_FEMdata>`
- :ref:`TEMdata <objectEMDataIndex_TEMdata>`
- :ref:`FEM3Dsounding <objectEMDataIndex_FEM3Dsounding>`
- :ref:`TEM3Dsounding <objectEMDataIndex_TEM3Dsounding>`

.. _objectEMDataIndex_FEMdata:

FEMdata
-------

For the ``FEMdata`` class, we assume the receivers measure the E and/or H-field along the Cartesian directions.
Transmitters associated with this data class can be:

    - magnetic dipoles
    - large-loop inductive sources
    - galvanic sources

The ``FEMdata`` is used in conjunction with the following codes:

    - `E3Dv1 <https://e3d.readthedocs.io/en/e3dinv/content/files/obsFile.html#observations-file>`_


.. _objectEMDataIndex_TEMdata:

TEMdata
-------

For the ``TEMdata`` class, we assume the receivers measure E, H or dB/dt along the Cartesian directions.
Transmitters associated with this data class can be:

    - magnetic dipoles
    - large-loop inductive sources
    - galvanic sources

The ``TEMdata`` is used in conjunction with the following codes:

    - `H3DTD <https://gif.eos.ubc.ca/sites/default/files/sdevriese/files/H3DTDinv_manual_v_1_2.pdf>`_
    - `TDoctree v1 <https://tdoctree.readthedocs.io/en/tdoctree_ver1/>`_


.. _objectEMDataIndex_EM1Dsounding:

FEM1Dsounding and TEM1Dsounding
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For the ``FEM1Dsounding`` and ``TEM1Dsounding`` classes, parameters describing both the transmitter and receiver are
required and used in the forward and inverse problems. This is the most
general format. It allows to easily store airborne data collected from
transmitters and receivers of arbitrary shapes and orientations.

For ``FEM1Dsounding`` and ``FEM1Dsounding`` objects, transmitters can either be defined as a ``dipole``
or ``loop`` source. The position of the receiver is set **relative to the
transmitter locations**. The following parameters are required:

    - **Along-line offset:** The along-line position of receivers, **relative to transmitter locations**
    - **Cross-line offset:** The cross-line position of receivers, **relative to transmitter locations**
    - **Vertical offset:** The vertical location of the receivers relative to the surface
    - **Dipole Moment:** Uses a right-handed **positive down** coordinate system

The ``FEM1Dsouding`` data class isused for:

    - `EM1DFM inversion <https://em1dfm.readthedocs.io/en/latest/#em1dfm-package>`_,

And the ``FEM1Dsounding`` data class is used for:

    - `EM1DTM inversion <https://em1dtm.readthedocs.io/en/latest/#em1dtm-package>`_



.. _objectEMDataIndex_FEM3Dsounding:

FEM3Dsounding
^^^^^^^^^^^^^

For ``FEM3Dsounding`` objects, the receivers measure either the E **or** H-field along the direction specified by the receiver.
Although each datum is associated with a location, the user must define the transmitters and receivers explicitly. For this data
object:

    - inductive sources and H-field receivers are defined using closed loops
    - galvanic sources and E-field receivers are defined when we do not close the loop

This data class is use for:

    - `E3Dv2 <https://e3d.readthedocs.io>`_
    - `E3Dv2 tiled <https://e3d.readthedocs.io/en/e3dinv_ver2_tiled>`_


.. _objectEMDataIndex_TEM3Dsounding:

TEM3Dsounding
^^^^^^^^^^^^^

For ``TEM3Dsounding`` objects, the receivers measure either E, H **or** dB/dt along the direction specified by the receiver.
Although each datum is associated with a location, the user must define the transmitters and receivers explicitly. For this data
object:

    - inductive sources, H-field receivers and dB/dt receivers are defined using closed loops
    - galvanic sources and E-field receivers are defined when we do not close the loop

This data class is use for:

    - `TDoctree v2 <https://tdoctree.readthedocs.io/en/tdoctree_ver2/>`_
    - `TDRH v2 <https://tdrh.readthedocs.io/en/tdrh_v2/>`_








