---
title: Compound Name (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>Compound Name</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: Compound Name (Schema)
---


# Compound Name `icsm.csdm.datatypes.compoundName`

A multiple part name, consisting of a set of strings with functional roles that can be combined into single string using a template.

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/icsm-au/3d-csdm-schema/blob/main/build/tests/csdm/datatypes/compoundName/" target="_blank">valid</a></strong>
</aside>

# Examples

## Example CompoundName



```json
{
    "id": "CompoundNameExample",
    "type": "CompoundName",
    "label": "IS II - DP 3333",
    "comment": "note: label may be absent or subject to rules regarding presence of parts",
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
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/datatypes/compoundName/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Ftests%2Fcsdm%2Fdatatypes%2FcompoundName%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "id": "CompoundNameExample",
  "type": "CompoundName",
  "label": "IS II - DP 3333",
  "comment": "note: label may be absent or subject to rules regarding presence of parts",
  "hasPart": [
    {
      "type": "Source",
      "label": "DP 3333"
    },
    {
      "type": "Stamp",
      "label": "IS II"
    }
  ],
  "@context": "https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/datatypes/compoundName/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Ftests%2Fcsdm%2Fdatatypes%2FcompoundName%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix commonpatterns: <https://linked.data.gov.au/def/csdm/commonpatterns/> .
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

[] rdfs:label "IS II - DP 3333" ;
    dcterms:hasPart [ rdfs:label "DP 3333" ;
            commonpatterns:namePartType "Source" ],
        [ rdfs:label "IS II" ;
            commonpatterns:namePartType "Stamp" ] .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/datatypes/compoundName/example_1_1.ttl">Open in new window</a>
</blockquote>


A name with a label, but also a set of parts with roles that can be validated against content rules.


# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
description: Compound Name
properties:
  label:
    anyOf:
    - type: 'null'
    - type: string
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  template:
    type: string
  hasPart:
    type: array
    items:
      type: object
      properties:
        label:
          type: string
          x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
        type:
          type: string
          x-jsonld-id: https://linked.data.gov.au/def/csdm/commonpatterns/namePartType
      required:
      - label
    x-jsonld-id: http://purl.org/dc/terms/hasPart
x-jsonld-extra-terms:
  name: https://linked.data.gov.au/def/csdm/commonpatterns/name
  CompoundName: https://linked.data.gov.au/def/csdm/commonpatterns/CompoundName
x-jsonld-prefixes:
  dct: http://purl.org/dc/terms/
  commonpatterns: https://linked.data.gov.au/def/csdm/commonpatterns/
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  csdm: https://linked.data.gov.au/def/csdm/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Fannotated%2Fcsdm%2Fdatatypes%2FcompoundName%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/schema.yaml" target="_blank">https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/schema.yaml</a>
* JSON version: <a href="https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/schema.json" target="_blank">https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
    "label": "rdfs:label",
    "hasPart": {
      "@context": {
        "type": "commonpatterns:namePartType"
      },
      "@id": "dct:hasPart"
    },
    "name": "commonpatterns:name",
    "CompoundName": "commonpatterns:CompoundName",
    "dct": "http://purl.org/dc/terms/",
    "commonpatterns": "csdm:commonpatterns/",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "csdm": "https://linked.data.gov.au/def/csdm/",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Fannotated%2Fcsdm%2Fdatatypes%2FcompoundName%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/context.jsonld" target="_blank">https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/compoundName/context.jsonld</a>

# Validation

## SHACL Shapes

The following sets of SHACL shapes are used for validating this building block:

* Compound Name <small><code>icsm.csdm.datatypes.compoundName</code></small>
  * [https://icsm-au.github.io/3d-csdm-schema/_sources/csdm/datatypes/compoundName/rules.shacl](https://icsm-au.github.io/3d-csdm-schema/_sources/csdm/datatypes/compoundName/rules.shacl)

# References

* [CSDM model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/icsm-au/3d-csdm-schema" target="_blank">https://github.com/icsm-au/3d-csdm-schema</a>
* Path:
<code><a href="https://github.com/icsm-au/3d-csdm-schema/blob/HEAD/_sources/csdm/datatypes/compoundName" target="_blank">_sources/csdm/datatypes/compoundName</a></code>

