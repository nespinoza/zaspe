# zaspe
A Code to Measure Stellar Atmospheric Parameters and their Covariance from Spectra

Author: Rafael Brahm (rbrahm@astro.puc.cl)

# About the code
ZASPE computes the atmospheric stellar parameters (Teff, log(g), [Fe/H] and vsin(i)) from echelle spectra via least squares minimization with a pre-computed library of synthetic spectra. The minimization is performed only in the most sensitive spectral zones to changes in the atmospheric parameters. The uncertainities and covariances computed by ZASPE assume that the principal source of error is the systematic missmatch between the observed spectrum and the sythetic one that produces the best fit. A detailed description of this code is available in Brahm et al. (2015). If you use this code for your research, please cite that publication.

In order to run ZASPE you will require a grid of synthetic spectra. ZASPE supports 3 public available libraries, namely Coelho et al. (2005), Husser et al. (2013) and Brahm et al. (2015). For a better performance we recommend to use the latter one, which is available in the following link. After minor modifications to the code, ZASPE is able to use any pre-computed library.

ZASPE accepts two formats of input spectra. The first one corresponds to the standard output of the CERES pipelines (Brahm et al. 2016 in prep) and the second one to a text file with 3 columns, where the first column refers to the echelle order, the second column to the wavelength and the third one to the flux. Each echelle order must have the same number of data points.

The file zaspe.pars contains all the variables that ZASPE will use. The supported entries are:

library: refers to the library of synthetic spectra that will be used: P: Husser et al. (2005), C: Coelho et al. (2013), R: Brahm et al. (2015).

wi: initial wavelength value to be considered in the fit.

wf: final wavelength value to be considered in the fit.

mod: ZASPE mode. P: compute only the optimal parameters. E: compute only the errors. PE: compute both, parameters and errors.

spec: file containing the obsreved spectrum.

RV0: approximate radial velocity of the observed spectrum w/r to the synthetic grid.

vsini: initial guess of vsin(i).

RESI: Instrumental Resolution of the spectrograph.

ncores: number of cores required for the paralelization of the algorithm.

trunc: number of pixels in the edges that will be neglected.

nit: maximum number of ZASPE iterations to obtain the best fit.

nsim: total number of Monte Carlo simulations required for computing the errors and the covariance structure (order 100 is enough).

fixG: if you want to fix log(g) to a certain value, you have to type that value here.

efixG: associated error of the fixed log(g) value.

T: if mod=E, you have to enter here the Teff value of the best fit.

G: if mod=E, you have to enter here the log(g) value of the best fit.

Z: if mod=E, you have to enter here the [Fe/H] value of the best fit.

R: if mod=E, you have to enter here the vsin(i) value of the best fit.

V: if mod=E, you have to enter here the RV value of the best fit.

wavP: path to the file containing the wavelength values of the Husser et al. (2013) models.

modP: path to the Husser et al. (2013) models.

modC: path to the Coelho et al. (2005) models.

modR: path to the Brahm et al. (2015) models.

In order to run ZASPE, you have to be in the directory containing the ZASPE codes and you have to type: python run_zaspe.py.

# Dependencies
Python, numpy, scipy, pyfits

# Installation

Just do

python install.py




