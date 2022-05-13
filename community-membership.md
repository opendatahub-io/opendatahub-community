# Community Membership

This document outlines the various responsibilities of contributor roles in the
Open Data Hub community.  The Open Data Hub project is subdivided into subprojects under SIGs.
Responsibilities for most roles are scoped to these subprojects.

| Role | Responsibilities | Requirements | Defined by |
| -----| ---------------- | ------------ | -------|
| Member | Active contributor in the community | Sponsored by 2 reviewers and multiple contributions to the project | Open Data Hub GitHub org member|
| Reviewer | Review contributions from other members | History of review and authorship in a subproject | OWNERS file reviewer entry |
| Approver | Contributions acceptance approval| Highly experienced active reviewer and contributor to a subproject | OWNERS file approver entry|
| Subproject owner | Set direction and priorities for a subproject | Demonstrated responsibility and excellent technical judgement for the subproject | [./sigs.yaml](./sigs.yaml) subproject OWNERS file *owners* entry |

## New contributors

[New contributors](./contributing.md) should be welcomed to the community by existing members,
helped with PR workflow, and directed to relevant documentation and
communication channels.

## Established community members

Established community members are expected to demonstrate their adherence to the
principles in this document, familiarity with project organization, roles,
policies, procedures, conventions, etc., and technical and/or writing ability.
Role-specific expectations, responsibilities, and requirements are enumerated
below.

## Member

Members are continuously active contributors in the community.  They can have
issues and PRs assigned to them, participate in SIGs through GitHub teams, and
pre-submit tests are automatically run for their PRs. Members are expected to
remain active contributors to the community.

**Defined by:** Member of the Open Data Hub GitHub organization

### Requirements

- Enabled [two-factor authentication](https://help.github.com/articles/about-two-factor-authentication) on their GitHub account
- Have made multiple contributions to the project or community.  Contribution may include, but is not limited to:
    - Authoring or reviewing PRs on GitHub. At least one PR must be **merged**.
    - Filing or commenting on issues on GitHub.
    - Contributing to SIG, subproject, or community discussions (e.g. meetings, Slack, email discussion forums).
- Subscribed to [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com).
- Have read the [contributor guide](./contributing.md).
- Actively contributing to 1 or more subprojects.
- Sponsored by 2 reviewers. **Note the following requirements for sponsors**:
    - Sponsors must have close interactions with the prospective member - e.g. code/design/proposal review, coordinating on issues, etc.
    - Sponsors must be reviewers or approvers in at least one OWNERS file within one of the Open Data Hub GitHub organizations.
- **Submit a membership request to [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com)**
   - Ensure your sponsors are @mentioned on the issue
   - Complete every item on the checklist ([preview the current version of the template](./membership.yaml))
   - Make sure that the list of contributions included is representative of your work on the project.
- Have your sponsoring reviewers reply confirmation of sponsorship: `+1`
- Once your sponsors have responded, your request will be reviewed by the Open Data Hub GitHub Admin team within a reasonable amount of time. Any missing information will be requested.

### Responsibilities and privileges

- Responsive to issues and PRs assigned to them.
- Responsive to mentions of SIG teams of which they are members.
- Active owner of code they have contributed (unless ownership is explicitly transferred)
  - Code is well tested
  - Tests consistently pass
  - Addresses bugs or issues discovered after code is accepted.
- Members can do `/lgtm` on open PRs.
- They can be assigned to issues and PRs, and people can ask members for reviews.
- Tests can be run against their PRs automatically.

**Note:** members who frequently contribute code are expected to proactively
perform code reviews and work towards becoming a primary *reviewer* for the
subproject that they are active in.

## Reviewer

Reviewers are able to review code for quality and correctness on some part of a
subproject. They are knowledgeable about both the codebase and software
engineering principles.

**Defined by:** *reviewers* entry in an OWNERS file in a repo owned by the
Open Data Hub project.

Reviewer status is scoped to a part of the codebase.

**Note:** Acceptance of code contributions requires at least one approver in
addition to the assigned reviewers.

### Requirements

The following apply to the part of codebase for which one would be a reviewer in
an OWNERS file.

- member for at least 3 months.
- Primary reviewer for at least 5 PRs to the codebase.
- Reviewed or merged at least 20 substantial PRs to the codebase.
- Knowledgeable about the codebase.
- Sponsored by a subproject approver
  - With no objections from other approvers.
  - Done through PR to update the OWNERS file.
- May either self-nominate, be nominated by an approver in this subproject.

### Responsibilities and privileges

The following apply to the part of codebase for which one would be a reviewer in
an OWNERS file.

- Tests are automatically run for PullRequests from members of the Open Data Hub GitHub organization.
- Code reviewer status may be a precondition to accepting large code contributions.
- Responsible for project quality control via code reviews.
  - Focus on code quality and correctness, including testing and factoring.
  - May also review for more holistic issues, but not a requirement.
- Expected to be responsive to review requests.
- Assigned PRs to review related to subproject of expertise.
- Assigned test bugs related to subproject of expertise.
- Granted "read access" to Open Data Hub repository.
- May get a badge on PR and issue comments.

## Approver

Code approvers are able to both review and approve code contributions.  While
code review is focused on code quality and correctness, approval is focused on
holistic acceptance of a contribution including: backwards / forwards
compatibility, adhering to API and flag conventions, subtle performance and
correctness issues, interactions with other parts of the system, etc.

**Defined by:** *approvers* entry in an OWNERS file in a repository owned by the
Open Data Hub project.

Approver status is scoped to a part of the codebase.

### Requirements

The following apply to the part of codebase for which one would be an approver
in an OWNERS file.

- Reviewer of the codebase for at least 3 months
- Primary reviewer for at least 10 substantial PRs to the codebase
- Reviewed or merged at least 30 PRs to the codebase
- Nominated by a subproject owner
  - With no objections from other subproject owners
  - Done through PR to update the top-level OWNERS file

### Responsibilities and privileges

The following apply to the part of codebase for which one would be an approver
in an OWNERS file.

- Approver status may be a precondition to accepting large code contributions.
- Demonstrate sound technical judgement.
- Responsible for project quality control via code reviews.
  - Focus on holistic acceptance of contribution such as dependencies with other features, backwards / forwards
    compatibility, API and flag definitions, etc.
- Expected to be responsive to review requests.
- Mentor contributors and reviewers.
- May approve code contributions for acceptance.

## Subproject Owner

Subproject Owners are the technical authority for a subproject in the Open Data Hub
project.  They *MUST* have demonstrated both good judgement and responsibility
towards the health of that subproject.  Subproject Owners *MUST* set technical
direction and make or approve design decisions for their subproject - either
directly or through delegation of these responsibilities.

**Defined by:** *owners* entry in subproject OWNERS files as defined by [sigs.yaml](./sigs.yaml)  *subproject.owners*

### Requirements

The process for becoming an subproject Owner should be defined in the SIG
charter of the SIG owning the subproject.  Unlike the roles outlined above, the
Owners of a subproject are typically limited to a relatively small group of
decision makers and updated as fits the needs of the subproject.

The following apply to the subproject for which one would be an owner.

- Deep understanding of the technical goals and direction of the subproject.
- Deep understanding of the technical domain of the subproject.
- Sustained contributions to design and direction by doing all of:
  - Authoring and reviewing proposals.
  - Initiating, contributing and resolving discussions (emails, GitHub issues, meetings).
  - Identifying subtle or complex issues in designs and implementation PRs.
- Directly contributed to the subproject through implementation and/or review.

### Responsibilities and privileges

The following apply to the subproject for which one would be an owner.

- Make and approve technical design decisions for the subproject.
- Set technical direction and priorities for the subproject.
- Define milestones and releases.
- Mentor and guide approvers, reviewers, and contributors to the subproject.
- Ensure continued health of subproject
  - Adequate test coverage to confidently release.
  - Tests are passing reliably (i.e. not flaky) and are fixed when they fail.
- Ensure a healthy process for discussion and decision making is in place.
- Work with other subproject owners to maintain the project's overall health and success holistically

## Inactive members

_Members are continuously active contributors in the community._

A core principle in maintaining a healthy community is encouraging active
participation. It is inevitable that people's focuses will change over time and
they are not expected to be actively contributing forever.

However, being a member of one of the Open Data Hub GitHub organizations comes with
an elevated set of permissions. These capabilities should not be used by those
that are not familiar with the current state of the Open Data Hub project.

Therefore members with an extended period away from the project with no activity
will be removed from the Open Data Hub Github Organizations and will be required to
go through the org membership process again after re-familiarizing themselves
with the current state.


### How inactivity is measured

Inactive members are defined as members of one of the Open Data Hub Organizations
with **no** contributions across any organization within 18 months. Both code and non-code contributions should be evaluated.