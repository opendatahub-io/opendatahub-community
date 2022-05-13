# SIG Roles and Organizational Governance

This charter adheres to the conventions described in the [Open Data Hub Charter Guide](./sig-charter-guide.md).
It will be updated as needed to meet the current needs of the Open Data Hub project.

In order to standardize Special Interest Group efforts, create maximum
transparency, and route contributors to the appropriate SIG, SIGs should follow
these guidelines:

- Have an approved Charter ([SIG charter process](sig-charter-guide.md))
- Meet regularly, at least for 30 minutes every 4 weeks, except November and
December.
- Keep up-to-date meeting notes, linked from the SIG's page in the community
repository.
- Record meetings and make them publicly available.
- Report activity with the community via the [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com) mailing list at
least once a year. 
  - Each SIG is assigned an update during the [Open Data Hub community meeting](./README.md) throughout the year.
- Participate in release planning meetings and retrospectives, and burndown
meetings, as needed.
- Ensure related work happens in a project-owned github repository, with
 code and tests explicitly owned and supported by the SIG, including issue
 triage, PR reviews, test-failure response, bug fixes, etc.
- Use the [forums provided](./README.md) as the primary means of working, communicating, and
collaborating, as opposed to private emails and meetings.
- Ensure contributing instructions are defined in the SIGs
folder located in the opendatahub-io/opendatahub-community repository if the groups contributor steps
and experience are different or more in-depth than the documentation listed in
the general [contributor guide](./contributing.md).
- Track and identify all SIG features in the current release.

## Roles

### Notes on Roles

Within this section "Lead" refers to someone who is a member of the union
 of a Chair or Subproject Owner role. There is no one lead to any
 Open Data Hub community group. Leads have specific decision making power over some
 part of a group and thus additional accountability. Each role is detailed below.  

- Initial roles are defined at the founding of the SIG or Subproject as part
of the acceptance of that SIG or Subproject.

#### Activity Expectations  

- Leads *SHOULD* remain active and responsive in their Roles.
- Leads taking an extended leave of 1 or more months *SHOULD* coordinate with other leads to ensure the role is adequately staffed during the leave.
- Leads going on leave for 1-3 months *MAY* work with other Leads to identify a temporary replacement.
- Leads of a role *SHOULD* remove any other leads or roles that have not communicated a leave of absence and either cannot be reached for more than 1 month or are not fulfilling their documented responsibilities for more than 1 month.
  - This may be done through a [super-majority](https://en.wikipedia.org/wiki/Supermajority#Two-thirds_vote) vote of Leads. If there are not enough *active* Leads, then a [super-majority](https://en.wikipedia.org/wiki/Supermajority#Two-thirds_vote) vote between Chairs and Subproject Owners may decide the removal of the Lead.

#### Requirements

- Leads *MUST* be at least a ["member" on our contributor ladder](./community-membership.md) to
be eligible to hold a leadership role within a SIG.
- SIGs *MAY* prefer various levels of domain knowledge depending on the
role. This should be documented.  
- Interest in working with others to help manage time and areas of contribution.

#### Escalations

- Lead membership disagreements *MAY* be escalated to the Steering Committee.

#### On-boarding and Off-boarding Leads

- Leads *MAY* decide to step down at anytime and propose a replacement.  Use
[lazy consensus](https://community.apache.org/committers/lazyConsensus.html) amongst other Leads with fallback on majority vote to accept
proposal.  The candidate *SHOULD* be supported by a majority of SIG contributors
 or the Subproject contributors (as applicable).
- Leads *MAY* select additional leads through a [super-majority](https://en.wikipedia.org/wiki/Supermajority#Two-thirds_vote) vote
amongst leads. This *SHOULD* be supported by a majority of SIG contributors or
Subproject contributors (as applicable).

### Chair

- SIG Chairs
  - Establish new subprojects
  - Decommission existing subprojects
  - Resolve X-Subproject technical issues and decisions
  - Number: 2-3
  - Membership tracked in [sigs.yaml](./sigs.yaml)

### Subproject Owner

- Subproject Owners
  - Scoped to a subproject defined in [sigs.yaml](./sigs.yaml)
  - Seed leads and contributors established at subproject founding
  - *SHOULD* be an escalation point for technical discussions and decisions in
  the subproject
  - *SHOULD* set milestone priorities or delegate this responsibility
  - Number: 2-3
  - Membership tracked in [sigs.yaml](./sigs.yaml)

### All Leads

- *SHOULD* maintain health of at least one subproject or the health of the SIG.
- *SHOULD* show sustained contributions to at least one subproject or to the
  SIG.
- *SHOULD* hold some documented role or responsibility in the SIG and / or at
  least one subproject
    (e.g. reviewer, approver, etc).
- *MAY* build new functionality for subprojects.
- *MAY* participate in decision making for the subprojects in which they hold roles.
- Includes all reviewers and approvers in OWNERS files for subprojects.
- *SHOULD* take an [Inclusive Open Source Community Orientation course](https://training.linuxfoundation.org/training/inclusive-open-source-community-orientation-lfc102/) in support of our community values
within 30 days from the date of their appointment.

### Other Roles
This governance document outlines the required roles for SIGs.  However, SIGs are allowed to operate how they see fit outside of minimum 
governance requirements, including defining more roles to sustain the group. If 
a SIG needs to change the Chair position to include or remove
duties, this needs to be approved by the Steering Committee. Newly created roles
that don't assume any responsibility of Chair should follow
the governing processes in the SIGs charter. 

Example of SIG roles created to help operations:

- The Release Team: Bug Triage, CI Signal, and more  
- API Reviewer and Moderator  
- Production Readiness Reviewer 
- PR Wrangler

Other roles...
- *MUST* be tracked on the SIGs README with a link to the role definition.
- *MUST* have the Steering Committees approval to proceed with roles that assume
duties from Chairs on a non-temporary basis. 
- *SHOULD* be documented in SIG charters if the role has delegation away from a
sig-governance.md listed role.
- *SHOULD* be sent to [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com) for awareness as a notice 
and a lazy consensus period when they are newly created.
- *MAY* Fill in for another named role on a temporary basis.

#### Subproject Creation

Option 1: by SIG Chairs

- Subprojects may be created by socializing the proposal to the corresponding SIG with fallback on majority vote of the corresponding SIG Chairs.  The result *SHOULD* be supported by the majority of the leads of the SIG.
  - Proposal *MUST* establish subproject owners.
  - [sigs.yaml](./sigs.yaml) *MUST* be updated to include subproject information and OWNERS files with subproject owners.
  - Where subprojects processes differ from the SIG governance, they must document how.
    - e.g. if subprojects release separately - they must document how release and planning is performed.

Option 2: by Federation of Subprojects

- Subprojects may be created by socializing the proposal to the corresponding SIG and accepted by [lazy-consensus](http://en.osswiki.info/concepts/lazy_consensus) with fallback on majority vote of
  subproject owners in the SIG.  The result *SHOULD* be supported by the majority of leads.
  - Proposal *MUST* establish subproject owners.
  - [sigs.yaml](./sigs.yaml) *MUST* be updated to include subproject information and OWNERS files with subproject owners.
  - Where subprojects processes differ from the SIG governance, they must document how.
    - e.g. if subprojects release separately - they must document how release and planning is performed.

Subprojects may create repos under *github.com/opendatahub-io* through [lazy-consensus](http://en.osswiki.info/concepts/lazy_consensus) of subproject owners.

- Subprojects must define how releases are performed and milestones are set.

### Technical processes

Subprojects of the SIG *MUST* use the following processes unless explicitly following alternatives
they have defined.

- Proposing and making decisions
  - Proposals sent as PRs and published to [odh-community@googlegroups.com](mailto:odh-community@googlegroups.com).
  - Follow proposal decision making process.

- Test health
  - Consistently broken tests automatically send an alert to the contributors.
  - SIG contributors are responsible for responding to broken tests alert. PRs that break tests should be rolled back if not fixed within 72 hours (business hours).

Issues impacting multiple subprojects in the SIG should be resolved by either:

- Option 1: SIG Chairs
- Option 2: Federation of Subproject Owners

### SIG Retirement

- In the event that the SIG is unable to regularly establish consistent quorum or otherwise fulfill its Organizational Management responsibilities
  - after 3 or more months it *SHOULD* be retired
  - after 6 or more months it *MUST* be retired