---
title: ModelMesh Serving
---

[ModelMesh Serving](https://github.com/kserve/modelmesh-serving) is the Controller for managing ModelMesh, a general-purpose model serving management/routing layer.

## Architecture
[ModelMesh Serving Architecture and Overview](https://github.com/kserve/modelmesh-serving/blob/main/README.md)

## User Use Cases
Data science users who would like a flexible, lightweight way to serve up 1->N models in their OpenShift environment.

## Implementation
There is a deployment created for modelmesh-controller, which is an operator that watches for the 2 CRDs included in the project.

1.  servingruntimes.serving.kserve.io - ModelMesh supports multiple different serving runtimes that can be defined in a custom resource.  By default, it includes support for the [triton-inference-server](https://github.com/triton-inference-server/server) as well as [seldon-mlserver](https://github.com/SeldonIO/MLServer)
1.  predictors.serving.kserve.io - A predictor custom resource defines the storage for a model to be served, credentials required to access that stored modek, and the type of the model to be served.  By default, a predictor can be interacted with via gRPC (natively) or via HTTP (via a built-in proxy).

## More info

While ModelMesh is part of the lager Kserve project, it can be installed standalone as I propose here.  The lightweight standalone installation does not require Knative/Istio/ServiceMesh, which may be an attractive option for some OpenShift installations.
