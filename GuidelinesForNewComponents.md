# Guidelines for Contributing New Components to Open Data Hub

This document describes the guidelines to submit new ideas such as new features and components to Open Data Hub. This specifically pertains to new components or large features that require an architecture review or a re-design of existing components. This document does not apply to small or incremental features, for those please open an issue with a "feature" label in the [Open Data Hub project](https://issues.redhat.com/projects/ODH/summary)

## Basic Requirements for a Component
Proposed components must have the following basic requirements:
1. The component is an open source project with a valid open source license.
2. The component should be aligned with Open Data Hub goals, architecture and roadmap.
3. All build and source files for the component must be publicly available. 
4. For component images and builds it is recommended to use [Red Hat Universal Base Images](https://catalog.redhat.com/software/containers/search?q=ubi&p=1) (UBI) based images.
5. The component must run on OpenShift or OKD platform. 

## Create a Proposal document
The first step in submitting a new component or a feature in Open Data Hub is to create a proposal document and place that in the proposal folder. Please name the file accordingly: <component-name>.md. 
The following information must be included in the proposal document
1. High level description of the component along with a high level architecture diagram.
2. A detailed description of the user use cases this components will provide. 
3. Lower level implementation design and details that include information such as integration implementation details, artifacts, endpoints, security considerations, multi-user support, authentication, etc.

## Present your Proposal to ODH Community Meeting
Present your proposal to the Open Data Hub Community in one of the community meetings. You can add your item to the agenda by editing the [wiki](https://github.com/opendatahub-io/opendatahub-community/wiki/Open-Data-Hub-Community-Meeting-Agenda) page and attending the appropriate ODH community meeting in this [calendar](https://github.com/opendatahub-io/opendatahub-community). 

## Open an Issue in Open Data Hub project
Open an Issue in the Open Data Hub [Jira project](https://issues.redhat.com/secure/RapidBoard.jspa?rapidView=8528&projectKey=ODH&view=planning.nodetail&issueLimit=100) describing the proposed component and pointing to the proposal documentation. In this issue the Open Data Hub community will discuss the new component and decide whether or not to move forward. 

## Submit a Pull Request After Approval
Once the opened issue is resolved and there is approval from the Open Data Hub community, a pull request with the implementation details can be submitted. A pull request must include comprehensive unit tests for the component integrated with Open Data Hub testing framework. If the component includes a UI element, integration with the Open Data Hub dashboard must also be included. It is also required that all new components expose a Prometheus endpoint for metric gathering. 

## Development Standards by Feature Level
 
The approval for any new component in ODH ultimately rests with the relevant Business Unit (BU). Once the Business Unit approves a component's inclusion, it must then meet the specific development requirements for its intended feature level (Dev Preview, ODH, or RHOAI). These requirements cover security, testing, packaging, and ongoing maintenance standards.

For detailed technical, security, and operational standards that apply throughout the development lifecycle, see the [Feature Development Requirements](feature-development-requirements.md) document.
