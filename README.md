# jovian_jrm09_internal_matlab

This repository contains MATLAB code used to calculate the JRM09 model (<a href="https://agupubs.onlinelibrary.wiley.com/doi/abs/10.1002/2018GL077312
">Connerney et al., 2018</a>) of Jupiter's internal magnetic field model in <a href="https://github.com/marissav06/jovian_jrm09_internal_matlab/blob/main/jovian_jrm09_internal_rtp.m">spherical (rtp)</a> or <a href="https://github.com/marissav06/jovian_jrm09_internal/blob/main/jovian_jrm09_internal_xyz.m">cartesian (xyz)</a> coordinates (note that <a href="https://github.com/marissav06/jovian_jrm09_internal_matlab/blob/main/jovian_jrm09_internal_xyz.m">jovian_jrm09_internal_xyz.pro</a> calls <a href="https://github.com/marissav06/jovian_jrm09_internal_matlab/blob/main/jovian_jrm09_internal_rtp.m">jovian_jrm09_internal_rtp.m</a> so users should download both files). 

Please see <a href="https://github.com/marissav06/jovian_jrm09_internal">https://github.com/marissav06/jovian_jrm09_internal</a> for the repository containing IDL code for the JRM09 model.

This code can be used with <a href="https://github.com/marissav06/con2020_matlab/blob/main/con2020_model_rtp.m">con2020_model_rtp.m</a> and <a href="https://github.com/marissav06/con2020_matlab/blob/main/con2020_model_xyz.m">con2020_model_xyz.m</a>, which gives the field produced by the Connerney et al. (2020) current sheet. 

<h3>Required inputs (System III Spherical, right handed):</h3>
<ul>
  <li>r_rj       - radial distance, in Rj. </li>                   
  <li>colat_rads - colatitude, in radians. Value(s) should be 0 <= colat_rads <=  pi. </li>
  <li>elong_rads - East longitude, right handed, in radians. Value(s) should be 0 <= elong_rads <= 2pi. </li>
</ul>

<h3>Required inputs (System III Cartesian):</h3>
<ul>
  <li>x_rj       - Jupiter SYSIII right-handed position in x, in Rj. </li>
  <li>y_rj       - Jupiter SYSIII right-handed position in y, in Rj. </li>
  <li>z_rj       - Jupiter SYSIII right-handed position in z, in Rj. </li>
</ul>

<h3>Outputs:</h3>
Magnetic field vector from the JRM09 internal magnetic field model, [Br, Btheta, Bphi] (spherical coordinates) or [Bx, By, Bz] (cartesian) in units of nT.

<h3>Usage:</h3>
<ul>
  <li>For internal field only: B = jovian_jrm09_internal_rtp(r_rj, colat_rads, elong_rads)</li>
 <li>For full field model: B = jovian_jrm09_internal_rtp(r_rj, colat_rads, elong_rads) + con2020_model_rtp(eq_type, r_rj, colat_rads, elong_rads)</li>
</ul>


This code was written by Marissa Vogt (mvogt@bu.edu) and Rob Wilson and was last updated January 2022
It is based on a routine originally written by K. Khurana and translated into IDL by Marissa Vogt in 2009 (for the VIP4 internal field model). 
Thanks to Masafumi Imai for providing code for his version of the JRM09 model, which was used to test and validate this code, and to Gabby Provan, Matt James, and Marty Brennan for helpful discussions.

