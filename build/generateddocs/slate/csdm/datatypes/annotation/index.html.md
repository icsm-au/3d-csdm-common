---
title: Generalised annotation (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>Generalised annotation</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: Generalised annotation (Schema)
---


# Generalised annotation `icsm.csdm.datatypes.annotation`

An annotation allowing multiple values, either links with descriptions or simple text.

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/icsm-au/3d-csdm-schema/blob/main/build/tests/csdm/datatypes/annotation/" target="_blank">valid</a></strong>
</aside>

# Examples

## Example CompoundName



```json
[
  {
    "description": "Annotation with link and role",
    "href": "http://example.org/aDocument",
    "role": "http://example.org/myReason",
    "rel": "related"
  },
  {
    "description": "Annotation with role",
    "role": "http://example.org/myReason"
  },
  "Plain text annotation"
]

```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/datatypes/annotation/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Ftests%2Fcsdm%2Fdatatypes%2Fannotation%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "@context": "https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/context.jsonld",
  "@graph": [
    {
      "description": "Annotation with link and role",
      "href": "http://example.org/aDocument",
      "role": "http://example.org/myReason",
      "rel": "related"
    },
    {
      "description": "Annotation with role",
      "role": "http://example.org/myReason"
    },
    "Plain text annotation"
  ]
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/datatypes/annotation/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Ftests%2Fcsdm%2Fdatatypes%2Fannotation%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ns1: <http://www.iana.org/assignments/> .
@prefix oa: <http://www.w3.org/ns/oa#> .
@prefix prof: <http://www.w3.org/ns/dx/prof/> .

[] dcterms:description "Annotation with link and role" ;
    ns1:relation <http://www.iana.org/assignments/relation/related> ;
    prof:hasRole <http://example.org/myReason> ;
    oa:hasTarget <http://example.org/aDocument> .

[] dcterms:description "Annotation with role" ;
    prof:hasRole <http://example.org/myReason> .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/datatypes/annotation/example_1_1.ttl">Open in new window</a>
</blockquote>


A name with a label, but also a set of parts with roles that can be validated against content rules.


# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
$defs:
  linkWithRole:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/geo/json-fg/link-role/schema.yaml
  codeRef:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
  Options:
    anyOf:
    - $ref: '#/$defs/linkWithRole'
    - properties:
        role:
          $ref: '#/$defs/codeRef'
        description:
          type: string
          x-jsonld-id: http://purl.org/dc/terms/description
      required:
      - description
    - type: string
  AnnotationSet:
    anyOf:
    - $ref: '#/$defs/Options'
    - type: 'null'
    - type: array
      items:
        $ref: '#/$defs/Options'
allOf:
- $ref: '#/$defs/AnnotationSet'
x-jsonld-prefixes:
  dct: http://purl.org/dc/terms/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Fannotated%2Fcsdm%2Fdatatypes%2Fannotation%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/schema.yaml" target="_blank">https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/schema.yaml</a>
* JSON version: <a href="https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/schema.json" target="_blank">https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/schema.json</a>


# JSON-LD Context

```json--ldContext
{
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
    "length": "dct:extent",
    "role": {
      "@id": "prof:hasRole",
      "@type": "@id"
    },
    "conformsTo": {
      "@id": "dct:conformsTo",
      "@type": "@id"
    },
    "description": "dct:description",
    "oa": "http://www.w3.org/ns/oa#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "dct": "http://purl.org/dc/terms/",
    "prof": "http://www.w3.org/ns/dx/prof/",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Ficsm-au.github.io%2F3d-csdm-schema%2Fbuild%2Fannotated%2Fcsdm%2Fdatatypes%2Fannotation%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/context.jsonld" target="_blank">https://icsm-au.github.io/3d-csdm-schema/build/annotated/csdm/datatypes/annotation/context.jsonld</a>

# References

* [CSDM model](https://github.com/icsm-au/3d-csdm)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/icsm-au/3d-csdm-schema" target="_blank">https://github.com/icsm-au/3d-csdm-schema</a>
* Path:
<code><a href="https://github.com/icsm-au/3d-csdm-schema/blob/HEAD/_sources/csdm/datatypes/annotation" target="_blank">_sources/csdm/datatypes/annotation</a></code>

