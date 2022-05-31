# Open Data Hub Repository Guidelines
This document attempts to outline a structure for creating and associating GitHub repositories with the Open Data Hub project. It also describes how and when repositories are removed.

The document presents a tiered system of repositories with increasingly strict requirements in an attempt to provide the right level of oversight and flexibility for a variety of different projects.

Requests for creating, transferring, modifying, or archiving repositories can be made by contacting [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com).

## Associated Repositories
Associated repositories conform to the Open Data Hub community standards for a repository, but otherwise have no restrictions. Associated repositories exist solely for the purpose of making it easier for the Open Data Hub community to work together. There is no implication of support or endorsement of any kind by the Open Data Hub project, the goals are purely logistical.

### Goals
To facilitate contributions and collaboration from the broader Open Data Hub community. Contributions to random projects with random CLAs (or DCOs) can be logistically difficult, so associated repositories should be easier.

### Rules
Must adopt the Open Data Hub Code of Conduct statement in their repository.
All code projects use the GNU General Public License v3.0. Documentation repositories must use the CC BY-SA 4.0.

## SIG repositories
SIG repositories serve as temporary homes for SIG-sponsored experimental projects or prototypes of new core functionality, or as permanent homes for SIG-specific projects and tools.

### Goals
To provide a place for SIGs to collaborate on projects endorsed by and actively worked on by members of the SIG. SIGs should be able to approve and create new repositories for SIG-sponsored projects without requiring higher level approval from a central body (e.g. steering committee or sig-architecture)

### Rules for new repositories
- For now all repos will live in github.com/opendatahub-io/\<project-name\>.
Must contain the topic for the sponsoring SIG - e.g. odh-sig-model-ops.

- Must adopt the Open Data Hub Code of Conduct
All code projects use the GNU General Public License v3.0. Documentation repositories must use the CC BY-SA 4.0.

- All OWNERS of the project must also be active SIG members.

- Must be approved by the process spelled out in the SIG's charter and a publicly linkable written decision should be available for the same.

- SIG must already have identified all of their existing code, with valid OWNERS files, in [sigs.yaml](./sigs.yaml).

Rules for donated repositories
The Open Data Hub organization is primarily intended to house net-new projects originally created in that organization. However, projects that a SIG adopts may also be donated.

In addition to the requirements for new repositories, donated repositories be reviewed by the SIG to address copyright and license updates that may be required.

## Core Repositories
Core repositories are considered core components of Open Data Hub. They are utilities, tools, applications, or libraries that are expected to be present in every or nearly every Open Data Hub release. Additionally, the opendatahub.io website and other project-wide infrastructure will remain in the Open Data Hub GitHub organization.

### Goals
Create a broader base of repositories so that the project can scale. Present expectations about the centrality and importance of the repository in the Open Data Hub ecosystem. Carries the endorsement of the Open Data Hub community.

### Rules
- Must live under github.com/opendatahub-io/<project-name>
- Must adopt the Open Data Hub Code of Conduct
- All code projects use the GNU General Public License v3.0. Documentation repositories must use the CC BY-SA 4.0.
- Must adopt all Open Data Hub automation (e.g. /lgtm, etc)
- All OWNERS must be members of standing as defined by ability to vote in Open Data Hub steering committee elections.
- Repository must be approved by [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com)

## Maintenance Mode
Projects that are considered "done" or not pursuing the development of new features but are relied on as a dependency can be considered in Maintenance mode.

When in maintenance mode, the community can expect the following from the owners of the project/repository:

- No concrete plan on introduction of new features.
- Incoming Issues and PR(s) will not be looked at in any regular cadence.
- Minimal upkeep for project language and dependency updates.
- Security-related features/updates to address.
- Explicit guidance around removal/transition to active state.
  
### Process for transitioning to maintenance mode
- SIG Chairs or technical leads can open PRs to add the label and a preamble in the README.md for the project.
- In addition, a notice will be sent out by the SIG Chairs or technical leads to the Open Data Hub mailing list with a fortnight for [lazy consensus](https://community.apache.org/committers/lazyConsensus.html) once the PR is opened.
### Rules
- Steering committee liaisons can also recommend a project/repository to transition to maintenance mode during the annual reporting process.
- When in doubt, the Steering Committee will be the decision-maker.
- Specific members who can help with the process will be identified & added to the OWNERS file for performing the required activities.

## Removing Repositories
As important as it is to add new repositories, it is equally important to prune old repositories that are no longer relevant or useful.

It is in the best interests of everyone involved in the Open Data Hub community that our various projects and repositories are active and healthy. This ensures that repositories are kept up to date with the latest Open Data Hub wide processes, it ensures a rapid response to potential required fixes (e.g. critical security problems) and (most importantly) it ensures that contributors and users receive quick feedback on their issues and contributions.

### Grounds for removal
SIG repositories and core repositories may be removed from the project if they are deemed inactive. Inactive repositories are those that meet any of the following criteria:

- There are no longer any active maintainers for the project and no replacements can be found.
- All PRs or Issues have gone un-addressed for longer than six months.
- There have been no new commits or other changes in more than a year.
- The contents have been folded into another actively maintained project.

Associated repositories are much more loosely associated with the Open Data Hub project and are generally not subject to removal, except under exceptional circumstances (e.g. a code of conduct violation).

## FAQ
### I want to start a new project, what should I do?

Is this a SIG-sponsored project? If so, convince some SIG to host it, take it to the SIG mailing list, meeting and get consensus, then the SIG can create a repository for you in the organization.

Is this a small-group or personal project? If so, create a repository wherever you’d like, and make it an associated project.

We suggest starting with the opendatahub-template-project to ensure you have the correct code of conduct, license, etc.

### When I donate my project, am I transferring my copyrights?

No. All contributors retain ownership of their copyrights in the code they donate. Instead, they are granting a license to the project.

Note that you should never modify or remove a third party's copyright notice if you are not authorized by them to do so.