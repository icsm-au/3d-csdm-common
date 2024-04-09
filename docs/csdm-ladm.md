# The 2D CSDM and the Land Administration Domain Model

<!--
:Author:    Andrew Hunter
:Email:     <andrew@edgegeomatics.co.nz>
:Date:      3 December 2023
:Updated:   
:Revision:  0.

:History: 
:Ver 0.1: Initial draft of document

-->

#### Table of Contents

1. [Introduction](#introduction)
2. [LADM](#ladm)
3. [Mapping the 2D Implementation to LADM](#mapping-the-2d-csdm-inplementation-to-ladm)
3. [References](#references)

## Introduction

The 2D Cadastral Survey Data Model implementation is a JSON encoding derived from the conceptual [3D Cadastral Survey 
Data Model (CSDM)](https://icsm-au.github.io/3d-csdm/) developed for [ICSM](https://www.icsm.gov.au/). The encoding has been designed to 
support the exchange of 2D cadastral survey data using jurisdictional cadastral surveying profiles that map 
local/regional vocabularies to the CSDM. The 2D Cadastral Survey Data Model implementation is for the transfer of data 
used by land administration organisations for the management of surveying component of land tenure systems.

It is useful to understand how this implementation fits into the broader land administration domain. The current ISO 
standard for land administration is ISO 19152 Land Administration Domain Model (LADM). Edition 1 of LADM was initially 
approved in 2012 [[1]](#1).  LADM organises information components of a land administration system being people, 
rights (the three Rs includes responsibilities and restrictions), administrative units, data on spatial units and 
surveying, and topology/geometry [[2]](#2).

## LADM

The 2012 version of LADM provided classes to manage people (LA_Parties), cadastral parcels (LA_SpatialUnits), and 
Interests in land (LA_Rights) plus numerous specialisations that fall under the general themes of Party, Administration, 
and Spatial Unit. However, Edition 1 of the standard provided little in the way of support for survey system information. 
The second edition of LADM is currently under development and the standard has been expanded to include several 
new parts:
* Part 1 Conceptual Model
* Part 2 Land Registration
* Part 3 Georegulation (Marine space)
* Part 4 Valuation
* Part 5 Spatial Plan Information
* Part 6 Implementation

Parts 1 and 2 cover Edition 1 of ISO 19152 and has extended Survey and Representation (Part 2) to enable survey 
observations to be included as part of a land administration system. Part 1 has now been approved for publication. Parts 
2, 4 and 5 are in the final stages of Committee Draft - resolving comments. Part 3 has completed balloting as a Draft 
International Standard, results are pending. Part 6 is preliminary and unlikely to proceed until Parts 2 to 5 are 
further advanced.

## Mapping the 2D CSDM implementation to LADM
A high level mapping of the major elements of the 2D CSDM JSON encoded implementation has been mapped to Parts 1 
[[3]](#3) and 2 [[4]](#4) of Edition 2 of ISO 19152 (as of the time of writing). At first glance the CSDM classes 
generally map well to the LADM classes with all CSDM classes finding a relevant home within the LADM framework, except 
for Occupation Marks and Occupation Features.

In [Figure 1](#fig_1) below, CSDM elements (depicted as classes) are the green elements on the left side of the diagram, 
and LADM classes are the blue elements on the right. In a number of instances at this general classification of the 
models the mapping is one to one. LADM splits survey observation methods into a number of more specialised classes (two are identified in 
[Figure 1](#fig_1) below), whereas the CSDM vectorObservations element is agnostic primarily because of the adoption of 
SOSA [[5]](#5) in the CSDM. This allows the same general pattern can be used for all types of observations. 
[Figure 2](#fig_2) shows the ICSM Equipment vocabulary associated to the various LADM Observation Classes. Note that 
LADM now includes classes for multibeam echo sounder data and ground penetrating radar data.

The other most obvious difference is between CSDM parcels and LADM SpatialUnits. Fundamentally, this is more a 
classification difference than a conceptual difference. It is expected that CSDM Parcels can readily map to 
La_SpatialUnit without loss of geometric data. For the 2D CSDM, a parcel is defined as a Polygon, and an LA_BoundaryFace 
is defined as a Face, which is a 3D equivalent of a Polygon. Boundaries (LA_BoundaryString/observedVectors) in both 
models are defined generally as a Curve [[3]](#3). However, at this time we are unaware of LADM implementations that 
allow non-linear Curves. The topological approach adopted in the CSDM is also derived from the same source as the 
SpatialUnit::TopoRelation in LADM, ISO 19107 [[6]](#6). So, while we are unaware of topological implementations of 
LADM,we expect that mapping of CSDM geometries to LADM geometries to be lossless.

What has not been assessed at this time is the ability to completely map all required CSDM jurisdictional elements to 
LADM classes. It is assumed that most will be able to be mapped, but until that exercise is undertaken it can not be 
guaranteed. Regardless, we do not have concerns that suggest development of an LADM profile for the CSDM is not feasible 
and that a LADM profile will meet the normal requirements of a land administration system.

<a id="fig_1">![Figure 1: CSDM Mapping to LADM Edition 2](images%2F2D%20CSDM%20mapping%20to%20LADM.bmp "Figure 1: CSDM Mapping to LADM Edition 2")</a>

<a id="fig_2">![Figure 2: CSDM Equipment Vocabulary mapped to LADM Observation Classes](images%2FCSDM-equip-vocab-LADM.bmp "Figure 2: CSDM Equipment Vocabulary mapped to LADM Observation Classes")</a>

# References
<a id="1">[1]</a> 
ISO. ISO 19152:2012 Land Administration Domain Model (LADM). https://www.iso.org/obp/ui/#iso:std:iso:19152:ed-1:v1:en.

<a id="2">[2]</a>
Lemmen, C., van Oosterom, P., & Bennett, R. (2015). The Land Administration Domain Model. Land Use Policy, 49, 535–545. https://doi.org/10.1016/j.landusepol.2015.01.014

<a id="3">[3]</a>
ISO. ISO/FDIS 19152-1:202X. Land Administration Domain Model - Part 1, General Feature Model.

<a id="4">[4]</a>
ISO. ISO/CD 19152-2:202X. Land Administration Domain Model - Part 2, Land Registration.

<a id="5">[5]</a>
W3C, OGC (2017) Semantic Sensor Network Ontology, https://www.w3.org/TR/vocab-ssn/

<a id="6">[6]</a>
ISO. ISO 19107:2019. Geographic information — Spatial schema. https://www.iso.org/obp/ui/#iso:std:iso:19107:ed-2:v1:en
