# Charter

This charter adheres to the conventions described in the [Open Data Hub Charter Guide](../sig-charter-guide.md) and uses the Roles and Organization Management outlined in [sig-goverance](../sig-governance.md).

## Scope

To create services for deploying and managing machine learning models and pipelines in OpenShift and across the hybrid cloud. Our users are defined as data scientists who are interested in incorporating ML Ops capabilities into their workflows.

### In scope

* Services and APIs for data scientists using pipelines to iterate over experimentation on models
* Services and APIs for data scientists deploying models to serving environment, potentially using pipelines
* Define and advocate for the ML Ops focused data scientist persona within the larger ODH community
* Ensure any platform and backend changes directly benefit the user
* Offer ease of use solutions through ODH website/tutorials
* Assist the ML Developer Experience SIG in developing ML Ops centric ODH Dashboard extensions

### Code, Images, Design, and Services Covered

* ODH Model Serving Operator
* Kubeflow Pipelines
* Model Mesh Serving
* Tutorials

### Out of scope

UXD for usage of ML Ops capabilities

### Roles and Organization Management

This SIG adheres to the Roles and Organization Management outlined in [sig-governance](../sig-governance.md).

## SIG Working Groups

**Working Groups**:

* **Pipelines** (#[wg-pipelines](https://odh-io.slack.com/archives/C03DY3YT151))
  * Members:
    * Project Lead: TBD
    * Team: TBD
  * Requirements for feature - <insert link>
    * Feature complete in ODH by September 2022
    * Complete Arch review doc by TBD
    * Review Arch doc with services and prodsec teams by TBD
    * Set regular meeting schedule for WG coordination (to be scheduled)
* **Model Serving** (#[wg-model-serving slack channel](https://odh-io.slack.com/archives/C035J0KA6UB))
  * Members:
    * Project Lead: Chad Roberts
    * Team: TBD
  * Requirements for feature <insert link>
    * Feature complete in ODH by end of August 2022
    * Review Arch doc with services and prodsec teams by TBD
    * Set regular meeting schedule for WG coordination (to be scheduled)
