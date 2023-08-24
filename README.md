This package is to update CRTM2.4.0 cloud database with new ice cloud scattering optics provided by Ping Yang’s group on Feb.13, 2023.

1, Download crtm-master.zip. then unzip crtm-master.zip, and delete crtm-master.zip after unzipping, cd crtm-master. Or git clone git@github.com:JCSDA/crtm.git.

2, ./Get_CRTM_Binary_Files.sh, then a folder fix will be obtained.

3, cd fix/CloudCoeff/netCDF/, wget -N https://github.com/Huang-Group-UMICH/CRTM2.4.0-modified_with_new_icecloud/raw/main/CloudCoeff.nc4. By doing this, the old CloudCoeff.nc4 is replaced with new CloudCoeff.nc4.

4. The other steps are the same as the original CRTM2.4.0 (https://github.com/JCSDA/crtm/blob/master/README.md).
   
Note: To use the new cloud database, fix/CloudCoeff/netCDF/CloudCoeff.nc4, the user should set Coeff_Format = 'netCDF' for example in src/Build/libsrc/test/check_crtm.F90.
