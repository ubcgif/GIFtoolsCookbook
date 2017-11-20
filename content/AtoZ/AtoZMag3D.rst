.. _AtoZMag3D:

.. include:: <isonum.txt>

A to Z Demo for Mag3D
=====================

This demo was created for the Fall 2017 consortium meeting. It is called "A to Z" because it shows how to start from a simple geology image all the way to an inversion, with **everything being done in GIFtools**!

This demo shows how to import a few basic files, design a survey, create a mesh, make a physical property model, forward model data, use that data and invert it.

While the demo is simple, it opens up a whole range of possibilities to **test hypotheses**, **explore the model space**, and **quantify the inversion quality**. See the :ref:`discussion questions <discuss>` to get started.

- **A to Z demo**
    - `Download the demo <https://owncloud.eoas.ubc.ca/s/lDVLwPD2LKI2QKK>`__
    - NOTE: Steps (without links) are also included with the download
    - NOTE: Requires at least GIFtools version 2.1.3 (Oct 2017)
- **Steps**
    - Start a new GIFtools project
        - :ref:`Set the working directory <projSetWorkDir>`
        - :ref:`Import the topography data <importTopo>`
        - :ref:`Import the geology image <importImage>`
        - :ref:`Create a legend for the geology image <importLegendFile>`
    - :ref:`Create a magnetic survey with the following parameters <createSurveySimple>`:
        - Height above topography = 50 m
        - Easting origin = 556,440 m
        - Northing origin = 7,133,000 m
        - Bearing = 0 degrees
        - Number of lines = 11
        - Line length = 2000 m
        - Line spacing = 150 m
        - Data spacing = 50 m
    - :ref:`Set the field parameters for the newly created magnetic survey <objectEditFieldParam>`:
        - Inclination = 83.3 degrees
        - Declination = 19.5 degrees
        - Field strength = 59,850 nT
    - **Create a mesh for the magnetic data (page needed under data/general/dataManipulation**
        - Core cells = 25 m
        - DOI = 400 m
        - Padding = 500 m on each side, 1000 m in depth
    - Create a model
        - :ref:`Create active cell model on mesh <createActiveCellsModel>`
        - :ref:`Start modelBuilder <createModelBuilder>`
        - :ref:`Create geology model from plan-view image <createGeoModelImage>`. Use a thickness of 200 m. The geology definition is in Notes.txt included with the download
        - :ref:`Create a physical property model <propModelFromGeoModel>`
    - :ref:`Create a forward model <createForward>`
        - :ref:`Edit the options <fwdmodStep3>`: set the survey, topography, and model 
        - :ref:`Write the files <fwdModStep4>`
        - :ref:`Run the code <fwdModStep5>`
        - :ref:`Import the predicted data <fwdModStep6>`
    - Work with the predicted data
        - :ref:`View the predicted data <viewData>`
        - :ref:`Add Gaussian noise <objectAddNoise>` (3% and 0 minimum value) and create a new data item
        - **Assign uncertainties using 3% plus a floor of 2 nT (page needed)**
    - :ref:`Create inversion item <createInv>`
        - :ref:`Edit the options <invStep2>`: set the mesh, data, and topography. Everything else can be left as default.
        - :ref:`Write all the files <invStep4>`
        - :ref:`Run all the files <invStep5>`
        - :ref:`Import the inversion results <invStep6>`
        - :ref:`View the convergence curves <invStep7>`

.. _discuss:

- Discussion questions
    - Survey and model
        - Does the survey need to be adjusted to better image the anomalous response?
        - Are we using the right geophysical method to detect the desired target?
        - ...
    - Forward model
        - Is the anomalous response large enough compared to expected noise and instrument sensitivity?
        - How does the data change if the model has greater or less physical property contrast?
        - How deep can the deposit be before we cannot detect it anymore?
        - ...
    - Inversion
        - Does the recovered model match expectations?
        - What can be done to improve the recovered model?
        - What happens when we start to use non-default parameters?
        - What happens when the uncertainties are increased or decreased?
        - Can we include reference models? Impose bounds? Include cell and face weighting?
        - What other information do we have to constrain the inversion?
        - ...






