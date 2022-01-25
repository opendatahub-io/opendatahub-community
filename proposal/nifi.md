---
title: Apache NiFi
---

[Apache Nifi](https://nifi.apache.org/) supports powerful and scalable directed graphs of data routing, transformation, and system mediation logic. It is an integrated data logistics platform for automating the movement of data between disparate systems. It provides real-time control that makes it easy to manage the movement of data between any source and any destination.

## Architecture

[NiFi Architecture and Overview](https://nifi.apache.org/docs/nifi-docs/html/overview.html#nifi-architecture)

## User Use Cases

Data practitioners who wants to implement automated ETL or other type of data gathering or processing workflows on top of OpenShift. Examples:

* Data gathering and aggreation from sensors in a factory, with MiniFi instances running on sensor devices and sending data to Nifi for consolidation and processing.
* Data extraction from a MongoDB transactional database to a MSSQL analytics database.
* Edge-to-Cloud data streaming pipelines.
* ...

## Implementation

NiFi is a stateful application that can be deployed as a StatefulSet in OpenShift. Such implementation is already available [here](https://github.com/guimou/odh-manifests/tree/master/nifi). This immplementation is already created as a set of kustomizations with overlays to propose different options (node number, authentication). As it's already formatted in a KfDef way, it can be deployed by the operator as-is.

## Authentication

Previously described implementation offers three mechanisms:

* Single User authentication, default configuration: one admin user is created from the configuration parameters in the manifest.
* OIDC Authentication, implemented as an overlay: connection to an OIDC provider through parameters in the KfDef. One user is designed as the initial admin (others through the configuration in NiFi UI).
* LDAP Authentication, implemented as an overlay: connection to LDAP through parameters in the KfDef. One user is designed as the initial admin (others through the configuration in NiFi UI).

No automated group memberships is implemented, although it can be done by modifying the configuration ConfigMap.

Authentication with OpenShift is not available as OpenShift only provides an Oauth 2.0 mechanism (no OIDC). Oauth proxy technique is not recommended as it would imply running NiFi unsecured. NiFi is an heavily secured application. It's either fully opened for testing purposes, or secured. In secure mode there is mutual certificate-based authentication between the different components, preventing the poor-man OAuth proxy authentication to be implemented.

## Integration with ODH

NiFi is a fully self-sustained UI-based application. So the only needed integration would be a tile on the dashboard to point the user to the interface.

## More info

NiFi is a components that data people are used to work with, as it has been part of HortonWorks and Cloudera for a long time. A fully UI-based, configuration-based tool could be a great addition for people wanting to create advanced workflows, including usage of hundreds of out of the box processors/connectors, without coding everything in Python. NiFi is also the engine that will run those workflows with real-time control, guaranteed delivery and high-availability.
