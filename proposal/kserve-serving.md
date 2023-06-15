---
title: KServe Model Serving Runtime
---

[KServe Model Serving Runtime](https://github.com/kserve/kserve) contains the controller to serve machine learning (ML) models on arbitrary frameworks. It aims to solve production model serving use cases by providing performant, high abstraction interfaces for common ML frameworks like Tensorflow, XGBoost, ScikitLearn, PyTorch, and ONNX.

[WIP] ModelMesh relationship


## Architecture
[KServe Control Plane Architecture](https://github.com/kserve/website/blob/main/docs/modelserving/control_plane.md)

[KServe Data Plane Architecture](https://github.com/kserve/website/blob/main/docs/modelserving/data_plane/data_plane.md)

## User Use Cases
[WIP] Data science users who would like a flexible, lightweight way to serve up 1->N models in their OpenShift environment.

## Implementation
[WIP]

## More info

KServe has two different installation configurations: Serverless and Raw Kubernetes Deployment.

Serverless requires Knative (OpenShift Serverless) and Istio (OpenShift Service Mesh), it is the default option and the option that offers all the KServe features, so it is the suggestion option for ODH users too.

This implies that Knative (OpenShift Serverless) and Istio (OpenShift Service Mesh) are going to be mandatory dependencies to install in the cluster to run the full KServe stack.