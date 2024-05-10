.. _e3dmtfile2:

MT / ZTEM data: E3DMT version 2
===============================

Formatting and examples for E3DMT version 2 data files can be found here:

    - `Observations file <https://e3dmt.readthedocs.io/en/manual_ver2/content/files/obsFile.html>`__
    - `Predicted data file <https://e3dmt.readthedocs.io/en/manual_ver2/content/files/preFile.html>`__
    - `Survey index file <https://e3dmt.readthedocs.io/en/manual_ver2/content/files/indexFile.html>`__
    - `Receiver file <https://e3dmt.readthedocs.io/en/manual_ver2/content/files/receiverFile.html>`__
    - `Supporting theory <https://e3dmt.readthedocs.io/en/manual_ver2/content/theory.html#natural-sources-mt-and-ztem>`__


















.. This file is the structure for MT and/or ZTEM data associated with the inversion program ``E3DMT``. The type of data is set by a data flag. Data that should be ignored are denoted by an *i*. The general format is:


.. .. figure:: ../../images/e3dmtfile.png
..     :align: center
..     :width: 400


.. Parameter definitions:

.. - ``n``: Number of datatype and frequency flags in the file (will need one for each frequency). The flag ``N_TRX`` preceeds this input.
  
.. - ``DT``: The data type flag. The flag ``DATATYPE`` preceeds this input. The options for the data flag are:
..     - ``MTZ``: MT data; impedance data with both imaginary and real parts.
..     - ``MTT``: ZTEM data; Hx and Hy are constant at the reference (base) station location. This is the most typical flag for ZTEM data.
..     - ``MTH``: ZTEM data; Reference (base) station is at each data location.
..     - ``MTE``: ZTEM data; Fixed reference (base) station that is calculated from the initial model for the reference station.

.. - ``F``: The frequency for the data type.  The flag ``FREQUENCY`` preceeds this input.

.. - ``nRec``: Number of receivers associated with the frequency given above for \\(j^{th}\\) data type flag. The flag ``N_RECV`` preceeds this input.

.. - [:math:`BaseX_{[j,k]} ...`]: This line is only present for ZTEM data that does *not* have the MTH datatype. The line consists of the (X,Y,Z) for the base station followed by "i" for the number of data columns given on the next line.

.. - [:math:`X_{[j,k]} ...`]: Easting (m) of the \\(k^{th}\\) receiver for the \\(j^{th}\\) data type.

.. - [:math:`Y_{[j,k]} ...`]: Northing (m) of the \\(k^{th}\\) receiver for the \\(j^{th}\\) data type.

.. - [:math:`Z_{[j,k]} ...`]: Elevation (m) of the \\(k^{th}\\) receiver for the \\(j^{th}\\) data type.
  
.. - ``data``: Columns of data / uncertainty pairs depending upon the data type:

..   - **MT data:** For MT data, the 16 data columns are in MT coordinates (X+ north, Y+ East, Z+ up) and consist of the following in order:
  
..      - :math:`ZXX^r`: Real part of the ZXX component
     
..      - :math:`ZXX^r_{stn}`: Standard deviation of the real part of the ZXX component       

..      - :math:`ZXX^i`: Imaginary part of the ZXX component
     
..      - :math:`ZXX^i_{stn}`: Standard deviation of the imaginary part of the ZXX component       

..      - :math:`ZXY^r`: Real part of the ZXY component
     
..      - :math:`ZXY^r_{stn}`: Standard deviation of the real part of the ZXY component       

..      - :math:`ZXY^i`: Imaginary part of the ZXY component
     
..      - :math:`ZXY^i_{stn}`: Standard deviation of the imaginary part of the ZXY component  

..      - :math:`ZYX^r`: Real part of the ZYX component
     
..      - :math:`ZYX^r_{stn}`: Standard deviation of the real part of the ZYX component       

..      - :math:`ZYX^i`: Imaginary part of the ZYX component
     
..      - :math:`ZYX^i_{stn}`: Standard deviation of the imaginary part of the ZYX component  

..      - :math:`ZYY^r`: Real part of the ZYY component
     
..      - :math:`ZYY^r_{stn}`: Standard deviation of the real part of the ZYY component       

..      - :math:`ZYY^i`: Imaginary part of the ZYY component
     
..      - :math:`ZYY^i_{stn}`: Standard deviation of the imaginary part of the ZYY component  
     

..   - **ZTEM data:** For ZTEM data, the 8 data columns are in MT coordinates (X+ north, Y+ East, Z+ down) and consist of the following in order:
  
..      - :math:`ZXY^r`: Real part of the ZXY component
     
..      - :math:`ZXY^r_{stn}`: Standard deviation of the real part of the ZXY component       

..      - :math:`ZXY^i`: Imaginary part of the ZXY component
     
..      - :math:`ZXY^i_{stn}`: Standard deviation of the imaginary part of the ZXY component  

..      - :math:`ZYX^r`: Real part of the ZYX component
     
..      - :math:`ZYX^r_{stn}`: Standard deviation of the real part of the ZYX component       

..      - :math:`ZYX^i`: Imaginary part of the ZYX component
     
..      - :math:`ZYX^i_{stn}`: Standard deviation of the imaginary part of the ZYX component  
    

.. **NOTE**: Each ``DATATYPE`` flag must precede the ``FREQUENCY`` flag *regardless of whether it is the same as the previous frequency*. See the examples below.


.. Examples
.. --------

.. The following are two examples of data files.

.. **Example 1**: MT data at 3 frequencies (100, 10, and 1 Hz) with 2 observations each for brevity:

.. .. figure:: ../../images/e3dmtEx1.png
..     :align: center
..     :width: 400


.. **Example 2**: ZTEM data at 2 frequencies (30 and 45 Hz) with 3 observations each with a single base station:

.. .. figure:: ../../images/e3dmtEx2.png
..     :align: center
..     :width: 400



