.. _signConvention:

Coordinates, Sign Conventions and Units: A Quick Guide
======================================================

Here we provide a quick guide for the following:

    - :ref:`Coordinates for data locations<sign_coord>`
    - :ref:`Types and sign conventions for data<sign_conv>`
    - :ref:`Units for physical properties and data<sign_units>`

Some codes may have internal coordinate systems. These details are not important here. This section is focused on the data that are read and output by each code.



.. _sign_coord:

Coordinates for Data Locations
------------------------------

Here, we define the coordinate systems for data points for each code. In general X is Easting, Y is Northing and Z is +ve up. The 1D codes are an exception; where -ve Z locations refer to positions above ground and the coordinate system is left-handed. Certain codes may use a different coordinate system internally. However, the majority of users will not need to worry about this. Certain codes may use unique :ref:`data conventions <sign_conv>`. The users **should** worry about this.




+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|  Type  |  Name     |  Versions   |Easting|Northing|Z +ve| Details                         |
+========+===========+=============+=======+========+=====+=================================+
|GUI     |GIFtools   |   All       |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|Gravity |GRAV3D     |5.0, 5.1, 6.0|   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|Gravity |GRAV PDE   |octree       |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|Magnetic|MAG3D      |5.0, 5.1, 6.0|   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|Magnetic|MAG PDE    |octree       |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|MVI     |MVI        | 3.0         |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|DC/IP   |DCIP2D     |  3.1, 5.0   |   X   |  N/A   | up  | :ref:`details <sign_dcip_coord>`|
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|DC/IP   |DCIP3D     |             |   X   |    Y   | up  | :ref:`details <sign_dcip_coord>`|
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|DC/IP   |DCIPoctree |octree       |   X   |    Y   | up  | :ref:`details <sign_dcip_coord>`|
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|FDEM    |EM1DFM     | 1.0         |   X   |    Y   |down | :ref:`details <sign_em1d_coord>`|
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|FDEM    |EH3D       |             |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|FDEM    |E3D        |octree       |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|TDEM    |EM1DTM     | 1.0         |   X   |   Y    |down | :ref:`details <sign_em1d_coord>`|
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|TDEM    |H3DTD      |             |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|TDEM    |TDoctree   |octree       |   X   |   Y    | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|MT/ZTEM |MTZ3D      |             |   X   |    Y   | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|MT/ZTEM |E3DMT      |1 (2014,2015)|   X   |   Y    | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+
|MT/ZTEM |E3DMT      |2 (2017)     |   X   |   Y    | up  |                                 |
+--------+-----------+-------------+-------+--------+-----+---------------------------------+

.. .. note::
..    - Potential fields should be pretty straight forward
..    - Example data files for DCIP2D, DCIP3D and DCIPoctree show borehole data as having -ve Z locations. Thus we believe it is right-handed with Z +ve up. **However**, the z location may be defined as a distance relative to the top of the mesh. Details need to be hashed out
..    - There is no indication that any CSEM codes (other than 1D codes) are in a coordinate system other than X (easting), Y (northing) and Z (+ve up). Example data files in manuals put Z locations as positive numbers.


.. _sign_dcip_coord:

DCIP details
~~~~~~~~~~~~

 PENDING



.. _sign_em1d_coord:

EM1DFM and EM1DTM details
~~~~~~~~~~~~~~~~~~~~~~~~~

The EM1DFM and EM1DTM codes read and write data files where X is Easting, Y is Northing and Z is +ve downward. Thus Z = -5 m indicates the observation location is 5 m above the surface; even if the surface is not at an elevation equal to 0 m. When loaded into GIFtools (Z +ve upwards), the Z values are automatically transformed into the correct elevation values. If EM1DFM or EM1DTM data are modeled from the GIFtools GUI in a scenario where there is surface topography, the resulting Z (elevation) values in GIFtools will take surface topography into account.



.. _sign_conv:

GIF Data Sign Conventions and Time-Dependency
---------------------------------------------

Here, we define the sign conventions for various data types and the :ref:`time-dependence for frequency domain codes <sign_time_conv>`. If data are not formatted using the proper convention, it is unlikely that the inversion will be able to fit the data and return meaningful results.

.. important:: Make sure you scroll all the way to the right within the table to see all information pertaining to a particular code.




+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|  Type  |  Name     |  Versions   |         Sign Convention                                                                                                             |
+========+===========+=============+=====================================================================================================================================+
|Gravity |GRAV3D     |5.0, 5.1, 6.0| +ve data represents +ve gravity anomalies                                                                                           |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|Gravity |GRAV PDE   |octree       | +ve data represents +ve gravity anomalies                                                                                           |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|Magnetic|MAG3D      |5.0, 5.1, 6.0| +ve data represents +ve magnetic anomalies (:ref:`details<sign_mag_conv>`)                                                          |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|Magnetic|MAG PDE    |octree       | +ve data represents +ve magnetic anomalies (:ref:`details<sign_mag_conv>`)                                                          |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|MVI     |MVI        | 3.0         | +ve data represents +ve magnetic anomalies (:ref:`details<sign_mag_conv>`)                                                          |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|DC/IP   |2D DCIP    |             |:math:`\mathbf{E}=-\nabla V` and :math:`\Delta V = V_N - V_M` (:ref:`details<sign_dcip_conv>`)                                       |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|DC/IP   |3D DCIP    |             |:math:`\mathbf{E}=-\nabla V` and :math:`\Delta V = V_N - V_M` (:ref:`details<sign_dcip_conv>`)                                       |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|DC/IP   |DCIP octree|octree       |:math:`\mathbf{E}=-\nabla V` and :math:`\Delta V = V_N - V_M` (:ref:`details<sign_dcip_conv>`)                                       |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Time-dependency is :math:`+i\omega t` (:ref:`details<sign_time_conv>`)                                                            |
|FDEM    |EM1DFM     | 1.0         | - Hx, Hy, Hz with Z-axis pointing downward (:ref:`details<sign_em1dfm_conv>`)                                                       |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Time-dependency is :math:`-i\omega t` (:ref:`details<sign_time_conv>`)                                                            |
|FDEM    |EH3D       |             | - Hx, Hy, Hz with z-axis pointing upwards                                                                                           |
|        |           |             | - Ex, Ey, Ez with z-axis pointing upwards                                                                                           |
|        |           |             | - Jx, Jy, Jz with z-axis pointing upwards                                                                                           |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Time-dependency is :math:`+i\omega t` (:ref:`details<sign_time_conv>`)                                                            |
|FDEM    |E3D        |octree       |                                                                                                                                     |
|        |           |             |                                                                                                                                     |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - H: Dot product of :math:`\mathbf{H}` and the direction defined by the receiver's dipole moment (:ref:`details<sign_em1dtm_conv>`) |
|TDEM    |EM1DTM     |1.0          | - dB/dt: Corresponding voltage induced in the receiver coil (:ref:`details<sign_em1dtm_conv>`)                                      |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Hx, Hy, Hz with Z-axis pointing upward                                                                                            |
|TDEM    |H3DTD      |             | - dBx/dt, dBy/dt, **-** dBz/dt with Z-axis pointing upward (:ref:`details<sign_tdem_conv>`)                                         |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Hx, Hy, Hz with z-axis pointing upward                                                                                            |
|TDEM    |TDoctree   |octree       | - dBx/dt, dBy/dt, -dBz/dt with Z-axis pointing upward (:ref:`details<sign_tdem_conv>`)                                              |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Time-dependency is :math:`-i\omega t`                                                                                             |
|MT/ZTEM |MTZ3D      |             | - The data convention has X = Northing, Y = Easting and Z = Down.                                                                   |
|        |           |             | - :ref:`MT details<sign_mt_conv>`, :ref:`ZTEM details<sign_ztem_conv>`                                                              |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Time-dependency is :math:`-i\omega t`                                                                                             |
|MT/ZTEM |E3DMT      |octree ver. 1| - The data convention has X = Northing, Y = Easting and Z = Down.                                                                   |
|        |           |             | - :ref:`MT details<sign_mt_conv>`, :ref:`ZTEM details<sign_ztem_conv>`                                                              |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+
|        |           |             | - Time-dependency is :math:`-i\omega t`                                                                                             |
|MT/ZTEM |E3DMT      |octree ver. 2| - The data convention has X = Northing, Y = Easting and Z = Down.                                                                   |
|        |           |             | - :ref:`MT details<sign_mt_conv>`, :ref:`ZTEM details<sign_ztem_conv>`                                                              |
+--------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------+


.. .. note::
..     - Time-dependency for FDEM codes was inferred from the initial formulation of Maxwell`s equations in the theory sections for each available manual; :math:`\nabla \times E = \mp i\omega B \rightarrow \pm i\omega t` convention. Exceptions: E3DMT ver 2 can be either. EM1DFM explicitly states a dependency of :math:`+i\omega t`.
..     - The theoretical background for DCIP2D, DCIP3D and DCIPoctree seem to indicate a :math:`E =-\nabla V` formulation base on the final expression :math:`\nabla \cdot \sigma \nabla V = \nabla \cdot J_s=-I \delta (r)`.
..     - Sign conventions for TDEM data were inferred from looking at an example TDoctree data file showing the response over a conductor. The positive decaying Hz and positive decaying dBz/dt indicated that the sign of the dBz/dt data were flipped. This was not the case for dBx/dt and dBy/dt. It is assumed that the same convention is used for H3DTD but I'm not sure. EM3DTM is explicitly stated however.
..     - Sign conventions for FDEM data (except EM1DFM) are a mystery right now
..     - Sign conventions for MTZTEM data are a mystery right now.



.. _sign_time_conv:

Time-dependency (Fourier convention)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The relationship between a time-dependent function :math:`f(t)` and its corresponding frequency response :math:`F(i \omega`) is given by the inverse Fourier transform:

.. math::
    f(t) = \mathbb{F}^{-1} \big [ F(i \omega) \big ] = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} F(i \omega) e^{\boldsymbol{\pm i\omega t}} d \omega.

where the choice in sign of :math:`\pm i\omega t` defines the Fourier convention. The choice in Fourier convention ultimately affects the phase relationship between real and imaginary components of :math:`F(i \omega)` and how Maxwell's equations are represented in the frequency (Fourier) domain. To demonstrate this, let us first show Maxwell's equations in the time domain:

.. math::
    \begin{align}
    \nabla \times \mathbf{e} &= - \frac{\partial \mathbf{b}}{\partial t} \\
    \nabla \times \mathbf{h} &= \mathbf{j} + \frac{\partial \mathbf{d}}{\partial t}
    \end{align}

- **Using** :math:`\boldsymbol{+i \omega t}` **convention:** If the inverse Fourier transform is defined using :math:`+ i\omega t`, then

.. math::
    \mathbb{F} \bigg [ \frac{d}{dt} f(t) \bigg ] = i\omega F (i \omega )

and Maxwell's equations in the frequency domain are:

.. math::
    \begin{align}
    \nabla \times \mathbf{E} &= - i\omega \mathbf{B} \\
    \nabla \times \mathbf{H} &= \mathbf{J} + i\omega \mathbf{D}
    \end{align}

where :math:`e^{+i\omega t}` is suppressed.

**Using** :math:`\boldsymbol{-i \omega t}` **convention:** If inverse Fourier transform is defined using :math:`- i\omega t`, then

.. math::
    \mathbb{F} \bigg [ \frac{d}{dt} f(t) \bigg ] = -i\omega F (i \omega )

and Maxwell's equations in the frequency domain are:

.. math::
    \begin{align}
    \nabla \times \mathbf{E} &= i\omega \mathbf{B} \\
    \nabla \times \mathbf{H} &= \mathbf{J} - i\omega \mathbf{D}
    \end{align}

where :math:`e^{-i\omega t}` is suppressed.

As we can see, the phase relationship between :math:`\mathbf{E}` and :math:`\mathbf{B}` in Faraday's law is different for each convention; similarly for :math:`\mathbf{H}` and :math:`\mathbf{D}` in the Ampere-Maxwell law. Thus it is important to know which convention is being used when examining the electric and magnetic fields for a particular FDEM code.

.. _sign_mag_conv:

Magnetics
~~~~~~~~~

**Total magnetic intensity data:**

For total magnetic intensity (TMI) data, the sign of the data is more or less determined by whether the secondary magnetic field has components parallel or anti-parallel to the Earth's inducing field; where the Earth's inducing field can be at a variety of orientations depending on latitude and regional variations. In this case, a positive data value generally indicates that the secondary magnetic field has vector components parallel to the Earth's inducing field; i.e. it 'adds to' the inducing field. In contrast, a negative data value indicates that components of the secondary field are anti-parallel, or 'oppose', the Earth's inducing field.

**Amplitude data:**

For amplitude data, a positive value indicates that the magnitude of the total observed magnetic field (:math:`\mathbf{B_p + B_s}`) is larger than the Earth's inducing field (:math:`\mathbf{B_p}`); i.e. :math:`| \mathbf{B_p + B_s} | > |\mathbf{B_p} |`. The opposite is true for negative data values.


.. _sign_dcip_conv:

DCIP data
~~~~~~~~~

In the electrostatic case, the Ampere-Maxwell equation shows that :math:`\nabla \times \mathbf{E} = 0` and that :math:`\mathbf{E}` can be written as the gradient of a scalar potential:

.. math::
    \mathbf{E} = \pm \nabla V.

By taking the divergence of Faraday`s law and substituting the previous expression, the DC resistivity problem is ultimately defined by the following expression:

.. math::

    - \nabla \cdot \sigma (\pm \nabla V) = \nabla \cdot \mathbf{j_e}

As we can see, our choice in the relationship between :math:`\mathbf{E}` and :math:`V` changes the sign convention for the voltage measurements. In the case of UBC GIF codes, we choose :math:`\mathbf{E} = - \nabla V`. By this convention, 1) secondary potentials are positive in the vicinity of positive electric charges and negative in the vicinity of negative electric charges, and 2) positive potentials are observed near current sources and negative potentials are observed near current sinks.


.. _sign_em1dfm_conv:

EM1DFM data
~~~~~~~~~~~

The EM1DFM code models data for a small loop transmitter with dipole moment in the X (Easting), Y (Northing) or Z (downward) direction, and receiver coils with dipole moments in the X (Easting), Y (Northing) or Z (downward) direction. Thus a Z oriented transmitter will have a primary field which points downwards. And positive Hz values indicate fields with vertical components pointing downward. In X and Y however, the primary field and observed field components are in the Easting and Northing directions, respectively. If working outside the GIFtools framework, it is important to realize that transmitters, receivers and data are defined in a left-handed coordinate system with Z +ve downward.

In GIFtools, we define transmitters and receiver for the 1D codes in the X (Easting), Y (Northing) and Z (upward) directions. So long as the appropriate sign change is applied, the EM1DFM code can be used to model data for transmitters and receivers defined within GIFtools. Therefore, the appropriate sign change is automatically applied to EM1DFM data when loaded into/exported from GIFtools.


.. _sign_em1dtm_conv:

EM1DTM data
~~~~~~~~~~~

PENDING**



.. _sign_tdem_conv:

H3DTD and TDoctree data
~~~~~~~~~~~~~~~~~~~~~~~

For most of the data columns (Hx, Hy, Hz, dBx/dt, dBy/dt), the data represent the true anomalous field components in the coordinate system that defines the data locations; i,e, X (Easting). Y (Northing) and Z (upwards). However, these codes represent the time-derivative of the vertical component as -dBz/dt.

The sign convention for dBz/dt data can be explained as follows. For coincident loop airborne systems, the true dBz/dt response observed at the center of the receiver coil is typically negative and decaying during the off-time. However, the decay curves for this component have historically been plotted as positive and decaying. This is done for two reasons. 1) A positive decay curve is analogous to the strength of a decaying inductive response. 2) The raw voltage induced within the receiver coil is in fact positive and decaying. This is because the induced EMF is proportional to -dB/dt. When people first plotted the raw voltages for this component, it was positive and decaying and the convention for plotting dBz/dt data was born.

.. _sign_mt_conv:

MT data
~~~~~~~

**Fourier Convention**

The NSEM GIF codes are formulated to use a :math:`-i\omega t` convention for the time-dependence. However, this may not match the convention used by data loaded into GIFtools from other sources. MT data loaded from EDI files generally uses the `MT/EMAP data interchange standard <https://seg.org/Portals/0/SEG/News%20and%20Resources/Technical%20Standards/seg_mt_emap_1987.pdf>`__ , which is :math:`+i\omega t`. If the convention used for the data does not match that of the code, it is unlikely that the inversion will be able to fit the data and return meaningful results.

We can determine the convention used by the data by examining the data. If data are represented using the :math:`\boldsymbol{+i \omega t}` convention and are in a right-handed coordinate system, then we expect:

    - at background locations: :math:`Z_{xy} \sim \dfrac{i \omega \mu}{k} \;\;\; \textrm{and} \;\;\; Z_{yx} \sim \frac{- i \omega \mu}{k} \;\;\; \textrm{where} \;\;\; k = \sqrt{i\omega \mu \sigma}`
    - :math:`Re[Z_{xy}] > 0`, :math:`\; Im[Z_{xy}] > 0` and :math:`\phi_{xy} \in [0^o, \; 90^o]` (:math:`\sim 45^o` for a half-space)
    - :math:`Re[Z_{yx}] < 0`, :math:`\; Im[Z_{yx}] < 0` and :math:`\phi_{yx} \in [-90^o, \; -180^o]` (:math:`\sim -135^o` for a half-space)

If data are represented using the :math:`\boldsymbol{-i \omega t}` convention (GIFtools) and are in a right-handed coordinate system (GIFtools), then for these data we expect:

    - at background locations: :math:`Z_{xy} \sim \dfrac{-i \omega \mu}{k} \;\;\; \textrm{and} \;\;\; Z_{yx} \sim \frac{ i \omega \mu}{k} \;\;\; \textrm{where} \;\;\; k = \sqrt{-i\omega \mu \sigma}`
    - :math:`Re[Z_{xy}] > 0`, :math:`\; Im[Z_{xy}] < 0` and :math:`\phi_{xy} \in [0^o, \; -90^o]` (:math:`\sim -45^o` for a half-space)
    - :math:`Re[Z_{yx}] < 0`, :math:`\; Im[Z_{yx}] > 0` and :math:`\phi_{yx} \in [90^o, \; 180^o]` (:math:`\sim 135^o` for a half-space)

As we can see, to switch from one convention to another we must:

    - Multiply the imaginary components of all impedance tensor elements by -1
    - Multiply the phase values for all elements of the impedance tensor by -1

**Data Convention**

MT data represent the entries of the impedance tensor (:math:`\mathbf{Z}`) where:

.. math::
    \begin{bmatrix} Z_{xx} & Z_{xy} \\ Z_{yx} & Z_{yy} \end{bmatrix} =
    \begin{bmatrix} E_{x}^{(1)} & E_{x}^{(2)} \\ E_{y}^{(1)} & E_{y}^{(2)} \end{bmatrix}
    \begin{bmatrix} H_{x}^{(1)} & H_{x}^{(2)} \\ H_{y}^{(1)} & H_{y}^{(2)} \end{bmatrix}^{-1}


MT data for GIF codes uses a labeling convention where X = Northing, Y = Easting and Z = Down. Superscript (1) denotes fields resulting from plane waves with electric fields polarized along the X (Northing) direction, and (2) denotes fields resulting from plane waves with with electric fields polarized along the Y (Easting) direction. The labeling of the impedance tensor elements is given by:

	- :math:`Z_{xx}` is Z-Northing-Northing
	- :math:`Z_{xy}` is Z-Northing-Easting
	- :math:`Z_{yx}` is Z-Easting-Northing
	- :math:`Z_{yy}` is Z-Easting-Easting

For more on this, see the `E3DMT manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#natural-sources-mt-and-ztem>`__


.. _sign_ztem_conv:

ZTEM data
~~~~~~~~~

**Data Convention**

ZTEM data represent transfer functions :math:`\mathbf{T_{zx}}` and :math:`\mathbf{T_{zy}}` where:

.. math::
    \begin{bmatrix} T_{zx} \\ T_{zy} \end{bmatrix} = \big ( H_x^{(1)} H_y^{(2)} - H_x^{(2)} H_y^{(1)} \big )^{-1}
    \begin{bmatrix} - H_y^{(1)} H_z^{(2)} + H_y^{(2)} H_z^{(1)} \\ H_x^{(1)} H_z^{(2)} - H_x^{(2)} H_z^{(1)} \end{bmatrix}


ZTEM data for GIF codes uses a labeling convention where X = Northing, Y = Easting and Z = Down. Superscript (1) denotes fields resulting from plane waves with electric fields polarized along the X (Northing) direction, and (2) denotes fields resulting from plane waves with with electric fields polarized along the Y (Easting) direction. The labeling of field elements is such that:

	- :math:`H_{x}` is the component of the magnetic field along the Northing direction
	- :math:`H_{y}` is the component of the magnetic field along the Easting direction
	- :math:`H_{z}` is the component of the magnetic field in the down direction

For more on this, see the `E3DMT manual <https://e3dmt.readthedocs.io/en/manual_ver1/content/theory.html#natural-sources-mt-and-ztem>`__


.. _sign_units:

Units
-----

Here, we define the physical property and data units used by each code.

**Physical Property Definitions:**

    - :math:`\boldsymbol{\rho :}` density
    - :math:`\boldsymbol{\kappa :}` susceptibility or effective susceptibility
    - :math:`\boldsymbol{\sigma :}` conductivity
    - :math:`\boldsymbol{\eta :}` Intrinsic chargeability. If linear approximation is chosen, any convention of intrinsic or integrated chargeability is acceptable. However, it will change the units of the corresponding data.

**Fields and Data Types:**

    - :math:`\mathbf{E}:` Electric field
    - :math:`\mathbf{J}:` Current density
    - :math:`\mathbf{H}:` Magnetic field intensity (auxiliary field)
    - :math:`\mathbf{B}:` Magnetic flux density
    - :math:`\partial \mathbf{B}/\partial t:` Time-derivative of the magnetic flux density
    - :math:`Z_{ij}:` The ij-th element of the impedance tensor
    - :math:`T_i:` The x or y component of the ZTEM transfer function


**Units Definitions:**

    - :math:`mGal:` milliGal
    - :math:`T:` Teslas
    - :math:`S:` Siemens
    - :math:`V:` Volts
    - :math:`A:` Amperes
    - :math:`ppm:` parts per million



.. important:: Make sure you scroll all the way to the right within the table to see all information pertaining to a particular code.




+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|  Type  |  Name     |  Versions   |     Property Units                    | Data Units                                                           |
+========+===========+=============+=======================================+======================================================================+
|Gravity |GRAV3D     |5.0, 5.1, 6.0|:math:`\rho = g/cm^3`                  | mGal                                                                 |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|Gravity |GRAV PDE   |octree       |:math:`\rho = g/cm^3`                  | mGal                                                                 |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|Magnetic|MAG3D      |5.0, 5.1, 6.0|:math:`\kappa = SI`                    | nT                                                                   |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|Magnetic|MAG PDE    |octree       |:math:`\kappa = SI`                    | nT                                                                   |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|MVI     |MVI        | 3.0         |:math:`\kappa = SI`                    | nT                                                                   |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - V/A for DC data (:ref:`details<sign_ip_units>`)                    |
|DC/IP   |2D DCIP    |             |- :math:`\eta \in [0,1]` or other      | - V/A and other for IP data (:ref:`details<sign_ip_units>`)          |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - V/A for DC data (:ref:`details<sign_ip_units>`)                    |
|DC/IP   |3D DCIP    |             |- :math:`\eta \in [0,1]` or other      | - V/A and other for IP data (:ref:`details<sign_ip_units>`)          |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |octree       |- :math:`\sigma = S/m`                 | - V/A for DC data (:ref:`details<sign_ip_units>`)                    |
|DC/IP   |DCIP octree|             |- :math:`\eta \in [0,1]` or other      | - V/A and other for IP data (:ref:`details<sign_ip_units>`)          |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - A/m                                                                |
|FDEM    |EM1DFM     | 1.0         |- :math:`\kappa = SI`                  | - ppm of primary field                                               |
|        |           |             |- :math:`\sigma = S/m`                 | - % of primary field                                                 |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - E: V/m                                                             |
|FDEM    |EH3D       |             |- :math:`\kappa = SI` (background only)| - H: A/m                                                             |
|        |           |             |                                       | - J: A/m :math:`\! ^2`                                               |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - E: V/m                                                             |
|FDEM    |E3D        |octree       |- :math:`\kappa = SI` (background only)| - H: A/m                                                             |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|TDEM    |EM1DTM     |1.0          |:math:`\sigma = S/m`                   | - B: nT, :math:`\mu\!` T or nT                                       |
|        |           |             |                                       | - dB/dt: :math:`\mu\!` V, mV or V (:ref:`details<sign_em1dtm_units>`)|
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - E: V/m                                                             |
|TDEM    |H3DTD      |             |- :math:`\kappa = SI` (background only)| - H: A/m                                                             |
|        |           |             |                                       | - dB/dt: T/s                                                         |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - H: A/m                                                             |
|TDEM    |TDoctree   |octree       |- :math:`\kappa = SI` (background only)| - dB/dt: T/s                                                         |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - :math:`Z_{ij}:` V/A (:ref:`details<sign_mt_units>`)                |
|MT/ZTEM |MTZ3D      |             |- :math:`\kappa = SI` (background only)| - :math:`T_i:` unitless (:ref:`details<sign_ztem_units>`)            |
|        |           |             |                                       | - E: V/m (if option chosen to output)                                |
|        |           |             |                                       | - H: A/m (if option chosen to output)                                |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - :math:`Z_{ij}:` V/A (:ref:`details<sign_mt_units>`)                |
|MT/ZTEM |E3DMT      |octree ver. 1|- :math:`\kappa = SI` (background only)| - :math:`T_i:` unitless (:ref:`details<sign_ztem_units>`)            |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+
|        |           |             |- :math:`\sigma = S/m`                 | - :math:`Z_{ij}:` V/A (:ref:`details<sign_mt_units>`)                |
|MT/ZTEM |E3DMT      |octree ver. 2|- :math:`\kappa = SI` (background only)| - :math:`T_i:` unitless (:ref:`details<sign_ztem_units>`)            |
+--------+-----------+-------------+---------------------------------------+----------------------------------------------------------------------+

.. .. note::
..     - Units for potential fields are explicitly stated in manuals
..     - Units for DCIP codes should be consistent and were more or less stated in the DCIP2D manual
..     - Units for EM1DFM and EM1DTM are explicitly stated in manuals
..     - Units for NSEM codes are inferred but likely correct
..     - **Units for 3D CSEM codes have been assumed but not verified**


.. _sign_dc_units:

DC data units
~~~~~~~~~~~~~

DC data are represented by the measured voltage (:math:`\Delta V`) normalized by the transmitter current (:math:`I`). Thus the units for DC data are V/A.


.. _sign_ip_units:

IP data units
~~~~~~~~~~~~~

Generally, IP data are represented by the measured off-time voltage (:math:`\Delta V (t)`) normalized by the transmitter current (:math:`I`); which would be in units for V/A. In this case, the user is forward modeling with and inverting for the intrinsic chargeability (:math:`\eta \in [0,1]`). If the user wishes to implement the linear model approximation, then other definitions of intrinsic chargeability (mV/V) or integrated chargeability (ms) can be used to define the chargeability. However, the units for the resulting IP data would no longer be V/A in this case.

.. _sign_em1dtm_units:

EM1DTM data units
~~~~~~~~~~~~~~~~~

The EM1DTM code represents components of the dB/dt response as the induced voltage within an arbitrarily oriented receiver coil. Where :math:`\mathbf{m}` is the dipole moment for the receiver coil, :math:`V = \mathbf{m} \cdot d\mathbf{B}/dt \,` (no minus sign) because the coordinate system is left-handed! Thus a +ve voltage corresponds to a +ve dB/dt response in the direction defining the dipole moment of the receiver coil (which is also defined in a left-handed coordinate system).


.. _sign_mt_units:

Impedance tensor (MT) data units
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

MT data represent the entries of the impedance tensor (:math:`\mathbf{Z}`) where:

.. math::
    \begin{bmatrix} Z_{xx} & Z_{xy} \\ Z_{yx} & Z_{yy} \end{bmatrix} =
    \begin{bmatrix} E_{x}^{(1)} & E_{x}^{(2)} \\ E_{y}^{(1)} & E_{y}^{(2)} \end{bmatrix}
    \begin{bmatrix} H_{x}^{(1)} & H_{x}^{(2)} \\ H_{y}^{(1)} & H_{y}^{(2)} \end{bmatrix}^{-1}


where 1 denotes fields resulting from plane waves with an electric field polarized along the x direction, and 2 denotes fields resulting from planes with with an electric field polarized along the y direction. For a 3D Earth, :math:`Z_{xy} = E_{x1}/H_{x2}`. Where the electric field units V/m and the magnetic field has units A/m, the units for elements of the impedence tensor is V/A.


.. important:: MT data generally use a labeling convention wherein X = Northing, Y = Easting and Z = Down.


.. _sign_ztem_units:

Transfer functions (ZTEM) data units
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ZTEM data represent the entries of a transfer function (:math:`\mathbf{T}`) where:

.. math::
    \begin{bmatrix} T_x \\ T_y \end{bmatrix} = \big ( H_x^{(1)} H_y^{(2)} - H_x^{(2)} H_y^{(1)} \big )^{-1}
    \begin{bmatrix} - H_y^{(1)} H_z^{(2)} + H_y^{(2)} H_z^{(1)} \\ H_x^{(1)} H_z^{(2)} - H_x^{(2)} H_z^{(1)} \end{bmatrix}

where 1 denotes fields resulting from plane waves with an electric field polarized along the x direction, and 2 denotes fields resulting from planes with with an electric field polarized along the y direction. Thus by dimensional analysis, the units of the transfer function elements :math:`T_x` and :math:`T_y` are unitless.



