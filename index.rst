..
  Technote content.

  See https://developer.lsst.io/restructuredtext/style.html
  for a guide to reStructuredText writing.

  Do not put the title, authors or other metadata in this document;
  those are automatically added.

  Use the following syntax for sections:

  Sections
  ========

  and

  Subsections
  -----------

  and

  Subsubsections
  ^^^^^^^^^^^^^^

  To add images, add the image file (png, svg or jpeg preferred) to the
  _static/ directory. The reST syntax for adding the image is

  .. figure:: /_static/filename.ext
     :name: fig-label

     Caption text.

   Run: ``make html`` and ``open _build/html/index.html`` to preview your work.
   See the README at https://github.com/lsst-sqre/lsst-technote-bootstrap or
   this repo's README for more info.

   Feel free to delete this instructional comment.

:tocdepth: 1

.. Please do not modify tocdepth; will be fixed when a new Sphinx theme is shipped.

.. sectnum::

.. TODO: Delete the note below before merging new content to the master branch.

.. note::

   **This technote is not yet published.**

   As part of the effort to maintain an up-to-date system performance model, we have been collecting all the as-built optical data. These data are integrated into a Zemax optical model, and used for system-level performance analyses and trade studies.

   This tech note describes these data, and how they are used in the Zemax model. The detailed performance analyses and trade studies are not within the scope of this tech note.

.. Add content here.
.. Do not include the document title (it's automatically added from metadata.yaml).

############
Introduction
############


The Rubin Observatory Construction Project maintains an integrated model of its optical system.
This has been proven to be useful in evaluating the aggregated impacts on its system performance.
In this tech note, we describe the as-built optical data for each optical component of the integrated Rubin Observatory system.
These data were collected at each component's factory acceptance testing.
Their usage in the system model has been approved by the respective subsystem scientists.

We also briefly discuss how the data are used in the system model. The software being used is Zemax.
The version of the model describe in this tech note is v3.12.
All the relevant files are found in `this DocuShare Collection <https://docushare.lsstcorp.org/docushare/dsweb/View/Collection-10042>`__.
For notes on older versions of the Zemax model, see `this confluence page <https://confluence.lsstcorp.org/display/SYSENG/As-built+optical+model>`__.
LSE-11 :cite:`LSE-11` is the summary document for the Rubin Obsevatory optical design.

Note that there are many other factors that could affect the system image quality. Examples include vibrations in the system and dome seeing.
For complete lists, see LTS-123 :cite:`LTS-123`, LTS-124 :cite:`LTS-124` for the Telescope and Site Subsystem,
and LCA-17 :cite:`LCA-17` for the Camera Subsystem.
Those are not addressed in this tech note, because they are not due to optical fabrications.

The detailed performance analyses and trade studies are not within the scope of this tech note.

####
M1M3
####

The M1M3 glass mirror was casted and polished at the University of Arizona Richard F. Caris Mirror Lab (RFCML).

Radius of Curvature and Conic
=============================

The Radii of Curvature (ROC) of M1 and M3 were measured at 21 C at the Richard F. Caris Mirror Lab of
the University of Arizona :cite:`Document-17506`.
The specificiations were also for T = 21 C :cite:`LTS-50`.
11.5 C is the average operating temperature on the summit, based on LTS-54 :cite:`LTS-54`.
We therefore correct the measured ROC of M1 and M3 to T=11.5 C and use those values in the integrated Zemax model.
The conversion was done with Finite Element model, where the main impact factor is the Coefficient of Thermal Expansion (CTE) of the glass.
The values below are also found in
`LCR-1036 <https://project.lsst.org/groups/ccb/node/1833>`__ and on
`this confluence page <https://confluence.lsstcorp.org/pages/viewpage.action?spaceKey=SYSENG&title=Optical+Design+Final+Optimization+-+Camera+Lens+Spacings>`__.

.. _table-m1m3-roc:

.. table:: M1M3 ROC.

    +----------+----------------------------+--------------------------+------------------------------------------+
    |          | Measured (mm) T=21 C       | Spec (mm) T=21 C         | Measured (mm) corrected to T=11.5 C      |
    +----------+----------------------------+--------------------------+------------------------------------------+
    | M1 ROC   | 19835.1 :math:`\pm` 0.2    | 19835.5 :math:`\pm` 1    | 19834.6 :math:`\pm` 0.2                  |
    +----------+----------------------------+--------------------------+------------------------------------------+
    | M3 ROC   | 8344.1 :math:`\pm` 0.1     | 8344.7 :math:`\pm` 1     |  8343.9 :math:`\pm` 0.1                  |
    +----------+----------------------------+--------------------------+------------------------------------------+

The conic constants of M1 and M3 were also measured at the Richard F. Caris Mirror Lab of
the University of Arizona :cite:`Document-17506`.
The specifications are found in LTS-50 :cite:`LTS-50`.

.. _table-m1m3-conic:

.. table:: M1M3 Conic Constants.

    +----------+----------------------------+--------------------------+
    |          | Measured                   | Spec                     |
    +----------+----------------------------+--------------------------+
    | M1 Conic |-1.21502 :math:`\pm` 0.00011|-1.2150 :math:`\pm` 0.0002|
    +----------+----------------------------+--------------------------+
    | M3 Conic | 0.15497 :math:`\pm` 0.00005| 0.1550 :math:`\pm` 0.0001|
    +----------+----------------------------+--------------------------+


M1M3 Polished Surfaces
======================

The M1M3 surfaces were measured at the Mirror Lab interferometrically under the test tower.
There were localized features on the surfaces, called crows' feet :cite:`Document-17171`, which were measured using the Slope-measuring Portable Optical Test System (SPOTS).
Final surfaces including both the lower order polishing errors and the crows' feet are shown in Figure :ref:`fig-m1m3`.

.. figure:: /_static/m1m3.png
   :name: fig-m1m3
   :target: ../_images/m1m3.png
   :alt: The polished M1M3 surfaces as measured by the Mirror Lab and the Rubin Observatory teams.

   The polished M1M3 surfaces as measured by the Mirror Lab and the Rubin Observatory teams. (The units are in microns).

.. _table-m1m3-dim:

.. table:: M1M3 surface map dimensions.

    +---+------------+--------------+--------------+-----------------+
    |   | Pixel      |  Aperture    | Array        | Clear aperture  |
    |   | size (mm)  |  size (mm)   | size (pixels)| diameter (mm)   |
    +---+------------+--------------+--------------+-----------------+
    | M1| 2.67       |  8403        | 3148 x 3148  | 8360            |
    +---+------------+--------------+--------------+-----------------+
    | M3| 1.25       |  5065        | 4053 x 4053  | 5016            |
    +---+------------+--------------+--------------+-----------------+


The M1M3 surfaces as measured are along surface normal.
In Zemax, the as-built surfaces are described as grid sag surfaces.
To get the surface sag from surface normal measurements, a slope correction has to be applied :cite:`Document-16390` to the surfaces shown above.

When using grid sag surfaces in Zemax, one of the recommendations is that any low spatial order components, if significant, are better modeled as Zernike coefficients, with the residual represented by the grid sag :cite:`zemax`.
Given the small magnitude of the surface errors (<20 nm for M1 and M3), we do not utilize the Zernike coefficients.
All the M1 and M3 polishing errors are described by their respective grid sag files.

M1-M3 Relative Positioning
==========================

The measured value of the M1-M3 vertex separation is shown in Table :ref:`table-m1m3-sep`

.. _table-m1m3-sep:

.. table:: M1M3 vertex separation.

    +----------+----------------------------+--------------------------+
    |          | Measured (mm)              | Spec (mm)                |
    +----------+----------------------------+--------------------------+
    | M1 Conic |233.8    :math:`\pm` 2      |  234.4 :math:`\pm` 0.1   |
    +----------+----------------------------+--------------------------+

According to the M1M3 final report by the Mirror Lab :cite:`Document-17506` and Document-19421 :cite:`Document-19421`,
when viewed in the M1M3 Coordinate System (CS) :cite:`SITCOMTN-003`,
the best-known M3 optical axis is displaced from M1 optical axis by 0.4 mm along -155 degree direction.
In the Zemax CS (ZCS) :cite:`SITCOMTN-003`, M3 is decentered from the M1 optical axis by (0.363, -0.169) mm.

For the wedge, Document-17506 :cite:`Document-17506` doesn't give the orientation of the M3 wedge relative to M1.
Document-19421 :cite:`Document-19421` reports 0.0161 mm Total Indicator Runout (TIR) along -100.0 degree direction in the M1M3 CS.
However, in calculating the x and y-tilts, it should be noted that the decenter of the M3 optical axis discussed above
(0.4mm along -155 degree direction in the M1 CS) is actually a rotation around the M3 center of curvature, aka, an aspheric slide.
This was confirmed by Mirror Lab personel via email.
The x and y-tilts in Zemax need to have two parts:

- a rotation of M3 surface around the M3 center of curvature, along -155 degree direction in the M1 CS, by 0.4/8343.9 radian = 4.8E-5 radian = 2.7E-3 degree. 8343.9 mm is the ROC of M3.
- a tilt of M3 surface around -10 degree direction in the M1 CS (so that the highest point on the perimeter is in the -100 degree direction), by 0.0161/(2508*2) = 3.2E-6 radian = 1.8E-4 degree. 2508 mm is the outer radius of M3. Note that this tilt angle is ~1/15 of the rotation due to decenter.

Projecting these two components to the x and y axis and adding them up gives -1.34E-3 degree of x-tilt and 2.52E-3 degree of y-tilt.
Converting into ZCS we get x-tilt of 1.34E-3 degree and y-tilt of 2.52E-3.

In Zemax, the M3 decenters and tilts can either be modeled using coordinate breaks before and after the M3 surface or by defining the tilt/decenter properties of the M3 surface :cite:`zemax`.

##
M2
##

The M2 mirror was polish by Harris Corporation in Rochester, New York.
The values below are also found on `this confluence page <https://confluence.lsstcorp.org/pages/viewpage.action?spaceKey=SYSENG&title=Optical+Design+Final+Optimization+-+Camera+Lens+Spacings>`__.
There is no temperature correction to the ROC because the M2 is made of ULE glass, which has a much smaller CTE than the M1M3 borosilicate mirror.

.. _table-m2:

.. table:: M2 Radius of Curvature and Conic Constants.

    +----------+----------------------------+--------------------------+
    |          | Measured                   | Spec                     |
    +----------+----------------------------+--------------------------+
    | M2 ROC   | 6790.05 :math:`\pm` 0.5 mm |6788.0 :math:`\pm` 1.5 mm |
    +----------+----------------------------+--------------------------+
    | M2 Conic |-0.2220  :math:`\pm` 0.0002 |-0.2220 :math:`\pm` 0.0001|
    +----------+----------------------------+--------------------------+

M2 Polished Surface
===================

The M2 final polished surface was measured interferometrically by Harris.
Since M2 is a convex mirror, measurements were first made on multiple segments of the mirror, which are subsequenty stitched together.
The linear discontinuities are due to separate ion-figuring runs.


.. figure:: /_static/m2.png
   :name: fig-m2
   :target: ../_images/m2.png
   :width: 130mm
   :alt: The polished M2 surface as determined by Harris and the Rubin Observatory teams.

   The polished M2 surfaces as determined by the Harris and the Rubin Observatory teams. (The units are in microns).

Early in the M2 polishing process, it was discovered that the M2 surface has a
`"swirl" feature <https://confluence.lsstcorp.org/pages/viewpage.action?pageId=64700431>`__.
This is due to the variation in material properties causing differences in responses to ion figuring.
The M2 surface map shown above is the sum of the interferometrically measured M2 surface and the synthesize swirl feature.
The swirl feature has a RMS of ~5 nm.

.. _table-m2-dim:

.. table:: M2 surface map dimensions.

    +---------------------------+-----------+--------------+--------------+-----------------+
    |                           | Pixel     |  Aperture    | Array        | Clear aperture  |
    |                           | size (mm) |  size (mm)   | size (pixels)| diameter (mm)   |
    +---------------------------+-----------+--------------+--------------+-----------------+
    | M2 (interferometer)       | 5.00      |  4000        | 801  x 801   | 3420            |
    +---------------------------+-----------+--------------+--------------+-----------------+
    | M2 (interferometer+swirl) | 1.00      |  3427        | 3428 x 3428  | 3420            |
    +---------------------------+-----------+--------------+--------------+-----------------+

Like the M1M3 surfaces, the M2 surface as measured is along surface normal.
To get the surface sag from surface normal measurements, a slope correction has to be applied :cite:`Document-16390`.

######
Lenses
######

L1L2
====

We have the L1 and L2 TWE maps. Do we have data on L1L2 alignment??? Is there an L1L2 combined TWE???


.. figure:: /_static/lensesRaw.png
   :name: fig-lenses-raw
   :target: ../_images/lensesRaw.png
   :alt: The raw TWE maps as received from the camera team.

   The raw TWE maps as received from the camera team (L1 and L2 data came in units of microns; L3 data came in units of meters and have been converted to microns).


coordinate systems used for the TWE maps??? I am assuming the same coordinate systems have been used as for the filters, is that true???

pixel size???

A positive number in the data array means the optical path going through that point is longer, i.e., there is larger phase delay.???

..
  check v3.12b model for what has been implemented what has not
  10/14/20, done with mirrors. all grid files in docushare collection for v3.12 are good to go.

L3
==


#######
Filters
#######

Transmitted Wavefront Maps
==========================

.. The filters were fabricated at Ball Aerospace and polished by Arizona Optical Systems.

.. figure:: /_static/filterRaw.png
   :name: fig-f-raw
   :target: ../_images/filterRaw.png
   :alt: The raw TWE maps as received from the camera team.

   The raw TWE maps as received from the camera team (The units have been converted from meters to microns).

The center of each data array is the center of the filter.
Raw TWE data came in the units of meters.
A positive number in the data array means the optical path going through that point is longer, i.e., there is larger phase delay.

The pixel resolution is provided for each filter in the table below.


.. _table-twe:

.. table:: Filter TWE map dimensions.

    +---+------------+--------------+--------------+
    |   | Pixel      |  TWE aperture| TWE array    |
    |   | size (mm)  |  size (mm)   | size (pixels)|
    +---+------------+--------------+--------------+
    | u | 1.25175    | 751.05       | 601 x 601    |
    +---+------------+--------------+--------------+
    | g | 0.59311    |  751.47      | 1268 x 1268  |
    +---+------------+--------------+--------------+
    | r | 0.59078    |  749.10      | 1269 x 1269  |
    +---+------------+--------------+--------------+
    | i | 0.59216    |  755.60      | 1277 x 1277  |
    +---+------------+--------------+--------------+
    | z | 0.59155    |  756.00      | 1279 x 1278  |
    +---+------------+--------------+--------------+
    | y | 0.59216    |  748.49      | 1265 x 1265  |
    +---+------------+--------------+--------------+



Throughputs
===========

Need internal reflection data to reproduce graph in `LCR-1705 <https://project.lsst.org/groups/ccb/node/3052>`__ ???

##################################
Relative positioning of the optics
##################################

L1-L2 Separation
================

.. What is the as-built value???

L2S2 to Filter S1
=================

The alignment of the L1L2 assembly to the rest of the camera (filter, L3, and the detector) is a static variable.
This is essentially a hexapod with 6 degrees of freedom (DOFs) on which we can do an one-time adjustment when the camera is fully assembled.
Before that this relative positioning contributes 5 optimization variables.
The rotation around the optical axis is not used in system optimizations.
Also note that the spacing was 349.58 mm in v3.3 optical design, and the as-built spacing is going to be roughly 3 mm less due to
`LCR-646 <https://project.lsst.org/groups/ccb/node/1270>`__.

Filter S1 to L3S1
=================

The thickness of the filter varies by band. But the distance between filter S1 and L3S1 is fixed at 72 mm.
This was 69 mm in v3.3 design. The filter was moved toward L2 by 3mm, due to `LCR-646 <https://project.lsst.org/groups/ccb/node/1270>`__.

L3S2 to Detector
================

The spacing between L3S2 and the detector plane is fixed at 28.821 mm. (What is the as-built value???)
The original v3.3 design had it at 28.5 mm.
This change is the result of a system wide optimization after we found out that the M2 ROC was slightly out of spec.
The decision was documented in
`LCR-1036 <https://project.lsst.org/groups/ccb/node/1833>`__ and on
`this confluence page <https://confluence.lsstcorp.org/pages/viewpage.action?spaceKey=SYSENG&title=Optical+Design+Final+Optimization+-+Camera+Lens+Spacings>`__.


##############
Merit Function
##############

The Merit Function (MF) optimizes the RMS spot radius over

- 30 Gaussian Quadrature (GQ) field points plus field center
- 30 GQ pupil coordinates
- 6 optical bands
- 5 wavelength per optical band

The GQ points are on a 5-ring 6-arm structure.

There are 20 variables currently used in optimizing the merit function:

- 5 DOFs for the M2 hexapod (piston, x-decenter, y-decenter, x-tilt and y-tilt)
- 10 DOFs for the camera hexapod (piston for 6 optical bands, x-decenter, y-decenter, x-tilt and y-tilt)
- 5 DOFs for aligning the L1L2 assembly to the (filter+L3+detector) (piston, x-decenter, y-decenter, x-tilt and y-tilt)

.. .. rubric:: References

.. Make in-text citations with: :cite:`bibkey`.

.. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
   :style: lsst_aa
