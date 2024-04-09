---
title: Survey Features (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>Survey Features</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: Survey Features (Schema)
---


# Survey Features `icsm.csdm.features.SurveyFeatures`

The set of geographic features present on a survey - these include the FeatureOfInterest for observations

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/icsm-au/3d-csdm-common/blob/main/build/tests/csdm/features/SurveyFeatures/" target="_blank">valid</a></strong>
</aside>

# Description

## Survey Point

Any point of interest in a survey. It may relate to a boundary corner (marked or unmarked), a cadastral mark, a geodetic reference mark, or an occupation mark.

This is an abstract class, usually implemented by a subclass such as a SurevyMark with additional details.


# Examples

## Example Survey Points



```json
{
  "@context": {
    "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
    "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
    "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
    "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
    "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypoint-purpose/",
    "nz-surveypoint-state": "https://linked.data.gov.au/def/csdm/nz-surveypoint-state/",
    "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
    "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
    "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
    "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
    "registered-surveyors": "https://example.org/surveyors/",
    "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
  },
  "id": "P1",
  "type": "Feature",
  "featureType": "BoundaryMark",
  "note": "All survey marks will have a monumented state - a physical monument may be absent however using a monument type which is an explicit statement about the state",
  "geometry": {
    "type": "Point",
    "coordinates": [
      1.1,
      2.7
    ]
  },
  "properties": {
    "purpose": "nz-surveypoint-purpose:boundary",
    "state": "nz-surveypoint-state:original",
    "monumentedBy": {
      "form": "nz-monument-form:pin",
      "condition": "nz-monument-condition:fair",
      "state": "nz-monument-state:present"
    },
    "name": {
      "label": "IS I - DP 3333",
      "hasPart": [
        {
          "type": "Source",
          "label": "DP 3333"
        },
        {
          "type": "Stamp",
          "label": "IS I"
        }
      ]
    }
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/surveymark">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fsurveymark&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "@context": [
    "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/context.jsonld",
    {
      "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
      "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
      "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
      "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
      "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypoint-purpose/",
      "nz-surveypoint-state": "https://linked.data.gov.au/def/csdm/nz-surveypoint-state/",
      "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
      "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
      "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
      "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
      "registered-surveyors": "https://example.org/surveyors/",
      "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
    }
  ],
  "id": "P1",
  "type": "Feature",
  "featureType": "BoundaryMark",
  "note": "All survey marks will have a monumented state - a physical monument may be absent however using a monument type which is an explicit statement about the state",
  "geometry": {
    "type": "Point",
    "coordinates": [
      1.1,
      2.7
    ]
  },
  "properties": {
    "purpose": "nz-surveypoint-purpose:boundary",
    "state": "nz-surveypoint-state:original",
    "monumentedBy": {
      "form": "nz-monument-form:pin",
      "condition": "nz-monument-condition:fair",
      "state": "nz-monument-state:present"
    },
    "name": {
      "label": "IS I - DP 3333",
      "hasPart": [
        {
          "type": "Source",
          "label": "DP 3333"
        },
        {
          "type": "Stamp",
          "label": "IS I"
        }
      ]
    }
  }
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/surveymark.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fsurveymark.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix commonpatterns: <https://linked.data.gov.au/def/csdm/commonpatterns/> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix eg1: <https://linked.data.gov.au/def/csdm/csd-example/> .
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix nz-monument-condition: <https://linked.data.gov.au/def/csdm/nz-monument-condition/> .
@prefix nz-monument-form: <https://linked.data.gov.au/def/csdm/nz-monument-form/> .
@prefix nz-monument-state: <https://linked.data.gov.au/def/csdm/nz-monument-state/> .
@prefix nz-surveypoint-purpose: <https://linked.data.gov.au/def/csdm/nz-surveypoint-purpose/> .
@prefix nz-surveypoint-state: <https://linked.data.gov.au/def/csdm/nz-surveypoint-state/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

eg1:P1 a surv:BoundaryMark,
        geojson:Feature ;
    rdfs:label [ rdfs:label "IS I - DP 3333" ;
            dct:hasPart [ rdfs:label "IS I" ;
                    commonpatterns:namePartType "Stamp" ],
                [ rdfs:label "DP 3333" ;
                    commonpatterns:namePartType "Source" ] ] ;
    rdfs:comment "All survey marks will have a monumented state - a physical monument may be absent however using a monument type which is an explicit statement about the state" ;
    surv:monumentedBy [ surv:condition nz-monument-condition:fair ;
            surv:form nz-monument-form:pin ;
            surv:state nz-monument-state:present ] ;
    surv:purpose nz-surveypoint-purpose:boundary ;
    surv:state nz-surveypoint-state:original ;
    geojson:geometry [ a geojson:Point ;
            geojson:coordinates ( 1.1e+00 2.7e+00 ) ] .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/surveymark.ttl">Open in new window</a>
</blockquote>


An example Survey Point showing use of GeoJSON geometry and compound names.
Note that the in FG-JSON "place" is used as a geometry element since "geometry" is defined to be WGS84,
 however by "prior agreement" an alternative CRS can be defined.

Either geometry will inherit its CRS from the container's defaults.
3D wil require an extended model however - possibly by extending FG-JSON - or adding explicit topology.


## Example Geodetic Mark



```json
{
  "@context": {
    "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
    "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
    "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
    "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
    "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/",
    "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
    "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
    "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
    "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
    "registered-surveyors": "https://example.org/surveyors/",
    "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
  },
  "id": "P2",
  "type": "Feature",
  "featureType": "GeodeticReferenceMark",
  "geometry": {
    "type": "Point",
    "coordinates": [
      2.1,
      3.7
    ]
  },
  "properties": {
    "name": {
      "label": "IS II - DP 3333",
      "hasPart": [
        {
          "type": "Source",
          "label": "DP 3333"
        },
        {
          "type": "Stamp",
          "label": "IS II"
        }
      ]
    },
    "purpose": "nz-surveypoint-purpose:geodeticref",
    "monumentedBy": {
      "form": "nz-monument-form:pin",
      "condition": "nz-monument-condition:fair",
      "state": "nz-monument-state:present"
    },
    "geodeticid": "XX 33455"
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/geodeticmark">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fgeodeticmark&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "@context": [
    "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/context.jsonld",
    {
      "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
      "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
      "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
      "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
      "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/",
      "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
      "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
      "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
      "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
      "registered-surveyors": "https://example.org/surveyors/",
      "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
    }
  ],
  "id": "P2",
  "type": "Feature",
  "featureType": "GeodeticReferenceMark",
  "geometry": {
    "type": "Point",
    "coordinates": [
      2.1,
      3.7
    ]
  },
  "properties": {
    "name": {
      "label": "IS II - DP 3333",
      "hasPart": [
        {
          "type": "Source",
          "label": "DP 3333"
        },
        {
          "type": "Stamp",
          "label": "IS II"
        }
      ]
    },
    "purpose": "nz-surveypoint-purpose:geodeticref",
    "monumentedBy": {
      "form": "nz-monument-form:pin",
      "condition": "nz-monument-condition:fair",
      "state": "nz-monument-state:present"
    },
    "geodeticid": "XX 33455"
  }
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/geodeticmark.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fgeodeticmark.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix commonpatterns: <https://linked.data.gov.au/def/csdm/commonpatterns/> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix eg1: <https://linked.data.gov.au/def/csdm/csd-example/> .
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix nz-monument-condition: <https://linked.data.gov.au/def/csdm/nz-monument-condition/> .
@prefix nz-monument-form: <https://linked.data.gov.au/def/csdm/nz-monument-form/> .
@prefix nz-monument-state: <https://linked.data.gov.au/def/csdm/nz-monument-state/> .
@prefix nz-surveypoint-purpose: <https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

eg1:P2 a surv:GeodeticReferenceMark,
        geojson:Feature ;
    rdfs:label [ rdfs:label "IS II - DP 3333" ;
            dct:hasPart [ rdfs:label "IS II" ;
                    commonpatterns:namePartType "Stamp" ],
                [ rdfs:label "DP 3333" ;
                    commonpatterns:namePartType "Source" ] ] ;
    surv:geodeticid "XX 33455" ;
    surv:monumentedBy [ surv:condition nz-monument-condition:fair ;
            surv:form nz-monument-form:pin ;
            surv:state nz-monument-state:present ] ;
    surv:purpose nz-surveypoint-purpose:geodeticref ;
    geojson:geometry [ a geojson:Point ;
            geojson:coordinates ( 2.1e+00 3.7e+00 ) ] .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/geodeticmark.ttl">Open in new window</a>
</blockquote>


An example Geodetic Mark extending Survey Point with additional geodeticid attribute


## Example Monument



```json
{
  "@context": {
    "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
    "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
    "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
    "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
    "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/",
    "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
    "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
    "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
    "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
    "registered-surveyors": "https://example.org/surveyors/",
    "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
  },
  "form": "nz-monument-form:pin",
  "condition": "nz-monument-condition:fair",
  "state": "nz-monument-state:present"
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/monument">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fmonument&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "@context": [
    "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/context.jsonld",
    {
      "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
      "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
      "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
      "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
      "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/",
      "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
      "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
      "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
      "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
      "registered-surveyors": "https://example.org/surveyors/",
      "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
    }
  ],
  "form": "nz-monument-form:pin",
  "condition": "nz-monument-condition:fair",
  "state": "nz-monument-state:present"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/monument.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fmonument.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix nz-monument-condition: <https://linked.data.gov.au/def/csdm/nz-monument-condition/> .
@prefix nz-monument-form: <https://linked.data.gov.au/def/csdm/nz-monument-form/> .
@prefix nz-monument-state: <https://linked.data.gov.au/def/csdm/nz-monument-state/> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .

[] surv:condition nz-monument-condition:fair ;
    surv:form nz-monument-form:pin ;
    surv:state nz-monument-state:present .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/monument.ttl">Open in new window</a>
</blockquote>


A monument as a standalone object


## Vectors



```json
{
  "@context": {
    "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
    "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
    "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
    "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
    "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/",
    "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
    "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
    "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
    "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
    "registered-surveyors": "https://example.org/surveyors/",
    "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
  },
  "id": "P1P3",
  "type": "Feature",
  "featureType": "ObservedVector",
  "geometry": null,
  "topology": {
    "type": "LineString",
    "references": [ "P1", "P3"]
  },
  "properties": {
    "fromSurvey": "csdref-1",
    "vectorPurpose": "code:aPurpose",
    "distance": 3.444
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/surveyvectors">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fsurveyvectors&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "@context": [
    "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/context.jsonld",
    {
      "@base": "https://linked.data.gov.au/def/csdm/csd-example/",
      "eg1": "https://linked.data.gov.au/def/csdm/csd-example/",
      "surveyable": "https://linked.data.gov.au/def/csdm/observedProperties/",
      "surveyproc": "https://linked.data.gov.au/def/csdm/observationProcedures/",
      "nz-surveypoint-purpose": "https://linked.data.gov.au/def/csdm/nz-surveypointpurpose/",
      "icsm-survey-type": "https://linked.data.gov.au/def/csdm/icsm-survey-type/",
      "nz-monument-form": "https://linked.data.gov.au/def/csdm/nz-monument-form/",
      "nz-monument-condition": "https://linked.data.gov.au/def/csdm/nz-monument-condition/",
      "nz-monument-state": "https://linked.data.gov.au/def/csdm/nz-monument-state/",
      "registered-surveyors": "https://example.org/surveyors/",
      "icsm-jurisdictions": "https://linked.data.gov.au/def/jurisdictions/"
    }
  ],
  "id": "P1P3",
  "type": "Feature",
  "featureType": "ObservedVector",
  "geometry": null,
  "topology": {
    "type": "LineString",
    "references": [
      "P1",
      "P3"
    ]
  },
  "properties": {
    "fromSurvey": "csdref-1",
    "vectorPurpose": "code:aPurpose",
    "distance": 3.444
  }
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/surveyvectors.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fsurveyvectors.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix eg1: <https://linked.data.gov.au/def/csdm/csd-example/> .
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .

eg1:P1P3 a surv:ObservedVector,
        geojson:Feature ;
    surv:vectorPurpose <code:aPurpose> ;
    geojson:topology [ a geojson:LineString ;
            geojson:relatedFeatures ( eg1:P1 eg1:P3 ) ] .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyFeatures/surveyvectors.ttl">Open in new window</a>
</blockquote>


An example vector (line between two points) using the topo-line schema from the generalised topo-feature module


# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
description: Survey Features
$defs:
  coderef:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
  nullableString:
    oneOf:
    - type: string
    - type: 'null'
  TopoLine:
    $ref: https://ogcincubator.github.io/topo-feature/build/annotated/geo/topo/features/topo-line/schema.yaml
  FeatureOptions:
    anyOf:
    - $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/geo/json-fg/feature/schema.yaml
    - $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/geo/json-fg/feature-lenient/schema.yaml
    - $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/geo/common/data_types/geojson/schema.yaml
  SurveyPointProperties:
    type: object
    properties:
      name:
        $ref: https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/datatypes/compoundName/schema.yaml
        x-jsonld-id: https://linked.data.gov.au/def/csdm/commonpatterns/name
        x-jsonld-type: '@id'
      purpose:
        oneOf:
        - $ref: '#/$defs/coderef'
        - type: array
          items:
            $ref: '#/$defs/coderef'
        x-jsonld-type: '@id'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/purpose
      has_provenance:
        $ref: https://ogcincubator.github.io/bblock-prov-schema/build/annotated/ogc-utils/prov/schema.yaml
      ptQuality:
        $ref: '#/$defs/coderef'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/commonpatterns/qualityClass
        x-jsonld-type: '@id'
      ptQualityMeasure:
        type: number
        x-jsonld-id: https://linked.data.gov.au/def/csdm/commonpatterns/qualityMeasure
        x-jsonld-type: '@id'
      comment:
        $ref: '#/$defs/nullableString'
        x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
    required:
    - purpose
  OccupationMark:
    allOf:
    - $ref: '#/$defs/FeatureOptions'
    - type: object
      properties:
        featureType:
          const: OccupationMark
        properties:
          $ref: '#/$defs/OccupationMarkProperties'
    required:
    - featureType
  OccupationMarkProperties:
    allOf:
    - $ref: '#/$defs/SurveyPointProperties'
    - type: object
      properties:
        age:
          type: string
          description: A string that may be constrained to a number or range using
            a regex
          x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/age
        note:
          type: string
          x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
      required:
      - age
  SurveyMarkProperties:
    allOf:
    - $ref: '#/$defs/SurveyPointProperties'
    - type: object
      properties:
        monumentedBy:
          $ref: '#/$defs/Monument'
          x-jsonld-type: '@id'
          x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/monumentedBy
      required:
      - monumentedBy
  GeodeticReferenceMark:
    allOf:
    - $ref: '#/$defs/FeatureOptions'
    properties:
      featureType:
        const: GeodeticReferenceMark
      properties:
        allOf:
        - $ref: '#/$defs/GeodeticReferenceMarkProperties'
    required:
    - featureType
  GeodeticReferenceMarkProperties:
    type: object
    allOf:
    - $ref: '#/$defs/SurveyMarkProperties'
    - type: object
      properties:
        geodeticid:
          $ref: https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/datatypes/compoundName/schema.yaml
          x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/geodeticid
      required:
      - geodeticid
  CadastralMark:
    properties:
      featureType:
        const: CadastralMark
      properties:
        allOf:
        - $ref: '#/$defs/SurveyMarkProperties'
    required:
    - featureType
  BoundaryMark:
    properties:
      featureType:
        const: BoundaryMark
      properties:
        allOf:
        - $ref: '#/$defs/SurveyMarkProperties'
    required:
    - featureType
  Monument:
    type: object
    properties:
      condition:
        $ref: '#/$defs/coderef'
        x-jsonld-type: '@id'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/condition
      form:
        $ref: '#/$defs/coderef'
        x-jsonld-type: '@id'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/form
      replaces:
        type: string
        format: uri-reference
        x-jsonld-type: '@id'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/replaces
      state:
        $ref: '#/$defs/coderef'
        x-jsonld-type: '@id'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/state
    required:
    - state
  SurveyedVector:
    x-json-comment: featureType is not defined - this is abstract and overidden by
      subclasses
    allOf:
    - $ref: '#/$defs/TopoLine'
    - featureType:
        const: SurveyedVector
    - properties:
        properties:
          $ref: '#/$defs/SurveyedVectorProperties'
      required:
      - featureType
  SurveyedVectorProperties:
    type: object
    properties:
      distance:
        type: number
      vectorPurpose:
        $ref: '#/$defs/coderef'
        x-jsonld-type: '@id'
        x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/vectorPurpose
      comment:
        $ref: '#/$defs/nullableString'
        x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
    required:
    - vectorPurpose
  AdoptedVector:
    x-json-comment: featureType is not defined - this is abstract and overidden by
      subclasses
    allOf:
    - $ref: '#/$defs/TopoLine'
    - featureType:
        const: AdoptedVector
    - properties:
        properties:
          $ref: '#/$defs/AdoptedVectorProperties'
      required:
      - featureType
  AdoptedVectorProperties:
    allOf:
    - $ref: '#/$defs/SurveyedVectorProperties'
    - properties:
        fromSurvey:
          $ref: '#/$defs/coderef'
          x-jsonld-type: '@id'
          x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/fromSurvey
anyOf:
- $ref: '#/$defs/BoundaryMark'
- $ref: '#/$defs/OccupationMark'
- $ref: '#/$defs/CadastralMark'
- $ref: '#/$defs/GeodeticReferenceMark'
- $ref: '#/$defs/Monument'
- $ref: '#/$defs/SurveyedVector'
x-jsonld-extra-terms:
  place: https://purl.org/geojson/vocab#geometry
  CadastralMark:
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/CadastralMark
    x-jsonld-type: '@id'
  BoundaryMark:
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/BoundaryMark
    x-jsonld-type: '@id'
  GeodeticReferenceMark:
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/GeodeticReferenceMark
    x-jsonld-type: '@id'
  ObservedVector:
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/ObservedVector
    x-jsonld-type: '@id'
  AdoptedVector:
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/SurveyedVector
    x-jsonld-type: '@id'
  label: http://www.w3.org/2000/01/rdf-schema#label
x-jsonld-prefixes:
  geojson: https://purl.org/geojson/vocab#
  surv: https://linked.data.gov.au/def/csdm/surveyfeatures/
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  commonpatterns: https://linked.data.gov.au/def/csdm/commonpatterns/
  csdm: https://linked.data.gov.au/def/csdm/
  geosparql: http://www.opengis.net/ont/geosparql#
  dct: http://purl.org/dc/terms/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Fannotated%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/schema.yaml" target="_blank">https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/schema.yaml</a>
* JSON version: <a href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/schema.json" target="_blank">https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
    "name": {
      "@context": {
        "hasPart": {
          "@context": {
            "type": "commonpatterns:namePartType"
          },
          "@id": "dct:hasPart"
        },
        "name": "commonpatterns:name"
      },
      "@id": "rdfs:label",
      "@type": "@id"
    },
    "purpose": {
      "@type": "@id",
      "@id": "surv:purpose"
    },
    "id": "@id",
    "featureType": "@type",
    "entityType": "@type",
    "has_provenance": {
      "@context": {},
      "@id": "dct:provenance",
      "@type": "@id"
    },
    "wasGeneratedBy": {
      "@context": {},
      "@id": "prov:wasGeneratedBy",
      "@type": "@id"
    },
    "wasAttributedTo": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasAttributedTo",
      "@type": "@id"
    },
    "wasDerivedFrom": {
      "@id": "prov:wasDerivedFrom",
      "@type": "@id"
    },
    "alternateOf": {
      "@id": "prov:alternateOf",
      "@type": "@id"
    },
    "hadPrimarySource": {
      "@id": "prov:hadPrimarySource",
      "@type": "@id"
    },
    "specializationOf": {
      "@id": "prov:specializationOf",
      "@type": "@id"
    },
    "wasInvalidatedBy": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasInvalidatedBy",
      "@type": "@id"
    },
    "wasQuotedFrom": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasQuotedFrom",
      "@type": "@id"
    },
    "wasRevisionOf": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasRevisionOf",
      "@type": "@id"
    },
    "mentionOf": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:mentionOf",
      "@type": "@id"
    },
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "links": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "rdfs:seeAlso"
    },
    "qualifiedGeneration": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        }
      },
      "@id": "prov:qualifiedGeneration",
      "@type": "@id"
    },
    "qualifiedInvalidation": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        }
      },
      "@id": "prov:qualifiedInvalidation",
      "@type": "@id"
    },
    "qualifiedDerivation": {
      "@context": {
        "hadGeneration": {
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            }
          },
          "@id": "prov:hadGeneration",
          "@type": "@id"
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        },
        "hadUsage": {
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            }
          },
          "@id": "prov:hadUsage",
          "@type": "@id"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedDerivation",
      "@type": "@id"
    },
    "qualifiedAttribution": {
      "@context": {
        "agent": {
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedAttribution",
      "@type": "@id"
    },
    "wasInfluencedBy": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasInfluencedBy",
      "@type": "@id"
    },
    "qualifiedInfluence": {
      "@context": {
        "influencer": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:influencer",
          "@type": "@id"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        },
        "agent": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedInfluence",
      "@type": "@id"
    },
    "provType": "@type",
    "hadMember": {
      "@context": {},
      "@id": "prov:hadMember",
      "@type": "@id"
    },
    "activityType": "@type",
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "wasAssociatedWith": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
      "@type": "@id"
    },
    "used": {
      "@context": {},
      "@id": "prov:used",
      "@type": "@id"
    },
    "wasStartedBy": {
      "@context": {},
      "@id": "prov:wasStartedBy",
      "@type": "@id"
    },
    "wasEndedBy": {
      "@context": {},
      "@id": "prov:wasEndedBy",
      "@type": "@id"
    },
    "invalidated": {
      "@context": {},
      "@id": "prov:invalidated",
      "@type": "@id"
    },
    "generated": {
      "@context": {},
      "@id": "prov:generated",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedUsage",
      "@type": "@id"
    },
    "qualifiedCommunication": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        }
      },
      "@id": "prov:qualifiedCommunication",
      "@type": "@id"
    },
    "qualifiedStart": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedStart",
      "@type": "@id"
    },
    "qualifiedEnd": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedEnd",
      "@type": "@id"
    },
    "qualifiedAssociation": {
      "@context": {
        "agent": {
          "@id": "prov:agent",
          "@type": "@id"
        },
        "hadRole": {
          "@id": "prov:hadRole",
          "@type": "@id"
        },
        "hadPlan": {
          "@id": "prov:hadPlan",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedAssociation",
      "@type": "@id"
    },
    "agentType": "@type",
    "actedOnBehalfOf": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:actedOnBehalfOf",
      "@type": "@id"
    },
    "qualifiedDelegation": {
      "@context": {
        "agent": {
          "@id": "prov:agent",
          "@type": "@id"
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedDelegation",
      "@type": "@id"
    },
    "Activity": "prov:Activity",
    "ActivityInfluence": "prov:ActivityInfluence",
    "Agent": "prov:Agent",
    "AgentInfluence": "prov:AgentInfluence",
    "Association": "prov:Association",
    "Attribution": "prov:Attribution",
    "Bundle": "prov:Bundle",
    "Collection": "prov:Collection",
    "Communication": "prov:Communication",
    "Delegation": "prov:Delegation",
    "Derivation": "prov:Derivation",
    "EmptyCollection": "prov:EmptyCollection",
    "End": "prov:End",
    "Entity": "prov:Entity",
    "EntityInfluence": "prov:EntityInfluence",
    "Generation": "prov:Generation",
    "Influence": "prov:Influence",
    "InstantaneousEvent": "prov:InstantaneousEvent",
    "Invalidation": "prov:Invalidation",
    "Location": "prov:Location",
    "Organization": "prov:Organization",
    "Person": "prov:Person",
    "Plan": "prov:Plan",
    "PrimarySource": "prov:PrimarySource",
    "Quotation": "prov:Quotation",
    "Revision": "prov:Revision",
    "Role": "prov:Role",
    "SoftwareAgent": "prov:SoftwareAgent",
    "Start": "prov:Start",
    "Usage": "prov:Usage",
    "ServiceDescription": "prov:ServiceDescription",
    "DirectQueryService": "prov:DirectQueryService",
    "Accept": "prov:Accept",
    "Contribute": "prov:Contribute",
    "Contributor": "prov:Contributor",
    "Copyright": "prov:Copyright",
    "Create": "prov:Create",
    "Creator": "prov:Creator",
    "Modify": "prov:Modify",
    "Publish": "prov:Publish",
    "Publisher": "prov:Publisher",
    "Replace": "prov:Replace",
    "RightsAssignment": "prov:RightsAssignment",
    "RightsHolder": "prov:RightsHolder",
    "Submit": "prov:Submit",
    "Dictionary": "prov:Dictionary",
    "EmptyDictionary": "prov:EmptyDictionary",
    "KeyEntityPair": "prov:KeyEntityPair",
    "Insertion": "prov:Insertion",
    "Removal": "prov:Removal",
    "generatedAtTime": {
      "@id": "prov:generatedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "invalidatedAtTime": {
      "@id": "prov:invalidatedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "startedAtTime": {
      "@id": "prov:startedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "value": "prov:value",
    "provenanceUriTemplate": "prov:provenanceUriTemplate",
    "pairKey": {
      "@id": "prov:pairKey",
      "@type": "http://www.w3.org/2000/01/rdf-schema#Literal"
    },
    "removedKey": {
      "@id": "prov:removedKey",
      "@type": "http://www.w3.org/2000/01/rdf-schema#Literal"
    },
    "influenced": {
      "@id": "prov:influenced",
      "@type": "@id"
    },
    "qualifiedPrimarySource": {
      "@id": "prov:qualifiedPrimarySource",
      "@type": "@id"
    },
    "qualifiedQuotation": {
      "@id": "prov:qualifiedQuotation",
      "@type": "@id"
    },
    "qualifiedRevision": {
      "@id": "prov:qualifiedRevision",
      "@type": "@id"
    },
    "has_anchor": {
      "@id": "prov:has_anchor",
      "@type": "@id"
    },
    "has_query_service": {
      "@id": "prov:has_query_service",
      "@type": "@id"
    },
    "describesService": {
      "@id": "prov:describesService",
      "@type": "@id"
    },
    "pingback": {
      "@id": "prov:pingback",
      "@type": "@id"
    },
    "dictionary": {
      "@id": "prov:dictionary",
      "@type": "@id"
    },
    "derivedByInsertionFrom": {
      "@id": "prov:derivedByInsertionFrom",
      "@type": "@id"
    },
    "derivedByRemovalFrom": {
      "@id": "prov:derivedByRemovalFrom",
      "@type": "@id"
    },
    "insertedKeyEntityPair": {
      "@id": "prov:insertedKeyEntityPair",
      "@type": "@id"
    },
    "hadDictionaryMember": {
      "@id": "prov:hadDictionaryMember",
      "@type": "@id"
    },
    "pairEntity": {
      "@id": "prov:pairEntity",
      "@type": "@id"
    },
    "qualifiedInsertion": {
      "@id": "prov:qualifiedInsertion",
      "@type": "@id"
    },
    "qualifiedRemoval": {
      "@id": "prov:qualifiedRemoval",
      "@type": "@id"
    },
    "asInBundle": {
      "@id": "prov:asInBundle",
      "@type": "@id"
    },
    "ptQuality": {
      "@id": "commonpatterns:qualityClass",
      "@type": "@id"
    },
    "ptQualityMeasure": {
      "@id": "commonpatterns:qualityMeasure",
      "@type": "@id"
    },
    "comment": "rdfs:comment",
    "monumentedBy": {
      "@context": {},
      "@type": "@id",
      "@id": "surv:monumentedBy"
    },
    "type": "@type",
    "properties": "@nest",
    "geometry": {
      "@context": {},
      "@id": "geojson:geometry"
    },
    "bbox": {
      "@container": "@list",
      "@id": "geojson:bbox"
    },
    "Feature": "geojson:Feature",
    "FeatureCollection": "geojson:FeatureCollection",
    "GeometryCollection": "geojson:GeometryCollection",
    "LineString": "geojson:LineString",
    "MultiLineString": "geojson:MultiLineString",
    "MultiPoint": "geojson:MultiPoint",
    "MultiPolygon": "geojson:MultiPolygon",
    "Point": "geojson:Point",
    "Polygon": "geojson:Polygon",
    "features": {
      "@container": "@set",
      "@id": "geojson:features"
    },
    "coordinates": {
      "@container": "@list",
      "@id": "geojson:coordinates"
    },
    "age": "surv:age",
    "note": "rdfs:comment",
    "geodeticid": {
      "@context": {
        "hasPart": {
          "@context": {
            "type": "commonpatterns:namePartType"
          },
          "@id": "dct:hasPart"
        },
        "name": "commonpatterns:name"
      },
      "@id": "surv:geodeticid"
    },
    "condition": {
      "@type": "@id",
      "@id": "surv:condition"
    },
    "form": {
      "@type": "@id",
      "@id": "surv:form"
    },
    "replaces": {
      "@type": "@id",
      "@id": "surv:replaces"
    },
    "state": {
      "@type": "@id",
      "@id": "surv:state"
    },
    "topology": {
      "@context": {},
      "@type": "@id",
      "@id": "geojson:topology"
    },
    "references": {
      "@id": "geojson:relatedFeatures",
      "@type": "@id",
      "@container": "@list"
    },
    "Arc": "geojson:Arc",
    "ArcWithCenter": "geojson:ArcWithCenter",
    "ArcByChord": "geojson:ArcByChord",
    "CircleByCenter": "geojson:CircleByCenter",
    "CubicSpline": "geojson:CubicSpline",
    "radius": "geojson:radius",
    "arcLength": "geojson:arcLength",
    "startTangentVector": "geojson:startTangentVector",
    "endTangentVector": "geojson:endTangentVector",
    "vectorPurpose": {
      "@type": "@id",
      "@id": "surv:vectorPurpose"
    },
    "place": "geojson:geometry",
    "CadastralMark": {
      "@id": "surv:CadastralMark",
      "@type": "@id"
    },
    "BoundaryMark": {
      "@id": "surv:BoundaryMark",
      "@type": "@id"
    },
    "GeodeticReferenceMark": {
      "@id": "surv:GeodeticReferenceMark",
      "@type": "@id"
    },
    "ObservedVector": {
      "@id": "surv:ObservedVector",
      "@type": "@id"
    },
    "AdoptedVector": {
      "@id": "surv:SurveyedVector",
      "@type": "@id"
    },
    "label": "rdfs:label",
    "CompoundName": "commonpatterns:CompoundName",
    "geojson": "https://purl.org/geojson/vocab#",
    "surv": "csdm:surveyfeatures/",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "commonpatterns": "csdm:commonpatterns/",
    "csdm": "https://linked.data.gov.au/def/csdm/",
    "geosparql": "http://www.opengis.net/ont/geosparql#",
    "dct": "http://purl.org/dc/terms/",
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Fannotated%2Fcsdm%2Ffeatures%2FSurveyFeatures%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/context.jsonld" target="_blank">https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyFeatures/context.jsonld</a>

# Validation

## SHACL Shapes

The following sets of SHACL shapes are used for validating this building block:

* Feature with topology <small><code>ogc.geo.topo.features.topo-feature</code></small>
  * [https://ogcincubator.github.io/topo-feature/_sources/features/topo-feature-collection/tests/topo-refs-exist.shacl](https://ogcincubator.github.io/topo-feature/_sources/features/topo-feature-collection/tests/topo-refs-exist.shacl)
  * [https://ogcincubator.github.io/topo-feature/_sources/features/topo-feature/tests/geometry-coordinates.shacl](https://ogcincubator.github.io/topo-feature/_sources/features/topo-feature/tests/geometry-coordinates.shacl)
* Compound Name <small><code>icsm.csdm.datatypes.compoundName</code></small>
  * [https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/_sources/csdm/datatypes/compoundName/rules.shacl](https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/_sources/csdm/datatypes/compoundName/rules.shacl)

# References

* [3D Cadastre Survey Data Model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/icsm-au/3d-csdm-common" target="_blank">https://github.com/icsm-au/3d-csdm-common</a>
* Path:
<code><a href="https://github.com/icsm-au/3d-csdm-common/blob/HEAD/_sources/csdm/features/SurveyFeatures" target="_blank">_sources/csdm/features/SurveyFeatures</a></code>

