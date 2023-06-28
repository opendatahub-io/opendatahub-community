---
title: KServe Model Serving Runtime
---

[KServe Model Serving Runtime](https://github.com/kserve/kserve) contains the controller to serve machine learning (ML) models on arbitrary frameworks. It aims to solve production model serving use cases by providing performant, high abstraction interfaces for common ML frameworks like Tensorflow, XGBoost, ScikitLearn, PyTorch, and ONNX.

It is designed as single model deployment logic so each model is served and scaled independently.  

ModelMesh is already a serving component part of KServe community and adopts the same Kubernetes CRD. It is included in the stack, but it is designed with the goal of high-scale, high-density and frequently-changing model use cases.

KServe Model Serving Runtime and ModelMesh play well together to cover all the possible use cases for ML serving. If you want to know more about ModelMesh, have a look to [ModelMesh serving document](modelmesh-serving.md)

## Architecture
[KServe Control Plane Architecture](https://github.com/kserve/website/blob/main/docs/modelserving/control_plane.md)

[KServe Data Plane Architecture](https://github.com/kserve/website/blob/main/docs/modelserving/data_plane/data_plane.md)

## User Use Cases
Data science users who would like a flexible, lightweight way to serve up 1->N models in their OpenShift environment.

## Implementation
There is a deployment created for kserve-controller, which is an operator that watches for multiple CRDs included in the project.

1. servingruntimes.serving.kserve.io - KServe supports multiple different serving runtimes that can be defined in a custom resource. 
2. inferenceservice.serving.kserve.io - An InferenceService custom resource defines the storage for a model to be served, credentials required to access that stored model, and the type of the model to be served.  By default, an inference service can be interacted with via gRPC (natively) or via HTTP (via a built-in proxy).
3. inferencegraphs.serving.kserve.io - An InferenceGraph custom resource defines a mechanism to compose different ML models (ensemble) to make a single more complex prediction.
4. clusterservingruntimes.serving.kserve.io - similar to servingruntimes custom resource but with the possibility to enable a specific serving runtime for the whole cluster. It is usually installed in `kserve` namespace following the getting started guides but it is not the approach that we suggest: in OpenShift namespace isolation is a good practice to enable different multi-tenant configuration so a namespace local serving runtime enables similar use cases.


## More info

KServe has two different installation configurations: Serverless and Raw Kubernetes Deployment.

Serverless requires Knative (OpenShift Serverless) and Istio (OpenShift Service Mesh), it is the default option and the option that offers all the KServe features, so it is the suggested option for ODH users too.

This implies that Knative (OpenShift Serverless) and Istio (OpenShift Service Mesh) are going to be mandatory dependencies to install in the cluster to run the full KServe stack.