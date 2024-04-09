---
title: Survey Observations (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>Survey Observations</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: Survey Observations (Schema)
---


# Survey Observations `icsm.csdm.features.SurveyObservations`

An Observation specialisation for an aspect of a survey - typically vectors with new or adopted bearings and distances.

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/icsm-au/3d-csdm-common/blob/main/build/tests/csdm/features/SurveyObservations/" target="_blank">valid</a></strong>
</aside>

# Description

## Survey Point

Any point of interest in a survey. It may relate to a boundary corner (marked or unmarked), a cadastral mark, a geodetic reference mark, or an occupation mark.

This is an abstract class, usually implemented by a subclass such as a SurevyMark with additional details.


# Examples

## New 2D vector



```json
{
  "type": "Feature",
  "geometry": null,
  "time": null,
  "place": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResultQuality": {
      "distanceAccuracy": 0.000100138048,
      "angleAccuracy": 0.028154691543,
      "distanceAccuracyClass": "http://any.valid/",
      "angleAccuracyClass": "http://any.valid/"
    },
    "hasResult": {
      "pose": {
        "angles": {
          "yaw": 231.38
        },
        "distance": 333207.1
      }
    }
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/newvector">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fnewvector&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "type": "Feature",
  "geometry": null,
  "time": null,
  "place": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResultQuality": {
      "distanceAccuracy": 0.000100138048,
      "angleAccuracy": 0.028154691543,
      "distanceAccuracyClass": "http://any.valid/",
      "angleAccuracyClass": "http://any.valid/"
    },
    "hasResult": {
      "pose": {
        "angles": {
          "yaw": 231.38
        },
        "distance": 333207.1
      }
    }
  },
  "@context": "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/newvector.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fnewvector.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix ns1: <https://linked.data.gov.au/def/csdm/surveyobs/> .
@prefix sosa: <http://www.w3.org/ns/sosa/> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] a geojson:Feature ;
    sosa:hasFeatureOfInterest <file:///github/workspace/l973158> ;
    sosa:hasResult [ surv:pose [ surv:distance 3.332071e+05 ] ] ;
    sosa:hasResultQuality [ ns1:angleAccuracyClass <http://any.valid/> ;
            ns1:angleAccuracyMeasure 2.815469e-02 ;
            ns1:distanceAccuracyClass <http://any.valid/> ;
            ns1:distanceAccuracyMeasure 1.00138e-04 ] ;
    sosa:madeBySensor [ ] ;
    sosa:observedProperty <https://linked.data.gov.au/def/csdm/property/pose> ;
    sosa:resultTime "2023-05-22T16:41:00" .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/newvector.ttl">Open in new window</a>
</blockquote>


An example observation of a vector based on bearing and distance - in 2D


## New 3D vector



```json
{
  "type": "Feature",
  "geometry": null,
  "time": null,
  "place": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResult": {
      "pose": {
        "angles": {
          "yaw": 231.38,
          "pitch": -0.001
        },
        "distance": 333207.1
      }
    }
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/newvector-3d">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fnewvector-3d&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "type": "Feature",
  "geometry": null,
  "time": null,
  "place": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResult": {
      "pose": {
        "angles": {
          "yaw": 231.38,
          "pitch": -0.001
        },
        "distance": 333207.1
      }
    }
  },
  "@context": "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/newvector-3d.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fnewvector-3d.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix sosa: <http://www.w3.org/ns/sosa/> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] a geojson:Feature ;
    sosa:hasFeatureOfInterest <file:///github/workspace/l973158> ;
    sosa:hasResult [ surv:pose [ surv:distance 3.332071e+05 ] ] ;
    sosa:madeBySensor [ ] ;
    sosa:observedProperty <https://linked.data.gov.au/def/csdm/property/pose> ;
    sosa:resultTime "2023-05-22T16:41:00" .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/newvector-3d.ttl">Open in new window</a>
</blockquote>


An example observation of a vector based on bearing,pitch (azimuth angle) and distance - in 3D


## Distance (Adopted bearing)



```json
{
  "type": "Feature",
  "geometry": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00+2",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResult": {
      "distance": 333207.1
    }
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/example_3_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fexample_3_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "type": "Feature",
  "geometry": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00+2",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResult": {
      "distance": 333207.1
    }
  },
  "@context": "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/example_3_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fexample_3_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix sosa: <http://www.w3.org/ns/sosa/> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] a geojson:Feature ;
    sosa:hasFeatureOfInterest <file:///github/workspace/l973158> ;
    sosa:hasResult [ surv:distance 3.332071e+05 ] ;
    sosa:madeBySensor [ ] ;
    sosa:observedProperty <https://linked.data.gov.au/def/csdm/property/pose> ;
    sosa:resultTime "2023-05-22T16:41:00+2" .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/example_3_1.ttl">Open in new window</a>
</blockquote>


Example Survey Observation - vector only distance


## Bearing (Adopted distance)



```json
{
  "type": "Feature",
  "geometry": null,
  "time": null,
  "place": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResult": {
      "pose": {
        "angles": {
          "yaw": 231.38,
          "pitch": -0.001
        }
      }
    }
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/example_4_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fexample_4_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "type": "Feature",
  "geometry": null,
  "time": null,
  "place": null,
  "properties": {
    "hasFeatureOfInterest": "l973158",
    "observedProperty": "pose",
    "resultTime": "2023-05-22T16:41:00",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    },
    "hasResult": {
      "pose": {
        "angles": {
          "yaw": 231.38,
          "pitch": -0.001
        }
      }
    }
  },
  "@context": "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/example_4_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fexample_4_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix sosa: <http://www.w3.org/ns/sosa/> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .

[] a geojson:Feature ;
    sosa:hasFeatureOfInterest <file:///github/workspace/l973158> ;
    sosa:hasResult [ surv:pose [ ] ] ;
    sosa:madeBySensor [ ] ;
    sosa:observedProperty <https://linked.data.gov.au/def/csdm/property/pose> ;
    sosa:resultTime "2023-05-22T16:41:00" .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/example_4_1.ttl">Open in new window</a>
</blockquote>


Example Survey Observation - vector only bearing


## Observation Collection



```json
{
  "@context": {
  },
  "id": "vectorObservations",
  "type": "FeatureCollection",
  "featureType": "sosa:ObservationCollection",
  "time": null,
  "properties": {
    "resultTime": "2023-05-24T00:00:00",
    "observedProperty": "surveyable:VectorDetermination",
    "usedProcedure": "surveyproc:traverse",
    "angleType": "angletype:bearing",
    "distanceType": "distancetype:ellipsoidal",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    }
  },
  "features": [
    {
      "type": "Feature",
      "geometry": null,
      "properties": {
        "hasFeatureOfInterest": "l973158",
        "hasResult": {
          "pose": {
            "angles": {
              "yaw": 231.38,
              "pitch": -0.001
            },
            "distance": 333207.1
          }
        }
      }
    }
  ]
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/collection">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fcollection&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "@context": [
    "https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld",
    {}
  ],
  "id": "vectorObservations",
  "type": "FeatureCollection",
  "featureType": "sosa:ObservationCollection",
  "time": null,
  "properties": {
    "resultTime": "2023-05-24T00:00:00",
    "observedProperty": "surveyable:VectorDetermination",
    "usedProcedure": "surveyproc:traverse",
    "angleType": "angletype:bearing",
    "distanceType": "distancetype:ellipsoidal",
    "madeBySensor": {
      "sensorType": "DifferentialGPS",
      "baseSensor": "gps+38666",
      "roverSensor": "gps+37544"
    }
  },
  "features": [
    {
      "type": "Feature",
      "geometry": null,
      "properties": {
        "hasFeatureOfInterest": "l973158",
        "hasResult": {
          "pose": {
            "angles": {
              "yaw": 231.38,
              "pitch": -0.001
            },
            "distance": 333207.1
          }
        }
      }
    }
  ]
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/collection.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Ftests%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fcollection.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix angletype: <https://linked.data.gov.au/def/csdm/defs/angletypes/> .
@prefix distancetype: <https://linked.data.gov.au/def/csdm/defs/distancetypes/> .
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix ns1: <https://linked.data.gov.au/def/csdm/surveyobs/> .
@prefix sosa: <http://www.w3.org/ns/sosa/> .
@prefix surv: <https://linked.data.gov.au/def/csdm/surveyfeatures/> .
@prefix surveyable: <https://linked.data.gov.au/def/csdm/defs/surveyableproperties/> .
@prefix surveyproc: <https://linked.data.gov.au/def/csdm/defs/surveyprocedures/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<http://www.example.com/features/vectorObservations> a sosa:ObservationCollection,
        geojson:FeatureCollection ;
    sosa:hasMember [ a geojson:Feature ;
            sosa:hasFeatureOfInterest <http://www.example.com/features/l973158> ;
            sosa:hasResult [ surv:pose [ surv:distance 3.332071e+05 ] ] ] ;
    sosa:madeBySensor [ ] ;
    sosa:observedProperty surveyable:VectorDetermination ;
    sosa:resultTime "2023-05-24T00:00:00" ;
    sosa:usedProcedure surveyproc:traverse ;
    ns1:angleType angletype:bearing ;
    ns1:distanceType distancetype:ellipsoidal .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/tests/csdm/features/SurveyObservations/collection.ttl">Open in new window</a>
</blockquote>


Example Collection of Survey Observations


# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
description: Survey Vector Observation
$defs:
  coderef:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
  SensorType:
    allOf:
    - properties:
        sensorType:
          $ref: '#/$defs/coderef'
      required:
      - sensorType
    - oneOf:
      - properties:
          sensorType:
            const: DifferentialGPS
          baseSensor:
            type: string
          roverSensor:
            type: string
        required:
        - baseSensor
        - roverSensor
      - properties:
          sensorType:
            not:
              const: DifferentialGPS
  angles:
    type: object
    description: 'Basic-YPR: Basic GeoPose using yaw, pitch, and roll to specify orientation
      - only yaw is mandatory allowing basic 2D applications'
    properties:
      yaw:
        type: number
      pitch:
        type: number
      roll:
        type: number
    required:
    - yaw
  pose-lenient:
    description: 'Basic-YPR: Basic GeoPose using yaw, pitch, and roll to specify orientation'
    type: object
    properties:
      angles:
        $ref: '#/$defs/angles'
    required:
    - angles
  SurveyVectorObsProps:
    allOf:
    - $ref: https://opengeospatial.github.io/ogcapi-sosa/build/annotated/sosa/properties/observation/schema.yaml
    - type: object
      properties:
        hasResultQuality:
          $ref: https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/datatypes/quality/schema.yaml
        hasResult:
          properties:
            pose:
              $ref: '#/$defs/pose-lenient'
              x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/pose
            angle:
              type: number
            distance:
              type: number
              x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyfeatures/distance
          anyOf:
          - required:
            - pose
          - required:
            - distance
          - required:
            - angle
          x-jsonld-id: sosa:hasResult
      required:
      - hasResult
  SurveyVectorObsFeature:
    allOf:
    - $ref: https://opengeospatial.github.io/ogcapi-sosa/build/annotated/sosa/features/observation/schema.yaml
    - properties:
        properties:
          $ref: '#/$defs/SurveyVectorObsProps'
  SurveyVectorObsCollection:
    allOf:
    - $ref: https://opengeospatial.github.io/ogcapi-sosa/build/annotated/sosa/properties/observationCollection/schema.yaml
    - properties:
        features:
          type: array
          items:
            $ref: '#/$defs/SurveyVectorObsFeature'
          x-jsonld-id: sosa:hasMember
          x-jsonld-container: '@set'
        properties:
          properties:
            angleType:
              $ref: '#/$defs/coderef'
              x-jsonld-type: '@id'
              x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyobs/angleType
              x-jsonld-base: https://linked.data.gov.au/def/csdm/defs/angletypes/
            distanceType:
              $ref: '#/$defs/coderef'
              x-jsonld-type: '@id'
              x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyobs/distanceType
              x-jsonld-base: https://linked.data.gov.au/def/csdm/defs/distancetypes/
            madeBySensor:
              $ref: '#/$defs/SensorType'
              x-jsonld-id: sosa:madeBySensor
              x-jsonld-base: https://linked.data.gov.au/def/csdm/sensors/Sensor
            observedProperty:
              $ref: '#/$defs/coderef'
              x-jsonld-id: sosa:observedProperty
              x-jsonld-type: '@id'
              x-jsonld-base: https://linked.data.gov.au/def/csdm/property/
          required:
          - madeBySensor
          - observedProperty
          not:
            required:
            - hasResult
anyOf:
- $ref: '#/$defs/SurveyVectorObsFeature'
- $ref: '#/$defs/SurveyVectorObsCollection'
x-jsonld-prefixes:
  csdm: https://linked.data.gov.au/def/csdm/
  surv: https://linked.data.gov.au/def/csdm/surveyfeatures/
  geopose: https://linked.data.gov.au/def/csdm/utils/geopose/
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  dct: http://purl.org/dc/terms/
  angletype: https://linked.data.gov.au/def/csdm/defs/angletypes/
  distancetype: https://linked.data.gov.au/def/csdm/defs/distancetypes/
  surveyproc: https://linked.data.gov.au/def/csdm/defs/surveyprocedures/
  surveyable: https://linked.data.gov.au/def/csdm/defs/surveyableproperties/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Fannotated%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/schema.yaml" target="_blank">https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/schema.yaml</a>
* JSON version: <a href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/schema.json" target="_blank">https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
    "type": "@type",
    "id": "@id",
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
      "@id": "sosa:hasMember",
      "@context": {
        "features": {
          "@container": "@set",
          "@id": "geojson:features"
        },
        "observedProperty": {
          "@id": "sosa:observedProperty",
          "@type": "@id"
        },
        "madeBySensor": {
          "@id": "sosa:madeBySensor",
          "@type": "@id"
        }
      }
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
    "featureType": "@type",
    "coordinates": {
      "@container": "@list",
      "@id": "geojson:coordinates"
    },
    "resultTime": "sosa:resultTime",
    "phenomenonTime": {
      "@id": "sosa:phenomenonTime",
      "@type": "@id"
    },
    "hasFeatureOfInterest": {
      "@id": "sosa:hasFeatureOfInterest",
      "@type": "@id"
    },
    "observedProperty": {
      "@context": {
        "@base": "https://linked.data.gov.au/def/csdm/property/"
      },
      "@id": "sosa:observedProperty",
      "@type": "@id"
    },
    "usedProcedure": {
      "@id": "sosa:usedProcedure",
      "@type": "@id"
    },
    "madeBySensor": {
      "@context": {
        "@base": "https://linked.data.gov.au/def/csdm/sensors/Sensor"
      },
      "@id": "sosa:madeBySensor",
      "@type": "@id"
    },
    "ActuatableProperty": {
      "@id": "sosa:ActuatableProperty",
      "@type": "@id"
    },
    "Actuation": {
      "@id": "sosa:Actuation",
      "@type": "@id"
    },
    "ActuationCollection": {
      "@id": "sosa:ActuationCollection",
      "@type": "@id"
    },
    "Actuator": {
      "@id": "sosa:Actuator",
      "@type": "@id"
    },
    "Deployment": {
      "@id": "sosa:Deployment",
      "@type": "@id"
    },
    "Execution": {
      "@id": "sosa:Execution",
      "@type": "@id"
    },
    "FeatureOfInterest": {
      "@id": "sosa:FeatureOfInterest",
      "@type": "@id"
    },
    "ObservableProperty": {
      "@id": "sosa:ObservableProperty",
      "@type": "@id"
    },
    "Observation": {
      "@id": "sosa:Observation",
      "@type": "@id"
    },
    "ObservationCollection": {
      "@id": "sosa:ObservationCollection",
      "@type": "@id"
    },
    "Platform": {
      "@id": "sosa:Platform",
      "@type": "@id"
    },
    "Property": {
      "@id": "sosa:Property",
      "@type": "@id"
    },
    "Procedure ": {
      "@id": "sosa:Procedure",
      "@type": "@id"
    },
    "Sample": {
      "@id": "sosa:Sample",
      "@type": "@id"
    },
    "SampleCollection": {
      "@id": "sosa:SampleCollection",
      "@type": "@id"
    },
    "Sampler": {
      "@id": "sosa:Sampler",
      "@type": "@id"
    },
    "Sampling": {
      "@id": "sosa:Sampling",
      "@type": "@id"
    },
    "Sensor": {
      "@id": "sosa:Sensor",
      "@type": "@id"
    },
    "Stimulus": {
      "@id": "sosa:Stimulus",
      "@type": "@id"
    },
    "System": {
      "@id": "sosa:System",
      "@type": "@id"
    },
    "actsOnProperty": {
      "@id": "sosa:actsOnProperty",
      "@type": "@id"
    },
    "deployedOnPlatform": {
      "@id": "sosa:deployedOnPlatform",
      "@type": "@id"
    },
    "deployedSystem": {
      "@id": "sosa:deployedSystem",
      "@type": "@id"
    },
    "detects": {
      "@id": "sosa:detects",
      "@type": "@id"
    },
    "forProperty": {
      "@id": "sosa:forProperty",
      "@type": "@id"
    },
    "hasDeployment": {
      "@id": "sosa:hasDeployment",
      "@type": "@id"
    },
    "hasInput": {
      "@id": "sosa:hasInput",
      "@type": "@id"
    },
    "hasMember": {
      "@id": "sosa:hasMember",
      "@type": "@id",
      "@context": {
        "observedProperty": {
          "@id": "sosa:observedProperty",
          "@type": "@id"
        },
        "madeBySensor": {
          "@id": "sosa:madeBySensor",
          "@type": "@id"
        },
        "features": {
          "@id": "sosa:hasMember",
          "@type": "@id"
        },
        "hasResult": {
          "@id": "sosa:hasResult",
          "@type": "@id"
        }
      }
    },
    "hasOriginalSample": {
      "@id": "sosa:hasOriginalSample",
      "@type": "@id"
    },
    "hasOutput": {
      "@id": "sosa:hasOutput",
      "@type": "@id"
    },
    "hasProperty": {
      "@id": "sosa:hasProperty",
      "@type": "@id"
    },
    "hasResult": {
      "@id": "sosa:hasResult",
      "@type": "@id",
      "@context": {
        "pose": "csdm:surveyfeatures/pose",
        "distance": "csdm:surveyfeatures/distance"
      }
    },
    "hasResultQuality": {
      "@id": "sosa:hasResultQuality",
      "@type": "@id"
    },
    "hasSample": {
      "@id": "sosa:hasSample",
      "@type": "@id"
    },
    "hasSampledFeature": {
      "@id": "sosa:hasSampledFeature",
      "@type": "@id"
    },
    "hasSimpleResult": {
      "@id": "sosa:hasSimpleResult",
      "@type": "@id"
    },
    "hasSubSystem": {
      "@id": "sosa:hasSubSystem",
      "@type": "@id",
      "@container": "@set"
    },
    "hasUltimateFeatureOfInterest": {
      "@id": "sosa:hasUltimateFeatureOfInterest",
      "@type": "@id"
    },
    "hosts": {
      "@id": "sosa:hosts",
      "@type": "@id",
      "@container": "@set"
    },
    "implementedBy": {
      "@id": "sosa:implementedBy",
      "@type": "@id"
    },
    "implements": {
      "@id": "sosa:implements",
      "@type": "@id"
    },
    "inDeployment": {
      "@id": "sosa:inDeployment",
      "@type": "@id"
    },
    "isActedOnBy": {
      "@id": "sosa:isActedOnBy",
      "@type": "@id"
    },
    "isFeatureOfInterestOf": {
      "@id": "sosa:isFeatureOfInterestOf",
      "@type": "@id"
    },
    "isHostedBy": {
      "@id": "sosa:isHostedBy",
      "@type": "@id"
    },
    "isObservedBy": {
      "@id": "sosa:isObservedBy",
      "@type": "@id"
    },
    "isPropertyOf": {
      "@id": "sosa:isPropertyOf",
      "@type": "@id"
    },
    "isProxyFor": {
      "@id": "sosa:isProxyFor",
      "@type": "@id"
    },
    "isResultOf": {
      "@id": "sosa:isResultOf",
      "@type": "@id"
    },
    "isResultOfMadeBySampler": {
      "@id": "sosa:isResultOfMadeBySampler",
      "@type": "@id"
    },
    "isResultOfUsedProcedure": {
      "@id": "sosa:isResultOfUsedProcedure",
      "@type": "@id"
    },
    "isSampleOf": {
      "@id": "sosa:isSampleOf",
      "@type": "@id"
    },
    "madeActuation": {
      "@id": "sosa:madeActuation",
      "@type": "@id"
    },
    "madeByActuator": {
      "@id": "sosa:madeByActuator",
      "@type": "@id"
    },
    "madeBySampler": {
      "@id": "sosa:madeBySampler",
      "@type": "@id"
    },
    "madeObservation": {
      "@id": "sosa:madeObservation",
      "@type": "@id"
    },
    "madeSampling": {
      "@id": "sosa:madeSampling",
      "@type": "@id"
    },
    "observes": {
      "@id": "sosa:observes",
      "@type": "@id"
    },
    "wasOriginatedBy": {
      "@id": "sosa:wasOriginatedBy",
      "@type": "@id"
    },
    "Accuracy": {
      "@id": "ssn-system:Accuracy",
      "@type": "@id"
    },
    "ActuationRange": {
      "@id": "ssn-system:ActuationRange",
      "@type": "@id"
    },
    "BatteryLifetime": {
      "@id": "ssn-system:BatteryLifetime",
      "@type": "@id"
    },
    "DetectionLimit": {
      "@id": "ssn-system:DetectionLimit",
      "@type": "@id"
    },
    "Drift": {
      "@id": "ssn-system:Drift",
      "@type": "@id"
    },
    "Frequency": {
      "@id": "ssn-system:Frequency",
      "@type": "@id"
    },
    "Latency": {
      "@id": "ssn-system:Latency",
      "@type": "@id"
    },
    "MaintenanceSchedule": {
      "@id": "ssn-system:MaintenanceSchedule",
      "@type": "@id"
    },
    "MeasurementRange": {
      "@id": "ssn-system:MeasurementRange",
      "@type": "@id"
    },
    "OperatingPowerRange": {
      "@id": "ssn-system:OperatingPowerRange",
      "@type": "@id"
    },
    "OperatingProperty": {
      "@id": "ssn-system:OperatingProperty",
      "@type": "@id"
    },
    "OperatingRange": {
      "@id": "ssn-system:OperatingRange",
      "@type": "@id"
    },
    "Precision": {
      "@id": "ssn-system:Precision",
      "@type": "@id"
    },
    "Resolution": {
      "@id": "ssn-system:Resolution",
      "@type": "@id"
    },
    "ResponseTime": {
      "@id": "ssn-system:ResponseTime",
      "@type": "@id"
    },
    "Selectivity": {
      "@id": "ssn-system:Selectivity",
      "@type": "@id"
    },
    "Sensitivity": {
      "@id": "ssn-system:Sensitivity",
      "@type": "@id"
    },
    "SurvivalProperty": {
      "@id": "ssn-system:SurvivalProperty",
      "@type": "@id"
    },
    "SystemLifetime": {
      "@id": "ssn-system:SystemLifetime",
      "@type": "@id"
    },
    "SurvivalRange": {
      "@id": "ssn-system:SurvivalRange",
      "@type": "@id"
    },
    "SystemCapability": {
      "@id": "ssn-system:SystemCapability",
      "@type": "@id"
    },
    "SystemProperty": {
      "@id": "ssn-system:SystemProperty",
      "@type": "@id"
    },
    "hasOperatingProperty": {
      "@id": "ssn-system:hasOperatingProperty",
      "@type": "@id"
    },
    "hasOperatingRange": {
      "@id": "ssn-system:hasOperatingRange",
      "@type": "@id"
    },
    "hasSurvivalProperty": {
      "@id": "ssn-system:hasSurvivalProperty",
      "@type": "@id"
    },
    "hasSystemCapability": {
      "@id": "ssn-system:hasSystemCapability",
      "@type": "@id"
    },
    "hasSystemProperty": {
      "@id": "ssn-system:hasSystemProperty",
      "@type": "@id"
    },
    "hasSurvivalRange": {
      "@id": "ssn-system:hasSurvivalRange",
      "@type": "@id"
    },
    "inCondition": {
      "@id": "ssn-system:inCondition",
      "@type": "@id"
    },
    "qualityOfObservation": {
      "@id": "ssn-system:qualityOfObservation",
      "@type": "@id"
    },
    "angleAccuracy": "csdm:surveyobs/angleAccuracyMeasure",
    "distanceAccuracy": "csdm:surveyobs/distanceAccuracyMeasure",
    "distanceAccuracyClass": {
      "@type": "@id",
      "@id": "csdm:surveyobs/distanceAccuracyClass"
    },
    "angleAccuracyClass": {
      "@type": "@id",
      "@id": "csdm:surveyobs/angleAccuracyClass"
    },
    "angleType": {
      "@context": {
        "@base": "https://linked.data.gov.au/def/csdm/defs/angletypes/"
      },
      "@type": "@id",
      "@id": "csdm:surveyobs/angleType"
    },
    "distanceType": {
      "@context": {
        "@base": "https://linked.data.gov.au/def/csdm/defs/distancetypes/"
      },
      "@type": "@id",
      "@id": "csdm:surveyobs/distanceType"
    },
    "geojson": "https://purl.org/geojson/vocab#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "oa": "http://www.w3.org/ns/oa#",
    "dct": "http://purl.org/dc/terms/",
    "sosa": "http://www.w3.org/ns/sosa/",
    "ssn-system": "ssn:systems/",
    "ssn": "http://www.w3.org/ns/ssn/",
    "csdm": "https://linked.data.gov.au/def/csdm/",
    "surv": "csdm:surveyfeatures/",
    "geopose": "csdm:utils/geopose/",
    "angletype": "csdm:defs/angletypes/",
    "distancetype": "csdm:defs/distancetypes/",
    "surveyproc": "csdm:defs/surveyprocedures/",
    "surveyable": "csdm:defs/surveyableproperties/",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Ficsm-au%2F3d-csdm-common%2Fmain%2Fbuild%2Fannotated%2Fcsdm%2Ffeatures%2FSurveyObservations%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld" target="_blank">https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/build/annotated/csdm/features/SurveyObservations/context.jsonld</a>

# Validation

## SHACL Shapes

The following sets of SHACL shapes are used for validating this building block:

* Survey Observations <small><code>icsm.csdm.features.SurveyObservations</code></small>
  * [https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/_sources/csdm/features/SurveyObservations/rules.shacl](https://raw.githubusercontent.com/icsm-au/3d-csdm-common/main/_sources/csdm/features/SurveyObservations/rules.shacl)
* Observation Properties <small><code>ogc.sosa.properties.observation</code></small>
  * [https://opengeospatial.github.io/ogcapi-sosa/_sources/properties/observation/rules.shacl](https://opengeospatial.github.io/ogcapi-sosa/_sources/properties/observation/rules.shacl)

# References

* [3D Cadastre Survey Data Model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/icsm-au/3d-csdm-common" target="_blank">https://github.com/icsm-au/3d-csdm-common</a>
* Path:
<code><a href="https://github.com/icsm-au/3d-csdm-common/blob/HEAD/_sources/csdm/features/SurveyObservations" target="_blank">_sources/csdm/features/SurveyObservations</a></code>

