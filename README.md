# 3D Cadastral Survey Data Model (Common Model) - JSON Encoding

The 3D CSDM and its sub-components are described [here](https://icsm-au.github.io/3d-csdm-schema/)

This repository defines an implementation of the 3D Cadastral Survey Data Model (3DCSDM) as a JSON encoding using the [OGC Building Blocks](https://github.com/opengeospatial/bblock-template) methdology.

The defined data exchange schema is **semantically annotated** with explicit links to the underlying conceptual and logical models repo: [https://icsm-au.github.io/3d-csdm/](https://github.com/icsm-au/3d-csdm).

The semantic annotation in turn provides the opportunity to declare explicit **profiles** of the specification for each implementing jurisdiction.

Profiles are defined in a separate repository [3d-csdm-profiles](https://github.com/icsm-au/3d-csdm-profiles), leaving this specification free of jurisdiction-specific artefacts and potentially relevant for use in any jurisdiction.

**Although extension and restrictions are possible, at this stage no variations in the 3D CSDM schema have been required to define profiles for the test jurisdictions.**

Given that implementation of profiles is the application procedure for this model, it is recommended to start with the [Reviewers Guide](https://github.com/icsm-au/3d-csdm-profiles/blob/main/REVIEW_GUIDE.md) provided for jurisdictional review processes.

A number of considerations for future maintenance, testing and extensions are provided in the form of a [RoadMap](docs/ROAD_MAP.md).

## Specification components

This specification is primarily machine-readable in the form of an **annotated JSON schema** supported by examples.

The **annotation** is in the form of embedded Web links in schema elements, and a corresponding [JSON-LD](https://json-ld.org/) context that reflects the schema structure.

**Logical constraints** are defined using SHACL, operating on the JSON-LD outputs (a form of RDF)

For many however it is expected that the JSON examples provided along with the JSON-schema will be sufficient to implement this specification, and the JSON-LD and SHACL rules just provide a testing option.

Application of the specification however will require additional rules about content - a series of controlled vocabularies. This content cannot be checked using JSON schema alone, but exploits the JSON-LD and SHACL rules defined. See [Testing](docs/testing.md)

It is **not necessary** to consume these specifications using the machine-readable forms however it may be necessary to look-up the links in the corresponding [CSDM Conceptual Model](https://icsm-au/3d-csdm/) to understand the semantics of specific elements.

The various components of the specification can be accessed per-module from the [generated documents](#docs).

_(NB improved documentation with embedded links per schema element may be available when supported by available tools)_

The encoding model uses the industry standard GeoJSON model, with the extensions supported by the OGC to provide for richer and more precise options:

- [FG-JSON](https://github.com/opengeospatial/ogc-feat-geo-json) : "Feature-Geometry" supporting extensible geometry types, feature typing and feature relationships.
- [JSON-LD](https://json-ld.org/) : "Linked Data" - semantic annotation supporting links to the underlying data model - which in turn allows for richer validation - especially of implementation profiles that constrain allowable data values
- [OGC Building Blocks](https://opengeospatial.github.io/bblocks/register.html) : The underlying common elements that support OGC standards and best practices. (See extensive details below)

This structure allows for:

- OGC API Features compatible schema ("ready to use") 
- reuse of building blocks for parts of the model (modules) defined by existing standards
- use of standardised tools to validate and compose a complete encoding from component building blocks
- use of standardised tools for documentation
- reuse of the component parts of the CSDM as building blocks for use in related applications
- reuse of the entire CSDM model as a building block in related applications 

<a id="doc"/>

## Further documentation

The OGC register of Building Blocks is [here](https://opengeospatial.github.io/bblocks/register.html)

This is a "permissive" schema suitable for international contexts, with ICSM common and specific jurisdictional profiles described with machine-readable constraints in a separate repository [https://github.com/icsm-au/3d-csdm-profiles](https://github.com/icsm-au/3d-csdm-profiles)

By "permissive" it means that:

* many properties are defined as simple strings, whereas implementing jurisdictions will typically want to impose constraints on such strings, such as use of controlled vocabularies, Web URIs or specific patterns.
* additional properties may be added to any schema element if required
* where appropriate properties may be single or multi-valued, by reference or nested objects

## Parsing and validation

The repository provides a 4-layer approach to parsing and validation of examples that can be extended to provide validation facilities for implementation activities:

- JSON syntax (well-formed)
- JSON schema (contains required elements)
- SHACL rules (has right content and combinations of optional elements)
- Custom parser ["PanCadastre"](https://github.com/openwork-nz/pancadastre) that derives full geometry representations from the topology and survey results (and other more sophisticated views)

Validations are performed automatically on each example (for both the full CSD schema and component modules) and thge validation results and all intermediate forms the example has been parsed and serialised into are published per module - e.g. [](https://icsm-au.github.io/3d-csdm-schema/build/tests/csdm/features/CSD/)

For more information about the parser/serialiser capabilities see the [PanCadastre tool repository](https://github.com/openwork-nz/pancadastre)

# Building Blocks - Technical Information

This repository uses the template from 
[OGC Building Blocks](https://opengeospatial.github.io/bblocks) to create a set of "building blocks" that can be used to create APIs and more complex application schemas.

Building Blocks encapsulate common patterns that software can provide specific implementations for, allow identification of interoperability based on these patterns and simplify the process of creating schemas by provide solutions to the tricky task of making the schemas match the intent of underlying specifications.


## General Building block repository structure


The `build/` directory contains the **_reusable assets_** for implementing this building block, in full or part, and the rest of the repository contain *sources* to build these assets.  *Sources* minimise redundant information and preserve original forms of inputs, such as externally published schemas etc.  This allow these to be updated safely, and also allows for alternative forms of original source material to be used whilst preserving uniformity of the reusable assets.

Note that the these components will be consistently structured for a given type of building block, and the editable components may vary according to the source material used to derive the building block, and therefore cannot be directly referenced.

### Editable components

- `features/`: schemas for the feature types defined by this bb (which is a "super-bb" containing at least oneOf these defined features)
- `datatypes/`: reusable schemas for (potentially complex) datatypes defined by this bb
- `aspects/`: groups of properties that may be included in feature types (equivalent to attribute groups in XML schema)
- `assets/`: Documentation assets (e.g. images) directory. See [Assets](#assets) below.

[More information on this template design and usage](https://github.com/opengeospatial/bblock-template/blob/master/USAGE.md)
