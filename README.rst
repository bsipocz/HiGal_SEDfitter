=================
Hi-Gal SED fitter
=================

API docs are on readthedocs_  All the good stuff happens in `fits.py
<higal_sedfitter/fits.py>`_ and `smooth.py <higal_sedfitter/smooth.py>`_.


Requires
--------

 * FITS_tools_
 * lmfit_
 * dust_emissivity_

Example
-------
.. code-block:: python

   >>> from astropy.io import fits
   >>> from astropy import units as u
   >>> from higal_sedfitter import smooth
   >>> from higal_sedfitter.fit import PixelFitter, fit_modified_blackbody_tofiles
   >>> target_header = fits.getheader('destripe_l048_PLW_wgls_rcal.fits')
   >>> smooth.smooth_images_toresolution(45*u.arcsec, skip_existing=False,
   ...                                   regrid=True, target_header=target_header)

   >>> pixelfitter = PixelFitter(bfixed=True)
   >>> fit_modified_blackbody_tofiles('destripe_l048_{0}_wgls_rcal_smregrid45.fits',
   ...                            pixelfitter=pixelfitter,
   ...                            out_prefix='higalsedfit_70to500_l048_beta1.75',
   ...                            integral=True)

Credits
-------
The base packages were written by Adam Ginsburg.  Ke Wang wrote the original
version of the SED fitter looping routine (``fit_modified_blackbody_tofiles``)
and performed most of the initial testing.


.. _FITS_tools: http://fits-tools.rtfd.org
.. _lmfit: http://lmfit.github.io/lmfit-py/
.. _dust_emissivity: https://github.com/keflavich/dust_emissivity
.. _readthedocs: http://hi-gal-sed-fitter.rtfd.org
