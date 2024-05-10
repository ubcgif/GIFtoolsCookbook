.. _AtoZNS_index:

.. include:: <isonum.txt>


Natural Source Electromagnetics (MT and ZTEM)
=============================================

This A to Z example tackles practical aspects of preparing and inverting natural source EM data (MT and/or ZTEM) using GIFtools.
Here the user begins with a set of EDI formatted MT survey files and Geosoft XYZ formatted ZTEM survey files.
The user will load the into the GIFtools framework, interpret the data and invert the data with two OcTree codes (E3DMT versions 1 and 2).
The goal of this exercise is to recover a conductive kimberlite pipe which lies under a moderately conductive overburden.

Once finished, the user will be familiar with:

    - The coordinate systems and Fourier convention generally used for MT and ZTEM data
    - Basic interpretation of MT data through apparent resistivities
    - Creating OcTree meshes based on survey geometry
    - Practical strategies for inverting natural source data with the E3DMT codes
    - Differences between E3DMT versions 1 and 2
    - How to jointly invert MT and ZTEM data using GIFtools

The full A to Z example is split into 4 parts:

.. toctree::
    :maxdepth: 1

    Loading, interpreting and preparing data <data>
    MT inversion <mt_inversion>
    ZTEM inversion <ztem_inversion>
    Joint MT/ZTEM inversion <joint_inversion>





