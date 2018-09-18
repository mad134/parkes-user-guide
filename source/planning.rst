Planning Your Observations
**************************

Applying for Observing Time
===========================

Parkes-specific information for upcoming semsters and submission deadlines can be found `here <http://www.atnf.csiro.au/observers/>`_,
while current and archived observing schedules can be found `here <http://www.parkes.atnf.csiro.au/observing/schedules/>`_.
Information regarding system capabilities not listed in the above can be addressed to ATNF-Parkes-Remobs[at]csiro.au

Observing Modes
===============

Spectral and continuum-line observations can be performed with all currently-available receivers and back-ends. Possible observing modes include:

* TRACK:  Simply track the position for the specified length of time.  

* LINE-POINT: Execute a 5-point pattern about a target, along with one off-source position for bandpass reference (not currently implemented).

* MX: The position is tracked in turn by each beam (Multibeam receiver only.)

* MXCAL: Observe a calibrator with each beam in turn (Multibeam receiver only.)

* SCAN: The telescope scans from one end to the other at a requested rate.  

* SPOT: Perform a four-point scan (forward/reverse in RA, forward/reverse in DEC), across a source for the purposes of defining pointing 
  offsets and calibration purposes.

* Equatorial-Horizontal Mixed Scans:

 * Here the telescope can perform AZ-EL "spider" scans (..., -90, -45, 0, 45, 90, ...) referenced to an RA/DEC position. 

 * The scans are conducted along the Great Circle passing through the source. Mapping an area in AZ-EL centred on the RA/DEC position is also possible.

* RSCAN/PSCAN:

 * RSCAN is the TCS equivalent to the ATCA RSCAN, where the telescope is continuously in scanning mode between to Azmiuth limits. 
   It has some precision synchronisation so that scans on subsequent days interleave correctly.

 * PSCAN is a variant of RSCAN in that an RSCAN is executed, in Azimuth, followed by a calibration observation. 
   Note that strict LST synchronisation is required. A file defining the cal source and the  Azimuth scan details needs to be consulted before each set.

Position Switching
------------------

There are three methods of switching. Not all methods are available with all receivers/back-ends.

Using the TRACK mode, the telescope alternates between an on and off-source position where the latter is assumed to be free of line emission. 
This mode is typically used for observing molecular lines such as Ammonia and Maser lines. Point-by-point mapping can be done with this mode.

Frequency Switching
-------------------

During an observation, the observing frequency alternates between a pair of frequencies. Both slow and fast modes are
available. This mode is often used for SCANNING on-the-fly observations which look at spatially-extended emission such as wide 
(Galactic HI and narrow hydrogen recombination spectral lines. The second (switched) frequency is used as a reference spectrum which
aids in data reduction and can increase signal to noise by at least a factor of two over the position-switching mode.  The total frequency switch
can be either "in-band" or "out-of-band". The size of the throw depends on the nature of the emission you are seeking. The throw
should be at least 2-3 times the width of the widest profile you might expect in your data. You should also be aware if you are observing
multiple spectral lines within a bandpass, some of the data processing applications such as *Livedata* produce ghosts which may
overlap and be confused with real spectra. For estimating the size of the required throw,  for wide Galactic HI observations, a frequency throw of
about 3 MHz with an 8 MHz bandwidth is the norm.

Beam Switching
--------------

This is currently restricted to Multibeam receivers (MX mode). The position is tracked in turn by each required beam of the 
Multibeam system. This mode is ideal for observing sources such as single galaxies (or multiple if all lie within the beam). When a beam is not 
looking at the source we assume it's collecting a reference spectrum from blank sky.  The prior and following scans are used to form the bandpass 
calibration.

Creating Schedule Files
=======================

For the majority of programs, you will be using the Telescope Control Software *tcs*. The *tcs* graphical user interface (*tcs* GUI)
is written in Glish/Tk and runs on a Linux workstation.  A Glish client runs on the same host as the *tcs* GUI which serves as a communications
channel between the *tcs* GUI and the (Linux) controller.

There are two ways to use *tcs*. The first is to select observing parameters from the *tcs* GUI via widgets and entry boxes. The second (**and recommended**)
is to use schedule files (simple text-files) which contain lists of keys and assosiated values which become the default parameters on the *tcs* GUI. In this way, it is 
possible to control the numerous components of the observing system. These systems include:

* Antenna Control (coord system, observation type)
* Tracking parameters (position, offset type, duration)
* Scanning parameters (scan center, scan range, duration/rate)
* Receiver control (receiver, focus, parallactic angle, feed angle)
* Correlator (mode, configuration)
* Local Oscillator (rest/sky frequency, bandwidth, channels, frequency switching/offset, frame)
* Cal Control Unit (enable/disable cal injection for receiver)
* Back End Controller Computer (enable :math:`T_{sys}` logging)

Until accustomed with the system, first-time users are strongly urged to use schedule files. Detailed information on keywords used in schedule files and
some examples can be found in the `TCS  documentation <http://www.atnf.csiro.au/computing/software/tcs/tcs.html>`_.

However, please note this is seriously out-of-date and you should consult this manual or note there are a number of online utilities which 
allow you to create a TCS schedule file for spectral-line, continuum and pulsar observations. For spectral-line and continuum observations 
there are online tools for

* `Position-switching: <http://www.parkes.atnf.csiro.au/observing/utilities/pswitch.php>`_
* `Tracking: <http://www.parkes.atnf.csiro.au/observing/utilities/track.php>`_ (with/without frequency-switching)
* `Beam-switching: <http://www.parkes.atnf.csiro.au/observing/utilities/track.php>`_
* `OTF-mapping: <http://www.parkes.atnf.csiro.au/observing/utilities/otfscan.php>`_
* `Scanning: <http://www.parkes.atnf.csiro.au/observing/utilities/otfscan.php>`_ (with/without frequency-switching), or
* `Calibration: <http://www.parkes.atnf.csiro.au/observing/utilities/spot.php>`_

For each form, there is help associated with each field, which the user fills in according to 
requirements. Below, we show two mapping examples as part of a ficticious project to characterise the
RCW41 HII region; one for continuum/polarisation at 2.8GHz and the other spectral-line,
looking at the first four transitions of the ammonia line. For Pulsar observations, there is an 
online tool for creating a PDFB pulsar schedule which contains instructions on how to go about 
producing a schedule from scratch. It is available `here <http://www.parkes.atnf.csiro.au/observing/utilities/pulsar_sched/>`_.

Spectral-line and Continuum Observations (non-pulsar)
=====================================================

Continuum/Polarisation Example
------------------------------

In this example, we will be using the 10CM concentric receiver (part of the 1050CM package) to create a 30x30 arcmin full stokes 
(allowing polarisation analysis) continuum map of the RCW41 HII region at 2.8GHz, using DFB3 with a bandwidth of 128MHz with 
8192 channels. We **disable** Tsys logging here as it contributes to the system noise. Actually, we should create two maps, 
the first consisting of a series of scans in RA (constant DEC), as done here, and the second map consisting of a series of scans in DEC 
(constant RA).  This basket-weaving allows for the removal of scan-line patterns, or *stripes* from single-dish radio maps. The width 
between adjacent scans in both maps is 60 arcseconds (1/6th of the 10CM beam). We will be using the online 
`OTF schedule tool <http://www.parkes.atnf.csiro.au/observing/utilities/otfscan.php>`_. The input parameters  to the online tool are shown below.

FIXME

Note this is only for the RA (constant DEC) scans. This is saved to your computer as a text file then uploaded to the Parkes computers 
before you start observing. According to the output, it will take approximately 70 minutes to complete the RA scans, plus another 70 
minutes for the DEC scans.

Spectral-line Example
---------------------

In this example, we will again map the RCW41 region, but this time, we will use the 13MM receiver
to map the Ammonia (1,1), (2,2) and (3,3) transitions. Again we will be using DFB4, the configuration will use 
256MHz bandwidth with /8192 channels. The observing method is the On-The-Fly Mapping. Here, the map is created by 
interleaving a reference position (done in TRACK mode), with scans across the region of interest. 
Note the reference position is assumed to be free of line-emission! In addition, we are only mapping 
a 10x10 arcminute region of RCW41. The width between adjacent scans is 20 arcseconds, or 1/3rd of
the 13MM beamwidth. We assume the RCW41 core is moving 3.7 km/s with respect to the LSR and so 
doppler tracking is enabled. The input parameters to the online tool are shown below.

FIXME

This is only for the RA (constant DEC) scans, which will take around 180 minutes to do, plus another 180 if we also (should) do the DEC scans.

Pulsar Observations
===================

A PDFB pulsar schedule can be created using `this tool <http://www.parkes.atnf.csiro.au/observing/utilities/pulsar_sched/>`_.
The web page contains instructions on how to go about producing a schedule from scratch. When completed, save the schedule and 
transfer it to a location that TCS can access and load. In filling out the form, the valid PDFB correlator configurations for both
FOLD and SEARCH modes are listed in the online tool.

Radio-Frequency Interference Considerations
===========================================

An RFI monitoring antenna sits FIXME. It monitors the frequency range 700 - 3000 MHz once every 20 seconds, with 2 MHz frequency resolution, 
and presents its data in `near-real time <https://www.narrabri.atnf.csiro.au/observing/rfi/weathermap_parkes/>`_ with a clickable
version available `here <https://www.narrabri.atnf.csiro.au/observing/rfi/monitor/rfi_monitor.html#parkes>`_. Three 
different plots are presented on the page: a “latest spectra” plot, a waterfall plot showing the last hour of data, and a polar skyplot 
that may help in determining the direction in which RFI is being generated.  Examples are shown below. The latest spectra plot always shows 
two of the most recent spectra obtained by the monitor, along with a “maximum hold” value for each channel over the last hour. The waterfall 
plot is useful for seeing emission switch on or off over the last hour. All data from the RFI monitor is archived from approximately 
November 2014. It is possible to `query the RFI database <https://www.narrabri.atnf.csiro.au/observing/rfi/monitor/rfi_monitor_archive_query.html>`_.

.. |rfi1| image:: ../../images/rfi_weathermap_spectra.png
.. |rfi2| image:: ../../images/rfi_weathermap_waterfall.png
.. |rfi3| image:: ../../images/rfi_weathermap_skyplot.png

+--------+-----------+--------+
| Spectra| Waterfall | Skyplot|
| |rfi1| | |rfi2|    | |rfi3| |
+--------+-----------+--------+

An introduction to site RFI and past surveys at the site is available `here <http://www.parkes.atnf.csiro.au/observing/rfi/>`_.

FIXME: Solar Interference - Ettore's report for MB20?


Standing Wave Reduction
=======================

For Parkes, characteristic small-scale ripple with periodicity 5.7 MHz arises from multiple reflections in the 26m space between 
the vertex at one end, and the focus and/or underside of the focus cabin at the other. @ref{fig:standwave} shows 22 GHz 
observations of a strong Ammonia source, G316.819, showing strong (1,1) and (2,2) transitions for 4 minutes (exact multiple of 
60 seconds). The two observations were taken one after the other, the first (upper panel) with no special 'de-rippling' 
measures, the lower taken in a mode where the receiver is moved cyclically up and down in the translator Y-axis to 'smear out' 
the ripple with amplitude 6.3mm peak-to-peak (:math:`\lambda/2`) and period 60 seconds. This technique is available for use 
with higher-frequency receivers only and proposers should contact Parkes Operations, ATNF-Parkes-Remobs[at]csiro.au before 
submitting proposals.

.. image:: ../../images/ripple.jpg
   :height: 300px
   :alt: Upper panel showing characteristic 5.7 MHz standing wave interference with lower panel showing a cleaner spectrum obtained with receiver cycling.

Dish Surface Quality
====================

A 4 GHz holography survey of the dish surface was performed prior to the 1995 upgrade of the focus cabin. The report is available
`here <http://www.atnf.csiro.au/observers/memos/d96f83~1.pdf>`_.

Other surveys at 3.95 GHz (June 1996) and 12.75 GHz (July 1996) were performed after the installation of the new focus cabin. These reports and
details of the readjustment of the inner 44m of the Parkes reflector in December 1996 are  available 
`here <http://www.atnf.csiro.au/people/Michael.Kesteven/PKS_HOLO/pks_holo.html>`_ and
`here <http://www.atnf.csiro.au/people/Michael.Kesteven/PKS_HOLO/surface_adjust.html>`_.

As part of the NASA Mars tracking contract in 2003/2004, the Parkes Telescope's surface was upgraded to make it more reflective and sensitive at 
X-band :math:`\sim` 8.5 GHz. The surface upgrade improved the telescope's performance by about 1 dB (or 25%). A technical report is available
`here <http://www.parkes.atnf.csiro.au/news_events/surface_upgrade/panel_report.pdf>`_.
