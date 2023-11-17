# Welcome to NebulaGraph {{ nebula.release }} Documentation

!!! note

    This manual is revised on {{ now().year }}-{{ now().month }}-{{ now().day }}.

NebulaGraph is a distributed and scalable graph database. It is the optimal solution in the world capable of hosting graphs with dozens of billions of vertices (nodes) and trillions of edges (relationships) with millisecond latency.

## Getting started

* [Quick start](2.quick-start/1.quick-start-workflow.md)
* [Preparations before deployment](4.deployment-and-installation/1.resource-preparations.md)
* [nGQL cheatsheet](2.quick-start/6.cheatsheet-for-ngql.md)
* [FAQ](20.appendix/0.FAQ.md)
* [Ecosystem Tools](20.appendix/6.eco-tool-version.md)
  
## Release notes

- [NebulaGraph {{nebula.release}}](20.appendix/release-notes/nebula-ent-release-note.md)
- [{{dashboard_ent.name}}](20.appendix/release-notes/dashboard-ent-release-note.md)
- [{{explorer.name}}](20.appendix/release-notes/explorer-release-note.md)
- [NebulaGraph Exchange](20.appendix/release-notes/exchange-ent-release-note.md)

## Other Sources

- [NebulaGraph Homepage](https://nebula-graph.io/)

## Symbols used in this manual

<!-- 
This manual has over 40 cautions.
This manual has over 30 dangers.
This manual has over 80 compatibilities and corresponding tips.
-->

!!! note

    Additional information or operation-related notes.

!!! caution

    May have adverse effects, such as causing performance degradation or triggering known minor problems.

!!! warning

    May lead to serious issues, such as data loss or system crash.

!!! danger

    May lead to extremely serious issues, such as system damage or information leakage.

!!! compatibility

    The compatibility notes between nGQL and openCypher, or between the current version of nGQL and its prior ones. 