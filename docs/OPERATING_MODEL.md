# Greyfoundry Operating Model

Status: Adopted baseline

Review cycle: At least annually, and after any material security incident, ownership change, funding change, or addition of a production-critical project.

## Executive summary

Greyfoundry uses a federated project model. Projects retain authority over their roadmaps and implementation while the organization sets a small number of common boundaries for identity, access, security, licensing, release integrity, community conduct, and continuity.

The model is intentionally lightweight at the current size. It is designed to add checks and delegation when specific scale or risk thresholds are crossed, rather than creating a large permanent hierarchy before it is needed. Authority should move to named teams and documented roles as contributors become qualified. Organization Owner access remains a break-glass and platform-administration capability, not a normal project role.

The most important unresolved continuity control is a second independent, trusted organization owner. No account should be shared and no person should be granted Owner merely to satisfy a numeric target. Until a qualified second owner exists, critical recovery material must be maintained outside any single workstation and changes that could lock out the only owner must not be enabled.

## Design principles

1. Projects are the primary delivery units. Organization policy defines shared safety boundaries, not product roadmaps.
2. Authority is assigned to teams wherever GitHub supports it. Individual grants are exceptional, time-bounded, and reviewed.
3. Least privilege applies to people, teams, applications, tokens, workflows, and release systems.
4. Every active repository has an accountable team, lifecycle state, criticality, and support commitment.
5. A repository cannot be described as supported or production-critical unless at least two independent people can maintain and recover it.
6. Decisions are recorded at the lowest durable level that affects future contributors.
7. Security and legal responsibilities can block a release within their defined scope, but cannot silently take over a project's roadmap.
8. Rules become stronger as impact, contributor count, and operational dependency increase.
9. Governance is reviewed and simplified when it stops producing useful accountability.

## Authority map

### Organization owners

Owners administer the GitHub organization, billing, recovery, and other capabilities that cannot be safely delegated. Owners may act in emergencies, but routine work belongs to scoped teams. The target is two to five independent, trusted owners. Shared accounts are prohibited.

### Governance team

The governance team maintains organization policy, repository lifecycle decisions, the organization profile repository, access reviews, continuity planning, and organization-wide decision records. It does not receive automatic write access to product repositories.

### Engineering team

The engineering team is a coordination and standards forum. Membership does not imply write access to every repository. Repository access is granted through project teams.

### Project maintainers and triage teams

Each active project has a `<project>-maintainers` team with Maintain access and, where useful, a `<project>-triage` team with Triage access. Maintainers own the project roadmap, technical decisions, contributor progression, and release readiness within organization policy.

### Security team

The security team uses GitHub's Security Manager role. It owns vulnerability intake, risk classification, coordinated disclosure, incident coordination, and security-policy exceptions. It should not receive unrelated source write access by default.

### Release engineering team

Release engineering uses GitHub's CI/CD Admin role and owns shared workflow policy, release automation, provenance, signing, artifact retention, and runner governance. It does not receive product write access merely because it operates release infrastructure.

### Legal-compliance team

Legal-compliance uses GitHub's Open-source license manager role. It owns license policy, notices, inbound and outbound dependency review, trademark guidance, and documented compliance exceptions.

### Community team

Community owns contributor experience, moderation procedures, public support routing, and community health. GitHub Moderator capability should be assigned to qualified people when independent moderators exist.

## Repository classification

Every repository carries four organization properties:

| Property | Purpose | Current values |
| --- | --- | --- |
| `lifecycle` | Delivery and retirement state | `incubating`, `active`, `maintenance`, `deprecated`, `archived` |
| `criticality` | Impact-based control tier | `low`, `moderate`, `high`, `critical` |
| `support` | Public commitment | `experimental`, `community`, `supported` |
| `owner_team` | Accountable GitHub team slug | Text |

The detailed transition rules are in [Repository Lifecycle](policies/REPOSITORY_LIFECYCLE.md).

## Decision domains

| Domain | Accountable body | Required consultation |
| --- | --- | --- |
| Project roadmap and architecture | Project maintainers | Affected contributors and shared-service owners |
| Organization policy and lifecycle | Governance | Affected maintainers; security or legal when in scope |
| Vulnerability handling | Security | Project maintainers; release engineering |
| Release infrastructure | Release engineering | Project maintainers; security for trust-boundary changes |
| License and trademark policy | Legal-compliance | Project maintainers; governance for organization-wide effects |
| Community enforcement | Community or designated moderators | Governance for appeals; security for credible threats |
| Owner appointment or removal | Existing owners | Governance and affected maintainers where confidentiality allows |

## Maturity stages

### Stage 0: founder-led baseline

Applies while there is one owner or fewer than three active maintainers.

- Written authority and lifecycle policy are mandatory.
- Team-based repository permissions are used even when one person belongs to each team.
- Destructive and force-push protection may be enabled where it does not block recovery.
- Review-count rules that cannot be independently satisfied remain disabled.
- The sole-owner risk is reviewed quarterly.

### Stage 1: continuity established

Begins when a second independent, trusted owner and at least two maintainers for each supported high-criticality repository exist.

- Require pull requests for protected default branches.
- Require at least one approval from someone other than the author.
- Require dismissal or re-approval after material changes.
- Test organization and repository recovery at least annually.
- Record maintainer appointment and removal decisions.

### Stage 2: multi-project organization

Begins at three active projects, five active maintainers, or two independent delivery teams.

- Establish a governance council of three to seven people with terms and conflict rules.
- Run quarterly access and repository-classification reviews.
- Require a documented repository intake decision.
- Publish an annual governance and sustainability review.
- Create an independent moderation and appeal path.

### Stage 3: material operational or financial dependency

Begins when Greyfoundry has employees or contractors, material recurring funding, production-critical downstreams, regulated data, or contractual support obligations.

- Separate budget approval from payment execution and reconciliation.
- Adopt incident severity, on-call, evidence retention, and post-incident requirements.
- Require release provenance and protected environments for production artifacts.
- Perform independent security review for critical trust boundaries.
- Evaluate GitHub Team or Enterprise for organization-wide rulesets, stronger identity integration, and policy enforcement.

### Stage 4: ecosystem stewardship

Begins only when multiple independent organizations rely on Greyfoundry and neutral governance is needed.

- Evaluate a nonprofit, fiscal host, or established foundation.
- Use multi-stakeholder elections or appointments with published terms.
- Separate trademark, budget, technical, and conduct appeals where scale justifies it.
- Preserve project autonomy unless ecosystem safety requires a shared rule.

## Contrarian views and risks

### More structure is not automatically safer

Complex councils and elections can create the appearance of accountability while leaving essential work unowned. Greyfoundry therefore adds bodies only when there are enough independent people to staff them and an explicit trigger has been crossed.

### Two-owner guidance can be misapplied

Adding an unqualified owner is worse than temporarily documenting the single-owner risk. The second owner must be independent, trusted, able to recover the organization, and willing to follow the access policy.

### Review rules can create a false control

A required approval from the only available maintainer is not independent review. Until independence exists, the organization prioritizes non-bypassable tests, signed or provenance-bearing releases, auditability, and narrow permissions.

### Metrics can be gamed

Issue counts, response times, and contribution volume do not prove health. Reviews should combine quantitative trends with ownership concentration, maintainer workload, unresolved security work, and contributor progression.

### Permanent founder authority creates succession risk

Founder-led operation is practical at the current size, but authority must transfer through documented roles as qualified contributors emerge. Ownership should not be the reward for contribution; it is a recovery and fiduciary responsibility.

## Annual review evidence

The governance team should record:

- owner and maintainer coverage, including recovery readiness;
- repository property accuracy and lifecycle transitions;
- team and individual access exceptions;
- stale tokens, applications, deploy keys, secrets, and environments;
- dependency, release, provenance, and security-control coverage by criticality;
- contributor absence risk and maintainer workload;
- funding concentration and conflicts of interest;
- incidents, near misses, policy exceptions, and overdue corrective actions;
- policies that should be removed, simplified, or strengthened.

## Open questions and activation gates

1. Who is the second independent, trusted organization owner? This remains open until a real person is nominated and accepts the responsibility.
2. What private conduct-reporting channel will be operated independently of project maintainers? Activate before broad community growth.
3. What legal entity, if any, should hold trademarks and funding? Decide only when actual funding, liability, or multi-party stewardship requires it.
4. When should Greyfoundry purchase a paid GitHub plan? Reassess when organization-wide rulesets, SSO, protected environments, or audit integration would replace meaningful manual work.
5. Which repositories will first qualify as `supported` and `high` or `critical`? Qualification requires two-person continuity and the controls in the lifecycle policy.

## Research basis

This model was checked against current platform guidance, secure-development frameworks, open-source governance models, and sustainability research. Sources are primary or project-maintained where available.

### Platform and security controls

- [GitHub: Best practices for organizations](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/best-practices-for-organizations)
- [GitHub: Roles in an organization](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization)
- [GitHub: About teams](https://docs.github.com/en/organizations/organizing-members-into-teams/about-teams)
- [GitHub: Requiring two-factor authentication](https://docs.github.com/en/organizations/keeping-your-organization-secure/managing-two-factor-authentication-for-your-organization/requiring-two-factor-authentication-in-your-organization)
- [GitHub: Personal access token policy](https://docs.github.com/en/organizations/managing-programmatic-access-to-your-organization/setting-a-personal-access-token-policy-for-your-organization)
- [GitHub: Repository rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)
- [GitHub: Organization rulesets](https://docs.github.com/en/organizations/managing-organization-settings/creating-rulesets-for-repositories-in-your-organization)
- [GitHub: Custom repository properties](https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization)
- [GitHub: Default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
- [NIST Secure Software Development Framework](https://csrc.nist.gov/pubs/sp/800/218/final)
- [CISA Secure by Design](https://www.cisa.gov/securebydesign)
- [SLSA specification](https://slsa.dev/spec/v1.2/)
- [OpenSSF Best Practices Badge](https://www.bestpractices.dev/en)
- [OpenSSF Scorecard](https://github.com/ossf/scorecard)
- [OpenSSF Security Insights](https://security-insights.openssf.org/)
- [OWASP SAMM governance model](https://owaspsamm.org/model/governance/)

### Governance and sustainability

- [Apache: How the ASF works](https://www.apache.org/foundation/how-it-works.html)
- [Apache: Project Management Committees](https://www.apache.org/foundation/how-it-works.html#pmc)
- [CNCF charter](https://github.com/cncf/foundation/blob/main/charter.md)
- [Kubernetes community governance](https://github.com/kubernetes/community/blob/master/governance.md)
- [Rust governance](https://www.rust-lang.org/governance)
- [Python PEP 13: Governance model](https://peps.python.org/pep-0013/)
- [Debian constitution](https://www.debian.org/devel/constitution)
- [Mozilla module ownership](https://www.mozilla.org/about/governance/policies/module-ownership/)
- [Eclipse development process](https://www.eclipse.org/projects/dev_process/)
- [TODO Group: Outbound open-source guide](https://todogroup.org/resources/guides/a-guide-to-outbound-open-source-software/)
- [Linux Foundation: Open Source Maintainers report](https://www.linuxfoundation.org/hubfs/LF%20Research/Open%20Source%20Maintainers%202023%20-%20Report.pdf)
- [CHAOSS: Contributor sustainability guide](https://www.chaoss.community/practitioner-guide-contributor-sustainability/)
- [Contributor Covenant 2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/)

