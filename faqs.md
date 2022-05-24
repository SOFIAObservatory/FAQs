# FAQs

## GREAT

### What is the size of the honeycomb map?

**A: It depends on the frequency, but generally HFA ~ 42" and LFA ~ 14"**

The size of the honeycomb pattern depends on your primary frequency: HFA or LFA. The size of one honeycomb map for the HFA has diameter of about 42”, while the central pixel moves only in an area with a diameter of about 14”. Therefore, this is also about the diameter of the area covered by the central pixel of the LFA. Since the FWHM of the LFA beam is about 14”, you get a highly oversampled map of the central LFA beam area. The outer pixels of the LFA won’t be of any interest for a source size of 15”. For the HFA, the outer pixels will ensure that you get your source and some adjacent sky mapped as well.

### How do heterodyne instruments work?

**A: By using a "Carrier Signal"**

See explanations by 1) [David Frayer (GBT)](https://greenbankobservatory.org/wp-content/uploads/2020/06/Tracing-the-Signal.pdf), 2) [ Dale E. Gary
(NJIT)](https://web.njit.edu/~gary/728/Lecture7.html), and 3) [James J. Condon and Scott Ransom (NRAO)](https://www.cv.nrao.edu/~sransom/web/Ch3.html#S6.SS4).

### What is the different between brightness temperature and radiation temperature?

**A: T<sub>A</sub>, T<sub>A</sub><super>*</super>, & T<sub>mb</sub> are convolved with different signal responses.**

Antenna temperature (T<sub>A</sub>): Actual measured noise temperature of antenna including inefficiencies and all other noise sources including the atmosphere. [Guan et al. (2012, A&A 542, L4)](http://dx.doi.org/10.1051/0004-6361/201218925) discusses the calibration scheme for GREAT, i.e. how to get from T<sub>A</sub> to T<sub>A</sub><super>*</super>.

Forward beam brightness temperature (T<sub>A</sub><super>*</super>): The convolution of the source brightness with the full forward antenna response. Also known as corrected antenna temperature, because it is the observed source antenna temperature corrected for atmospheric attenuation, radiative loss, and rearward scattering and spillover.

Main-beam brightness temperature (T<sub>mb</sub>): The convolution of the source brightness distribution on the sky with the main-beam profile of the telescope.

### How do I get from brightness temperature to flux density?

**A: [See GREAT Observer's handbook (Section 6.3.2)](https://www-sofia.atlassian.net/wiki/spaces/OHFC1/pages/1147523/6.+GREAT#6.3.2-Conversion-from-Temperature-to-Flux-Density)**




### What do the GREAT filenames mean?

**A: Depends on Level of data (older data may have different names)**

The GREAT team can deliver several types of data. Level 3 data are typically fully calibrated individual spectra. The GREAT team delivers two CLASS files for each project to the SOFIA Science Center. One of the files contains the source spectra in units of the forward- beam brightness temperature, T<sub>A</sub><super>*</super>, and additional output spectra such as receiver over system temperature, T<sub>A</sub> / T<sub>sys</sub>, plots, Sky-Hot spectra and fits, and spectra of the optical depth used to calibrate the data. The second Level 3 file contains source spectra only, in units of the main-beam temperature, TMB.

Level 4 data are CLASS data products converted to FITS-files that are a combination of Level 3 spectra, such as average spectra or spectral data cubes. Usually, the Level 4 data is in TMB units, but there are instances where the data is calibrated on the T<sub>A</sub><super>*</super> scale. Check the header and/or the ancillary documents. Level 4 files can contain multiple frequencies for a single target/source. The data can come from several flights. It will be associated to one flight in the data base. Level 4 files will not contain multiple sources.

See [video by Juan Luis Verbana](https://www.youtube.com/watch?v=Sg3tlLMGH5Q) on GREAT data products.

## EXES

### How do I get an absolute flux calibration of EXES data?

**A: Contact the Helpdesk**

If you are interested in the absolute flux calibration of EXES data please contact the Helpdesk. The conversion factor to absolute flux units (ergs s<sup>-1</sup> cm<sup>-2</sup> (cm<sup>-1</sup>)<sup>-1</sup> x 78.4 -->
 Jy) was recently updated. Depending on when the data were taken, a more accurate scaling can be applied.

## FORCAST

### Why are the USPOT exposure times higher than before (before Cycle 10)?

**A: Due to a change in the ET calculation (related to low thermal backgrounds)**

In Cycle 10 a correction was made to the USPOT exposure time calculation. This primarily affected estimates at 5 and 6 microns where the thermal background of the sky is lower than those of the other filters and grisms.

The instrument scientists aim to keep a consistent thermal background to avoid issues of nonlinearity, keeping the same level of charge in the detector wells relative to the saturation level. Due to the relatively lower thermal background at 5 and 6 microns the chop frequency is on the lower side and the frame-rate must be at least twice as large as the chop rate plus throwaways. When using F056, F064, and/or G063 FORCAST ends up throwing away more frames due to the lower thermal background and this creates the inflated overhead values at these wavelengths. Taking this into account now provides a more realistic estimate of the observing overheads.

### How can we check for memory/persistence issues?

**A: Check the residual spectrum in the raw chopped frames**

Persistence is an effect on the detector, where observing a bright source leaves a temporary impression in subsequent observations. If you suspect your data are contaminated by this effect, check the residual spectrum in the raw chopped frames of your data. If there is a lasting impression, you should be able to see it in these frames. Also, check if other observations were done between the bright object in question and the data that you are concerned about.

### Should I worry about saturating the FORCAST detector?

**A: Probably not**

Very bright objects can cause linear stripes across the array that have a very slight (few percent) affect on the flux of the target but can intercept extended regions of lower flux surrounding the object making analysis difficult. Also when dealing with very bright sources the overall sensitivity of the array can be reduced which also can be detrimental if you are trying to detect very faint sources in the same field of very bright sources. This is not a worry typically until you get in the realm of hundreds of Janskys and also trying to detect faint sources of emission.

### How do I find the on-sky angle of the FORCAST grism slit?

**A: The "SKY_ANGL" keyword**

Within the [header information](#what-is-the-best-way-to-access-the-fits-header-information) of the data should be a "SKY_ANGL" keyword which is the long-axis position angle of the slit on the sky in degrees E of N.

### What is the FORCAST photometric uncertainty?

**A: Typically 5-15%**

The uncertainty is typically between 5-15%. To calculate this value you must add (in quadrature) the measurement of the flux calibration error ([header keyword](#what-is-the-best-way-to-access-the-fits-header-information): ERRCALF), and the possible uncertainty on the flux model. The uncertainty is typically less variable in the short wavelength camera (SWC) and slightly more variable in the long wavelength camera (LWC) and in spectroscopy mode. For more details as well as a demonstration of the uncertainty calculation in python see the [SOFIA data analysis cookbooks](<https://sofia-data-analysis-cookbooks.readthedocs.io/en/latest/>).

### Has a COMA aberration correction been done on the data?

**A: No, but it's unlikely to be needed**

We can get some COMA effects in nod/match chop mode if the data have large (60") chops. Other than that, we do not typically see any COMA aberation.

### Is there a ghost in my data?

**A: Possibly, but more likely if observing at 11.2um in dichroic mode**

Within this filter and mode, a smaller and fainter secondary source can be seen next to the source with a flux ~1-2% of the main source. This effect can be exploited to detected faint sources at 11.2um, but with a broader filter than the 11.1um filter.

### How many dithers do I need for photometry?

**A: 3 is fine but 5 is better**

Dithers take around 8 seconds to complete, and help compensate for bad pixels around the edges of the detector and the paint fleck effect seen after Cycle 7 in the short wavelength array. We encourage 5 dithers, however, 3 can be sufficient.

### Can subtract the PSF from my image?

**A: Yes, but this can be difficult**

Given the nature of the observatory, the PSF during your observation may differ significantly from the PSF during the observation of the standard star. PSF-subtraction is commonly done by averaging the PSF of the standard star over the observation.

## FIFI-LS

### How to get an upper limit on a FIFI-LS detection?

**A: By averaging multiple fits to single-position ramps**

The best way to estimate the error is by fitting multiple individual ramps at a single position using the raw data, and averaging the results. It is important that this is done using the raw data, as higher-level spectra are smoothed. If telluric features are not correctly removed and appear in the smoothed spectrum, fitting these ramps can result in an over-estimate of the error.

If the target is a point source another method is to evaluate the flux in several positions where no sources are expected. This however, only gives a rough estimate of the error since the pixel response varies across the detector.

### Should I use FIFI-LS or GREAT for \[CII\]?

**A: FIFI-LS (in most cases)**

Unless the line you are targeting is expected to be bright, it will not likely be detected by GREAT. We suggest using FIFI-LS for targeting \[CII\] due to its faster mapping speed. The trade-off, however, is that GREAT has a much higher spectral resolution. If the spectral resolution is critical, GREAT may be the better choice. See observing documentation and [SITE](<https://dcs.arc.nasa.gov/proposalDevelopment/SITE/index.jsp>) for more details.

### What is the beam/psf size of FIFI-LS?
**A: The telescope PSF**

The intrinsic PSF of FIFI-LS is smaller than the PSF from the SOFIA telescope for most of the spectral range. Therefore, the telescope PSF should be the dominating factor for the effective spatial resolution of FIFI-LS on SOFIA. SOFIA's PSF size is highly wavelength dependent. For longer wavelengths, the PSF size is diffraction limited. For shorter wavelengths (<30 um) the PSF depends on diffraction, shear layer seeing, jitter, pointing accuracy, stability and drift (see [Temi et al. 2018](<https://www.worldscientific.com/doi/full/10.1142/S2251171718400111>)). It should also be noted that the pixel size of FIFI-LS is smaller than the PSF, meaning that the data are intentionally oversampled.

### What is the pixel size of FIFI-LS data?

**A: 3" (red channel) and 1.5" (blue), but these pixels are oversampled**

The PSF is oversampled in the FIFI-LS data. The spacing in the spatial dimensions (dx) is fixed for each channel at 3.0 arcseconds in the RED and 1.5 arcseconds in the BLUE. These values are chosen to ensure an oversampling of the spatial FWHM by at least a factor of three. The projected pixel sizes, more representative of the spatial resolution of the data, are 12” in the red channel and 6” in the blue channel.


## The Data and Data Analysis

### What is the boresight?

**A: The window that lets in light.**

The boresight is the rectangular region that light passes through to get to the instruments. The boresight is occasionally calibrated to ensure no loss of signal outside of this window.


### What is the best way to access the FITS header information?

**A: Using python, DS9, or other packages**

If you have astropy installed, and you are interested for example in the "WVZ_OBS" keyword, use the following command in a terminal:

```
fitsheader filename | grep WVZ_OBS
```
or within python:

```
from astropy.io import fits

with fits.open(filename) as hdul:
   header = hdul[0].header
   print(header['WVZ_OBS'])
```

*filename* corresponds to the name of the file (and its absolute path).

You can also see the full header through IRSA. After launching your search, select the desired FITS file in the relevant instrument tab on the left hand side. A Data tab will appear, from which you can access the full header (using the 'information' icon).

### How to get the PWV from the header

**A: FITS header keyword: WVZ_OBS**

PWV stands for precipitated water vapor. This is a measurement of the quantity of water vapor present in the column of atmosphere over SOFIA during the observation. Since the atmospheric telluric lines affect the spectra taken with the SOFIA telescope, it is important to quantify the PWV to correct the spectrum for the atmospheric absorption.

The header of each raw FIFI-LS file in the archive contains several keywords reporting the precipitated water vapor measurement.

Two keywords report the precipitated water vapor as measured by the "water vapor monitor" of SOFIA:
 -  WVZ_STA
 -  WVZ_END

These are the measurements taken at the beginning and end of acquisition of a file. Unfortunately, these measurements are not reliable. The "water vapor monitor" is not very accurate and sometimes does not work at all.

In the latest two years we implemented a direct way to measure the water vapor by monitoring during the flight several atmospheric lines.
The result of the fits of these lines compared to the atmospheric model is conserved in the keyword:
- WVZ_OBS

This value of water vapor is used for the atmospheric correction during the data reduction.

### What version of redux was used to reduce my data?

**A: FITS header keyword: PIPEVERS**

Within the reduced data products fits file there is a [header keyword](#what-is-the-best-way-to-access-the-fits-header-information), PIPEVERS, which lists the redux version.

### What do the quality assurance comments mean, and should I be worried?

**A: Look for Known Problem Codes and obvious words like contamination, problem, or failure.**

SOFIA is aware of several common issues with the data that we denote with 4-letter codes starting with the letter O. We have a [list of the Known Problems](<https://www.sofia.usra.edu/sites/default/files/USpot_DCS_DPS/Documents/DCS_Known_Issues.pdf>) and their associated codes hosted on the SOFIA website. If you are still worried about the quality of the data after identifying any known issues, please contact the Helpdesk (sofia_help@sofia.usra.edu).

Additionally, be aware of Quality Assurance comments with words like: contamination, problem, failure, artifact, degradation, or issue. If the comments include words like acquisition or test, you may not have the correct file.

<!-- ### What does this file extension mean?

**A: It differs for each instrument.**

Typically, a filename follows the template Flight_IS_MOD_AOR-ID_SPECTEL_Type_FN1-FN2.fits, where:

*Flight*: SOFIA flight number </br>
*IS*: instrument identifier </br>
*SPE*: specifies the instrument mode </br>
*AOR-ID*: is the 8 digit AOR identifier for the observation </br>
*SPECTEL*: is the keywords specifying the spectral configuration </br>
*Type*: three letters identifying the product type </br>
*FN1*: is the file number corresponding to the first input file </br>
*FN2*: is the file number corresponding to the last input file </br>

Additional information on common *Types* of Level 3 & 4 data:

**FORCAST Photometry** </br>
COA: Level 2 coadded image </br>
CAL: Level 3 calibrated image </br>
MOS: Level 4 mosaicked image </br>

**FORCAST Spectroscopy** </br>
CRM: Level 3 calibrated spectrum </br>
COA: Level 3 coadded spectrum </br>
CMB: Level 3 combined spectrum </br>
SCB: Level 4 spectral cube </br>

**EXES** </br>
COA: Level 3 averaged spectrum using all frames </br>
CMD: Level 3 combined spectrum </br>
MRD: Level 3 merged spectrum </br>

**FIFI-LS** </br>
CAL: Level 3 flux calibrated data </br>
WGR: Level 3 wavelength_resampled (???) </br>
WXY: Level 4 FIFI-LS data </br>

**HAWC+** </br>
MRG: Level 2 map of merged dithers </br>
CAL: Level 3 calibrated data </br>
PMP: Level 4 map of polarization vectors

**GREAT** </br>
TMB: Level X ? -->

### How do I find out if the data products are the raw or calibrated files?

**A: You can usually use the Level of the data product; Levels 3 and 4 are fully-calibrated.**

Data products come in different levels depending on the processing that has been done. Generally the higher the level, the more calibrated for analysis.


### I can’t tell if my detection is real or noise, what can I do?

**A: Contact the help-desk**

If you have a tentative detection, consult the instrument and data handbooks to ensure the signal is outside of the expected uncertainty. Identify any known problems using the quality assurance comments within the data. If you are still unsure of your detection, contact the SOFIA helpdesk.


## The Observatory

### Where can I access the SOFIA filter curves?

**A: SVO filter service**

The Spanish Virtual Observatory ([SVO](<http://svo2.cab.inta-csic.es/svo/theory/fps3/index.php?id=SOFIA>)) provides filter/transmission curves for many observatories including SOFIA.
