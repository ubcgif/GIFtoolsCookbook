.. _videoTutorials:

Video Tutorials
===============

Below is our entire collection of video tutorials!

**Overview**

- :ref:`General functionality <VToverview>`

**Data types**

- :ref:`Magnetics data <VTmagdata>`
- :ref:`Gravity data <VTgravdata>`
- :ref:`DC data <VTdcdata>`
- :ref:`IP data <VTipdata>`
- :ref:`Frequency-domain EM data <VTfemdata>`
- :ref:`Time-domain EM data <VTtemdata>`
- :ref:`Magnetotellurics data <VTmtdata>`
- :ref:`Z-axis tipper data <VTztemdata>`
- :ref:`Physical property and borehole data <VTppdata>`
- :ref:`Topography data <VTtopodata>`

**Meshes**

- :ref:`3D tensor mesh <VT3dmesh>`
- :ref:`OcTree mesh <VTocmesh>`

**Models**

- :ref:`Cell-centred discretized model <VTccmodel>`
- :ref:`Face-centred discretized model <VTfcmodel>`

.. _VToverview:

General functionality covering all data types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Main look and feel of GIFtools: `YouTube <https://www.youtube.com/embed/Kqm0TyNJ-vQ>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/lookAndFeel.wmv>`__ (11 MB)
- Import ascii-based XYZ files: `YouTube <https://youtu.be/FOLEVdzM944>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/importDataXYZ.wmv>`__ (18 MB)
- Import ascii-based CSV files: `YouTube <https://youtu.be/khmT9Gd5SZ0>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/importDataCSV.wmv>`__ (23 MB)
- Import ascii-based XYZ or CSV files for EM data: `YouTube <https://youtu.be/O11BicvXxx0>`__, `download <https://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/EMimport.wmv>`__ (49 MB)
- Import GIF-formatted files: `YouTube <https://youtu.be/xqhvcGcqwJc>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/ioData.wmv>`__ (5 MB)
- Change the number of openMP threads for executables and find the version number: `YouTube <https://youtu.be/KMZA7q85og8>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/openMPandAbout.wmv>`__ (12 MB)
- General data GUI: `YouTube <https://youtu.be/JopurLh1fQc>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/dataGUI.wmv>`__ (87 MB)
- General model GUI: `YouTube <https://youtu.be/UfotZKDYgJI>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/modelGUI.wmv>`__ (123 MB)
- Create a tensor mesh: `YouTube <https://youtu.be/IIUDA5e1wfc>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/simpleTensorMesh.wmv>`__ (34 MB)
- Using the modelBuilder module: `YouTube <https://youtu.be/uXipYfitAIw>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/modelBuilder.wmv>`__ (11 MB)
- Assign simple uncertainties to any data set: `YouTube <https://www.youtube.com/watch?v=Hv7fEbApYHk>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/simpleUncert.wmv>`__ (7 MB)
- Use of data calculators: `YouTube <https://youtu.be/57Ii6zYLr04>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/dataCalculators.wmv>`__ (35 MB)
- Use of calculator for models: `YouTube <https://youtu.be/5xoQe7tvTDw>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/modelCalculator.wmv>`__ (16 MB)
- View convergence curves for an inversion: `YouTube <https://youtu.be/yPO3snYtxgM>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/convergenceCurves.wmv>`__ (15 MB)
- Create topography data from data: `YouTube <https://youtu.be/TKljJn-AB14>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/createTopoFromData.wmv>`__ (8 MB)
- Downsample data using a mesh: `YouTube <https://youtu.be/w5dcDiPh0fw>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/dsToMesh.wmv>`__ (26 MB)
- Remove data outside of a mesh: `YouTube <https://youtu.be/BoJHdTkxpDM>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/removeDataOutsideOfMesh.wmv>`__ (11 MB)
- Set i/o headers: `YouTube <https://youtu.be/_a8YHtT0vLY>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/ioHeader.wmv>`__ (8 MB)
- Rename data headers: `YouTube <https://youtu.be/t1dd-U2NIyg>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/renameDataHeaders.wmv>`__ (5 MB)
- Set the number of OMP threads: `YouTube <https://youtu.be/iDOL4JOIHw8>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/setOMPthreads.wmv>`__ (9 MB)
- View data as a table: `YouTube <https://www.youtube.com/watch?v=J7eU3W-BTAg>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/tableView.wmv>`__ (8 MB)


Data types
^^^^^^^^^^
In this section, we summarize the general functionality associated with each data type that can be used within GIFtools.

.. _VTmagdata:

**Magnetics data (MAGdata)**

- I/O of GIF-formatted mag3d data files: see :ref:`general <VToverview>` functionality
- I/O of ascii-based CSV and XYZ file type: see :ref:`general <VToverview>` functionality
- Change/set (anomaly) inclinations, declinations, and field strength: `YouTube <https://youtu.be/_3nP0msIEk8>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/magDataChangeParam.wmv>`__ (2.9 MB)
- Remove DC bias: `YouTube <https://youtu.be/2c1gY0xY068>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/magDataRemoveDCbias.wmv>`__ (7.7 MB)
- De-trend data with polynomial fits: `YouTube <https://youtu.be/XxaWr2Qb8Uo>`__, `download <http://www.eoas.ubc.ca/~kdavis/giftoolsdocs/calculateTrends.wmv>`__ (17.5 MB) (or via the data GUI)
- Assign standard deviations (% and/or floor) to data: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality
- Output files for forward modelling: `YouTube <https://youtu.be/cwCHZIkbYIQ>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/magfor3d.wmv>`__ (10 MB)
- Set up input files for use with mag3d inversion: `YouTube <https://youtu.be/j07EmUFJ8wk>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/magInversionSetup.wmv>`__ (14.5 MB)
- Read output files from mag3d and view predicted data, recovered models, and inversion diagnostics (e.g., Tikhonov curve): `YouTube <https://youtu.be/-sQPMDyhHI4>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/magInversionLoadView.wmv>`__ (26 MB)
- Perform joint inversion on multiple magnetic data sets with mag3d: `YouTube <https://youtu.be/TK5WDJTDDgk>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/jointInversionMag.wmv>`__ (50 MB)
- Perform equivalent source processing (with magsenes and maginves): `YouTube <https://youtu.be/H60nQ6KKTbs>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/mages.wmv>`__ (25 MB)
- Add Gaussian noise to the data: `YouTube <https://youtu.be/aAEo570HRUk>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/addGaussianNoise.wmv>`__ (6 MB)

.. _VTgravdata:

**Gravity data (GRAVdata)**

- I/O of GIF-formatted grav3d data files: see :ref:`general <VToverview>` functionality
- I/O of ascii-based CSV and XYZ file type: see :ref:`general <VToverview>` functionality
- De-trend data with polynomial fits: see :ref:`magnetic data <VTMagdata>` or via the data GUI
- Assign standard deviations (% and floor) to data: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality

.. tip:: Check the magnetic data section, too, as often what works there, also works for gravity (both being potential field data).

.. _VTdcdata:

**Direct current data (DCdata)**

- I/O of GIF-formatted dcip2d and dcip3d data files: see :ref:`general <VToverview>` functionality
- Import DCIP ascii files: `YouTube <https://youtu.be/pSlLpcB6Bn4>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/importDCIPascii.wmv>`__ (15 MB)
- Create 2D data sets from 3D data and combine 2D data sets into 3D data files: `YouTube <https://youtu.be/xDurE0FmxoQ>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/dcip3dTo2d.wmv>`__ (27 MB)
- Add standard deviations (% and floor) to data: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality
- Calculate normalized voltage from apparent resistivity: `YouTube <https://youtu.be/NvtsJUzsBeE>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/appRhoToVoltage.wmv>`__ (8 MB)
- Calculate apparent resistivity from normalized voltage: `YouTube <https://www.youtube.com/watch?v=PYyxYapqm34>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/voltageToAppRho.wmv>`__ (6 MB)
- Create input files and run make_wdat.exe: `YouTube <https://www.youtube.com/watch?v=RQbkrrGy7l8>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/useCalcWdat.wmv>`__ (24 MB)

.. _VTipdata:

**Induced polarization data (IPdata)**

- I/O of GIF-formatted dcip2d and dcip3d data files: see :ref:`general <VToverview>` functionality
- Import DCIP ascii files: `YouTube <https://youtu.be/pSlLpcB6Bn4>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/importDCIPascii.wmv>`__ (15 MB)
- Add standard deviations (% and floor) to data: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality

.. _VTfemdata:

**General frequency-domain EM data (FEMdata)**

- I/O of GIF-formatted E3Dinv data files: see :ref:`general <VToverview>` functionality
- I/O of ascii-based CSV and XYZ file type: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality
- Simple and column calculator (same functionality as TEM): `YouTube <https://youtu.be/QSeR3ALMu88>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/emCalculators.wmv>`__ (5 MB)
- Assigning frequency-based uncertainty to EM data (same functionality as TEM): `YouTube <https://youtu.be/fknpgzhUVIc>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/emUncert.wmv>`__ (19 MB)

.. _VTtemdata:

**General time-domain EM data (TEMdata)**

- I/O of GIF-formatted TDoctree or H3DTD data files: see :ref:`general <VToverview>` functionality
- I/O of ascii-based CSV and XYZ file type: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality
- Add AEM coincident loop sources: `YouTube <https://youtu.be/h9Vd-YPmuvY>`__, `download <http://www.eoas.ubc.ca/~kdavis/giftoolsdocs/addCoincidentLoop.wmv>`__ (10 MB)
- Add AEM offset loop sources: `YouTube <https://youtu.be/Z0Aikqpnt2o>`__, `download <http://www.eoas.ubc.ca/~kdavis/giftoolsdocs/addOffsetLoopSources.wmv>`__ (15 MB)
- Simple and column calculator: `YouTube <https://youtu.be/QSeR3ALMu88>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/emCalculators.wmv>`__ (5 MB)
- Assigning time-based uncertainty to EM data: `YouTube <https://youtu.be/fknpgzhUVIc>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/emUncert.wmv>`__ (19 MB)

.. _VTmtdata:

**Magnetotelluric EM data (MTdata)**

- I/O of GIF-formatted MT3Dinv data files: see :ref:`general <VToverview>` functionality
- I/O of ascii-based CSV and XYZ file type: see :ref:`general <VToverview>` functionality
- Import EDI files: `YouTube <https://youtu.be/kTxPQ81GDOw>`__, `download <http://www.eoas.ubc.ca/~sdevries/Videos/importEDIfiles.wmv>`__ (14 MB)
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality

.. _VTztemdata:

**Z-Axis tipper EM data (ZTEMdata)**

- I/O of GIF-formatted MT3Dinv data files: see :ref:`general <VToverview>` functionality
- I/O of ascii-based CSV and XYZ file type: see :ref:`general <VToverview>` functionality
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality
- Add a base station: `YouTube <https://www.youtube.com/watch?v=IfKbArPCR6E>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/ztemAddBaseStation.wmv>`__ (5 MB)

.. _VTppdata:

**Physical property data (BOREdata and PROPdata) via modelBuilder**

- Load borehole property, collar, and optional survey files: `YouTube <https://youtu.be/p052VHix-DM>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/importBoreholeData.wmv>`__ (60 MB)
- Edit datum or standard deviation or completely remove them: see :ref:`general <VToverview>` functionality
- Discretize borehole and property data onto a GIF mesh: `YouTube <https://youtu.be/PhEErJ7REy0>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/discBoreholeData.wmv>`__ (90 MB)
- Assign bounds and create a reference model for GIF inversions: `YouTube <https://youtu.be/PhEErJ7REy0>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/discBoreholeData.wmv>`__ (90 MB)
- Create weighting functions to add soft constraints to GIF inversions: `YouTube <https://youtu.be/hrKy1pVAjCQ>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/makeWeightingFunctions.wmv>`__ (24 MB)
- Work in any units and convert them at the end to the proper units required for inversion via the calculators: see :ref:`general <VToverview>` functionality

.. _VTtopodata:

**Topography data (TOPOdata)**

- I/O and view GIF topography data files: `YouTube <https://youtu.be/SOtGqgozQMc>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/topoImportGIF.wmv>`__ (5.8 MB)
- Load and view Canadian Digital Elevation Data (CDED): `YouTube <https://youtu.be/f9ynycNikXk>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/importCDED.wmv>`__ (13 MB)
- Merge topography data sets together: `YouTube <https://youtu.be/2WDOsSN2srg>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/mergeTopo.wmv>`__ (11 MB)
- Down-sample: `YouTube <https://youtu.be/Bq1glleI3sM>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/topoDownSample.wmv>`__ (7.6 MB)
- Extend topography to mesh edges: `YouTube <https://youtu.be/dTczNnNOPBk>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/extendTopoToMesh.wmv>`__ (6 MB)
- Create 2D topography from 3D: `YouTube <https://www.youtube.com/watch?v=P-PrZ74Bgrw>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/topo3dTo2d.wmv>`__ ( MB)

Meshes
^^^^^^
In this section, we summarize the general functionality associated with each type of mesh that can be used within GIFtools.

.. _VT2dmesh:

.. _VT3dmesh:

**Three-dimensional tensor mesh (mesh3D)**

- I/O and view 3D tensor meshes (for use with 3D codes): `YouTube <https://youtu.be/y0oIlPu_4Pw>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/ioMesh3d.wmv>`__ (9.8 MB)
- Create meshes internally with GIFtools for potential-field data: see :ref:`general <VToverview>` functionality
- Create a simple mesh: `YouTube <https://youtu.be/UpQJiZVRiIU>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/createSimpleMesh.wmv>`__ (13 MB)

.. _VTocmesh:

**OcTree meshes (meshOctree)**

- I/O and view the ocTree meshes (for use with ocTree codes): `YouTube <https://youtu.be/Cq27wKDFRNY>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/ioMeshOctree.wmv>`__ (9.4 MB)
- Create refined octree mesh and active cell model from topography: `YouTube <https://youtu.be/GTBLjUICt88>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/refineOcTreeFromTopo.wmv>`__ (21 MB)

Models
^^^^^^
In this section, we summarize the general functionality associated with each type of model that can be used within GIFtools.

.. _VTccmodel:

**Cell-centred discretized models (GIFmodel)**

- I/O and view GIF models: see :ref:`general <VToverview>` functionality
- Build reference models for inversion using other GIFmodels, geologic information, and/or borehole data: see :ref:`modelBuilder <VTppdata>` functionality
- Use a simple calculator to convert between units and change the unit description: `YouTube <https://youtu.be/x9Hhj5Crzjc>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/modelCalculator.wmv>`__ (5 MB)
- Create active cell models from topography data (TOPOdata): `YouTube <https://youtu.be/rJFbWIBp6mE>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/activeCellTopo.wmv>`__ (16 MB)
- Create simple constant-value models: `YouTube <https://youtu.be/Jnl6_SKRFQ0>`__, `download <http://www.eoas.ubc.ca/~rshekhtm/giftoolsdocs/createConstantModel.wmv>`__ (4.7 MB)
- Assign value to air cells: `YouTube <https://youtu.be/heDq7Of5IIs>`__, `download <https://www.eoas.ubc.ca/~sdevries/Videos/applyAirCells.wmv>`__ (13 MB)


.. _VTfcmodel:

**Face discretized models (FACEmodel)**

- I/O and view GIF models discretized on faces (e.g., weighting files): see :ref:`general <VToverview>` functionality (model GUI will view FACEmodels)
- Create face weighting for inversion based on a reference model: see :ref:`modelBuilder <VTppdata>` functionality

