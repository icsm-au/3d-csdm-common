# CSDM Data Exchange Specification Testing Recommendations

<!--
:Author:    Rob Atkinson
:Email:     <rob.atkinson@surroundaustralia.com>
:Date:      12 December 2023
:Updated:   
:Revision:  0.1

:History: 
:Ver 0.1: Initial draft of document

-->

This document supplements the [technical details of the testing mechanism](https://github.com/opengeospatial/bblock-template/blob/master/USAGE.md#validation-and-tests) developed in conjunction with the OGC research team.

It provides a high-level overview of the "modular testing" environment and a recommended testing process.

The complete specification is quite complex, given the extensive requirements for metadata for each component. 

The nature of JSON schema is that validation process may try to match many possible options, and reporting of non-compliance is often tricky to interpret.

See also [suggestions for testing tools] provided (https://github.com/opengeospatial/bblock-template/blob/master/TESTING.md#tools)

## Profile testing (integration testing)

Below are described lower-level testing procedures required for refinement and update of the CSDM model and schema.

Practically, however, the implementation is always via a specific profile defining content rules for a jurisdiction.

Profiles are just "modules" in the technical design - and can be reused to create even more specialised profiles for particular applications. For example, a set of constraints may be applied to supporting documentation and occupation features for transport corridors or similar application.

Testing is performed locally on a *working copy* of the [CSDM Profiles Repository](https://github.com/icsm-au/3d-csdm-profiles) using the [process defined in OGC Building Blocks]((https://github.com/opengeospatial/bblock-template/blob/master/USAGE.md#validation-and-tests) )

This is done using docker as per the [Building Blocks documentation](https://github.com/opengeospatial/bblock-template/blob/master/USAGE.md#output-testing):

```
docker run --pull=always --rm --workdir /workspace -v $(pwd):/workspace \
  ghcr.io/opengeospatial/bblocks-postprocess  --clean true
```
It is **recommended** that profiles are developed using separate tests for each component of a CSD before collating a complete survey example. 


## Modules (unit testing)

The CSDM Encoding Specification is a modular design, referencing reusable sub-components.

Each module (or "Building Block") has its own integrated testing and examples.

Testing of content often requires contextual information that can be separated out from examples - for example a line can reference a set of points defined in an extra file.

The set of additional files to support deeper testing is called the "content closure", and is defined in each module's ```bblock.json``` configuration file. 

**Reusing a module inherits all its tests automatically - but not the "content closure"**


## Testing the tests

The provision of examples under a modules's ```tests/``` directory can include tests with a ```-fail.json``` suffix.

These tests should test specific rules, to ensure they are correctly applied and catch failures. 

These are not necessary, and can be added to any component, but provide confidence in the development of tests.

Such tests have been developed for key patterns such as topological integrity. 

## "Container" testing

The most complex part of the testing process is meeting the minimal requirements for mandatory metadata for a survey description - the "container" object named "CSD".

It is highly recommended that tests are undertaken by using a simple skeleton and adding the components specifically related to the test case.

## Regression testing

Regression testing is automated for a given module through the use of "github actions".

However, if an "upstream" module (or "dependency") is modified, then testing of downstream modules needs to be triggered.

At the moment this is a manual process, however it could be configured to periodically check for updates.

The OGC Building Block toolkit is expected to undergo continuous improvements, and it is recommended that regular regression testing be performed.

(Note that a fork or clone of the repository can be used to perform regression testing, and changes reviewed before updating the main repository).





