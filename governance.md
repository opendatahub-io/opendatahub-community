# Governance
The Open Data Hub community abides by the [Open Data Hub code of conduct](https://github.com/opendatahub-io/opendatahub-community/blob/master/CODE_OF_CONDUCT.md). 

Here is an excerpt:

*In the interest of fostering an open and welcoming environment, we as contributors and maintainers pledge to making participation in our project and our community a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity and expression, level of experience, education, socio-economic status, nationality, personal appearance, race, religion, or sexual identity and orientation.*

As a member of the Open Data Hub project, you represent the project and your fellow contributors. We value our community tremendously and we'd like to keep cultivating a friendly and collaborative environment for our contributors and users. We want everyone in the community to have positive experiences.

## Community membership
See [community membership](./community-membership.md).

## Community groups
The project is comprised of the following types of subgroups:
- Special Interest Groups, SIGs
  - Subprojects
- Working Groups, WGs
- Committees
 
## SIGs
The Open Data Hub project is organized primarily into Special Interest Groups, or SIGs. Each SIG is composed of members from multiple companies and organizations, with a common purpose of advancing the project with respect to a specific topic, such as Data Scientist Experience. Our goal is to enable a distributed decision structure and code ownership, as well as providing focused forums for getting work done, making decisions, and onboarding new contributors. Every identifiable subpart of the project (e.g., github org, repository, subdirectory, API, test, issue, PR) is intended to be owned by some SIG.

Areas covered by SIGs may be vertically focused on particular components or functions, cross-cutting/horizontal, spanning many/all functional areas of the project, or in support of the project itself.

SIGs must have at least one and ideally two SIG chairs at any given time. SIG chairs are intended to be organizers and facilitators, responsible for the operation of the SIG and for communication and coordination with the other SIGs, the Steering Committee, and the broader community.

Each SIG must have a charter that specifies its scope (topics, subsystems, code repos and directories), responsibilities, areas of authority, how members and roles of authority/leadership are selected/granted, how decisions are made, and how conflicts are resolved. See the SIG charter process for details on how charters are managed. SIGs should be relatively free to customize or change how they operate, within some broad guidelines and constraints imposed by cross-SIG processes (e.g., the release process) and assets (e.g., the Open Data Hub repo).

A primary reason that SIGs exist is as forums for collaboration. Much work in a SIG should stay local within that SIG. However, SIGs must communicate in the open, ensure other SIGs and community members can find notes of meetings, discussions, designs, and decisions, and periodically communicate a high-level summary of the SIG's work to the community.

See [sig governance](./sig-governance.md) for more details about current SIG operating mechanics, such as mailing lists, meeting times, etc.

### Subprojects
Specific work efforts within SIGs are divided into subprojects. Every part of the Open Data Hub code and documentation should be owned by some subproject. Some SIGs may have a single subproject, but many SIGs have multiple significant subprojects with distinct (though sometimes overlapping) sets of contributors and owners, who act as subproject’s technical leaders: responsible for vision and direction and overall design, choose/approve change proposal approvers, field technical escalations, etc.

Example subprojects for a few SIGs:

- SIG Notebook Server/Image Lifecycle Management: notebook server images, version control, image pipelines
- SIG Data Scientist Experience: jupyter notebook controller, dashboard, tutorials

Subprojects for each SIG are documented in [sigs.yaml](./sigs.yaml).

## Working Groups
We need community rallying points to facilitate discussions/work regarding topics that are short-lived or that span multiple SIGs.

Working groups are primarily used to facilitate topics of discussion that are in scope for Open Data Hub but that cross SIG lines. If a set of folks in the community want to get together and discuss a topic, they can do so without forming a Working Group.

See [working group governance](./wg-governance.md) for more details about forming and disbanding Working Groups.

Working groups are documented in [sigs.yaml](./sigs.yaml).

## Committees
Some topics, such as Security or Code of Conduct, require discretion. Whereas SIGs are voluntary groups which operate in the open and anyone can join, Committees do not have open membership and do not always operate in the open. The steering committee can form committees as needed, for bounded or unbounded duration. Membership of a committee is decided by the steering committee, however, all committee members must be community members. Like a SIG, a committee has a charter and a chair, and will report to the steering committee periodically, and to the community as makes sense, given the charter.

## Cross-project Communication and Coordination
While most work shouldn’t require expensive coordination with other SIGs, there will be efforts (features, refactoring, etc.) that cross SIG boundaries. In this case, it is expected that the SIGs coordinate with each other and come to mutually agreed solutions. In some cases, it may make sense to form a Working Group for joint work. Cross-SIG coordination will naturally require more time and implies a certain amount of overhead. This is intentional to encourage changes to be well encapsulated whenever possible.

On the other hand, some SIGs may have project-wide impact. Even those that do not may sometimes need to make changes or impose new processes or conventions that affect other SIGs. In these cases, project-wide communication processes will need to be followed. For example, proposals with project-wide impact will need to be announced more broadly, with the opportunity for members of other SIGs to provide feedback and guidance. However, the SIG that owns the area, according to its charter, will own the decision. In the case of extended debate or deadlock, decisions may be escalated to the Steering Committee, which is expected to be uncommon.

## Repository guidelines
All new repositories under Open Data Hub github orgs should follow the process outlined in the [Open Data Hub repository guidelines](./odh-repositories.md).
