# aperture_effects
<h1>Aperture effects in Galaxy Mass Estimation</h1>

One of the most widely used Galaxy Mass catalogues,
the [MPA-JHU catalog](https://www.sdss.org/dr15/data_access/value-added-catalogs/?vac_id=mpa-jhu-stellar-masses), relies on SDSS (Sloan Digital Sky Survey) spectra and SDSS photometry to constrain galaxy masses.

The [SDSS spectra](https://www.sdss.org/dr12/spectro/) are taken using optic fibers with
an angular diameter of 180 micrometers, i.e. spanning 3 arcseconds
in the sky. Thus the spectra are obtained for only a fraction
of the galaxy.

With the advent of [Integral Field Units](https://www.sdss.org/dr13/manga/manga-tutorials/what-is-ifu-spectroscopy/), we can now obtain spatially resolved spectra of galaxies that will allow us to test the aperture effects
in galaxy mass estimation.The largest IFU-based survey currently underway is
MaNGA (Mapping Nearby galaxies at Apache Point) and I use 6000
galaxies from MaNGA and employ the same mass estimation as the MPA-JHU
at multiple apertures.

<figure>
    <center>
        <img src="images/manga_schematic.jpg"
			 alt="manga_schematic"
			 width = "500"/>
        <figcaption><i>Schematic of MaNGA IFU and the spatially
        resolved spectra obtained thus </i></figcaption>
    </center>
</figure>


<figure>
    <center>
        <img src="images/manga_9890_12702.png"
			 alt="manga_9890_12702"
			 width = "500"/>
        <figcaption> <i>A sample MaNGA galaxy viewed
         through the IFU </i></figcaption>
    </center>
</figure>

<h2> Getting a Multiple Aperture View </h2>

<figure>
    <center>
        <img src="images/gal_aperture_redshifts.png"
			 alt="gal_aperture_redshifts"
			 style="width: 500px;"/>
        <figcaption><b> The 3'' view of the same galaxy at
         multiple reshifts </b></figcaption>
    </center>
</figure>

<h2> How offset are the indicators at varying apertures? </h2>
