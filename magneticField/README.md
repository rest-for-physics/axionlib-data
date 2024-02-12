
File : README.md

Creation Date : 13rd June 2019

---

Description
===========

This data directory contains different definitions of magnetic fields that can be read by `TRestAxionMagneticField`. For more detail see the documentation of that class.

Conventions
===========

- `File contents` : Each magnetic file contains a list with 6 columns. The three first columns are the position X,Y,Z in mm and the three last columns are the values of the magnetic field in these positions in T. These files are used to define the nodes of a regular grid mesh.

- All positions are in mm and T wich are the units by default of REST !

- `Filename` : AUTHOR_YYYYMM.dat.

- `X, Y, Z definitions` : The origin is set in the center of the domain, so that x_max=-x_min (the same for y and z). The Z direction is along the magnetic bore symmetry axis. The X and Y axis are defined such that (X,Y,Z) is a direct system.

- The `dat` files are fixed columns ASCII text files, while the `.bin` are binary files containing the same information in 4-bytes float precision.


List of magnetic fields available 
=================================

- `Bykovskiy_201906.dat` : It contains the magnetic field definition for babyIAXO with a regular mesh precision of 50mm in X,Y and Z

- `Bykovskiy_202004.bin` : It contains the magnetic field definition for babyIAXO with a regular mesh precision of 10mm in X and Y, and 50mm in Z.

- `Bykovskiy_202004.xls` : The original file generated with Matlab used to provide the file `Bykovskiy_202004.bin`.

- `Mentink_202401.bin` : It contains the magnetic field definition for babyIAXO with a regular mesh precision of 10mm in X,Y and 50mm in Z. It defines the field between -10m and 10m, reproducing the magnetic volume size as defined in the original file.

- `Mentink_202401_cutoff.bin` : It contains the magnetic field definition for babyIAXO with a regular mesh precision of 10mm in X,Y and 50mm in Z. It defines the field between -6m and 6m, introducing an artificial cut-off to the original file size. The field in that boundary is already below 0.1T.
