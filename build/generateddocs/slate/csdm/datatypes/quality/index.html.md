---
title: SurveyQuality (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>SurveyQuality</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: SurveyQuality (Schema)
---


# SurveyQuality `icsm.csdm.datatypes.quality`

A extensible quality descriptor object with standard properties for survey point and vector observations.

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/icsm-au/3d-csdm-common/blob/main/build/tests/csdm/datatypes/quality/" target="_blank">valid</a></strong>
</aside>

# Examples

## Example Quality Object



```json
{
  "distanceAccuracy": 0.000100138048,
  "angleAccuracy": 0.028154691543,
  "distanceAccuracyClass": "http://any.valid/",
  "angleAccuracyClass": "http://any.valid/"
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-common/build/tests/csdm/datatypes/quality/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-common%2Fbuild%2Ftests%2Fcsdm%2Fdatatypes%2Fquality%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "distanceAccuracy": 0.000100138048,
  "angleAccuracy": 0.028154691543,
  "distanceAccuracyClass": "http://any.valid/",
  "angleAccuracyClass": "http://any.valid/",
  "@context": "https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-common/build/tests/csdm/datatypes/quality/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-common%2Fbuild%2Ftests%2Fcsdm%2Fdatatypes%2Fquality%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix ns1: <https://linked.data.gov.au/def/csdm/surveyobs/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] ns1:angleAccuracyClass <http://any.valid/> ;
    ns1:angleAccuracyMeasure 2.815469e-02 ;
    ns1:distanceAccuracyClass <http://any.valid/> ;
    ns1:distanceAccuracyMeasure 1.00138e-04 .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-common/build/tests/csdm/datatypes/quality/example_1_1.ttl">Open in new window</a>
</blockquote>


Example quality object.
 
Schema checking is limited to datatypes of present properties as all are optional.


# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
description: Survey Vector Observation Quality
properties:
  angleAccuracy:
    type: number
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyobs/angleAccuracyMeasure
  distanceAccuracy:
    type: number
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyobs/distanceAccuracyMeasure
  distanceAccuracyClass:
    type: string
    x-jsonld-type: '@id'
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyobs/distanceAccuracyClass
  angleAccuracyClass:
    type: string
    x-jsonld-type: '@id'
    x-jsonld-id: https://linked.data.gov.au/def/csdm/surveyobs/angleAccuracyClass
x-jsonld-prefixes:
  csdm: https://linked.data.gov.au/def/csdm/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-common%2Fbuild%2Fannotated%2Fcsdm%2Fdatatypes%2Fquality%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/schema.yaml" target="_blank">https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/schema.yaml</a>
* JSON version: <a href="https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/schema.json" target="_blank">https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
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
    "csdm": "https://linked.data.gov.au/def/csdm/",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-common%2Fbuild%2Fannotated%2Fcsdm%2Fdatatypes%2Fquality%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/context.jsonld" target="_blank">https://icsm-au.github.io/3d-csdm-common/build/annotated/csdm/datatypes/quality/context.jsonld</a>

# References

* [CSDM model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/icsm-au/3d-csdm-common" target="_blank">https://github.com/icsm-au/3d-csdm-common</a>
* Path:
<code><a href="https://github.com/icsm-au/3d-csdm-common/blob/HEAD/_sources/csdm/datatypes/quality" target="_blank">_sources/csdm/datatypes/quality</a></code>

