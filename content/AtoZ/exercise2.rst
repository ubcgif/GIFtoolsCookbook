.. _exercise2:

.. include:: <isonum.txt>

Forward model a survey
======================

In this activity, you are given a magnetic airborne survey location file, a topography file over the TKC area, a mesh, and a susceptibility model. There is also a file with the magnetic survey parameters (inclination, declination, field strength). The goal is to forward model magnetic data using the `MAG3D <http://mag3d.readthedocs.io/en/v6/>`__ code.

- **Task: forward model a magnetic data**
        - `Download the activity <https://www.eoas.ubc.ca/~sdevries/ActivitiesForLearning/Exercise2.zip>`__
- **Discussion questions**
    - What does the data look like?
    - What, if anything, can be adjusted to the survey to minimize cost or improve the coverage of the anomalous response?
    - Can you assign uncertainties to the data?
- **Take it a bit further**
    - Sometimes we use a topo active cell model instead of a topo file in the GIF codes; can you create a topo active cell model?
    - Suppose you also have a second physical property model and imported it. Can you convert the current survey to a different data type?
- **Helpful links**
    - :ref:`Recipe for creating a forward model <createForward>`
    - :ref:`View model in 3D <viewModel>`
    - :ref:`Create active cells model <createActiveCellsModel>`
    - **Assign uncertainties (page needed)**






