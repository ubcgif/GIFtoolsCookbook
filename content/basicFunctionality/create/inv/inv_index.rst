.. _createInv:

.. include:: <isonum.txt>

Create an inversion
===================

.. figure:: ../../../../images/createInv.png
    :align: center
    :width: 400

.. _createMagInv:

Create a mag inversion
----------------------

There are four different inversion objects that can be created to invert magnetic data using a 3D mesh. The first three are using the program ``MAG3D`` with version control (5.0, 5.1, 6.0). The fourth is a magnetic-vector inversion using the program ``MVI``. To use an octree mesh, the code ``OCTMAGDE`` can be used. The menus needed to create these are:

**Create** |rarr| **Inversion** |rarr| **Magnetics** |rarr| **Induced (MAG3D 5.0)**

**Create** |rarr| **Inversion** |rarr| **Magnetics** |rarr| **Induced (MAG3D 5.1)**

**Create** |rarr| **Inversion** |rarr| **Magnetics** |rarr| **Induced/amplitude (MAG3D 6.0)**

**Create** |rarr| **Inversion** |rarr| **Magnetics** |rarr| **MVI (magnetic vector)**

**Create** |rarr| **Inversion** |rarr| **Magnetics** |rarr| **PDE (octree)**


**NOTE**: GIFtools inversion objects will take care of the prerequisite weighting and sensitivity programs prior to inversion for the user.


.. _createGravInv:

Create a gravity inversion
--------------------------

There are three different inversion objects that can be created to invert gravity data using a 3D mesh. These objects use the program package ``GRAV3D`` with version control (5.0, 5.1, and 6.0). The menus needed to create these are:

**Create** |rarr| **Inversion** |rarr| **Gravity** |rarr| **GRAV3D 5.0**

**Create** |rarr| **Inversion** |rarr| **Gravity** |rarr| **GRAV3D 5.1**

**Create** |rarr| **Inversion** |rarr| **Gravity** |rarr| **GRAV3D 6.0**

**Create** |rarr| **Inversion** |rarr| **Gravity** |rarr| **PDE (octree)**

**NOTE**: GIFtools inversion objects will take care of the prerequisite weighting and sensitivity programs prior to inversion for the user.


.. _createGGInv:

Create a gravity graviometry inversion
--------------------------------------

Gravity gradiometry data can be inverted using a 3D mesh using the code ``GG3D``. The menu needed to create such an item is:

**Create** |rarr| **Inversion** |rarr| **Gravity gradiometry** |rarr| **GG3D**

**NOTE**: GIFtools inversion objects will take care of the prerequisite weighting and sensitivity programs prior to inversion for the user.


.. _createDCIPInv:

Create a DC/IP inversion
------------------------

DC/IP data can be inverted using a 2D mesh, 3D mesh, and an octree mesh. All of these can be accessed through the menu for DC/IP:

.. figure:: ../../../../images/createInv.png
    :align: center
    :width: 400


2D DC/IP
^^^^^^^^

To create a DC/IP 2D inversion using the software package ``DCIP2D``, use the menu structure:

- DC: **Create** |rarr| **Inversion** |rarr| **DC/IP** |rarr| **2D DC**

- IP: **Create** |rarr| **Inversion** |rarr| **DC/IP** |rarr| **2D IP**

To set the parameters for the inversion, see :ref:`edit options <invEditOptions_dcip2d>`.


3D DC/IP
^^^^^^^^

To create a DC/IP 3D inversion using the software package ``DCIP3D``, use the menu structure:

- DC: **Create** |rarr| **Inversion** |rarr| **DC/IP** |rarr| **3D DC**

- IP: **Create** |rarr| **Inversion** |rarr| **DC/IP** |rarr| **3D IP**

To set the parameters for the inversion, see :ref:`edit options <invEditOptions_dcip3d>`.


Octree DC/IP
^^^^^^^^^^^^

To create a DC/IP octree inversion using the software package ``DCIPoctree``, use the menu structure:

- DC: **Create** |rarr| **Inversion** |rarr| **DC/IP** |rarr| **Octree DC**

- IP: **Create** |rarr| **Inversion** |rarr| **DC/IP** |rarr| **Octree IP**

To set the parameters for the inversion, see :ref:`edit options <invEditOptions_dcipoctree>`.


.. _createFEMInv:

Create an FEM data inversion
----------------------------

Frequency-domain EM (FEM) data can be inverted through the program ``E3D``, which requires an :ref:`ocTree mesh <meshOctreefile>`. To create the inversion object, use the menu structure:

**Create** |rarr| **Inversion** |rarr| **Frequency-domain EM** |rarr| **E3D (octree)**

**Create** |rarr| **Inversion** |rarr| **Frequency-domain EM** |rarr| **EM1DFM (1D)**


.. _createTEMInv:

Create an TEM data inversion
----------------------------

Time-domain EM data, such as airborne TEM, surface/borehole UTEM, TEMSAM data can be inverted using a multitude of executables. To create the inversion objects, use the menu structure:

**Create** |rarr| **Inversion** |rarr| **Time-domain EM** |rarr| **H3DTD ver 1 (tensor)**

**Create** |rarr| **Inversion** |rarr| **Time-domain EM** |rarr| **H3DTD ver 2 (tensor)**

**Create** |rarr| **Inversion** |rarr| **Time-domain EM** |rarr| **TDoctree (octree)**

**Create** |rarr| **Inversion** |rarr| **Time-domain EM** |rarr| **TDoctree tiled (octree)**

**Create** |rarr| **Inversion** |rarr| **Time-domain EM** |rarr| **TDoctree v2 (octree)**

**Create** |rarr| **Inversion** |rarr| **Time-domain EM** |rarr| **TDRH v2 (octree)**


.. _createMTZTEMInv:

Create a natural-source EM inversion
------------------------------------

Natural-source EM data, such as ZTEM or MT data can be inverted using ``MTZ3D``, ``E3DMT ver 1`` or ``E3DMT ver 2``. To create the inversion objects, use the menu structure:

**Create** |rarr| **Inversion** |rarr| **Natural-source EM** |rarr| **MTZ3D (tensor)**

**Create** |rarr| **Inversion** |rarr| **Natural-source EM** |rarr| **E3DMT ver 1 (octree)**

**Create** |rarr| **Inversion** |rarr| **Natural-source EM** |rarr| **E3DMT ver 2 (octree)**



























