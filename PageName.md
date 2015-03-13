# Introduction #

The phoenix asteroids project for 2013 involved the Boulder Astronomy and Space Society exploring offering the core of an internship to local high school students. The overall goal of the project was to explore astrometry under less than ideal front-range Colorado skies in conjunction with the OSIRIS-REx project.

The main issue came down to no bright OSIRIS-REx asteroids were available for the equipment we were using.

The project involved automating the process of planning, observing, taking and managing data, reducing data, reporting data and developing documentation for all the steps and scripts used.




# Details #

The planning process uses a ~/RawData directory with a etc/ subdirectory.
The mpcbash script was developed to get the observing ephemerides from the Minor Planet Center and message the data into a tabular format for use at the telescope. A script pair gettargs/jplexpect was developed to get data from the JPL HORIZONs database. In both cases these data were processed with the csv2report script to generate a csv file; then the csv file was processed with csv2tex to produce a pdf via LaTeX.

The coordinates were examined for each target asteroid, and ds9 was used to acquire a reference survey image with WCS and a catalog of stars (Usually the UCAC4 catalog for astrometry or the GCS 2.3 for magnitudes).

These and other pertinent files were deposited into the etc/ sub-directory for use at the telescope.

More to come...