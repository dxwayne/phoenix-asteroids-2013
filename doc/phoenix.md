Phoenix Asteroids 2013
======================

2017-08-30T21:47:10-0600

This repository is the result of doing some OSIRIS/REx asteroid
observations during the summer of 2013. This code is offered for
use by other asteroid investigators.

note: The project started under the Google code repository, and
was exported to github. In the intervening years, a line was
added to the jplexpect script and the widespread use of
Markdown was implemented.

This revision does not really change the project, but brings it
back up to date.


Name mpcbash
============


Synopsis
--------

	mpcbash <asteroid> [<record count>]

Description
-----------

To get the asteroid’s cphemerides from the Minor Planet Center for the
given asteroid for a given number of records. The asteroid designation
should follow the MPC name guidelines. The optional record count is
for ten minute intervals, defaulting to 1440 to supply ten days of
predictions. The starting date defaults to “tomorrow” (man date). This
works well for the continental United States. Change scripts to your
needs.

Output
------

Output is an ASCII report converted from HTML output by 
html2text (man html2text). Saves to <asteroid>_mpcresults.txt.

...
2013 08 15 021000 19 11 46.4 +38 00 38    ...
2013 08 15 022000 19 11 46.4 +38 00 34    ...
2013 08 15 023000 19 11 46.4 +38 00 30    ...
2013 08 15 024000 19 11 46.4 +38 00 26    ...
2013 08 15 025000 19 11 46.4 +38 00 22    ...
...

Column 3 is hhmmss, where hh is hours, mm is minutes and ss is seconds.


Examples
--------

mpcbash 3581
	Next ten days of cphemerides for asteroid 3581.

mpcbash 3581 144
	Next 24 hours of information.

mpcbash 3581| && cat 3581_mpcresults.txt | awk '/^20/ { print $1, $2, $3, $4; }'

Notes
-----
The script is hardwired for Sommer’s Bausch Observatory code = 463.

Authors
-------
Wayne Green, Ashley Lopez, Trey Wager, Steve Hartung

Reporting Bugs
--------------
 See github phoenix-asteroids-2013.

Copyright
---------
2013 new free BSD license

See Also
--------
gettargs, jplexpet, mpcbash, csv2tex, csv2report

Name csv2report
===============
  dig data from JPL, mpc and APASS files.

Synopsis
---------

csv2report <textfile>

Description
-----------

The csv2report script take output from jplhorizons web query or output
from jplexpect and produces a comma separated file. The script also
accepts output from mpcbash and the AAVSO APASS Catalog.  Output from
csv2report can then be passed to csv2tex

Examples
---------

csv2report 3581_jplresults
csv2report 3581_mpcresults
csv2report ds9.apass.catalog

Authors
-------

Wayne Green, Ashley Lopez, Trey Wager, Steve Hartung


Copyright
---------
2013 new free BSD license


See Also
--------

gettargs - jplexpet, mpcbash, csv2tex, csv2report

Name gettargs
=============

Synopsis
--------

gettargs <list of targets>

Description
-----------

Create a separate text file with each asteroid target,one per
line. Then supply the list to gettargs. The script gettargs supplies
each target in turn to the jplexpect script (man jplexpect).

Examples
--------

list.txt :
3518
Ceres
Themis
Toutatis
<eof>

gettargs list.txt

The script will produce a series of files, one per asteroid. Example : 3518_jplresults.txt.

Authors
-------

Wayne Green, Ashley Lopez, Trey Wager, Steve Hartung

Copyright
---------
2013 new free BSD license


See Also
--------

gettargs - jplexpect, mpcbash, csv2tex, csv2report

Name jplexpect
==============

Synopsis
--------

jplexpect <asteroid id> <start time> <end time> <step size> <center>

Where: asteroid id is JPL’s asteroid number; start time is JPL time
format YYYY-MM-DD hh:mm; step size is in minutes; center is
observatory code.

Description
-----------

The jplexpect script is written in “expect” (man expect). The script
performs a telnet connection to horizons.jpl.nasa.gov on port
6775. Change defaults as needed. Default answers to the prompts are
built in.

Examples
--------

jplexpect 3581 “2013-08-15 0:00” “2013-08-16 0:00” 10m 463

Output is in 3581_jplresults.txt.

If you create a file with one asteroid per line and use the gettargs
script, each asteroid will be sent to the jplexpect script in a batch
mode.

Authors
-------

Wayne Green, Ashley Lopez, Trey Wager, Steve Hartung

Reporting Bugs
--------------

See the Google code project: phoenix-asteroids-2013.

Copyright
---------

2013 new free BSD license

See Also
--------

gettargs, jplexpet, mpcbash, csv2tex, csv2report