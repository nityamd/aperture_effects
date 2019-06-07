# aperture_effects
The following is a description of the context of the code and the problem statement. The notebook describes the calculation for a single galaxy, how <i>aperture_spec.py</i> works and how to use <i>aperture_spec.py</i> to obtain multiple aperture measurements of any spectral indicator for any galaxy.

<h1>Aperture effects in Galaxy Mass Estimation</h1>

One of the most widely used Galaxy Mass catalogues,
the [MPA-JHU catalog](https://www.sdss.org/dr15/data_access/value-added-catalogs/?vac_id=mpa-jhu-stellar-masses), relies on SDSS (Sloan Digital Sky Survey) spectra and SDSS photometry to constrain galaxy masses.

The [SDSS spectra](https://www.sdss.org/dr12/spectro/) are taken using optical fibers with
an angular diameter of 180 micrometers, i.e. spanning 3 arcseconds
in the sky. Thus the spectra are obtained for only a fraction
of the galaxy.

With the advent of [Integral Field Units](https://www.sdss.org/dr13/manga/manga-tutorials/what-is-ifu-spectroscopy/), we can now obtain spatially resolved spectra of galaxies that will allow us to test the aperture effects
in galaxy mass estimation.The largest IFU-based survey currently underway is
[MaNGA (Mapping Nearby galaxies at Apache Point)](https://www.sdss.org/surveys/manga/) and I use 6000
galaxies from MaNGA and employ the same mass estimation as the MPA-JHU
at multiple apertures.

<figure>
    <center>
        <img src="images/manga_schematic.jpg"
			 alt="manga_schematic"
			 width = "500"/>
        <figcaption><i>Schematic of MaNGA IFU and the spatially
        resolved spectra obtained.&nbsp;</i></figcaption>
    </center>
</figure>

<h1> Getting a Multiple Aperture View </h1>

<figure>
    <center>
        <img src="images/manga_9890_12702.png"
			 alt="manga_9890_12702"
			 width = "500"/>
        <figcaption> <i>A sample MaNGA galaxy at a redshift of z = 0.0392 viewed
         through the IFU; Image Credit: Dana Berry / SkyWorks Digital Inc., David Law, and the SDSS collaboration.</i></figcaption>
    </center>
</figure>

For every such galaxy, the output of the data reduction pipeline is a "datacube", a 3D array with 2 spatial dimensions and one spectral
dimension. We study the galaxy properties, thus in this so-called spaxel (spatial + pixel) space. For the galaxy shown above, I have
plotted the flux as a function of the spaxel space in the following plot. The circles show the 3'' view of the galaxy (akin to what
  the SDSS spectra would see) if the galaxy were shifted to higher redshifts.

<figure>
    <center>
        <img src="images/gal_aperture_redshifts.png"
			 alt="gal_aperture_redshifts"
			 width = "500"/>
        <figcaption><i> The 3'' view of the same galaxy at
         multiple reshifts </i></figcaption>
    </center>
</figure>

<h1> How offset are the indicators at varying apertures? </h1>

For any MaNGA galaxy at redshift z<sub>obs</sub>, we can thus simulate what the SDSS Main Sample spectrum would have looked like if it had observed the galaxy at that redshift or any higher redshift. We simply calculate the spectrum within an aperture that is 3′′ diameter (if we are simulating the Main Sample spectrum at z<sub>obs</sub>) or larger (if we are simulating the spectrum at a larger z). For any spectral measurement we can then compare the measurement of the total spectrum in the MaNGA cube to that which would have been measured through a 3′′ aperture at a given redshift.

Since galaxies come in a range of sizes and spectral profiles, this difference will vary from galaxy to galaxy and we must look at a large sample. Importantly, for a chosen redshift z<sub>new</sub> at which to evaluate the degree of bias, we can only use a sample of galaxies with z<sub>obs</sub> ≤ z<sub>new</sub>.

Two key spectral indicators used in estimating galaxy masses in the MPA-JHU catalog are the Balmer Delta absorption line and the
4000 Angstrom break in galaxies. For the 6000 MaNGA galaxies surveyed so far, I use <i>aperture_spec.py</i> to estimate these indicators. The plot shown below shows how the 3'' measurements at the redshift of the galaxy compares to the full aperture measurement at three z<sub>new</sub> redshifts.

<figure>
    <center>
        <img src="images/varying_apertures.png"
			 alt="varying_apertures"/>
        <figcaption><i> A comparison of full aperture vs 3'' measurements of the two key spectral indicators that go into the galaxy mass calculation as per the MPA-JHU method.</i></figcaption>
    </center>
</figure>
