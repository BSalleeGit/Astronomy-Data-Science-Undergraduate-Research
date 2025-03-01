# Undergraduate-Research
# Project Overview:
This project shows my personal contributions to the Astronomy research paper: [Validation of the Bond et al. (2010) SDSS-derived kinematic models for the Milky Way’s disk and halo stars with Gaia Data Release 3 proper motion and radial velocity data](https://www.aanda.org/articles/aa/full_html/2024/08/aa49653-24/aa49653-24.html). The work was done under the supervision of [Željko Ivezić](https://www.lsst.org/about/team/lsst-director), Director of the Vera C. Rubin Observatory Construction Project and professor at the University of Washington. The purpose of the paper was to model, visualize, and confirm the measurements for a set of 3 million stars within the Milky Way Galaxy as well as over 300,000 quasars. These measurements can then be later used at the [Vera C. Rubin Observatory](https://rubinobservatory.org/) to speed up the processing time of new data and measurements gathered by the observatory during the Legacy Survey of Space and Time ([LSST](https://rubinobservatory.org/explore/how-rubin-works/lsst)) where over 60 petabytes of data are expected to be gathered over the project's lifetime.

My contributions to the paper are spread across the three parts in this repository. 

1) The first part involved querying the European Space Agency's [Gaia database](https://gea.esac.esa.int/archive/) to gather info on specific features of a selection of stars within the Milky Way. Using this data I produced a series of Hertzsprung-Russell diagrams which were color-coded by four properties we were interested in visualizing, the count of stars per pixel, star age, star metallicity (FeH), and the star's reddening. Several Mollweide distribution plots of these four groups were then created to visualize the distribution of these stars across the night sky as seen from Earth. 

2) The second part involved querying multiple catalogs from the Gaia database and crossmatching them to our base sample of stars to produce a dataset covering the various measurements, physical properties, and error ratios of those measurements for our star sample. This dataset was given to other members of the team so that they may use it for their own analyses for other parts of the paper. 

3) The third part involved filtering our star sample and dataset to a range of stars between the distances of 400 - 600 pc (parsecs, a unit of distance used in astronomy). I then used this new set of ~800,000 stars and visualized them in polar plots to show their locations upon the sky and separated them by a set of 3-dimensional velocity measurements that were gathered during part 2. 


# Installation & Setup:
I would **strongly** recommend not attempting to recreate this project as there are dependencies on astronomy specific packages that are required to run parts of the project. All of the astronomy packages are free to use and operate in ways similar to more common languages/packages (for example: Astroquery is used in much the same way as SQL), but the time involved in the set-up and execution of unique packages and the large amount of data points (3 million unique stars with multiple features each) may simply not be worthwhile. Viewing the notebook is a much quicker way to sufficiently understand the project.

## Resources Used:
**Editor Used:** Jupyter Lab 3.3.2

**Python Version:** 3.9.18

## Python Packages Used:
**Data Gathering:** [Astroquery](https://astroquery.readthedocs.io/en/latest/) (a SQL-based package for querying astronomical databases)

**Data Manipulation:** Pandas, NumPy

**Data Visualization:** Matplotlib, [Healpy](https://healpy.readthedocs.io/en/latest/)

**Machine Learning:** [AstroML](https://www.astroml.org/) (a Python module for statistical analysis, machine learning, and data mining for astronomy)



# Data
## Source Data
**Part 1 - Gold Sample FGKM:** The notebook of my first contribution to the paper. Involves gathering the initial star sample and desired properties of them before creating color coded Hertzsprung-Russell and Mollweide diagrams of the sample.

**Part 2 - Measurements & Properties Dataset:** The notebook of my second contribution to the paper. Involves querying multiple catalogs on the Gaia database to produce a dataset of various properties and measurements for the star sample. This dataset was provided to the rest of the team to perform their own analyses with.

**Part 3 - FGKM Proper Motion & Radial Velocity Plots:** The notebook of my third contribution to the paper. Involved using the filtered master dataset (400-600pc data file) to a series of polar plot to visualize the star's 3-dimensional velocity measurements.

**Final Paper - Validation of the Bond et al.:** A PDF of the final published research paper as found on either the Astronomy & Astrophysics Journal database or the Arxiv archive. My contributions can be seen in Figures 1, 9, and 10 as well as sections 2,0, 3.3, and the Appendix.

**[MWKinematicsFGKM](https://github.com/sidchaini/MWKinematicsFGKM):** Repository with public data access to reproduce the results of the entire paper, not just my own contributions. 


## Data Acquisition
All of the data was acquired by using [Astroquery](https://astroquery.readthedocs.io/en/latest/) (a SQL-based package for querying astronomy databases) to access the European Space Agency's [Gaia database](https://gea.esac.esa.int/archive/) to gather our initial star sample. Various catalogs within the Gaia database were then queried and crossmatched with the IDs for our star sample to produce matching data for the variety of measurements and physical properties needed for further analysis with our star sample.

## Data Preprocessing

For the creation of the Hertzsprung-Russell diagrams in Part 1, [AstroML](https://www.astroml.org/) was used to create the bins for each pixel from the Gaia data. AstroML used a binned 2d statistic to compute the mean of the values of points within the bins; basically creating a generalization of a histogram 2d function so that we could plot our 3 million data points, each representing a single star.

For the creation of the polar plots in Part 3, a series of special functions from the [Healpy](https://healpy.readthedocs.io/en/latest/) package were used to create bins from the various measurements for the pixels so that could then be properly plotted on a sphere. I ran into many issues with pixels not properly displaying on the spheres, but creating a mask for each plot solved the issue. There remain some spots on the plots with missing data, the largest of which can be explained by a blindspot of the Gaia spacecraft and its instruments as it rotated and gathered data, the rest are simply missing values for our distance selection and have been masked over for the sake of plot visibility.

# Results & Evaluation

For disc stars, the Gaia data validated the SDSS data from 0-5 kpc (kiloparsec), and for halo stars the Gaia data validated the SDSS data out to 15 kpc. This means that our work confirms that the Bond et al. kinematic models are  sufficient for use in simulated catalogs of the Milky Way's stars, such as those that will be used by the LSST, and can be successfully implemented in the LSST's data pipelines for processing the raw data collected. 


# Future Work
The LSST, based in part from this data, will provide its own kinematic constraints on main-sequence stars out to distances of about 30 kpc, significantly further than possible with Gaia data. The LSST will eventually create a 20 petabyte data catalog and the total data volume after processing will be several hundred petabytes made available across multiple data releases. 

# Acknowledgments
I would first like to acknowledge and thank [Professor Željko Ivezić](https://www.lsst.org/about/team/lsst-director) for the opportunity to work with him on this paper and for his guidance and insight throughout it.

I would also like to acknowledge and thank the other collaborators who worked on this paper with Professor Ivezic and I;  Bruno Dominguez, Siddharth Chaini, and Karlo Mrakovci. 
