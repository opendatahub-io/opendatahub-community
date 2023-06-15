---
title: KServe Model Serving Runtime
---

[KServe Model Serving Runtime](https://github.com/kserve/kserve) contains the controller to serve machine learning (ML) models on arbitrary frameworks. It aims to solve production model serving use cases by providing performant, high abstraction interfaces for common ML frameworks like Tensorflow, XGBoost, ScikitLearn, PyTorch, and ONNX.

[WIP] ModelMesh relationship


## Architecture
[KServe Control Plane Architecture](https://github.com/kserve/website/blob/main/docs/modelserving/control_plane.md)

[KServe Data Plane Architecture](https://github.com/kserve/website/blob/main/docs/modelserving/data_plane/data_plane.md)

## User Use Cases
Data science users who would like a flexible, lightweight way to serve up 1->N models in their OpenShift environment.

## Implementation
[WIP]

## More info

KServe has two different installation configurationsWhile ModelMesh is part of the lager Kserve project, it can be installed standalone as I propose here.  The lightweight standalone installation does not require Knative/Istio/ServiceMesh, which may be an attractive option for some OpenShift installations.
