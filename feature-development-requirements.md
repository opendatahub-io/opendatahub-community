# Open Data Hub (ODH) & OpenShift AI (RHOAI) Feature Development Requirements

## Overview

This document defines the **development standards and requirements** for features across different maturity levels within the **Open Data Hub (ODH)** and **Red Hat OpenShift AI (RHOAI)** product ecosystems. Understanding these requirements helps teams plan their development approach and ensures consistent quality standards across all features.

---

## Table of Contents
* [Overview](#overview)
* [Feature Maturity Levels](#feature-maturity-levels)
* [Component Onboarding Process](#component-onboarding-process)
* [RHOAI Features (Tech Preview or GA)](#rhoai-features-tech-preview-or-ga)
  * [Security Requirements](#security-requirements-rhoai)
  * [Packaging Requirements](#packaging-requirements-rhoai)
  * [Acceptance Criteria](#acceptance-criteria)
* [ODH Features](#odh-features)
  * [Security Requirements](#security-requirements-odh)
  * [Testing Requirements](#testing-requirements)
  * [Packaging Requirements](#packaging-requirements-odh)
  * [Maintenance Requirements](#maintenance-requirements)
  * [Development Requirements](#development-requirements)
* [Dev Preview Features](#dev-preview-features)
  * [Prerequisites](#prerequisites-dev-preview)
  * [Repository and Documentation](#repository-and-documentation-dev-preview)
  * [Technical Requirements](#technical-requirements-dev-preview)
  * [Future Considerations](#future-considerations)
* [Tech Preview Features](#tech-preview-features)
  * [Prerequisites](#prerequisites-tech-preview)
  * [Repository and Documentation](#repository-and-documentation-tech-preview)
  * [Technical Requirements](#technical-requirements-tech-preview)
  * [Progression to GA](#progression-to-ga)
* [Obsolete and Deprecated Features](#obsolete-and-deprecated-features)
  * [Deprecation Process](#deprecation-process)
  * [Obsolescence Criteria](#obsolescence-criteria)
  * [Removal Process](#removal-process)
  * [Jira Process](#jira-process)
* [Getting Started](#getting-started)
  * [For Component Onboarding](#for-component-onboarding)
  * [For Existing Components](#for-existing-components)
  * [Support and Questions](#support-and-questions)
* [Document Maintenance](#document-maintenance)

---

## Feature Maturity Levels

Components in ODH and RHOAI follow a structured maturity progression with mandatory governance requirements:

### Component Integration Lifecycle

All component integrations must progress through defined maturity stages with proper governance approval:

1. **Dev Preview** → 2. **Tech Preview** → 3. **General Availability (GA)** → 4. **Obsolete/Deprecated**

#### Mandatory Prerequisites (All Levels)
- **Architect Council Approval**: An approved RFE (Request for Enhancement) by the Architect Council is **non-negotiable**
- **STRAT Document**: An associated STRAT document must be in place with the appropriate maturity level in the title
- **Jira Template Usage**: Use the appropriate Jira template and clone child issues using "RHOAIENG: Clone Epic & child issues"

| Feature Level | Repository Location | Support Model | Release Process | Integration Requirements | Jira Template |
|---------------|-------------------|---------------|-----------------|-----------------------------------------------------------------------------|---------------|
| **Dev Preview** | [opendatahub-io](https://github.com/opendatahub-io) | Unsupported/Experimental | Fast release in RHOAI only | Must meet [Dev Preview standards](#dev-preview-features) | [RHOAIENG-31244](https://issues.redhat.com/browse/RHOAIENG-31244) |
| **Tech Preview** | [opendatahub-io](https://github.com/opendatahub-io) | Limited Community Support | Fast release in RHOAI only | Must meet [Tech Preview standards](#tech-preview-features) | [RHOAIENG-31290](https://issues.redhat.com/browse/RHOAIENG-31290) |
| **RHOAI Features (GA)** | [red-hat-data-services](https://github.com/red-hat-data-services) | Full Red Hat Support | Released as part of RHOAI | Must complete Tech Preview + [RHOAI integration standards](#rhoai-features-tech-preview-or-ga) | [RHOAIENG-31303](https://issues.redhat.com/browse/RHOAIENG-31303) |
| **ODH Features** | [opendatahub-io](https://github.com/opendatahub-io) | Limited Community Support | Released as part of ODH | Must meet [ODH integration standards](#odh-features) | N/A |
| **Obsolete/Deprecated** | Various | End-of-Life | Removal from future releases | Follow [deprecation process](#obsolete-and-deprecated-features) | TBD |

---

## Component Onboarding Process

To onboard a new component into the ODH/RHOAI platform operator, follow the structured process using the appropriate Jira template based on your target maturity level.

### Step 1: Select Your Maturity Level

Choose the appropriate entry point for your component:

- **Dev Preview**: For experimental/early-stage components
- **Tech Preview**: For more stable components ready for broader testing  
- **General Availability (GA)**: For production-ready components (must complete Tech Preview first)

### Step 2: Clone the Appropriate Jira Template and Follow Workflow Steps

#### For Dev Preview Components
**Clone [RHOAIENG-31244](https://issues.redhat.com/browse/RHOAIENG-31244)** to onboard a new component into ODH/RHOAI platform operator as Dev Preview

**Process:**
1. Navigate to [RHOAIENG-31244](https://issues.redhat.com/browse/RHOAIENG-31244)
2. Use "RHOAIENG: Clone Epic & child issues" to create your component-specific epic
3. Update the component name in the cloned epic title
4. Complete the following workflow steps (from template child issues):

**Dev Preview Workflow Steps:**
1. **Repository added to ODH/RHOAI** - Add repository to ODH/RHOAI organization using the [repository request form](https://docs.google.com/forms/d/e/1FAIpQLSdw9JBPdjhuBfaYzk5_IB_Nqw1KU1MEtZroLcuaPFmPp5cmNg/viewform)
2. **Integration with ODH operator** (2 week notice!) - Follow [component integration steps](https://github.com/opendatahub-io/opendatahub-operator/blob/incubation/components/README.md)
3. **Integration with RHOAI operator** (2 week notice!) - Follow [RHOAI build integration](https://issues.redhat.com/browse/RHOAIENG-17225) instructions
4. **Onboard to RHOAI Build** (2 week notice!) - Complete build integration following [RHOAIENG-17225](https://issues.redhat.com/browse/RHOAIENG-17225)
5. **Follow component integration steps** - Complete [component integration documentation](https://github.com/opendatahub-io/opendatahub-operator/blob/main/docs/COMPONENT_INTEGRATION.md)
6. **Installation, usage, contact information** - Document installation/usage instructions and provide team contact information
7. **Multi-Architecture Support** (Optional) - Support for ODH/RHOAI architectures (consult [supported configurations](https://access.redhat.com/articles/rhoai-supported-configs))
8. **Designed for FIPS** - Meet [Designed for FIPS requirements](https://spaces.redhat.com/display/RHODS/Dev+Preview+and+FIPS+and+Disconnected) or obtain exception
9. **Add component to Jira** - Contact Rick Dixon to have component added to Jira tracking

#### For Tech Preview Components  
**Clone [RHOAIENG-31290](https://issues.redhat.com/browse/RHOAIENG-31290)** to onboard a new component into ODH/RHOAI platform operator as Tech Preview

**Process:**
1. Navigate to [RHOAIENG-31290](https://issues.redhat.com/browse/RHOAIENG-31290)
2. Use "RHOAIENG: Clone Epic & child issues" to create your component-specific epic
3. Update the component name in the cloned epic title
4. Complete the following workflow steps (from template child issues):

**Tech Preview Workflow Steps:**
1. **Integration with RHOAI operator** (2 week notice!) - Complete RHOAI operator integration with monitoring and API documentation
2. **Integration with ODH operator** (2 week notice!) - If not completed in Dev Preview, follow ODH integration steps
3. **Repository added to ODH/RHOAI** - If not completed in Dev Preview, add repository to organizations
4. **Create component in Jira** - Contact Rick Dixon to add component to Jira tracking
5. **Test with disconnected environment** - Validate functionality in air-gapped environments using [disconnected cluster setup](https://spaces.redhat.com/spaces/RHODS/pages/339591460/Create+a+disconnected+cluster+install+RHOAI+and+delete+it+when+finished)
6. **Multi-Architecture Support** - Support all RHOAI architectures including x86, Power, Z, and aarch64 (RHOAI 2.25+)
7. **RHOAI ONLY: AI Platform Core Components (AIPCC) Integration** - Use AIPCC tool packages where applicable (see [AIPCC documentation](https://docs.google.com/document/d/1g5aiGwLcgijs7Klpugj5LiKpVf0gxweUDLPPB-BrU1k/edit))
8. **Testing requirements** - Complete comprehensive testing including unit, functional, integration, regression, and end-to-end tests
9. **Security requirements** - Complete security architecture review, add repository to Snyk scanning, and meet CVE SLA requirements
10. **MUST meet designed for FIPS** - Meet [FIPS enablement requirements](https://spaces.redhat.com/display/RHODS/FIPS+Enablement+for+RHOAI+Images) or obtain business unit approval and exception
11. **Feature documented in architecture diagrams** - Add component to [official architecture documentation](https://github.com/opendatahub-io/architecture-decision-records/blob/main/documentation/arch-overview.md)
12. **Ensure work with supported lifecycles** - Verify compatibility with [RHOAI support lifecycle](https://access.redhat.com/support/policy/updates/rhoai-sm/lifecycle)
13. **Add source repo(s) to Snyk** - Enable Snyk scanning for security vulnerability detection
14. **Add component data to product-definitions** - Add component mappings for vulnerability tracking
15. **Add component support for must-gather** - Create gather scripts in [must-gather repository](https://github.com/red-hat-data-services/must-gather/)
16. **Add Prometheus config for component** - Add basic metrics and monitoring configuration
17. **Add support for the new component in QE repositories** - Update ods-ci, Jenkins, and olminstall repositories

#### For General Availability Components
**Clone [RHOAIENG-31303](https://issues.redhat.com/browse/RHOAIENG-31303)** to onboard a new component into ODH/RHOAI platform operator as GA

**Prerequisites:** Must have completed Tech Preview requirements first

**Process:**
1. Navigate to [RHOAIENG-31303](https://issues.redhat.com/browse/RHOAIENG-31303)
2. Use "RHOAIENG: Clone Epic & child issues" to create your component-specific epic
3. Update the component name in the cloned epic title
4. Complete the following workflow steps (from template child issues):

**General Availability Workflow Steps:**
1. **Ensure everything was completed under Tech Preview** - Verify all Tech Preview requirements from [RHOAIENG-31290](https://issues.redhat.com/browse/RHOAIENG-31290) are satisfied
2. **Security Requirements** - Resolve any exceptions raised in Tech Preview and complete security architecture review for major feature changes
3. **Acceptance Criteria** - Complete final validation including:
   - Requirements validation by Business Unit and owning team
   - All required documentation reviewed and approved  
   - All testing requirements satisfied
   - Reference [GA acceptance criteria documentation](https://docs.google.com/document/d/1EEXJEVa9P4hOZAms85OSpphj2wyLrchbr4SLYtFBDBM/edit)

### Step 3: Track Progress

Use the epic's progress tracking to monitor completion of all required steps. The epic will show percentage completion based on child issue status.

---

## RHOAI Features (Tech Preview or GA)

For a feature to be released as part of RHOAI, the following requirements must be satisfied. It's recommended to initiate this process **one month prior** to integration.

RHOAI features must satisfy all [ODH requirements](#odh-features) **plus** the additional requirements below:

<h3 id="security-requirements-rhoai">Security Requirements</h3> 

- **Security Architecture Review** for any major feature changes after addition to ODH
- **Container and Repository Scanning** using Snyk
- **Threat Modeling** integration with SDElement

<h3 id="packaging-requirements-rhoai">Packaging Requirements</h3>

- **RHOAI Build Integration** - Added to [RHOAI build](https://issues.redhat.com/browse/RHOAIENG-17225) pipeline for new components
- **Multi-Architecture Support** - Must support all architectures available in RHOAI
- **AIPCC Tool Integration** - Must use packages built and provided by the AIPCC tool

### Acceptance Criteria
- **Requirements Validation** - All ODH and RHOAI requirements met and accepted by Business Unit and owning team
- **Documentation Complete** - All required documentation reviewed and approved
- **Testing Complete** - All testing requirements satisfied

---

## ODH Features

To transition a [Dev Preview feature](#dev-preview-features) to an ODH feature, the requirements below must be met. It's recommended to initiate this process **one month prior** to integration.

<h3 id="security-requirements-odh">Security Requirements</h3>

- **Security Architecture Review** with ProdSec security architect and platform security architect
- **Konflux Integration** implemented and verified
- **FIPS Compliance** - Must meet "[Designed for FIPS](https://spaces.redhat.com/display/RHODS/FIPS+Enablement+for+RHOAI+Images)" requirements

### Testing Requirements
- **Unit Tests** - Comprehensive unit test coverage
- **Functional Tests** - Feature functionality validation
- **Integration Tests** - Component integration verification
- **Regression Tests** - Backward compatibility testing
- **End-to-End Tests** - Complete workflow validation

<h3 id="packaging-requirements-odh">Packaging Requirements</h3>

- **Operator Integration** - New components added to the [ODH operator](https://issues.redhat.com/browse/RHOAIENG-6413)
- **Disconnected Environment Support** - Must function in air-gapped environments
- **Multi-Architecture Support** - Must support all architectures available in ODH
- **AI Platform Core Components (AIPCC) Integration** *(Future)* - Must use AIPCC tool packages when available for upstream use

### Maintenance Requirements
- **Regular Updates** - Commitment to ongoing updates and improvements
- **Bug Fixes** - Timely resolution of reported issues
- **CVE Management** - Security vulnerability patching process

### Development Requirements
- **Architecture Approval** - RHOAI Architect team approval of feature architecture
- **Architecture Documentation** - Feature documented in official [architecture diagrams](https://github.com/opendatahub-io/architecture-decision-records/blob/main/documentation/arch-overview.md)
- **Ownership Agreement** - Clear agreement between feature owners and contributors on work division

---

## Dev Preview Features

Dev Preview features follow [Red Hat's Dev Preview](https://access.redhat.com/support/offerings/devpreview) guidelines and represent the entry point for new component integrations:

<h3 id="prerequisites-dev-preview">Prerequisites</h3>
- **Approved RFE** by the Architect Council with associated STRAT document (title must include "Dev Preview")
- **Jira Template**: Use [RHOAIENG-31244](https://issues.redhat.com/browse/RHOAIENG-31244)

<h3 id="repository-and-documentation-dev-preview">Repository and Documentation</h3>
- **Repository Location** - Should ideally be part of the ODH organization
- **Usage Documentation** - Clear installation and usage instructions
- **Contact Information** - Team contact details for support and questions
- **Release Notes** - Feature documented in ODH release notes or repository documentation

<h3 id="technical-requirements-dev-preview">Technical Requirements</h3>
- **Multi-Architecture Support** *(Optional)* - Support for ODH/RHOAI architectures preferred but not required
- **FIPS Exception** - Obtain ["Designed for FIPS" exception](https://spaces.redhat.com/display/RHODS/Dev+Preview+and+FIPS+and+Disconnected) if requirements cannot be met

### Progression Path
- **Next Step**: Advance to [Tech Preview](#tech-preview-features) after meeting stability and maturity requirements

### Future Considerations
- **API Design** - TODO: [Define APIs and implementation approach for seamless v1 integration](https://issues.redhat.com/browse/RHOAIENG-26470)

---

## Tech Preview Features

Tech Preview features follow [Red Hat's Tech Preview](https://access.redhat.com/support/offerings/techpreview) guidelines and represent the next maturity level after Dev Preview:

<h3 id="prerequisites-tech-preview">Prerequisites</h3>
- **Must have completed Dev Preview requirements** or demonstrate equivalent maturity
- **Approved RFE** by the Architect Council with associated STRAT document (title must include "Tech Preview")
- **Jira Template**: Use [RHOAIENG-31290](https://issues.redhat.com/browse/RHOAIENG-31290)

<h3 id="repository-and-documentation-tech-preview">Repository and Documentation</h3>
- **Repository Location** - Should be part of the ODH organization
- **Enhanced Documentation** - Comprehensive installation, usage, and troubleshooting guides
- **Contact Information** - Dedicated team contact details for support
- **Release Integration** - Feature integrated into RHOAI release process

<h3 id="technical-requirements-tech-preview">Technical Requirements</h3>
- **Stability Requirements** - More rigorous testing and validation than Dev Preview
- **Multi-Architecture Support** - Support for ODH/RHOAI architectures strongly recommended
- **Performance Validation** - Basic performance benchmarking completed
- **Security Review** - Initial security assessment completed

### Progression to GA
- **GA Prerequisites** - Must complete all Tech Preview requirements before advancing to General Availability
- **GA Template**: Use [RHOAIENG-31303](https://issues.redhat.com/browse/RHOAIENG-31303) for GA progression

---

## Obsolete and Deprecated Features

Components may become obsolete or deprecated due to technology evolution, security concerns, or strategic changes. This section outlines the process for managing end-of-life features.

### Deprecation Process
- **Deprecation Notice** - Official announcement with timeline for removal
- **Migration Path** - Clear guidance for users to transition to alternatives
- **Support Timeline** - Defined support end-date with advance notice
- **Documentation Updates** - All documentation marked with deprecation warnings

### Obsolescence Criteria
- **Security Vulnerabilities** - Unresolvable security issues
- **Technology Evolution** - Superseded by better alternatives
- **Maintenance Burden** - Unsustainable maintenance requirements
- **Strategic Alignment** - No longer aligns with product direction

### Removal Process
- **Community Notice** - Advance notification to community
- **Final Support Period** - Last supported release cycle
- **Archive Process** - Code archived with historical reference
- **Documentation Cleanup** - Removal from active documentation

### Jira Process
- **Template**: TBD - Jira template for deprecation process to be defined
- **Tracking**: Use component-specific Jira epics for deprecation tracking

---

## Getting Started

### For Component Onboarding
1. **Review Requirements**: Understand the requirements for your target maturity level using this document
2. **Obtain Prerequisites**: Ensure you have Architect Council RFE approval and STRAT document
3. **Clone Jira Template**: Use the appropriate template based on your component's maturity:
   - **Dev Preview**: Clone [RHOAIENG-31244](https://issues.redhat.com/browse/RHOAIENG-31244)
   - **Tech Preview**: Clone [RHOAIENG-31290](https://issues.redhat.com/browse/RHOAIENG-31290)
   - **General Availability**: Clone [RHOAIENG-31303](https://issues.redhat.com/browse/RHOAIENG-31303)
4. **Follow Template Steps**: Complete all child issues in your cloned epic
5. **Meet Technical Requirements**: Ensure your component meets all requirements for your target maturity level

### For Existing Components
1. **Assess Current State**: Evaluate your component against the requirements for your desired maturity level
2. **Plan Progression**: If advancing maturity levels, clone the appropriate template for your target level
3. **Address Gaps**: Use this document to identify and address any missing requirements
4. **Engage Teams**: Work with architecture and security teams as outlined in the template workflow

### Support and Questions
- **General Questions**: Contact `openshift-ai-core-platform
- **Build Issues**: Contact `openshift-ai-devops`
- **Template Questions**: Comment on the original template Jira issues
- **Community Support**: Join ODH community meetings and mailing lists
- **Process Questions**: Reach out to feature level coordinators

---

## Document Maintenance

This document is maintained by the ODH community and should be updated as requirements evolve. We welcome your contributions and feedback to keep this document accurate and helpful. For questions or suggested changes, please open an issue or pull request in the [opendatahub-community repository](https://github.com/opendatahub-io/opendatahub-community).

**Last Updated:** October 2025
