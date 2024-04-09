# 3D CSDM Implementation Road Map

<!--
:Author:    Andrew Hunter
:Email:     <andrew@edgegeomatics.co.nz>
:Date:      11 December 2023
:Updated:   
:Revision:  0.2

:History: 
:Ver 0.1: Initial draft of document
:Ver 0.2: Added topology discussion, 11 December 2023

-->

#### Table of Contents

1. [Introduction](#introduction)
2. [Current State](#current-state) 
3. [Objectives](#objectives)
4. [Development Phases](#development-phases)
5. [Testing & Validation](#testing-and-validation)
6. [Timeline](#timeline)


## Introduction

The 2D CSDM implementation has been developed using a mix of JSON/JSON-LD/GeoJSON/JSON-FG. GeoJSON [[1]](#1) and 
JSON-FG [[2]](#2) add geometry capability to the implementation. GeoJSON [[1]](#1) adopts seven geometry types defined 
in OGCs [Simple Features Specification for SQL Rev 1.1](https://portal.ogc.org/files/?artifact_id=829). The specification does not officially support 3D 
geometries. GeoJSON has been designed to represent simple spatial features, and it primarily deals with 2D geometries. 
However, there have been discussions generally within the geospatial community, and proposals by the JSON-FG Standards 
Working Group [[2]](#2) to extend GeoJSON to support 3D geometries. 

We note that there are a number of extensions or variations of JSON that include 3D features. They are mostly optimised 
for specific purposes. One notable initiative is the Khronos Group's glTF (GL Transmission Format) [[3]](#3). glTF is a 
standard for transmission and visualisation of 3D scenes and models. It uses JSON for describing the scene structure and 
binary data for geometry, textures, and other attributes.

While glTF has gained significant industry support, it is fundamentally about streaming meshes based on faces. It 
requires all faces be triangulated. From a 3D cadastral parcel perspective triangulation of faces seems overly complex, 
given a key requirement of the 3D CSDM is the identification of points and lines/boundaries and the roles they play in 
the construction of 3D topology to define cadastral parcels. 

The focus of the 3D CSDM implementation phase is on addressing the representation of 3D cadastral parcels considering 
the complexities of cadastral data sets, particularly non-convex geometries, and determination and documentation of 
the intersection of 3D parcels.

At this time the JSON-FG [[2]](#2) proposal for the specification of 3D geometries is a suitable candidate for 
representation of 3D cadastral parcels.

## Current State

The following is a summary of the [3D CSDM Geometries](3d_csdm_geometries.md) discussion focusing on the JSON-FG proposal 
to extend JSON-FG to include 3D geometries. The proposal is currently a draft proposal, but has been released for public 
comment.

GeoJSON [[1]](#1) primarily supports 2D geometries and lacks official support for 3D geometries. OGC's Features and 
Geometries JSON (JSON-FG) Software Working Group [[2]](#2) has introduced a set of new 3D geometry types that include 
Polyhedron, MultiPolyhedron, Prism, and MultiPrism. 

Polyhedra are a <code>Solid</code> geometry defined by bounding surfaces, sometimes called a <code>Shell</code>. A 
<code>Shell</code> can include voids. The JSON-FG representation of a Polyheron is a MultiPolygon array, where the first 
array represents the exterior boundary of the Polyhedron and subsequent arrays represent interior voids. The Polyhedron 
is relevant for the specification of 3D cadastral parcels as the <code>shell</code> is the equivalent of the boundary 
faces of a 3D cadastral parcel. It is an implementation of the Boundary Representation (B-Rep) approach defined in ISO 
19107:2019 [[4]](#4). It is able to define non-convex geometries and geometries with voids that are often encountered in 
a Cadastral dataset. The JSON-FG proposal [[2]](#2) also defines a MultiPolyhedron to enable collections of Polyhedra to 
be grouped together and is expected to be a suitable representation for an Aggregate or Composite Parcel where there are 
multiple cadastral parcels held under a single title.

A Prism is an extrusion of a base geometry from a lower elevation to an upper elevation. From a cadastral perspective it 
is an appropriate geometry for representation of a private unit within a building. JSON-FG's proposal for a Prism limits 
extrusion along the Z axis. As with the Polyhedron example, a MultiPrisim is also proposed.

The proposed geometries align with the ICSM Conceptual Model for 3D Cadastral data, but additional geometries are 
required to construct more complex geometries necessary to represent cadastral parcels for easements or tunnels that 
might be defined by a non-linear curve. These types of geometries are called swept path geometries. A prism is a 
specialisation of a swept path geometry.

The GeoJSON-FG specification for a Polyhedron requires that unique Polyhedron do not intersect. From the perspective of 
a Cadastre, this suggests that if two 3D cadastral parcels intersect (Parcel A and Parcel B), say a height-limited Fee 
Simple Parcel (Parcel A) and an Easement Parcel (Parcel B), then the two parcels must be split into parts defined by 
those parts that are common to both parcels - the **Intersection** (Parcel A &cap; Parcel B) of the parcels (say Part 2), 
and those parts of the parcels that do not intersect (say Parts 1 (Parcel A - Parcel B) and 3 (Parcel B - Parcel A)). 

The Parcels are then aggregated as two MultiPolyhedron. Parcel A equals Part 1 plus Part 2, and Parcel B equals Part 2 
plus Part 3.

An alternative and arguably simpler approach, as outline during the development of the 
[ICSM Conceptual Model for 3D CSDM](https://icsm-au.github.io/3d-csdm-design/2022/spec.html), is to not split 3D parcels into parts as described above, but define an 
**intersection curve** [[5]](#5) that describes where two solids explicitly meet.

Data integrity and consistency is critical for the management of cadastral data.  Integrating topological support 
ensures that 3D parcels are correctly represented and appropriately connected to other cadastral parcels in accordance
with jurisdictional requirements. Integrating appropriate topological support can also assist with the management of 
parcel boundaries as parcels are subdivided to ensure that spatial relationships between boundaries, boundary faces and 
survey marks that are maintained in a manner that ensures the ongoing integrity of the cadastre.

While research and application libraries focusing on 2D topological relationships are relatively mature, 3D solutions 
whether in the general CAD domain, Standards domain or application libraries, is limited. There are a number of software 
packages available for testing closure of 3D objects, but they have all been shown to be limited to some degree when 
tested on 3D CityGML data converted to STL [[6]](#6). To the best of our knowledge desktop geospatial software such as 
ArcGIS, QGIS, or SuperMap include little in the way of 3D topological support. Development of 3D topological rules is 
more advanced in the database domain, but Oracle Spatial is the only database solution that offers 3D topological 
support by default. Custom topological extensions focusing on 3D cadastral parcels have been developed within research 
settings for PostgreSQL and Oracle databases, and Python frameworks [[7]](#7).

In order to develop a 3D CSDM implementation it will be beneficial to develop a set of spatial geometries and spatial 
functions that ensure that 3D parcels contained in a 3CSDM are valid geometries and that they pass standard topological 
tests expected by jurisdictions. The scope of geometries and spatial functions required, and specification of a test 
suite will be the focus of the participatory design phase, i.e., co-design of the 3D CSDM implementation.

## Objectives
The objectives of the 3D CSDM implementation phase is to:
1. Develop a specification for 3D geometries required for a cadastral survey dataset; 
2. Extend the 2D reference implementation to a 3D specification with JSON-LD encoding rules for the exchange of 3D cadastral survey data; 
3. Generate sample cadastral survey datasets in JSON-LD representing a range of 3D survey information for participating jurisdictions; and 
4. Extend PanCadastre software to parse, validate and serialise 3D cadastral survey datasets in JSON-LD.

## Development Phases
**Phase 1**
* Establish initial simple 3D test cases
* Review of state of existing FOSS tools and standards support
* Finalisation of reference implementation architecture
* Showcase

**Phase 2**
* Implementation and testing of reference implementation
* Generation of 3D test cases
* Development of 3D topological functionality
* Showcase

**Phase 3**
* Refinement of reference implementation test cases and code
* Refinement of encoding specification deliverables
* Final presentation

## 3D CSDM Schema Documentation
3D Schema Documentation will follow a similar pattern to that adopted during the 2D CSDM implementation work. The model 
maintenance methodology will leverage automated testing capabilities, developed during the 2D CSDM implementation and
allow for regular co-design sessions focused on model refinement, the underlying requirements of the test cases, and 
cross-checking that test cases and test evaluation procedures adequately cover requirements. Updates to the encoding 
specification will use the same infrastructure, but do not require co-design input for an agreed scope, and instead only 
require quality review through the design of test criteria.

## Testing and Validation
Testing and validation will follow the same methodology implemented for the 2D CSDM implementation. The approach is 
based on the deployment of a reference implementation and integration of validation processes into the continuous 
integration/continuous deployment pipeline constructed within a GitHub environment. The methodology will adopt industry 
standard technologies for automation. We will continue with Model Encoding Testing Methodology that provides a 
repeatable process for exposing an agreed (co-designed) set of representative examples and APIs for exposing the 3D CSDM 
specification.

In addition to extending the 2D CSDM validation suite to 3D, in order to ensure that a valid set of geometries is 
contained in a 3D CSDM it is anticipated that a minimal set of functions will be required. All functionality is to be 
integrated into the existing PanCadastre software. It is expected that the set of functions will at least include the 
following:

1. Test to ensure <code>face</code> normal is outwards;
2. Test to ensure that <code>Solid</code> is well-formed and closed;
3. Test for intersection of geometries;
4. Function to compute non-planar <code>Face</code> surface;
5. Function to compute Surface-Surface intersection;
6. Function to construct Intersection Curve from two or more geometries that intersect;
7. Test that Intersection Curve closes.
8. If adopting a strict B-Rep approach, functions to split geometries that intersect and rebuild geometries from parts;
9. Functionality to rotate <code>base</code> geometry so that it is perpendicular to the <code>path</code> geometry.
10. Identification and development of spatial operators required for validation of a 3D cadastral dataset.

## Timeline

Phase 1 - 2 months

Phase 2 - 6 months

Phase 3 - 2 months

## References
<a id="1">[1]</a> 
Butler, H., Daly, M., Doyle, A., Gillies, S., Hagen, S., & Schaub, T. (2016). GeoJSON (7946). 
https://datatracker.ietf.org/doc/html/rfc7946

<a id="2">[2]</a> 
Open Geospatial Consortium (2023) OGC Features and Geometries JSON - Part 1: Core. 
https://docs.ogc.org/DRAFTS/21-045.html

<a id="3">[3]</a> 
Khronos Group (2023) What is gITF?, https://www.khronos.org/gltf/

<a id="4">[4]</a>
ISO. ISO 19107:2019. Geographic information — Spatial schema. https://www.iso.org/obp/ui/#iso:std:iso:19107:ed-2:v1:en

<a id="5">[5]</a>
Barnhill, R. E., Farin, G., Jordan, M., & Piper, B. R. (1987) Surface/surface intersection. *Computer Aided Geometric 
Design*, 4(1), 3–16. https://doi.org/10.1016/0167-8396(87)90020-3

<a id="6">[6]</a>
Saeedrashed, Y. S., & Benim, A. C. (2019) Validation Methods of Geometric 3D-CityGML Data for Urban Wind Simulations. 
*E3S Web of Conferences*, 128, 10006. https://doi.org/10.1051/e3sconf/201912810006

<a id="7">[7]</a>
Salleh, S., Ujang, U., & Azri, S. (2021) 3D topological support in spatial databases: An overview. *The International 
Archives of the Photogrammetry, Remote Sensing and Spatial Information Sciences*, 46, 473–478.
