.. _quickStartGuide:

GIFtools quick-start guide
==========================

In this section, you will find:

- :ref:`Installation guide <install>`
- :ref:`Navigating GIFtools <lookAndFeel>`
- :ref:`Tutorial guide  <tutorials>`


.. _install:

Installation of GIFtools
------------------------

To install GIFtools, you will need to go the the website and download the latest installation executable (`Log-in required <https://gif.eos.ubc.ca/GIFtools/downloads>`_). The two available are either ``GIFtools_vXpX_install`` or ``GIFtools_vXpX_offlineInstall``. The only difference is that the off-line install is much bigger to ensure that the Matlab run-time environment that is needed is accessible if not already installed. The former installation executable will use the internet to call Matlab to check on the environment and download if necessary. Either way, **you will need administrator privileges**. Once downloaded here are the 7 steps to follow:


1. Double click on executable, which will lead you to this screen (you can trust us...):

.. figure:: ../images/giftoolsInstall1.png
    :align: center
    :width: 400



If you use a proxy server *and* you are using the `GIFtools_vXpX_install.exe`, you will need to click on the **Connection Settings** button and put the server name and port along with a user ID and password to access the internet.

2. Click **Next** and choose the installation directory for GIFtools. This does *not* necessarily need to be in ``C:\Program Files\GIF``! If you have created another folder somewhere on your computer, you may install GIFtools there (e.g., ``D:\GIFtools\``)

.. figure:: ../images/giftoolsInstall2.png
    :align: center
    :width: 400



**NOTE 1**:  If you have previous versions of GIFtools on your computer, you can put the latest version in the parent directory (e.g., ``C:\Program Files\GIF``). This directory will also be where you should place all of your executables (i.e. inversion executables, MeshTools3D, etc.) that GIFtools would require. Here is an example:

.. figure:: ../images/giftoolsInstall3.png
    :align: center
    :width: 400



**NOTE 2**: If you chose the ``Add a shortcut to the desktop`` option, you will need to perform step 7 on that shortcut too!


4. Click **Next**: One of two things will now happen, either (1) you will have to install the run-time compiler or (2) the compiler will already be installed. If (1), follow the on-screen instructions (most likely just keep clicking next) and this will lead you to step 5. If (2) this window will show up:

.. figure:: ../images/giftoolsInstall4.png
    :align: center
    :width: 400


5. You are ready for install! Click **Install >**. It will take a minute or two.

.. figure:: ../images/giftoolsInstall5.png
    :align: center
    :width: 400




6. If everything worked out, you will get to the screen below giving you step 7's instructions. Click **Finish** and **read below to finish the install** so the link is not broken.

.. figure:: ../images/giftoolsInstall6.png
    :align: center
    :width: 400




7. Fix the *Start-in*  directory link for GIFtools. Go to the Start menu and find `GIFtools_vXpX` and **right-click** and select **properties**:

.. figure:: ../images/giftoolsInstall7.png
    :align: center
    :width: 300




Note that the *Start in:* field is blank. **Copy and paste** the *Target:*  field to the *Start in:* field. Then **remove GIFtools_vXpX.exe from the Start in** field so that only the directory is present:

.. figure:: ../images/giftoolsInstall8.png
    :align: center
    :width: 300

Click **Apply** and then **OK**. GIFtools is now installed and can be started from the Start menu


Installation notes
^^^^^^^^^^^^^^^^^^

- *Why did we have to do step 7?* Windows makes a copy in the registry and starts GIFtools there. The visualization package (VTK) that is used requires static Java libraries and therefore GIFtools needs to be started where those dynamic libraries are located. 
 
- *Manual shortcuts to desktop do not require step 7!* If you have gone into GIFtools ``application`` directory, right-clicked and chose ``Create shortcut``, then the the shortcut (by default it will ask you if you want to put it on the desktop) will already have the *Start in:* field adjusted.



.. _lookAndFeel:

Navigating GIFtools
-------------------

The next four subsections will describe the main components of GIFtools pointed out below:


.. figure:: ../images/giftoolsLookAndFeel.png
    :align: center
    :width: 400

The following video also introduces the look and feel of GIFtools:

.. raw:: html

        <div style="margin-top:10px; margin-bottom:20px;" align="center">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/Kqm0TyNJ-vQ" frameborder="0" allowfullscreen></iframe>
        </div>


Menus
^^^^^
GIFtools is **menu** driven. To perform any action, the user can select from the appropriate menu at the top of the GIFtools window (or right-click the object to bring up the menu options). The four main menus that are always available are:

#. **Project**: This menu allows you to save / load / add a project, set the working directory (where the project will write/look for files) or set the number of OpenMP threads (for running inversions).

#. **Edit**: This menu will let you rename, copy, or delete the object that is currently selected.

#. **Import**: This is the main menu structure for importing items (data, meshes, etc) into GIFtools (see :ref:`Importing Files <import>` for a list of items to import).

#. **Create**: This menu allows the user to create items such as Folders (to keep the tree organized; see below), Workflows, Inversions, and other items that may call Fortran executables created by UBC-GIF

Beyond these four menus, additional menus will appear depending upon the item that is selected, such as ``Visualization`` (above is an example when selecting a mesh3D item):


Tree
^^^^

All of the items in GIFtools fall under a **GIFproject**. Beyond that, each is present in the tree structure on the right-side. Folders can be created or are transformed (in the case of inversions that have been loaded) to contain other items. In the above case, the gravity gradiometry data (GGdata object), topography (TOPOdata object), and mesh (mesh3D object) are in the folder ``final``, but are still in the project. To move items to a folder, simply **left-click, drag-and-drop** the item into the folder. To get items back to the main project folder, drag-and-drop to the GIFproject at the very top.


Information panel
^^^^^^^^^^^^^^^^^

Every item selected has a panel that shows up on the right-side of the main GIFtools window. This panel gives the user a brief over-view of the item, such as the number of cells for a mesh, or the number of frequencies in an FEMdata (Frequency-ElectroMagnetics Data) item. For data items, certain columns must be denoted in order to export them for inversion. These are known as :ref:`input/output headers <objectSetioHeaders>` (often referred to as ``i/o headers``). 

Notes section
^^^^^^^^^^^^^

This is a section where a log of what has happened to the selected item is recorded. Additionally, users may write their own comments in this section to remind them what was performed. To write notes, click on the note section and begin typing.


.. _tutorials:

Tutorial guide
--------------

This cookbook will get you to specific dialog boxes to finish your task(s). When you get to a dialog box and are not sure what to do, look for the question mark button:

.. figure:: ../images/questionMark.png
    :align: center
    :width: 400


The button will link you to a short tutorial on how (a) you got there and (b) what to do inside the dialog box. If you find a bad link, *please* email us a ubcgif[at]eos[dot]ubc[dot]ca and let us know!


