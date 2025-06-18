# Open Data Hub (ODH) & OpenShift AI (RHOAI) Feature Development Requirements

## Overview

This document defines the **development standards and requirements** for features across different maturity levels within the **Open Data Hub (ODH)** and **Red Hat OpenShift AI (RHOAI)** product ecosystems. Understanding these requirements helps teams plan their development approach and ensures consistent quality standards across all features.

---

## Table of Contents
* [Overview](#overview)
* [Feature Maturity Levels](#feature-maturity-levels)
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
    * [Repository and Documentation](#repository-and-documentation)
    * [Technical Requirements](#technical-requirements)
    * [Future Considerations](#future-considerations)
* [Getting Started](#getting-started)
    * [For New Contributors](#for-new-contributors)
    * [For Existing Features](#for-existing-features)
    * [Support and Questions](#support-and-questions)
* [Document Maintenance](#document-maintenance)

---

## Feature Maturity Levels

| Feature Level | Repository Location | Support Model | Release Process | Integration Requirements                                                    |
|---------------|-------------------|---------------|-----------------|-----------------------------------------------------------------------------|
| **RHOAI Features** | [red-hat-data-services](https://github.com/red-hat-data-services) | Full Red Hat Support | Released as part of RHOAI | Must meet [RHOAI integration standards](#rhoai-features-tech-preview-or-ga) |
| **ODH Features** | [opendatahub-io](https://github.com/opendatahub-io) | Limited Community Support (see [Community Guidelines](https://github.com/opendatahub-io/opendatahub-community#community-guidelines) for details) | Released as part of ODH; production-ready development begins | Must meet [ODH integration standards](#odh-features)                        |
| **Dev Preview Features** | Preferably [opendatahub-io](https://github.com/opendatahub-io) | Unsupported/Experimental | Add-on installations require usage and installation documentation | Must meet [Dev Preview standards](#dev-preview-features)                                           |

---

## RHOAI Features (Tech Preview or GA)

For a feature to be released as part of RHOAI, the following requirements must be satisfied. It's recommended to initiate this process **one month prior** to integration.

RHOAI features must satisfy all [ODH requirements](#odh-features) **plus** the additional requirements below:

<h3 id="security-requirements-rhoai">Security Requirements</h2> 

- **Security Architecture Review** for any major feature changes after addition to ODH
- **Container and Repository Scanning** using Snyk
- **Threat Modeling** integration with SDElement

<h3 id="packaging-requirements-rhoai">Packaging Requirements</h2>

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

<h3 id="security-requirements-odh">Security Requirements</h2>

- **Security Architecture Review** with ProdSec security architect and platform security architect
- **Konflux Integration** implemented and verified
- **FIPS Compliance** - Must meet "[Designed for FIPS](https://spaces.redhat.com/display/RHODS/FIPS+Enablement+for+RHOAI+Images)" requirements

### Testing Requirements
- **Unit Tests** - Comprehensive unit test coverage
- **Functional Tests** - Feature functionality validation
- **Integration Tests** - Component integration verification
- **Regression Tests** - Backward compatibility testing
- **End-to-End Tests** - Complete workflow validation

<h3 id="packaging-requirements-odh">Packaging Requirements</h2>

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

Dev Preview features follow [Red Hat's Dev Preview](https://access.redhat.com/support/offerings/devpreview) guidelines:

### Repository and Documentation
- **Repository Location** - Should ideally be part of the ODH organization
- **Usage Documentation** - Clear installation and usage instructions
- **Contact Information** - Team contact details for support and questions
- **Release Notes** - Feature documented in ODH release notes or repository documentation

### Technical Requirements
- **Multi-Architecture Support** *(Optional)* - Support for ODH/RHOAI architectures preferred but not required
- **FIPS Exception** - Obtain ["Designed for FIPS" exception](https://spaces.redhat.com/display/RHODS/Dev+Preview+and+FIPS+and+Disconnected) if requirements cannot be met

### Future Considerations
- **API Design** - TODO: [Define APIs and implementation approach for seamless v1 integration](https://issues.redhat.com/browse/RHOAIENG-26470)

---

## Getting Started

### For New Contributors
1. Review the [Guidelines for Contributing New Components](GuidelinesForNewComponents.md)
2. Identify your target feature level based on maturity and support requirements
3. Ensure your component meets the basic requirements for your chosen level
4. Begin working through the checklist for your target feature level

### For Existing Features
1. Assess your current feature against the requirements for your target level
2. Create a gap analysis identifying missing requirements
3. Develop a roadmap to address gaps with your team
4. Engage with the appropriate architecture and security teams early in the process

### Support and Questions
- **Community Support:** Join ODH community meetings and mailing lists
- **Process Questions:** Reach out to feature level coordinators

---

## Document Maintenance

This document is maintained by the ODH community and should be updated as requirements evolve. We welcome your contributions and feedback to keep this document accurate and helpful. For questions or suggested changes, please open an issue or pull request in the [opendatahub-community repository](https://github.com/opendatahub-io/opendatahub-community).

**Last Updated:** June 2025