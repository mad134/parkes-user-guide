Preface
#######

About this Guide
================
This manual describes how to apply for observing time, plan and carry out observations and the data access protocols for the CSIRO Parkes Radio Telescope.

A PDF version is available `here <http://www.parkes.atnf.csiro.au/observing/documentation/pks_userguide/ParkesUserGuide.pdf>`_ . 

This manual is a reference guide and it is not necessary that it be read to completion in order to use Parkes. Chapter 1 describes the telescope and the observatory grounds. Chapter 2 details the various receiver and correlators at Parkes. Information in this chapter can be useful for any planning of science proposals and/or upcoming observations. Chapter 3 deals with applying for and planning with Parkes. Chapter 4 goes into detail regarding remote observations and what is needed to be done before and during your observations. Finally, Chapter 5 gives a short introduction to data storage, handling and reduction.

**If you find that this guide does not accurately describe the correct usage of Parkes or its subsequent systems, please email the Parkes Users Guide (PUG) editorial team at <xxx_userguide@atnf.csiro.au>.
Comments to the documentation are especially welcomed.**

Conventions
===========

Please note the following conventions are used throughout this document.

* Computer system names, e.g., **joffrey**

* Software packages, e.g., ``Miriad``

* Software program, e.g., ``TCS``

* Command tip example, e.g.

.. tip::
   df -h

* Filename and path, e.g. ``nova.conf`` is located in ``/nfs/online``

.. * GUI element, e.g., Please enable the :guilabel:`Antenna` widget on ``TCS``.

* Keyboard key combination, e.g., Press ``Ctrl+A`` to switch between services.

.. * Menu sequence, e.g., Go to :menuselection:`Project > Compute`

* Placeholder for changeable parameter, e.g. ``medusa#``

* Optional parameter, e.g. [#]

* Observing hints, attention and warnings, e.g.

.. note::
   This is an observing hint.

.. warning::
   This is a warning message.

* Source code snippets, e.g.

.. code-block:: python

    In [69]: lines = plot([1,2,3])

    In [70]: setp(lines)
      alpha: float
      animated: [True | False]
      antialiased or aa: [True | False]
      ...snip
