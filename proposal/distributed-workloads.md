---
title: Distributed Workloads and Workload Orchestration
---

**Keywords**
CodeFlare, AppWrapper, MCAD, InstaScale

**Introduction**
Distributed Workloads is a simple, user-friendly abstraction for scaling, queuing and resource management of distributed AI/ML and Python workloads. It consists of three components: CodeFlare SDK, Multi-Cluster Application Dispatcher (MCAD) and InstaScale.

[CodeFlare SDK](https://github.com/project-codeflare/codeflare-sdk) is an intuitive user-friendly Python library that allows the user to request, access and manage remote resources with specs of their choice such as the desired distributed compute framework (ie. Ray), worker count, CPU, GPU and memory. The SDK can request to scale up or down the desired resources (ie. Ray Cluster) by generating and interfacing with an AppWrapper, a MCAD CRD, that submits the job request with desired resources to MCAD. Although currently the AppWrapper supports only the Ray framework (that has a dependency on [KubeRay](https://github.com/ray-project/kuberay)), future work will focus on extending the AppWrapper to other distributed frameworks as well.

[Multi-Cluster Application Dispatcher](https://github.com/project-codeflare/multi-cluster-app-dispatcher) (MCAD) is a Kubernetes controller providing mechanisms for applications to manage batch jobs in a single or multi-cluster environment. It is capable of (i) providing an abstraction for wrapping all resources of the job or application and treating them holistically, (ii) queuing job or application creation requests and applying different queuing policies, e.g., First In First Out, Priority, and (iii) dispatching the job to one of multiple clusters, where a MCAD queuing agent runs, using configurable dispatch policies.

[InstaScale](https://github.com/project-codeflare/instascale) is an on-demand resource scaling tool in the cloud. Within the resource limits set by the user, InstaScale can quickly scale up aggregated resources for distributed computing jobs, and just as easily release the resources once the job (ie. MCAD AppWrapper job) is complete. 

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
The implementation of Distributed Workloads with Ray is demonstrated as part of the CodeFlare PoC demo:
[Link to the demo](https://drive.google.com/file/d/1SxySCzxrJi1NZFf_kRlgoiV9ipWmXbhF/view?usp=sharing)

## Owners Information and Maintenance Plan
Selbi Nuryyeva - RHODS team - Red Hat

Mustafa Eyceoz - PSAP team - Red Hat

Atin Sood - IBM Research team - IBM

The owners are committed to maintaining and testing the Distributed Workloads with each new release of its every component and ODH.

## More Info
CodeFlare SDK: https://github.com/project-codeflare/codeflare-sdk

MCAD: https://github.com/project-codeflare/multi-cluster-app-dispatcher

InstaScale: https://github.com/project-codeflare/instascale

KubeRay: https://github.com/ray-project/kuberay 
