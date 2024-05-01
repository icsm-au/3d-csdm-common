# 3D Road Map

<!--
:Author:    Rob Atkinson
:Email:     <rob.atkinson@surroundaustralia.com>
:Date:      5 December 2023
:Updated:   
:Revision:  0.1

:History: 
:Ver 0.1: Initial draft of document

-->

#### Table of Contents

1. [Introduction](#introduction)
2. [LADM-Parcels](#parcels)
3. [ISO 19157 Data Quality](#dqm)

<a id="introduction"/>

## Introduction

During development of the 2D version of the CSDM encoding specification a number of areas were identified where alignment with other standards would be preferable, however no *canonical* encodings were available in a compatible form.

These areas are suggested for iterative review and refinement as further testing progresses in order to minimise incompatibilities with emerging standards (and support uptake process through use of common approaches).

There are a number of alignment methods possible, however all require development of an approach to long term sustainability and maintenance that is beyond the scope of the initial design and testing phase.

One alignment option is to actively participate in the development and testing of international standards using this initial development as an input. Its strong basis in existing standards and innovative and significantly improved testing methdology means that some components at least would be strong candidates for adoption in a wider community. Care has been taken to isolate local specific concerns into the separate profile specification layer.

<a id="parcels"/>

## LADM (Parcels model)

The parcels module is a discrete module in the ontology, however is currently implemented as a component of the container (CSD) encoding schema.

It can be factored out into a separate module at any time, with the encoding retaining backwards compatibility.

The rationale for this conflation is twofold:

1. For the purposes of development and testing, the Parcels design is extensively based on topological cross-references to other elements of the CSD and does not really "stand-alone".
2. A future JSON encoding LADM model[[1]](#1) may require an alignment via a "schema wrapper" that uses the LADM schema where appropriate but that retains cross-CSD references and specific metadata requirements.
3. that any alignment with a future LADM parcels encoding standard will require extensive updates to the CSD examples using the parcels anyway, and this refactoring can be done at one time in one place. 

A OGC LADM Specifications Working Group (SWG) is being established (voting on the charter is currently underway).
 
In the meantime, intentions to develop an encoding standard for LADM have been published[[3]](#3), with a workshop in September 2024.
 
"This workshop will provide solid input to the "Implementation" part of Edition II of LADM, to be developed in collaboration with OGC. The workshop should enable making important choices, such as the technical encodings."
 
Initial discussions with the OGC on methodology have been undertaken, and a request to bring the 3D CSDM encoding experience to this workshop has been forthcoming as a result.



<a id="dqm"/>

## ISO 19157 - Data Quality Measures

ISO 19157 is in the process of creating a register of Data Quality Measures.


# References
<a id="1">[1]</a> 
ISO. ISO 19152:2012 Land Administration Domain Model (LADM). https://www.iso.org/obp/ui/#iso:std:iso:19152:ed-1:v1:en.

<a id="2">[2]</a> 
ISO. ISO ISO 19157-1:2023 Geographic information - Data quality. https://www.iso.org/standard/78900.html

<a id="3">[3]</a> 
https://gdmc.nl/3DCadastres/workshop2024/ 
