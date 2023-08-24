This package is to update CRTM2.4.0 cloud database with new ice cloud scattering optics provided by Ping Yang’s group on Feb.13, 2023.

1, Download crtm-master.zip. then unzip crtm-master.zip, and delete crtm-master.zip after unzipping, cd crtm-master. Or git clone git@github.com:JCSDA/crtm.git.

2, ./Get_CRTM_Binary_Files.sh, then a folder fix will be obtained.

3, cd fix/CloudCoeff/netCDF/, wget -N https://github.com/Huang-Group-UMICH/CRTM2.4.0-modified_with_new_icecloud/raw/main/CloudCoeff.nc4. By doing this, the old CloudCoeff.nc4 is replaced with new CloudCoeff.nc4.

4. The other steps are the same as the original CRTM2.4.0 (https://github.com/JCSDA/crtm/blob/master/README.md), as follows:
   
   Configuration Step 1

    ls  configuration/
      for example, ./configuration/gfortran-debug.setup

    (note the .  -- for a detailed discussion of . vs. source see: https://unix.stackexchange.com/questions/58514/what-is-the-difference-between-and-source-in-shells)

    Configuration Step 2

    ./Set_CRTM_Environment.sh
    Again noting the leading . . This sets the required environment variables to identify various paths needed to build. CRTM_ROOT, CRTM_SOURCE_ROOT, etc.

    Configuration Step 3
   
    cd src/
    cd Build/
    make clean  
    cd ..  
    make realclean  
    make  
    The commands make clean and make realclean ensures that the underlying links, compiled files, generated Makefiles. are removed to avoid conflicts with a clean build. The command make at the 
     src/ level performs the linking process between the upper level src/** directories and the src/Build/libsrc directory.

    Note: After runnin make, you may see certain "nc4" files listed as missing, these are files that will be converted to netCDF4 format, but have not yet been added.

    Assuming no fatal error messages, continue to the Build steps below.

    Build Step 1

    cd Build/
    ./configure --prefix=${PWD}
    make clean
    make -j4
    (See additional options for configure below. -j4 sets the number of parallel make processes to 4.)

     Now we have finally compiled the linked source codes that reside in the libsrc/ directory. Please note that once the source codes are linked in the libsrc directory, all development and 
    testing can occur at the Build/ level. In the libsrc/ directory, the source codes link back to the version-controlled counterparts, so you'll want to answer "yes" to any queries about opening 
    the version controlled codes when trying to edit them (this occurs in emacs, for example).

   Build Step 2

   cd libsrc/
   ls -l *.mod
   ls -l *.a
   make check
   make install
   The ls commands are to verify that indeed the .mod files have been created and the library file (which external codes link against) has also been created. The make check command builds and runs 
   the default CRTM test check_crtm, located in the src/Build/libsrc/test directory.

   make install installs the library in the directory defined by the command configure --prefix=directory_name.
