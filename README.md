# DDSCAT 7.3 Introduction

Discrete Dipole Scattering (DDSCAT) is a Fortran code for calculating scattering and absorption of light by irregular particles and periodic arrangement of irregular particles.

It has been jointly developed by 
* [Bruce T. Draine](http://en.wikipedia.org/wiki/Bruce_T._Draine) Department of Astrophysical Sciences, Princeton University, draine@astro.princeton.edu
* Piotr J. Flatau Scripps Institution of Oceanography, University of California San Diego, pflatau@ucsd.edu  

The current version, DDSCAT 7.3.3 (released 2019 July 10), supersedes previous versions, which are no longer supported.
The source code for DDSCAT 7.3.3 is available on this website.  The latest update is 2020 May 13 (fixed a bug that affected nearfield calculations done with multiple values of the rotation angle Phi.)

* DDSCAT can calculate scattering and absorption by isolated particles (e.g., dust grains, ice crystals). 
* DDSCAT can calculate scattering and absorption by periodic structures with applications to photonics and studies of arrays of nanostructures (for example absorption by periodic arrangement of finite cylinders, cubes, etc). 
* DDSCAT offers capability for very fast near field calculation

DDSCAT 7.3 differs from DDSCAT 7.2 by offering these options: 

* DDSCAT 7.3 includes the "Filtered Coupled Dipole" method as an option
* DDSCAT 7.3 can now efficiently calculate both E and B throughout a user-specified rectangular volume containing the target.  The polarization P, and nearfield E (and B, if desired) are saved as files.
* DDSCAT 7.3 now reports the macroscopic E field within the target, rather than the "microscopic" E field as in the past.
*  The DDSCAT 7.3 distribution includes a separate F90 code, DDPOSTPROCESS.f90, designed to read the stored P and E (and B) and perform postprocessing calculations (e.g., calculating the Poynting flux).  DDPOSTPROCESS.f90 can be modified by the user to do additional postprocessing calculations, or to output results in other formats.
* As with DDSCAT 7.2.2, the DDSCAT 7.3 distribution includes VTRCONVERT.f90 to support visualization of the target geometry using the Visualization Toolkit
* There are new versions of the conjugate gradient solvers

DDSCAT 7.3.3 is publicly available, and is now considered to be the standard version of DDSCAT. If you choose to use it, please send email to draine@astro.princeton.edu  registering as a user; registered users of DDSCAT will be notified when updates to the code are made. As always, please let us know if you encounter problems downloading DDSCAT, or if you have trouble using DDSCAT (but **please** read the manual carefully before reporting problems!) 

DDSCAT 7.3 is gratis, subject to the GNU General Public License.  You may copy, distribute, and/or modify the software identified as under this agreement.  If you distribute copies of this software, you must give the recipients all the rights that you have. 


## DDSCAT references

If you use DDSCAT, we request that you reference some of the papers on which DDSCAT is based
* [Review paper is available from J. Opt. Soc. Am. site.](http://www.opticsinfobase.org/josaa/abstract.cfm?uri=josaa-11-4-1491) Draine, B.T., & Flatau, P.J., "Discrete dipole approximation for scattering calculations", J. Opt. Soc. Am. A, 11, 1491-1499 (1994) (we check citations to this paper to track the overall DDSCAT use; on occasion we implement code improvements that way!)
* Draine, B.T., & Flatau, P.J., "Discrete-dipole approximation for periodic targets: theory and tests", J. Opt. Soc. Am. A, 25, 2593-2703 (2008). (if you use this option of the code)
* P. J. Flatau and B. T. Draine, "Fast near field calculations in the discrete dipole approximation for regular rectilinear grids," Opt. Express 20, 1247-1252 (2012) (if you use this option of the code)
* P. J. Flatau and B. T. Draine, "Light scattering by hexagonal columns in the discrete dipole approximation," Opt. Express  22, 21834-21846 (2014).


## DDSCAT downloading and distribution notes

We make available for download a gzipped tarfile containing complete source code and documentation for DDSCAT 7.3. To get full DDSCAT distribution begin with downloading the User Guide. If you are using LINUX/UNIX operating system get the source code distribution. For this version you will need to compile the code. This offers opportunity to set the best compilation flags, MPI, Open-MP, etc. For Windows users we offer a simple precompiled version of an earlier release (7.3.0); this is probably the fastest way to get started but also somewhat limited in ability to make source code changes. Really large DDSCAT runs should probably be done on 64-bit UNIX/LINUX.


## Windows version

Recently (2019) Microsoft made available Windows Subsystem for Linux (WSL) and you can install UBUNTU (LINUX) as an app. This is very simple and we describe this process in the recent versions of the manual. This is a prefered way to run DDSCAT on Windows. Currently, to run DDSCAT on Windows you will need to know how to use a "command window" (there is no graphical interface).  Also notice that by default Windows operating system hides some files - that may influence your ability to "see" files extensions such as ddscat.par. For large problems with, say one milion of dipoles or more, you will run into 2Gbyte memory limit if you are using a 32-bit computer. To solve this problem on both Windows and Linux move to a 64-bit operating system and use 64-bit compilers. You may also run into stack size limitation when running the code with OpenMP. In such case try
 * ulimit -s unlimited
