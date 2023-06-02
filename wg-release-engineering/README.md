# Release Engineering Working Group

A working group is dedicated to release engineering and optimization for MLOps and data science teams that use ODH. This group will be responsible for designing, developing, and documenting a unified set of methods and tooling needed by MLOps teams to ensure that their ML models are performing well in production and are maximizing business value. We will focus on use-cases that encompass automated traffic engineering for new versions of ML models in an ODH cluster, and automated validation of ML model versions in production using their performance, business, and ML metrics.

## Stakeholder SIGs

* [SIG ML Ops](/sig-ml-ops)

## Expected WG lifetime

6 months

## Meetings

TBD

## Organizers

* [Alan Cha](https://github.com/Alan-Cha)
* [Taneem Ibrahim](https://github.com/taneem-ibrahim)
* [Michael Kalatar](https://github.com/kalantar)
* [Srinivasan Parthasarathy](https://github.com/sriumcp)
* [Atin Sood](https://github.com/atinsood)

## Contact
- Slack: TBD
- [Mailing list] TBD
- [Open Community Issues/PRs] TBD

## Goals

* Establish a framework for release optimization and engineering within the ODH ecosystem.
* Drive higher-value for ODH eco-system components through Iter8. The components that will benefit from this work includes the model serving components, namely ModelMesh, TrustyAI, OpenVINO, and the storage components, namely, Prometheus and Ceph.
* Provide guidance and tooling for MLOps teams using ODH for the following use-cases.
    - Reliable and automated traffic engineering: blue-green, canary, and mirroring
    - Metrics-driven validation: A/B/n testing, performance testing
    - Metrics-driven validation (future roadmap): Golden testing, drift detection

## Deliverables

* Enable installation of Iter8 through ODH operator
* [Phase 1] Document traffic engineering use-cases for Kserve modelmesh
* [Phase 2] Document performance validation experiments for KServe modelmesh
* [Phase 3] Document A/B/n testing experiments for KServe modelmesh
* [Phase 4] Document traffic engineering use-cases for model serving based on TrustyAI and OpenVINO
* [Phase 5] Document performance validation experiments for model serving based on TrustyAI and OpenVINO
* [Phase 6] Document A/B/n testing experiments for model serving based on TrustyAI and OpenVINO

## Useful references

[Iter8 documentation](https://iter8.tools).