# Interests

<!--
:Author:    Andrew Hunter
:Email:     <andrew@edgegeomatics.co.nz>
:Date:      21 December 2023
:Updated:   
:Revision:  0.1

:History: 
:Ver 0.1: Initial draft of document
-->

#### Table of Contents

1. [Introduction](#introduction)
2. [Interest Elements](#interest-elements)
3. [Examples](#examples)

## Introduction

The [3D CSDM](https://icsm-au.github.io/3d-csdm/) defines
[Interests](https://icsm-au.github.io/3d-csdm/parcels.html#LandInterest) as *ownership or security towards real
property*. So an Interest in Real property can be diverse and includes Estates in Fee Simple, Leasehold, Stratum held by
individuals, forms of co-ownership such as Joint Tenancy, Customary, Timeshare, and partial rights such as Caveats,
Easements, Profit &agrave; Prendre, Covenants, etc. With regard to information required for the documentation of an
Interest, they can be equally varied.

As such, to simplify specification of many different types of Interests and avoid potential for too many ways of providing additional details we
have developed a set of standardised elements to allow explicit descriptions of different cases, either with free text of by reference to other objects in the Cadastral Survey Dataset, or potentially using URI to external sources, dependending on local implementation requirements.

The following describes elements and metadata that have been developed to describe Interests and presents various 
patterns that can be implemented depending on jurisdictional need.

## Interest Elements
| Title                                 | Descriptions                                                                                                                                                                                                                                                                                                                                                                          | Required   | Use Where                           |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|-------------------------------------|
| <code>adminUnit</code>                | An element used to describe an administrative unit. Typically includes an <code>href</code> element,  a <code>rel</code> element with the value "related"; and a <code>role</code> element.                                                                                                                                                                                           | No         | Both Primary and Secondary parcel   |
| <code>benefited</code>                | An element used to reference an easement with no dominant tenement, i.e., an easement in gross, or a caveat imposed by a municipality, for example.                                                                                                                                                                                                                                   | No         | Secondary parcel                    |
| <code>benefitedParcels[]</code>         | Array element used to identify land adjacent to the Burdened land, by parcel ID, that has the rights attached to it.                                                                                                                                                                                                                                                                  | No         | Both Primary and Secondary parcel   |
| <code>burdenedParcels[]</code>          | Array element used to identify the land, by parcel ID, over which rights are given under an easement.                                                                                                                                                                                                                                                                                 | No</br>Yes | Primary parcel</br>Secondary parcel |
| <code>dateExpire</code>               | The date-time element declaring when an interest expires.                                                                                                                                                                                                                                                                                                                             | No         | Both Primary and Secondary parcel   |
| <code>dateInForce</code>              | Date and time the interest was created.                                                                                                                                                                                                                                                                                                                                               | No         | Both Primary and Secondary parcel   |
| <code>desc</code>                     | Free text describing the Interest or providing other relevant information.                                                                                                                                                                                                                                                                                                            | No         | Both Primary and Secondary parcel   |
| <code>entitlementPortion</code>       | A number (percent) assigned to each strata lot that determines the share of common property and assets belonging to the strata lot. If <code>liabilityPortion</code> is not used, then it is also used to determine the share of expenses and liabilities each strata lot owner is responsible for.                                                                                   | No         | Primary parcel                      |
| <code>href</code>                     | An element that points to a jurisdictional vocabulary and notation for an administrative unit;                                                                                                                                                                                                                                                                                        | No         | Both Primary and Secondary parcel   |
| <code>interest</code>                 | A string element identifying the interest. It could be a title reference, an easement document numer, etc.                                                                                                                                                                                                                                                                            | No         | Both Primary and Secondary parcel                             |
| <code>interestLink</code>             | A resource identifier (IRI), ideally the ID of the document describing the interest.                                                                                                                                                                                                                                                                                                  | Yes        | Both Primary and Secondary parcel   |
| <code>interests[]</code>                | Array element used to group parcel interests. The element may be empty for a Primary Parcel, whereas a Secondary Parcel must specify a set of interests.                                                                                                                                                                                                                              | Yes        | Both Primary and Secondary parcel   |
| <code>interestType</code>             | Jurisdictional vocabulary describing the type of interest                                                                                                                                                                                                                                                                                                                             | Yes        | Both Primary and Secondary parcel   |
| <code>label</code>                    | String element for assigning a label to a secondary parcel.                                                                                                                                                                                                                                                                                                                           | No         | Secondary parcel                    |
| <code>liabilityPortion<code>          | A number (percent) assigned to each strata lot that determines the share of expenses and liabilities that each lot owner is required to pay.                                                                                                                                                                                                                                          | No         | Primary parcel                      |
| <code>originalNotificationLink</code> | A resource identifier (IRI) that links to a document that creates the interest.                                                                                                                                                                                                                                                                                                       | No         | Both Primary and Secondary parcel   |
| <code>referencedParcel</code>         | The Primary parcel ID that an interest relates to that is not the ID of the ID of the parcel that contains the Interest. For example, if a consent condition requires the current parcel is to be amalgamated with another parcel, then the Interest may identify the Primary parcel, or if a covenant covers part of the parcel then the ID of the Secondary parcel may be included. | No         | Both Primary and Secondary parcel   |
| <code>references[]</code>               | An array element that contains a list of things related to the <code>references</code> parent element.                                                                                                                                                                                                                                                                                | No         | Both Primary and Secondary parcel   |
| <code>rel</code>                      | Default value is "related", indicating that the administrative unit is related to the interest.                                                                                                                                                                                                                                                                                       | No         | Both Primary and Secondary parcel   |
| <code>role</code>                     | An element that points to a jurisdictional vocabulary and notation that describes the role of an administrative unit.                                                                                                                                                                                                                                                                 | No         | Both Primary and Secondary parcel   |
| <code>statuteLink</code>              | A resource identifier (IRI) that links to the relevant statute and section that enables an interest.                                                                                                                                                                                                                                                                                  | No         | Both Primary and Secondary parcel   |
| <code>statuteName</code>              | String element for describing relevant statute and section that enables an interest.                                                                                                                                                                                                                                                                                                  | No         | Both Primary and Secondary parcel   |


## Examples
The follow highlights a range of possible Interest patterns that have been used in the examples. Each pattern is 
described briefly, followed by the general pattern used in the example, and then an example with jurisdictional data 
included. The general pattern is transformed to the jurisdictional example by replacing the curly brackets, { and }. and 
the text in between with relevant jurisdictional values. The intent is not to provide an exhaustive set of examples, but
rather show the flexibility of the Interests implementation.

The following pattern and example describe a Certificate of Title reference for a Primary parcel. The example includes 
<code>interestLink</code> and <code>interestType</code> elements, with the <code>interestLink</code> specifying a 
resource identifier, and the <code>interestType</code> element specifying the type of interest.

~~~json lines
{
  "interestLink": "{IRI}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}"
}
~~~
~~~json lines
{
  "interestLink": "6589-1256",
  "interestType": "wa-interest-type:ct"
}
~~~
The following pattern and example describe a notification or memorial, specifically an amalgamation condition of consent 
required by a responsible administrative unit. The pattern includes an <code>interest</code> element containing a string 
defining the interest reference, <code>dateInForce</code> element being a dateTime when the notification came into force
, an <code>interestType</code> element specifying the type of interest, a <code>referencedParcel</code> element 
the parcel ID theat the notification affects, and a <code>desc</code> element describing the interest.

~~~json lines
 {
  "interest": "{interest}",
  "dateInForce": "{dateTime}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "referencedParcel": "{parcel ID}",
  "desc": "{description}"
}
~~~
~~~json lines
 {
  "interest": "321-852-698",
  "dateInForce": "2025-12-21T00:05:38Z",
  "interestType": "nz-interest-type:a",
  "referencedParcel": "5146568",
  "desc": "Lot 1 shall hold a one twelfth share of Lot 29 DP 119553 (Legal Lot Access) and that an individual Record of Title be issued in accordance therewith."
}
~~~

The following is an example identical to the example above, but is for a notice or memorial describing a Covenant.  

~~~json lines
{
  "interestLink": "{IRI}",
  "dateInForce": "{dateTime}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "referencedParcel": "{parcel ID}",
  "desc": "{description}"
}
~~~
~~~json lines
{
  "interestLink": "568-9654-8975",
  "dateInForce": "2023-03-10T11:34:16Z",
  "interestType": "nz-interest-type:c",
  "referencedParcel": "8446456",
  "desc": "Lot 2 DP 572532 is subject to a Significant Ecological Area shown as the area marked Z."
}
~~~

The following example sets out a pattern to document entitlements and liabilities for a strata lot. It includes a 
<code>interestLink</code> element containing specifying a resource identifier for the interest, an 
<code>interestType</code> element specifying the type of interest, a <code>parcelReference</code> element containing a 
Primary parcel ID that the interest relates to, and <code>entitlementPortion</code> and <code>liabilityPortion</code> 
elements specifying the share of common property and assets held by the parcel owner and the share of expenses and 
liabilities that the parcel owner is required to pay.

~~~json lines
{
  "interestLink": "{IRI}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "referencedParcel": "{parcel ID}",
  "entitlementPortion": "{integer number between 0 and 100}",
  "liabilityPortion": "{integer number between 0 and 100}"
}
~~~
~~~json lines
{
  "interestLink": "123-345-597",
  "interestType": "vic-interest-type:o-c",
  "referencedParcel": "1-PS914576",
  "entitlementPortion": "50",
  "liabilityPortion": "50"
}
~~~

The following is a conventional easement example. It includes a <code>interestLink</code> element containing a resource 
identifier for the interest, <code>label</code> element being a string element assigned to the secondary parcel, 
<code>interestType</code> element specifying the type of interest, a <code>statuteName</code> element being a string 
element describing the statute and section that enables an interest, <code>burdenedParcels</code> element containing an 
array of parcel IDs over which rights are given under the easement, and a <code>benefitedParcels</code> element an array 
element that identifies land adjacent to the Burdened land, by parcel ID, that has the rights attached to it.

~~~json lines
{
  "interestLink": "{IRI}",
  "label": "{string}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "statuteName": "{Statute and section}",
  "burdenedParcels": [
    "{Parcel ID}",
    "{Parcel ID}",
    ...
  ],
  "benefitedParcels": [
   "{Parcel ID}",
    "{Parcel ID}",
    ...
  ]
}
~~~

~~~json lines
{
  "interestLink": "e-123456789",
  "label": "E1",
  "interestType": "vic-interest-type:easement-drainage",
  "statuteName": "Section 12(2) of the Subdivision Act 1988, Victoria",
  "burdenedParcels": [
    "1-PS914576X",
    "2-PS914576X",
    "3-PS914576X"
  ],
  "benefitedParcels": [
    "1-PS914576X",
    "2-PS914576X",
    "3-PS914576X"
  ]
}
~~~                      

The following covenant example is similar to the easement example above. It includes a <code>interestLink</code> element 
containing a resource identifier for the interest, an <code>interestType</code> element specifying the type of interest, 
a <code>statuteLink</code> element being a resource identifier (IRI) that links to the relevant statute and section that 
enables an interest, an <code>originalNotificationLink</code> the specifies a CURIE that links to a document that 
creates the interest, a <code>dateExpires</code> element defining when the Covenant expires, a 
<code>burdenedParcels</code> element containing an array of parcel IDs over which rights are given under the easement, 
and a <code>benefitedParcels</code> element an array element that identifies land adjacent to the Burdened land, by 
parcel ID, that has the rights attached to it.

~~~json lines
{
  "interestLink": "{IRI}",
  "interestType": "{jurisdiction}-secondary-purpose:{secondary purpose notation}",
  "statuteLink": "{jurisdiction}-interest:{statue notation for interest}",
  "originalNotificationLink": "{CURIE pointing to jurisdiction document store}:{document ID}",
  "dateExpires": "dateTime",
  "burdenedParcels": [
    "{parcel ID}"
  ],
  "benefitedParcels": [
    "{parcel ID}",
    "{parcel ID}",
    ...
  ]
}
~~~
~~~json lines
{
  "interestLink": "689-654-852",
  "interestType": "wa-secondary-purpose:restrictive-covenant-building-envelope",
  "statuteLink": "wa-interest:easement-tla-136D",
  "originalNotificationLink": "wa-doc:M443039",
  "dateExpires": "2022-12-31T23:59:59Z",
  "burdenedParcels": [
    "1301"
  ],
  "benefitedParcels": [
    "1302",
    "1303",
    "1304",
    "1305",
    "1306"
  ]
}
~~~

The following notification example is similar to the covenant example above, except there is no 
<code>benefitedParcel</code> element, and a <code>desc</code> element has been included to describe the notification 
interest.

~~~json lines
{
  "interestLink": "{IRI}",
  "interestType": "{jurisdiction}-secondary-purpose:{secondary purpose notation}",
  "statuteLink": "{jurisdiction}-interest:{statue notation for interest}",
  "originalNotificationLink": "{CURIE pointing to jurisdiction document store}:{document ID}",
  "desc": "{description}",
  "burdenedParcels": [
    "{parcel ID}"
  ]
}
~~~
~~~json lines
{
  "interestLink": "689-654-800",
  "interestType": "wa-secondary-purpose:notification",
  "statuteLink": "wa-interest-type:165-pda",
  "originalNotificationLink": "wa-doc:M443040",
  "desc": "Mosquitoes",
  "burdenedParcels": [
    "1301"
  ]
}
~~~

The following is an example of a covenant required by an administrative unit. The administrative unit is described by 
reference to an administrative unit using the same pattern used to identify the administrative units for the CSD.
~~~json lines
{
  "label": "{string}",
  "interestLink": "{IRI}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "statuteName": "{String describing relevant Statute and section}",
  "burdenedParcels": [
    "{parcel ID}"
  ],
  "benefited": {
    "references": [
      {
        "adminUnit": {
          "href": "{jurisdictional administrative unit}:{administrative unit notation}",
          "rel": "related",
          "role": "icsm-admin-unit-type:{administrative unit type notation}"
        }
      }
    ]
  }
}
~~~
~~~json lines
{
  "label": "Z",
  "interestLink": "123-456-789",
  "interestType": "nz-interest-type:ta-c-c",
  "statuteName": "Section 6(c) of the Resource Management Act 1991, New Zealand",
  "burdenedParcels": [
    "8446455"
  ],
  "benefited": {
    "references": [
      {
        "adminUnit": {
          "href": "nz-territorial-authority:076",
          "rel": "related",
          "role": "icsm-admin-unit-type:territorialAuthority"
        }
      }
    ]
  }
}
~~~
The following is an example of an Easement in Gross required by an administrative unit. In this example the 
administrative unit is described using a string value.

~~~json lines
{
  "interestLink": "{IRI}",
  "label": "{string}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "statuteName": "{String describing relevant Statute and section}",
  "burdenedParcels": [
    "{parcel ID}",
    "{parcel ID}",
    ...
  ],
  "benefited": {
    "references": [
      "{Name of administrative unit}"
    ]
  }
}
~~~

~~~json lines
{
  "interestLink": "e-123456790",
  "label": "E1",
  "interestType": "vic-interest-type:easement-in-gross-drainage-sewerage",
  "statuteName": "Section 12(2) of the Subdivision Act 1988, Victoria",
  "burdenedParcels": [
    "1-PS914576X",
    "2-PS914576X",
    "3-PS914576X"
  ],
  "benefited": {
    "references": [
      "Maribyrnong City Council"
    ]
  }
}
~~~

The following is an example of an Easement where the statute reference is a defined using an <code>href</code> CURIE.

~~~json lines
{
  "interest":"{string}",
  "label": "{string}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "statuteName": "{String describing relevant Statute and section}",
  "href": "{CURIE}",
  "burdenedParcels": [
    "{parcel ID}",
    "{parcel ID}",
    ...
  ],
  "benefitedParcels": [
    "{parcel ID}",
    "{parcel ID}",
    ...
  ]
}
~~~
~~~json lines
{
  "label": "E1",
  "interestType": "vic-interest-type:easement-drainage",
  "statuteName": "Section 12(2) of the Subdivision Act 1988, Victoria",
  "href": "vic-leg:sa1988153/s12.html",
  "burdenedParcels": [
    "1-PS914576X",
    "2-PS914576X",
    "3-PS914576X"
  ],
  "benefitedParcels": [
    "1-PS914576X",
    "2-PS914576X",
    "3-PS914576X"
  ]
}
~~~
The following is an example of a Restrictive Covenant described by a <code>desc</code> element. The Restrictive Covenant 
is for a conservation area in this instance covered under s. 38 of the Community Titles Act and s.54 of the Community 
Titles Regulations, Western Australia.

~~~json lines
{
  "interestLink": "{IRI}",
  "interestType": "{jurisdiction}-interest-type:{interest type notation}",
  "burdenedParcels": [
    "{parcel ID}"
  ],
  "desc": "{description}"
}
~~~

~~~json lines
{
  "interestLink": "345-098-456",
  "interestType": "wa-interest-type:res-cov-cta-38-reg-54-conserv",
  "burdenedParcels": [
    "11636634"
  ],
  "desc": "PA 15 (Bates/Mulkas Cave Art Site) Gov. Gaz. 5/4/1974 pg. 1180"
}
~~~
