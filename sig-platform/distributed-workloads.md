---
title: Distributed Workloads and Workload Orchestration
---

**Keywords**
CodeFlare, AppWrapper, MCAD, InstaScale

**Introduction**
Distributed Workloads is a simple, user-friendly abstraction for scaling, queuing and resource management of distributed AI/ML and Python workloads. It consists of three components: CodeFlare SDK, Multi-Cluster Application Dispatcher (MCAD) and InstaScale.

[CodeFlare SDK](https://github.com/project-codeflare/codeflare-sdk) is an intuitive user-friendly Python library that allows the user to request, access and manage remote resources with specs of their choice such as the desired distributed compute framework (ie. Ray), worker count, CPU, GPU and memory. The SDK can request to scale up or down the desired resources (ie. Ray Cluster) by generating and interfacing with an AppWrapper, a MCAD CRD, that submits the job request with desired resources to MCAD. Although currently the AppWrapper supports only the Ray framework (that has a dependency on [KubeRay](https://github.com/ray-project/kuberay)), future work will focus on extending the AppWrapper to other distributed frameworks as well.

[Multi-Cluster Application Dispatcher](https://github.com/IBM/multi-cluster-app-dispatcher) (MCAD) is a Kubernetes controller providing mechanisms for applications to manage batch jobs in a single or multi-cluster environment. It is capable of (i) providing an abstraction for wrapping all resources of the job or application and treating them holistically, (ii) queuing job or application creation requests and applying different queuing policies, e.g., First In First Out, Priority, and (iii) dispatching the job to one of multiple clusters, where a MCAD queuing agent runs, using configurable dispatch policies.

[InstaScale](https://github.com/IBM/multi-cluster-app-dispatcher/tree/cluster-autoscale) is an on-demand resource scaling tool in the cloud. Within the resource limits set by the user, InstaScale can quickly scale up aggregated resources for distributed computing jobs, and just as easily release the resources once the job (ie. MCAD AppWrapper job) is complete. 

Altogether, Distributed Workloads will allow the ODH user to seamlessly run and manage jobs that are distributed across the aggregated resources, all from within the custom notebook environment. 

**Advantages of Distributed Workloads Components Over Alternatives**

*CodeFlare SDK*
- Enhances and simplifies the user experience for data scientists when performing and managing complex tasks of distributed computing and batch processing, all from within a Jupyter notebook environment
- Seamless transition from client to large scale backend with no code refactoring
- Simplified cloud-native scale out without requiring Kubernetes expertise
- Transparent execution on specialized hardware

*Multi-Cluster Application Dispatcher (MCAD)*
- Offers flexibility and extensibility to wrap Ray clusters, Spark clusters or any other desired resource kind
- Allows for direct submission of jobs, deployments, stateful sets, or any other Kube kind, which provides infinite customizability
- In addition to runnable components of the app, non-runnable components such as secrets, service definitions, config maps etc. are included with the app in one holistic AppWrapper definition
- Job meta-scheduler (job queue manager)
- Checks for available resources, quota limits, as well as queue ordering policy (e.g., priority queue)
- Holds the job until ready, rather than immediately creating pods and throwing responsibility onto basic Kubernetes scheduler
- Provides the ability to implement multiple desirable quota management policies based on customer use case
- Potential for plug-and-play/configurable resource quota management
- Enhanced user experience for the data scientist by eliminating the need to manually coordinate with other users of a shared cluster to run a large training job that will require freeing large amounts of cluster resources

*InstaScale*
- Cluster elasticity catering for large distributed job requirements, realizing instant scaling by acquiring resources in the cloud in a demand-driven way based on queued jobs’ resource requests
- Resources are acquired from the cloud provider at job start/finish time, and released immediately as soon as the job completes, which minimizes the cost of resources, as none are kept idle
- Selects right provider instance sizes on behalf of the user

Current state of community landscape regarding batch processing and scaling is summarized here:
[Openshift Batch and Open Source landscape](https://docs.google.com/document/d/1N6cqIwylnDRtqHoxiq8GdwO7AbvkcNEdpWil2CzkzNU/edit?usp=sharing)

**User Use Cases**
- *Data Scientists* need self-service access to ephemeral high-performance compute infrastructure (i.e, multi-node GPU enabled clusters) for performing distributed computation. This platform supports both on-prem and cloud based environments.
- *Cluster Administrators* can provide the capacity for on-demand infrastructure to their data scientist users, while implementing per user quota policies for fair access and limiting cloud spend. 
- *Cluster Users’* requests of infrastructure for distributed compute jobs or interactive development environments will be placed in a queue until the necessary cluster resources become available.      

## Architecture
The architecture and typical workflow for a sample Ray distributed workload are depicted below.
![Screenshot from 2022-12-02 14-57-05](https://user-images.githubusercontent.com/43946617/206355518-4b3ecd06-7290-4c4c-9f21-8bfb02011927.png)

------------------------------------------------------------------------------------------------------------------------------

![Screenshot from 2022-12-02 14-56-13](https://user-images.githubusercontent.com/43946617/206355725-96eba2dd-1b2f-489e-a396-981bdc6f0819.png)

## Implementation
The prerequisites for CodeFlare (or DCG) are:
- OpenShift 4.11+
And if GPUs are used:
- GPU operator
- NFD
If Ray Clusters are created:
- KubeRay operator

The script below will install MCAD, InstaScale, and the KubeRay operator in an OpenShift cluster:
```# MCAD
git clone https://github.com/IBM/multi-cluster-app-dispatcher.git -b quota-management
helm list -n kube-system
cd multi-cluster-app-dispatcher/deployment/mcad-controller/
helm upgrade --install --wait mcad . --namespace kube-system --set loglevel=4 --set image.repository=darroyo/mcad-controller --set image.tag=quota-management-v1.29.40 --set image.pullPolicy=Always --set configMap.name=mcad-controller-configmap --set configMap.quotaEnabled='"false"' --set coscheduler.rbac.apiGroup="scheduling.sigs.k8s.io" --set coscheduler.rbac.resource="podgroups"
cd ../../..
rm -rf multi-cluster-app-dispatcher

# INSTASCALE
git clone https://github.com/IBM/multi-cluster-app-dispatcher.git -b cluster-autoscale
cd multi-cluster-app-dispatcher/instascale/deployment/
oc apply -f instascale-sa.yaml
oc apply -f instascale-clusterrole.yaml
oc apply -f instascale-clusterrolebinding.yaml
oc apply -f deployment.yaml
cd ../../..
rm -rf multi-cluster-app-dispatcher

# RAY (via KubeRay Operator)
oc create -k "github.com/ray-project/kuberay/ray-operator/config/crd?ref=v0.3.0"
helm install kuberay-operator --namespace ray-system --create-namespace $(curl -s https://api.github.com/repos/ray-project/kuberay/releases/tags/v0.3.0 | grep '"browser_download_url":' | sort | grep -om1 'https.*helm-chart-kuberay-operator.*tgz')

# ClusterRole Patch
git clone https://github.com/IBM/multi-cluster-app-dispatcher.git -b quota-management
cd multi-cluster-app-dispatcher/doc/usage/examples/kuberay/config
oc delete ClusterRole system:controller:xqueuejob-controller || true
oc apply -f xqueuejob-controller.yaml
oc delete clusterrolebinding kuberay-operator
oc create clusterrolebinding kuberay-operator --clusterrole=cluster-admin --user="system:serviceaccount:ray-system:kuberay-operator"
cd ../../../../../..
rm -rf multi-cluster-app-dispatcher
```


CodeFlare SDK is readily available in a custom notebook. The custom notebook can be added to a cluster via an imagestream:
```kind: ImageStream
apiVersion: image.openshift.io/v1
metadata:
  name: codeflare-notebook
  labels:
    opendatahub.io/notebook-image: 'true'
  annotations:
    opendatahub.io/notebook-image-name:
      "Codeflare Notebook"
    opendatahub.io/notebook-image-desc: "Custom Jupyter notebook image with Codeflare-cli, Python 3.8, Ray 1.13 and PyTorch 1.12."
spec:
  lookupPolicy:
    local: true
  tags:
    - annotations:
        openshift.io/imported-from: quay.io/openshift-batch/codeflare-ray113-py38-custom-nb
      name: stable
      from:
        kind: DockerImage
        name: quay.io/openshift-batch/codeflare-ray113-py38-custom-nb:v1.5
      name: "v1.5"
      referencePolicy:
        type: Source 
```
by running the command:
`oc apply -f imagestream.yaml`

Additionally MCAD, InstaScale and KubeRay will need to be installed on the cluster (please see links under More Info for installation instructions).

The implementation of Ray distributed computing job with CodeFlare is  as a PoC:
[Link to the demo](https://drive.google.com/file/d/1SxySCzxrJi1NZFf_kRlgoiV9ipWmXbhF/view?usp=sharing)

## Owners Information and Maintenance Plan
Selbi Nuryyeva - RHODS team - Red Hat

Mustafa Eyceoz - PSAP team - Red Hat

Atin Sood - IBM Research team - IBM

The owners are committed to maintaining and testing the Distributed Workloads with each new release of its every component and ODH.

## More Info
CodeFlare SDK: https://github.com/project-codeflare/codeflare-sdk

MCAD: https://github.com/IBM/multi-cluster-app-dispatcher → will be moving under CodeFlare organization Dec 2022

InstaScale: https://github.com/IBM/multi-cluster-app-dispatcher/tree/cluster-autoscale  → will be moving under CodeFlare organization Dec 2022

KubeRay: https://github.com/ray-project/kuberay 
