Remote Observing
****************

Introduction
============

Remote observing with the Parkes telescope is the default mode of operation.
Suitably qualified observers can observe from anywhere with adequate connectivity,
from the Marsfield Science Operations Centre (SOC) or from Parkes itself (for complex or non-standard
observations, or in other circumstances where this is the more sensible option).


Remote observing requirements
=============================

The remote observer will need the following:

* An active CSIRO login account ('nexus'). To establish an account, follow the instructions `here <http://www.atnf.csiro.au/cgi-bin/atnfres/ident_request.pl>`_.
  Allow 5 working days for the account to be established.

* To book as an observer for the scheduled observations using the `Observer PORTAL <https://parkes-ops.atnf.csiro.au/PORTAL/index.php>`_,
  under the “Book” tab; see below for an example on how to perform project bookings. Ideally this should be done at least 2 weeks prior to observing.

* To have completed the online Observing induction and have conducted a face-to-face
  induction at the SOC in Sydney (or via video conference) under the supervision
  of a trainer before being qualified as a Remote Observer.

* A computer with the following:
 * Access to the internet;
 * A recent version of a commonly used operating system.
 * A VNC application such as VNC viewer, TightVNC , Chicken of the VNC, Remoter for Mac.
 * A web browser that supports HTML5 and has javascript enabled; supported browsers are: Firefox v16+, Sarafi v6+ and
   Chrome v23+. Internet Explorer v8+.
 * A screen size at least 1920 x 1200 is recommended; a multiple screen setup will be beneficial for more complex observing
   setups for observing from places other than the SOC (i.e., where two instances of TCS are required).

How to book for observing projects
----------------------------------

An example of booking for an observation is shown below.

* Log onto the PORTAL and click on the "Book" tab. The interface should look like that below.

* Click on "Booking details" and enter your details on the left-hand side. This includes information such as your location and any other details
  relevant to the booking in the Comments section. If you are observing for a NAPA or ToO observation,

* To request Green Time, you can double-click on 'Green Time' and enter a project code if known or enter 'PX' if a new observation.

* You can filter against specific projects using the "Select Project" dropdown on the right-hand side.
  Select your project and click on "showFilter". In the example below, future blocks for project P486 are shown. Click on "reloadSched"
  to display all projects. Clicking on the project code in this table will change the calendar view to that starting date.

* Once you have your selected project(s), you will see a "Book" button next to observing blocks. To place your name against any
  block, click on "Book". The PORTAL will process the request and if everything is okay (i.e., you have all relevant details filled out),
  the button will change from "Book" to "Cancel" (see image below.) At this stage booking for the first P486 block is complete and
  you can make subsequent bookings as required. If you navigate to the relevant schedule calendar block(s), your name will be listed.
  Each schedule block in the calendar will show who is observing- those observing from the SOC are indicated in white.

* If you make a mistake- say book against the wrong project, you simply click the "Cancel" button for that observing block.
  Your name will also be removed from the Schedule calendar block.

Remote Observing Support
========================

The remote observer in need of assistance should, in general, consult these in the order given below.

* Online documentation, e.g. the Online User Guide (this document).

* The designated Project Expert. This is equivalent to the DA role at Narrabri, but specific to the project.
  This is usually an expert observer of the Parkes Telescope.

* The Emergency Contact Person (ECP) can be contacted for emergencies only, out of business hours. They are not to
  be contacted for issues relating to observing unless they pose a threat to the antenna safety. They are notified
  by the TPS (see below).

The role of the Remote Observer is to monitor the progress of the observation and the condition of the telescope and
collected data through a variety of interfaces. During the observation, this monitoring is the remote observers' primary
responsibility.

The state of the telescope is monitored by its automated protection system, the TPS (Telescope Protection System). The
TPS monitors the critical telescope systems, and acts in favour of the safety of the telescope if adverse conditions are
detected. Its actions include stowing the telescope or disabling its motion, switching between alternate power sources
for the telescope and initiating observatory staff intervention. Monitoring displays used for observing will inform the
observer of any action taken by the TPS.

VNC setup
=========
.. tip::
   The current VNC password can be obtained from `here < http://www.atnf.csiro.au/observers/passwords/>`_.

Using VNC outside of CSIRO
--------------------------

If necessary, download a VNC client (e.g. TightVNC, Chicken of the VNC, Remoter for Mac).
The following can be setup within the client for 'one-click' connection or manually
through terminals.

Establish an ssh tunnel into ATNF for VNC's use, you will need one tunnel for each screen. With two terminals open, type the following: ::

  ssh your_ident@@orion.atnf.csiro.au -L 5901:joffrey.atnf.csiro.au:5901
  ssh your_ident@@orion.atnf.csiro.au -L 5902:joffrey.atnf.csiro.au:5902

Here, *your_ident* is your CASS *nix account (NOT your NEXUS account). This is a requirement for remote observing.

Now, start the VNC Client on your local computer and connect to 127.0.0.1:5901, which is the VNC display for TCS, LOBOSS, etc.

Next, start another VNC Client on your local computer and connect to 127.0.0.1:5902, which is for backends such as DFB3/DFB4 and MoniCA.


Using VNC from the SOC
-----------------------

Parkes Observing from the Science Operations Center (SOC) is done in a dedicated room with three monitors connected to the machine ``pyxis``.
The username and password can be obtained from SOC observing support. The recommended layout for observing is shown below in FIXME.

FIXME

The VNC servers on joffrey are run as user ``pksobs``.

Once the above is done, open two terminals, one in each screen on the SOC Parkes observing machine (``pyxis``) and  type: ::

 vncviewer joffrey.atnf.csiro.au:1

in the first screen, then in the second, type ::

  vncviewer joffrey.atnf.csiro.au:2





Prior to commencing observing
=============================
Ensure:

   *  You have logged into the Parkes Observing Portal (https://parkes-ops.atnf.csiro.au/PORTAL/index.php) and FROG (https://parkes-ops.atnf.csiro.au/FROG/index.php).
   *  You have contacted the current observing team (or local Parkes staff member) that is listed on the PORTAL chat page.
   *  Following communication with the current observer/staff, clicked on the registration of current observer/staff and entered your details.

Additionally you may require:

* Pulsar Online Monitor: http://www.parkes.atnf.csiro.au/online/psrmon/

*  APSR: http://apsr-srv0.atnf.csiro.au/apsr/
*  BPSR: http://hipsr-srv0.atnf.csiro.au/bpsr/
*  CASPSR: http://caspsr-srv0.atnf.csiro.au/caspsr/

The above three require internal access, if not on a CSIRO network you will need to:

 ssh -L 30000:hipsr-srv0:80 ident@orion.atnf.csiro.au

Where ident is your ATNF *nix account which can be obtained from a link on the login page of the PORTAL. Once you have connected as above, you
point your browser to: ::

 http://localhost:30000/apsr/ , http://localhost:30000/bpsr/ or http://localhost:30000/caspsr/




Observing start up
==================
TCS
---

On ``joffrey:1``, in the first virtual window. If TCS is already running, it is recommended you close it and exit the terminal (especially if
interleaving projects are pulsar and spectral/continuum in nature.) Open a terminal on joffrey and type: ::

 tcs

From the startup GUI, select the relevant mode for your observations (and select the expert mode). Select the relevant recall state if there is one.
For example:

*  For DFB4 spectral--line/continuum observing select:
 **  DIGITAL F'BANK (time binning)
 **  EXPERT MODE
 **  SELECT PROJECT (if present, via bottom menu)
*  For Pulsar observing select:
 **  Pulsar observing modes.
 **  EXPERT MODE
 **  SELECT PROJECT (if present, via bottom menu).
 **  Once open:
  ***  Select PDFB4.
  ***  FOLD or SEARCH MODE
  ***  SELECT relevant schedule
*  Focus: Enable
*  Antenna: Enable

If the antenna doesn't enable, likely it means that either another TCS is still running with antenna enabled (which takes the antenna control) or
other software is controlling the antenna.

* Auxillary: Enable
* Correlator: Enable
* Sched agent: CTRL for Spectral-line/Continuum and GUI for Pulsar
* Sched files (Spectral--line/Continuum observations).
 * Click on Sched file and select OWN, then select the schedule file.
 * For Spectral-line and Continuum projects, schedule files are located in /home/pksobs/Projects/PXXX/ or /nfs/online/local/tcs/sched/pXXX .
 * For Pulsar projects, schedule files are usually located in /psr1/tcs/sched/ .

The indication that this is TCS primary is shown on the title bar of the TCS GUI.

TCS alternative
---------------

On ``joffrey:1``, in the second virtual window. If you are using another instance of TCS (i.e., you are using DFB3/DFB4 simultaneously),
open a ``myrcella`` terminal (right--most terminal icon on taskbar) and type: ::

  start_alt
  tcs alt

If you are NOT using another instance of TCS, you may use this virtual window for other purposes, but note anything you open may be closed at the
start of the next observing session. The indication that this is TCS alt is shown on the title bar of the TCS GUI. It is important to note that
if TCS primary is running DFB3, then the alternative TCS must use DFB4. The same DFB cannot be used by both TCS's. It is important to note the
dummy antenna systems are started by start_alt, otherwise file header parameters will be incorrect.

.. tip::
   Note that start_alt kills existing processes before restarting them.
   For Pulsar projects, schedules such as the following should be used: P456_MB_PDFB4A.sch (note the ``A`` for alternate.)

LOBOSS, LOGUI and OPERFCC
-------------------------

On ``joffrey:1``, in the third virtual window. On the bottom panel, click on "Observing Tools" and start LOBOSS, OPERFCC and LOGUI.


With OPERFCC, you can move a receiver on axis. TCS should do this as long as you have the "receiver" key in your schedule file(s). If using atsnap to drive the antenna, you will
need to place your receiver on focus manually by selecting your receiver and press  "Place selected receiver on axis".

PKMC
----

On ``joffrey:1``, in the fourth virtual window. On the bottom panel, click on "Observing Tools" and start PKMC.

* ``Focus Cabin Switches -> Camera`` TCS should do this, but on PKMC, turn off all cameras but pressing the "Camera" button to red (off).
  ``Failure to do this may cause RFI for your observations``. ``TCS`` and ``FROG`` will also alert you if the cameras are still on. See
  the site.alarms.FCCCams point name under the ``Alarm Manager`` tab.

*  ``Focus Cabin Switches -> Rx`` For all receivers, you should use PKMC to turn your receiver ON/OFF. Click on LNA buttons to turn them GREEN (on) or RED (off)

   .. error::
   If the receiver is labeled "Local or not present" instead of "Remote", you will need to contact local staff. Also, if the System Control label
   is in "Local", contact local staff to place control to "Remote".

* ``Switch Matrix`` This is usually managed by TCS, no user action required. Some non-standard configurations require a special setup.
  If so directed by the support staff you will need to run an smrun script from ``joffrey``: smrun ~/smsetup/pXXX.cmd
  "pXXX" is your project code. Note the filename may be different, check with local operations staff.
  To check whether the Matrix is correctly set, you can check the connections via the Switch Matrix GUI.

*  ``Cal Control Unit`` If Tsys is to be recorded using DFB4  =>  Set the Calibration signal
        *  Managed by ``TCS`` with CALMODE = SYNC keyword in schedule. CALMODE = OFF disables Tsys measurements.
        *  Click "show" of the "Cal Control Unit"
        *  Turn off all cal signals
        *  Turn on cal signal "row  of your receiver => column BEC-Sync0"
        *  The TCS schedule command "enable becc" enables Tsys logging.
        *  This is a spectral-line / continuum option only.

*  If Frequency switching with DFB3 is to be used  =>  Set the Calibration signal (freq sw):
        *  Must be done manually, TCS cannot set this automatically!
        *  Turn on cal signal "Conv Rack Freq SW => column MBCor FreqSW"
        *  Turn off all undesired cal signals
        *  This is a spectral-line / continuum option only.

*  If frequency-switching with MB20 and MBCor is to be used => Set the Calibration signal:
        *  Must be done manually, TCS cannot set this automatically!
        *  Turn on cal signal "MB FreqSW => MBCor FreqSW"
        *  Turn off all undesired cal signals
        *  This is a spectral-line / continuum option only.


DFB4
----

On ``joffrey:2``, in the first virtual window.

If using DFB4, on the bottom panel, click on ``Backend Tools'' (twice) to open two ssh connections to pkccc4. In the first, type ::

  corkill
  spd

Now, in the second terminal, type ::

  sdfb4

for continuum/spectral-line projects, or for Pulsar observations, type ::

  pdfb4

SPD
---
On ``joffrey:2``, in the first virtual window, in addition to dfb4
  Some basic commands ::

  * sel * to see all bandpass data
  * sel 11 to see spectra (DFB only)
  * sel pp11 to see profiles (DFB only)
  * sel aa, bb, cc, dd display Pol A/B, first (aa/bb) and second (cc/dd) IF
  * bins 1 - N time-binning mode only: it shows the first N bins of a time-cycle (DFB only)
  * x toggle "x" axis:  channels <=> frequencies
  * a auto scale amplitude. You can define limits, e.g. a 0 1e3
  * ch x-y show only channels from #x to #y. It is usually useful to skip first and lasts channels, e.g. ch 5-8185
  * avg|noavg to enable/disable time averaging.
  * quit to exit spd.

  .. tip::
     Additional commands for SPD can be found `here <http://www.atnf.csiro.au/people/wwilson/spd_linux.html>`_.

MoniCA
------

On ``joffrey:2`` in the fourth virtual window. On the bottom panel, click on ``Observing Tools'' and start MoniCA.

After selecting the ``Parkes`` site, you can select  the appropriate monitoring GUI from the ``Navigator`` menu. Suggested monitoring items:

*  Navigator -> favourites -> Generators
*  Navigator -> environment -> lightning -> summary_graph
*  Navigator -> pksobs -> site -> currentalerts

.. tip::
   To display multiple panels, click Window -> New window and select the page to display from there.

Observing
=========

Conversion System
-----------------

For spectral-line and continuum projects, to set LO attenuation, in any terminal, type ::

  lorun ~/losetup/pXXX.cmd

where "pXXX" is your project code. Check the ~/losetup directory for a full list.

For Pulsar projects, to set LO attenuation, use specific scripts. For example, type ::

  lorun ~/losetup/mb.cmd

for the 20CM Multibeam receiver, or type ::

  lorun ~/losetup/3100+732.cmd

for the 1050CM receiver.

Check the ~/losetup directory for a full list. For both cases, to check the attenuators are correctly and press REFRESH on LOGUI. Check C12ATT,
C30ATT, C40ATT (if using 64/128 MHz BW), and check C50ATT (if using  256 MHz BW). See if these are set to the desired levels as set in the .cmd file.

Stowing and Unstowing
---------------------

   If you are unstowing the telescope for observing, you must follow the following procedures:

   * Login in and check the chat utility is available on the Observing PORTAL.
   * Check that the Telescope State is set to “OBSERVING” (on the chat utility.)
   * Establish a dialogue with the current contact via phone call from details provided on the chat utility via the Observing PORTAL.
   * Once permission to observe is obtained and the antenna is handed over to you, you need to register as the observer in charge via the Observing PORTAL.
   * Follow the appropriate handover procedure as outlined below.

   With the MCP in Computer Remote, you can stow/unstow the antenna using TCS. Under the "ACTION PANEL"
   (top right of TCS GUI), you press the "Stow" button. Once complete, this will disable the drives in Azimuth
   and for Zenith, the antenna will drive to the Zenith Stop position (~ -0.54 deg) and put in the locking pin.

   .. warning::
      The safety timer will also be disabled.

   To unstow the antenna, press the "Unstow-ExLim" button on TCS, under the "ACTION PANEL" section,
   top right on the TCS GUI. This will remove the Zenith locking pin, drive the antenna out of limits
   and leave both drives enabled. Note again, that the MCP must also be in Computer Remote.

   .. warning::
      You can only start observing with TCS if the antenna is enabled and the Zenith angle is greater than 1.2 degrees.

Get up and running guides
-------------------------



DATA
====

      On any machine, data is located in directories:

      *  /nfs/PKCCC4_1   => DFB4 pulsar
      *  /nfs/PKCCC4_2   => DFB4 spectral-line/continuum
      *  /nfs/PKCCC4_3   => DFB4 pulsar

      .. note::
         Please restrict data processing to machines ``pictor`` or ``lagavulin``.


Telescope Protection System
===========================

The purpose of the Telescope Protection System (TPS) is to only capture issues that would have a major impact if not acted on in a timely manner.
The TPS is a standalone controller which communicates with systems such as power, weather, vibration monitoring, cryogenics and other equipment.
These devices are also connected to MoniCA, which the TPS also references.

Weather and wind restrictions
-----------------------------

With the introduction of the TPS, it will not longer be the responsibility of the observer to concern themselves with monitoring weather conditions,
only data quality. However, observers should be aware what TPS will do in terms of protecting the antenna in terms of bad weather conditions, which
are listed below.

Storm Park
----------

The site.alarms.Lightning[0-4] point names under the ``Alarm Manager`` tab in ``FROG`` shows the alarms range from simply indicating (distant) lightning
has been detected (priority 0-1), through to an alarm indicating you should perhaps consider parking the antenna (priority 3-4). ``FROG`` will sound
an alert for priority level 2 threats or higher. The observer should acknowledge these alarms and act appropriately, or if appropriate, shelve or
de-shelve if required (i.e., if there is a false alarm).

For reference, if using Monica, the lightning threat (trigger) levels are (TPS equivalents in brackets):

* No Threat (No threat)
* Distant Lightning (Low threat)
* Some Lightning (Moderate threat)
* ENABLE GENERATORS (Severe threat)
* STORM PARK (Severe threat)

A lightning threat level of moderate (or greater) triggers the Generator automatic start point in Monica, causing the TPS to start the generator and
run for at least 15 minutes. If after 15 minutes, the lightning threat level is less than moderate the generator will stop and power will revert to
mains (if available), otherwise it will run for further 15 minutes and so on.

If the threat level is moderate and there is no generator ``OR`` the level is severe, the generator will follow the same procedure above, but the
antenna will also be stowed.

Automated Wind Park
-------------------

The ``SERVO``  computer monitors the speed and direction of the wind from the paddock sensor, and will stow the dish automatically above limits
(defined in the table below) to ensure the safety of the antenna. Winds can be monitored with ``FROG``.

================== ===== ==== =======
\                  Peak2 Gust Average
================== ===== ==== =======
Ane #1 (Az front)  58    54   42
Ane #1 (Az front)  58    54   42
Ane #1 (Az back)   46    42   35
Ane #2 (Az front)  66    62   48
Ane #2 (Az back)   53    48   40
================== ===== ==== =======

During an automated wind park, the antenna drives to an Azimuth that has the wind at least 60-degrees away from the back of the dish without
driving into an Azimuth limit.  If you are observing near one of the limits and there is an easterly wind this could involve driving up to 100
or so degrees. In addition, the antenna will drive to a (software limit) Zenith angle of 1.2 degrees.

.. important::
   If the wind is particualry high, the antenna can be driven into the Zenith hardware limit past 1.2 degrees.
   You will need to exit the limit by stowing and then unstow the antenna using the "Unstow - ExLim" button on TCS.

The Peak (2 consecutive readings), Gust (5 readings in the last 180), and  Average (15 readings in the last 20) values (in km/hr) must be
satisfied for a wind park to occur. The ``Az back'' for each Anemometer are for winds within Azimuths 150 degrees < Az < 210 degrees (ie,
winds within 30 degrees of the back of the antenna). The ``Az front'' values are for the remaining 300 degrees ``front-on''sector.
A wind park holds the antenna at the software limit (Ze ~ 1.2 deg.) limit for 10 minutes until the countdown expires. At the end of this period
the antenna is free to obey any pending or new commands.

There is also a "wind park mode" in TCS which is relevant only when using the DFBs in pulsar search mode. If enabled, TCS will attempt to complete
a DFB search mode observation even if the antenna stops tracking due to a wind park, power failure, or manual override from the MCP; this preserves
the continuity of the time series). If the antenna becomes available before the observation has completed TCS will command it to return to the
target position.

.. warning::
   Once an automatic wind park has occurred, the antenna must not be moved until permissible conditions have prevailed for at
   least 10 minutes. If conditions are poor, the antenna must be fully stowed.

Current Park
------------

The wind has a greater effect on the Zenith motor currents of the dish at high Zenith angles and if it is directed either towards the
surface or the back of the dish. The main problem is that a strong wind onto the back of the dish can "hold it down" causing
the motor currents to reverse (the counter weight is heavier than the dish). In this case, you might receive a 'HIGH/LO Current Stow'.
In a physical sense, the low current condition is intended to detect overbalancing of the antenna
when a strong wind blows into the back of the dish. The threshold for the low current condition is three occurances in 120 seconds
where the magnitude between the Zenith motor currents is greater than 30 Amps. For the high current condition to be triggered, the sum of the Zenith
currents must be less than -5 Amps for more than three seconds in the last 120 seconds where the antenna not slewiing upwards.

Once parked, you are required to wait at least 10 minutes to see if the conditions allow for observing to resume. Typically this
is true if the ``peak wind is below 40 km/s``, but it depends on the elevation of your source.

Power Supply
============

You can monitor the Mains and generator power (GenSet) with `Monica <http://www.narrabri.atnf.csiro.au/open-monica/OpenMoniCA.JNLP>`_.
Click on Parkes - Navigator - favourites - generators. Monica should be running on the fourth virtual desktop of
the VNC server, ``joffrey:1`` (you can install MoniCA using the link above). The likely scenarios are dealt with separately below.

Power failure - Brief mains glitch
----------------------------------

In this situation, due to the drive UPS, the MCP and the Azimuth and Zenith
drives will not disable. The MCP remains under computer control.  If the dish
is still in lock capture range of the ME the antenna will reacquire lock and
the drive can resume. On the MoniCA display, you should see the following:

*  LS4 - Mains power available : true
*  GPC31 - Generator start enabled : false

Power failure - Generator starts automatically
----------------------------------------------

If there is a failure of the mains for longer than a second, the generator should start automatically.  Once it is up to speed it will be switched to
supply the antenna. As the MCP is connected to the Drive UPS, the Azimuth and Zenith drives should still be enabled. On the Monica display display,
you should see the following:

*  LS4 - Mains power available : false
*  GPC31 - Generator start enabled : true

If both of these items are false, proceed as described in "Severe Power Failure - no mains or generator".

Severe Power Failure - no mains or generator
--------------------------------------------

When the mains power is available again, and has been stable for a period of around 1 minute, the suppy will automatically revert
from generator to mains. The MCP will remain on and because the generator synchronises with the mains on transfer back to mains power, it happens
without a break, so the UPS suffers no break in input power.

Severe Power Failure - no mains or generator
--------------------------------------------

The TPS continuously checks to see if there is power, whether it be from the mains or site generator. If the TPS does not receive an acknowlegement
that there is power, from the mains OR the generator, the TPS will automatically stow the antenna using the drive UPS.
