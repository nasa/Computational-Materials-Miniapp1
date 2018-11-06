# Computational-Materials-Miniapp1-

This mini-app is a simple test code for calculating potential energy, 
forces and stresses of an atomistic structure using EAM potential.

-----------------------------------------------------------------------
Requirements:
* Linux
* FORTRAN compiler (2003 or newer)
-----------------------------------------------------------------------
Edit the provided makefile for specific compiler option of your choice
-----------------------------------------------------------------------
Compilation: use the provided makefile with the following options:
> make            ! compiles with -O3 optimization on !
> make DEBUG=TRUE ! compiles with check and warning flags on !

-----------------------------------------------------------------------
Example (test) directory:
./CM_MINI1.test

Running a tets case:
run CM_mini1.bat script from CM_MINI1.test directory:
> CM_mini1.bat

-----------------------------------------------------------------------
Required input files:

pot.dat - interatomic potential setup file
./NiCoAl_dat  - folder with potential files as described in pot.dat
structure.plt - input atomic structure file

--- Available test structures ---
in STR directory:
Ni85Al15_N4k.plt - 4,000 atoms Ni3Al crystal
Ni85Al15_N64k.plt - 64,000 atoms Ni3Al crystal
Ni85Al15_N256k.plt - 256,000 atoms Ni3Al crystal
 
Use any of the above structures by linking them to structure.plt, e.g.,
ln -s ./STR/Al_N500_T100K.plt structure.plt
 
-----------------------------------------------------------------------
Execution:   

cd ../CM_MINI1.test
./CM_mini1

Execution options: (see also ./CM_MINI1.test/CM_mini1.bat script)

./CM_mini1           # run, using default options - see below
./CM_mini1 -n 10     # do 10 itterations (default: -n 1)
./CM_mini1 -n 10 -r  # do 10 itterations with random changes
                     # (default: no randomization)
./CM_mini1 -v 1      # run version 1 (default: -v 0) - gives a possibility
                     # to test different versions of a subroutine.
                     # currently: -v 0 executes the code using
                     # subroutine get_neighbors (CM_mini1.f)
                     # while -v 1 executes the code using
                     # subroutine get_neighbors_vect (CM_mini1.f)
                     # see subroutine force_global(iver):
-----------------------------------------------------------------------
       select case (iver)
        case(0) 
         call get_neighbors
        case(1) 
         call get_neighbors_vect
        case default 
         call get_neighbors
       end select
=======================================================================
 Notices:
 Copyright 2018 United States Government as represented by the 
 Administrator of the National Aeronautics and Space Administration. 
 All Rights Reserved.
 
 Disclaimers:
 No Warranty: THE SUBJECT SOFTWARE IS PROVIDED "AS IS" WITHOUT ANY
 WARRANTY OF ANY KIND, EITHER EXPRESSED, IMPLIED, OR STATUTORY, 
 INCLUDING, BUT NOT LIMITED TO, ANY WARRANTY THAT THE SUBJECT SOFTWARE 
 WILL CONFORM TO SPECIFICATIONS, ANY IMPLIED WARRANTIES OF 
 MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, OR FREEDOM FROM 
 INFRINGEMENT, ANY WARRANTY THAT THE SUBJECT SOFTWARE WILL BE ERROR 
 FREE, OR ANY WARRANTY THAT DOCUMENTATION, IF PROVIDED, WILL CONFORM 
 TO THE SUBJECT SOFTWARE. THIS AGREEMENT DOES NOT,IN ANY MANNER, 
 CONSTITUTE AN ENDORSEMENT BY GOVERNMENT AGENCY OR ANY PRIOR RECIPIENT 
 OF ANY RESULTS, RESULTING DESIGNS, HARDWARE, SOFTWARE PRODUCTS 
 OR ANY OTHER APPLICATIONS RESULTING FROM USE OF THE SUBJECT SOFTWARE. 
 FURTHER, GOVERNMENT AGENCY DISCLAIMS ALL WARRANTIES AND LIABILITIES 
 REGARDING THIRD-PARTY SOFTWARE, IF PRESENT IN THE ORIGINAL SOFTWARE,
 AND DISTRIBUTES IT "AS IS." 
 
 Waiver and Indemnity:
 RECIPIENT AGREES TO WAIVE ANY AND ALL CLAIMS AGAINST THE UNITED STATES
 GOVERNMENT, ITS CONTRACTORS AND SUBCONTRACTORS, AS WELL AS ANY PRIOR 
 RECIPIENT.  IF RECIPIENT'S USE OF THE SUBJECT SOFTWARE RESULTS IN ANY 
 LIABILITIES, DEMANDS, DAMAGES, EXPENSES OR LOSSES ARISING FROM SUCH
 USE, INCLUDING ANY DAMAGES FROM PRODUCTS BASED ON, OR RESULTING FROM, 
 RECIPIENT'S USE OF THE SUBJECT SOFTWARE, RECIPIENT SHALL INDEMNIFY AND
 HOLD HARMLESS THE UNITED STATES GOVERNMENT, ITS CONTRACTORS AND 
 SUBCONTRACTORS, AS WELL AS ANY PRIOR RECIPIENT, TO THE EXTENT
 PERMITTED BY LAW. RECIPIENT'S SOLE REMEDY FOR ANY SUCH MATTER SHALL 
 BE THE IMMEDIATE, UNILATERAL TERMINATION OF THIS AGREEMENT.

