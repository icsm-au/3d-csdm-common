# Quality

<!--
:Author:    Andrew Hunter
:Email:     <andrew@edgegeomatics.co.nz>
:Date:      23 December 2023
:Updated:   
:Revision:  0.1

:History: 
:Ver 0.1: Initial draft of document
-->

#### Table of Contents

1. [Introduction](#introduction)


## Introduction
Survey Points, Survey Observations, and Parcels all allow quality measures to be includes as part of their metadata. The 
jurisdictions have generally acknowledged that ICSM's [Standard for the Australian Survey Control Network (SP1)](https://www.icsm.gov.au/sites/default/files/2020-12/Standard-for-Australian-Survey-Control-Network_v2.2.pdf) is
to be adopted. SP1 defines quality in terms of uncertainty. Uncertainty is defined as doubt about the validity of a 
measurement or result of a measurement (e.g., a position). Uncertainty is an indication of how wrong a value may be and 
is used to quantify the level of survey quality, expressed as a standard deviation in the International System of Units 
(SI) expanded to the 95% confidence level.

This definition is focused on measurements. However, we note that with respect to cadastral survey data, it can be 
argued that there are two general types of quality metrics. One being observation quality, i.e., what is the quality of 
field observations; and two, computational quality, or how well does a set of survey observations (and adoptions) fit to 
the cadastral network.

In order for the quality measures to be interpreted appropriately it is important that different types of quality 
measures required by a jurisdiction are clearly defined.

Given the implementation developed to date, survey points include a <code>pointQualityMeasure</code> element for 
describing the quality of the survey point given the survey framework that the survey point is connected to. In the 
examples, the value is a <code>float</code> data type. For observations, there are <code>distanceAccuracy</code> and 
<code>angleAccuracy</code> elements to specify the quality of the vector observation. As with survey points, the values 
included in the examples are <code>float</code> data types. At this stage jurisdictions do not appear to include parcel 
quality in their LandXML/ePlan or CSD data.

Jurisdictions define accuracy criteria to ensure that the cadastral survey system maintains an appropriate level of 
accuracy. These metrics are often specified as a constant plus scale factor, or as a relative fraction. They are 
essentially pass/fail criteria used as part of the assessment of information collected as part of a cadastral survey. It 
is the surveyors responsibility to meet specified quality metrics where practicable. 

Given survey equipment and computational methods frequently used today, covariance matrices may also be an appropriate 
method for specifying quality metrics.

Further guidance re quality metadata can also be found in [ISO 19157-1:2023 - Geographic Information - Data Quality](https://www.iso.org/obp/ui/#iso:std:iso:19157:-1:ed-1:v1:en). 
ISO 19157 is a standard for describing the quality of geographic data.