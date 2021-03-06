A (hopefully vaguely useful) python library for cosmology.

Ian Harrison 2012-
Christopher Lovell 2013-




To use the Eisenstein & Hu fitting functions located in the EH/ directory
you must first build the extensions and locate them in your current directory.

Luckily this is all done within setup.py:

      $ python setup.py build_ext --inplace

You can then import the power and tf_fit modules:

e.g.    import EH.power as power




Example usage:

from pycosmo.cosmology import *

wmap7 = Cosmology() # creates a default cosmology

wmap7_st = Cosmology(hmf_type='st') # create a cosmology with a Sheth-Tormen hmf
wmap7_st_fnl.f_nl = 100 # add some primoridal non-Gaussianity

lnm_arr = linspace(log(1.e13), log(1.e18), 100)

# calculate z=0 mass functions for the two cosmologies
hmf1 = wmap7.dndlnm(lnm_arr, 0.e0)
hmf2 = wmap7_st_fnl.dndlnm(lnm_arr, 0.e0)

# calculate EVS of haloes in z=0 hypersurface for the two cosmologies
phi_max1, lnm_arr = evs_hypersurface_pdf(cosm=wmap7)
phi_max2, lnm_arr = evs_hypersurface_pdf(cosm=wmap7_st_fnl)

