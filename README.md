# LabVIEW-DXF-Parser
A tool that parses DXF files for LabVIEW.

Software Requirements: LabVIEW 2014 (but can be saved for previous versions)

Background:
The DXF file is basically an ASCII file, and its structure is clearly documented in the documentation for AutoCAD. (http://images.autodesk.com/adsk/files/acad_dxf0.pdf)
Most 2D contours are encoded using the "POLYLINE" or the "LWPOLYLINE" command.  They basically do the same thing, but parsing them is a little different.  This example only parses DXFs that use "POLYLINE", this command is found in older AutoCAD files.

The file structure is...

<Start>
POLYLINE

VERTEX
10
(Some X)
20
(Some Y)
30
...


VERTEX
10
(Some X)
20
(Some Y)
30
...

SEQEND

*So VERTEX keeps repeating until the line is ended by SEQEND

However, "LWPOLYLINE" is a little different.

<Start>
LWPOLYLINE
<some tags and stuff>
AcDbPolyline
10
(Some X)
20
(Some Y)
10
(Some X)
20
(Some Y)

<keeps repeating>

Another LWPOLYLINE will start a new line segment.

The parsing method for LWPOLYLINE will need to be written at another time.
