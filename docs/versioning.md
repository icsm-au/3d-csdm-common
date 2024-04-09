# Versioning Considerations

<!--
:Author:    Rob Atkinson
:Email:     <rob.atkinson@surroundaustralia.com>
:Date:      12 December 2023
:Updated:   
:Revision:  0.1

:History: 
:Ver 0.1: Initial draft of document

-->

Development of a versioning and maintenance approach is strongly recommended as further testing and refinements are undertaken.

The underlying **git** publication methodology supports several options, depending on sophistication of users.

At a basic level, [testing](testing.md) can be done on a local *working copy* cloned from the online repository.

Use of [Git pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests) using "forks" is recommended to propagate changes.

Defining a versioning nomenclature should take into account ICSM practices, and if no guidance is relevant then a versioning policy for models and encoding schema should be defined and documented.

At this stage *no* specific versioning practices have been instituted, however on final delivery a git tag shall be applied to the state of each delivered repository.

Further work is required to define versioning strategies for cascading updates from upstream dependencies. The OGC Building Blocks environment will be extended to provide automated support for this at some point.