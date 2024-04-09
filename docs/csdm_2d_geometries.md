# 2D CSDM Geometries

<!--
:Author:    Andrew Hunter
:Email:     <andrew@edgegeomatics.co.nz>
:Date:      19 November 2023
:Updated:   
:Revision:  0.3

:History: 
:Ver 0.1: Initial draft of document
:Ver 0.2: Added Aggregate Polygons - 29 November 2023
:Ver 0.3: Added Occupation Marks - 8 December 2023
-->

#### Table of Contents

1. [Introduction](#introduction)
2. [Points](#points)
3. [Curves](#curves)
    1. [LineStrings](#linestrings)
    2. [Arcs](#arcs)
    3. [Circles](#circles)
    4. [Splines](#splines)
4. [Polygons](#polygons)
5. [Aggregate Polygons](#aggregate-polygons)
6. [Subtended Angles](#subtended-angles)
7. [Occupation Marks](#occupation-marks)

## Introduction

GeoJSON adopts seven geometry types defined in
OGCs [Simple Features Specification for SQL Rev 1.1](https://portal.ogc.org/files/?artifact_id=829), being <code>
Point</code>, <code>MultiPoint</code>,
<code>LineString</code>, <code>MultiLineString</code>, <code>Polygon</code>, <code>MultiPolygon</code>, and
<code>GeometryCollection</code>. These geometries all use linear interpolation between vertices.

While many cadastral boundaries are linear, i.e., straight, there are numerous examples of non-linear boundaries, such
as circular arcs (boundaries parallel to a curved road centerline), splines (natural features such as water boundaries),
and circles (some mining leases, for example). Similarly, the exterior and interior rings of 2D cadastral parcels can be
composed of both linear and non-linear geometries.

NZs LandXML and VIC ePlan include <code>ReducedArcObservation</code> for specification of boundary arcs and
<code>IrregularLine</code> to capture natural (general) boundaries such as river banks or shorelines. WA uses
<code>CircularArcRecord</code> and <code>TopographicString</code> to capture equivalent boundary geometries. NZs LandXML
and VICs ePlan also contain a <code>Curve</code> class that requires a <code>Start</code> and <code>End</code> point,
and <code>Radius</code> and <code>Rotation</code> elements to define a circular <code>Curve</code>.

Note that units used throughout the 3D CSDM specification are defined by the Coordinate Reference System assigned to a 
CSD. Hence, the length unit is metre, and angular unit is degree.

Through various workshop discussions with project jurisdictions it is agreed that the 2D/3D CSDM requires specification
of non-linear geometries commonly required for cadastral datasets.

The following sections describe the geometries included in the 2D CSDM implementation.

## Points

Following ISO 19107's topological approach to the definition of geometries, and
[OGC's JSON-FG](https://docs.ogc.org/per/21-017r1.html) information encoding, <code>Point</code> geometries are defined
by a <code>place</code> element that contains an <code>id</code> element to uniquely identify the <code>Point</code>, a
<code>type</code> element specifying the type of geometry being defined, and a <code>coordinate</code> pair as follows:

~~~json lines
{
  "id": "123456",
  "place": {
    "type": "Point",
    "coordinates": [
      794317.443,
      398759.23
    ]
  }
}
~~~

The coordinate values are with respect to the Coordinate Reference System (CRS) defined by the CSD's CRS elements.

## Curves

A curve is the general term used to describe a 1D geometry between two points on a surface. If the curve is straight
(linear) then it can be described using a GeoJSON <code>LineString</code> element. If it is non-linear and the radius is
constant then it can be described by an arc or a circle.
The [OGC Features and Geometries JSON Working Group](https://github.com/opengeospatial/ogc-feat-geo-json/blob/main/proposals/circular-geometry-objects.adoc)
has
proposed an update to the JSON-FG specification to extend JSON-FG to include geometries for arcs and circles.

If the radius of curvature is not constant, then an alternative specification is required. Through discussion the
jurisdictions have agreed that Cubic Splines are appropriate for the representation of natural features such as water
boundaries.

### LineStrings

A <code>LineString</code> geometry contains a <code>topology</code> element and is defined by referencing (an ordered
list) the coordinate identifiers for the start and end point of the <code>LineString</code>. Given a boundary line or a
survey observation is generally defined by the two end points of the line or observation, a <code>LineString</code>
<code>topology</code> element representing a right-line boundary vector or a survey observation must contain two
references to <code>Point</code> geometry IDs.

Where a natural feature (irregular boundary) such as a Mean High Watermark is to be represented by a right-line
boundary (straight lines between survey points defining the natural feature), more than two <code>Point</code> geometry
IDs are required.

~~~json lines
{
  "id": "234561",
  "topology": {
    "type": "LineString",
    "references": [
      "1746055",
      "1746030"
    ]
  }
}
~~~

### Arcs

To represent non-linear boundaries the CSDM has proposed three <code>Arc</code> geometries, two <code>Spline</code>
geometries and a single <code>Circle</code> geometry.

The three arc specifications include <code>ArcWithCentre</code>, <code>ArcByChord</code> and JSON-FG's <code>Arc</code>.

An <code>Arc</code> consists of three points with circular interpolation used to define the curve between points. It
starts at the first point referenced, goes through the second point and ends at the third point. As
such arc orientation is unnecessary.

~~~json lines
{
  "id": "345612",
  "topology": {
    "type": "Arc",
    "references": [
      "1746055",
      "1746030",
      "1746032"
    ]
  }
}
~~~

An <code>ArcWithCentre</code> consists of three points with circular interpolation used to define the curve between
points. It starts at the first point referenced and ends at the second point. The third point is the
centre of the arc. Arc <code>orientation</code> (clockwise or counterclockwise) is required to ensure that the arc is
constructed on the appropriate side of the arc chord between the arcs start and end points.

~~~json lines
{
  "id": "345612",
  "topology": {
    "type": "ArcWithCenter",
    "references": [
      "1746055",
      "1746030",
      "1746032"
    ],
    "orientation": "cw"
  }
}
~~~

An <code>ArcByChord</code> consists of two points with circular interpolation used to define the curve between
points. It starts at the first point referenced and ends at the second point. The line between the points represents the
arc Chord. Arc <code>orientation</code> (clockwise or counterclockwise) is required to ensure that the arc is
constructed on the appropriate side of the arc chord between the start and end points of the arc. <code>radius</code> is
required to determine the rate of curvature of the arc relative to the chord.

~~~json lines
{
   "id": "456123",
   "topology": {
      "type": "ArcByChord",
      "references": [
         "1746055",
         "1746030"
      ],
      "orientation": "cw",
      "radius": 9.13
   }
}
~~~

Note that the CSDM requires <code>radius</code> and <code>arcLength</code> elements for all arcs. They have been
excluded in these examples to limit noise.

### Circles

In instances where a boundary is defined by a circle, the JSON-FG Circle geometry (four points on the circumference of
the circle) could be adopted to represent the circle boundary. However, through consultation with the jurisdictions a
simpler representation that more closely matches survey practice has been defined. A <code>CircleByCenter</code>
consists of a single center point and a <code>radius</code> element, with circular interpolation being used to define
the circumference of the circle.

~~~json lines
{
  "id": "561234",
  "topology": {
    "type": "CircleByCenter",
    "references": [
      "1746055"
    ],
    "radius": 40.00
  }
}
~~~

### Splines

Following ISO 19107:2019, a cubicSpline curve is a polynomial spline of degree 3, and may be described by tangent
vectors at the start and end points of the spline and at least three control points including the start and end points.
When included, the direction of the start and end tangent vectors are used to determine the shape of the cubic spline.
Cubic interpolation is used to define the spline curve between points. The tangents may be included in the specification
of a <code>CubicSpline</code>.

To this end two specifications have been proposed for the CSDM implementation, <code>CubicSpline</code> and
<code>CubicSplineWithTangents</code>.

~~~json lines
{
  "id": "612345",
  "topology": {
    "type": "CubicSpline",
    "references": [
      "14",
      "102",
      "103",
      "104",
      "12"
    ]
  }
}
~~~

~~~json lines
{
  "id": "1234567",
  "topology": {
    "type": "CubicSplineWithTangents",
    "startTangentVector": {
      "references": [
        "101",
        "14"
      ]
    },
    "endTangentVector": {
      "references": [
        "12",
        "105"
      ]
    },
    "references": [
      "14",
      "102",
      "103",
      "104",
      "12"
    ]
  }
}
~~~

## Polygons

GeoJSON's <code>Polygon</code> geometry is restricted to linear interpolation between vertices. However, as the CSDM
implementation adopts a topological construction for 1D and 2D geometries, it is only necessary to specify a single
pattern for a <code>Polygon</code> as the <code>topology</code> element references a set of <code>Curve</code> IDs that
define the exterior followed by any interior rings describing the <code>Polygon</code>. The <code>references</code>
contains an array of arrays. The first array being the extrior ring, and subsequent arrays being interior rings. The
<code>Curve</code> IDs can be <code>LineStrings</code>, <code>Arcs</code>, <code>Circles</code>, or
<code>CubicSplines</code> curves. For a <code>Polygon</code> to be well-formed, the exterior ring should be defined
counterclockwise, and interior rings clockwise.

Because observed vectors may be measured in any direction it is expected that the parser will check that exterior and
interior rings close and are ordered correctly.

~~~json lines
{
  "id": "2345671",
  "topology": {
    "type": "Polygon",
    "references": [
      [
        "234567",
        "234568",
        "234569",
        "234570"
      ]
    ]
  }
}
~~~

A <code>Polygon</code> with a void.

~~~json lines
{
  "id": "2345671",
  "topology": {
    "type": "Polygon",
    "references": [
      [
        "234567",
        "234568",
        "234569",
        "234570"
      ],
      [
        "334567",
        "334568",
        "334569",
        "334570"
      ]
    ]
  }
}
~~~

## Aggregate Polygons

An Aggregate polygon is used to represent a **Parcel Aggregate**, being a *collection of parcels whose collective extent
may be described as a spatial unit.*

For the 2D CSDM an <code>AggregatePolygon</code> is proposed to gather a set of polygons into one geometry. The
<code>topology</code> element references a set of <code>Polygon</code> IDs that are contained in the **Parcel
Aggregate**.

**Parcel Aggregate** is a simple list, whereas a <code>MultiPolygon</code> is a nested list of <code>Polygons</code>
which are a nested list of rings.

~~~json lines
{
  "id": "3456712",
  "topology": {
    "type": "AggregatePolygon",
    "references": [
      "234567",
      "234568",
      "234569"
    ]
  }
}
~~~

## Subtended Angles

A subtended angle is an angle formed by two lines, or line segments that originate from the same point and extend to two
different points on a circle's circumference. In other words, it's the angle created by two lines or line segments that
radiate from the **center** of a circle and intersect at points on the circumference of the circle.

From a surveying perspective the line segments are commonly referred to as Backsight or Reference Object (RO) and
Foresight or Target. The centre point is the Setup Station.

For the CSDM implementation it is assumed that the angle is measured clockwise from the RO to the Target, and must be
positive angles.

The <code>topology</code> element that describes a <code>SubtendedAngle</code> is an ordered list of features that first
references a point geometry representing the location of the subtended angle (the Setup Station), and then two
LineString geometry IDs representing the vector from the Setup Station to the Reference Object (RO) and the Setup
Station to the Target, in that order.

~~~json lines
{
  "id": "843843843",
  "topology": {
    "type": "SubtendedAngle",
    "references": [
      "184",
      "313",
      "312"
    ]
  }
}

~~~

## Occupation Marks

As defined in [3D CSDM: Survey Features](https://icsm-au.github.io/3d-csdm/surveyfeats.html#OccupationMark) an **Occupation Mark**
*means a mark used for a cadastral survey to define the location of an occupation feature near a cadastral boundary* An
**Occupation Feature** *means those long-established features that might be used to determine the limits of an
occupier’s land, and that are used to exclude possession by others, e.g., fences, walls, trees, hedges, buildings,
ditches, or other artificial things; and natural land features such as a water body. An occupation feature is disjoint
from (has no common elements with) a boundary.*

DE-9IM [[1]](#1)[[2]](#2) defines nine intersection patterns that can occur between two geometries, such as points, 
lines, and polygons. When one geometry is a <code>Point</code> we end up with the following possible relationships:
* can be **equal** if both geometries are points;
* can **touch** another line geometry
* or **touch** or be **within** another an area geometry.

Given conventional survey methods take observations to the surface of **Occupation Features** the **Touches** 
relationship is the normal topological relationship between an **Occupation Mark** and an **Occupation Feature**.

An **Occupation Mark** is a subclass of a <code>SurveyPoint</code> and inherit many of the properties of a
<code>SurveyPoint</code>. As an **Occupation Mark** is not monumented the <code>monumentedBy</code> is not included in
the specification of an **Occupation Mark**. However, as an **Occupation Mark** defines where an **Occupation Feature**
is located, a <code>topology</code> element is included. The <code>topology</code> type is **Touches**. The 
<code>references</code> element contains a list of **Occupation Feature** IDs that the **Occupation Mark** touches.

~~~json lines
{
  "topology": [
    {
      "type": "Touches",
      "references": [
        "964008",
        "964022"
      ]
    }
  ]
}
~~~
**Occupation Feature** IDs may be JSON-LD links to the occupation feature data; they may be <code>href</code> links to an OCG API 
compliant resource containing the occupation feature data, or they may be feature IDs of occupation features in a 
GeoJSON Feature Collection element, <code>occupationFeatures</code>, contained in the CSDM dataset.


### References
<a id="1">[1]</a> 
Egenhofer, M., & Franzosa, R. D. (1991). Point-set topological spatial relations. International Journal of Geographical 
Information Systems, 5(2), 161–174. https://doi.org/10.1080/02693799108927841

<a id="2">[2]</a> 
Egenhofer, M., & Herring, J. (1990). Categorizing binary topological relations between regions, lines and points in 
geographic databases, the 9-intersection: Formalism and its Use for Natural Language Spatial Predicates. Santa Barbara 
CA National Center for Geographic Information and Analysis Technical Report, 94, 1–28.