This package is originally from https://github.com/JCSDA/crtm/tree/master, but it modifies Get_CRTM_Binary_Files.sh to update fix/CloudCoeff/netCDF/CloudCoeff.nc4 with new CloudCoeff.nc4 which includes new ice cloud scattering optics provided by Ping Yang’s group on Feb.13, 2023.

1, Download crtm-master-modified.tgz

2, tar -xvzf crtm-master-modified.tgz

3, cd crtm-master-modified/

4. The following steps are the same as the original CRTM2.4.0 (https://github.com/JCSDA/crtm/blob/master/README.md).
   
Note: To use the new cloud database, fix/CloudCoeff/netCDF/CloudCoeff.nc4, the user should set Coeff_Format = 'netCDF' for example in src/Build/libsrc/test/check_crtm.F90.
