# Autopilot Proposal for Inclusion with Open Data Hub

## High level Description

Infrastructure stability is fundamental to the success of AI training and inference workloads. While anomalies cannot be avoided, we can provide automatic tools designed to detect and report infrastructure-level issues during the lifetime of these AI workloads. 

[Autopilot](https://github.com/IBM/autopilot), initially developed and recently open sourced by IBM Research, is a Kubernetes-native tool that implements a set of advanced health checks to monitor and detect infrastructure issues while running AI workloads. Autopilot’s methods and thresholds are based on IBM experience in training and serving large-scale language models.  
 
The goal of this project is to help enable Kubernetes/OpenShift to become the premier platform to orchestrate the full life cycle of AI workflows. From pre-processing and model training, to adaptation and distillation, and, finally, inference serving. 

Autopilot follows a three-stages inspection process (figure 1). Pre-flight system check run before the AI workload is started to confirm the status of the infrastructure. In-flight monitoring routinely takes place during the workload to alert the owner of potential issues. Finally, Post-flight system evaluations are done after the job is completed to assure that the infrastructure is left in a working state. 

![image](https://media.github.ibm.com/user/96687/files/4a7c81ba-857a-43d4-bc82-0784ef81b270)
Figure 1. Autopilot’s three-stage inspection process

## High level Architecture Design  

Autopilot is deployed through a Kubernetes DaemonSet on worker nodes with one or more GPUs. Health checks are run locally in the pod, or coordinated across pods, as in the case of network testing. Findings are exposed over Prometheus to a Grafana dashboard, and alerts can be issued via Slack or OpenShift Alerts when and if critical issues are detected.  A service API is exposed to allow a user check status and trigger manual health checks.  

![image](https://media.github.ibm.com/user/96687/files/0d466863-a19e-459d-a492-e2275377d4b9)
Figure 2. Autopilot, deployed on every GPU node, expose health checks and metrics though Kubernetes-native interfaces 

## Description of Use Cases 

In AI training jobs, which may run for weeks or months, anomalies in the GPUs and network can happen anytime and often go undetected. In this case, performance degrades suddenly and a deep diagnostic is needed to identify the root cause, delaying or deleting the current job. Similarly, hardware anomalies can greatly disrupt the throughput and latency of an AI inference server. 

With Autopilot, the owner of an AI workload can be assured that infrastructure where the job runs is working order from the moment the jobs starts until it finishes. Any problems that are detected during the lifetime of the job are issued as alerts so that they can be quickly addressed.  

## Lower Level Implementation Details

#### Integration  

Autopilot pods and jobs are deployed on GPU nodes via a Kubernetes DeamonSet 

#### Implementation details 

Autopilot health checks and operational code is written in a combination of Python, GoLang, bash and CUDA 

 
#### Artifacts 

The Autopilot container image is based off `nvidia/cuda:12.1.1-runtime-ubuntu20.04` and includes the following packages: iperf3, iputils-ping, pciutils, wget, net-tools, dgcmi.  
 

#### Endpoints 

Autopilot provides a service API endpoint for gathering status and triggering checks, as well as a metrics endpoint for publishing Prometheus metrics 

#### Security considerations 

Autopilot is deployed without privilege but with access to GPUs 

#### Multi-user support 

n/a 

#### Authentication 

n/a 

#### Misc.  

n/a 
