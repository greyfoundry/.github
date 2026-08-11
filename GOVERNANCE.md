# Greyfoundry governance

Greyfoundry uses a federated project model. Project maintainers own technical direction and delivery within a small organization-wide boundary for access, security, licensing, releases, community safety, funding integrity, and continuity.

The complete model and its maturity gates are documented in the [Greyfoundry Operating Model](docs/OPERATING_MODEL.md).

## Principles

- Delegate routine authority to named teams.
- Keep Organization Owner access for platform administration, recovery, billing, and emergencies.
- Give projects autonomy over roadmaps and architecture unless a shared security, legal, release, or community boundary applies.
- Use the least privilege needed by people, teams, applications, tokens, and workflows.
- Classify every repository by lifecycle, criticality, support commitment, and accountable team.
- Record significant and exceptional decisions in a durable place.
- Add governance bodies only when there are enough independent people and a documented scale trigger has been crossed.

## Teams and responsibility

- `governance`: organization policy, continuity, access review, repository lifecycle, and stewardship of this repository. It has Maintain access to `.github`, not automatic access to product repositories.
- `engineering`: cross-project coordination and standards. Membership does not grant broad repository write access.
- `{project}-maintainers`: Maintain access and project technical authority.
- `{project}-triage`: issue, discussion, label, and pull-request stewardship without source write access.
- `security`: GitHub Security Manager responsibility for vulnerability and security policy.
- `release-engineering`: GitHub CI/CD Admin responsibility for shared release systems.
- `legal-compliance`: GitHub Open-source license manager responsibility for licensing, notices, trademarks, and dependency policy.
- `community`: contributor experience and moderation. Moderator capability is assigned to qualified people when independent capacity exists.

Direct individual repository grants are temporary exceptions. Recurring access belongs in a team.

## Repository roles

- **Read**: discussion, review, and non-code participation.
- **Triage**: issue, discussion, label, and pull-request management without source write access.
- **Write**: contributors who must push branches. Fork-based contribution is preferred when practical.
- **Maintain**: trusted project maintainers who manage normal repository operations without destructive administration.
- **Admin**: exceptional repository administration. Broad teams should not receive Admin by default.

## Decision authority

Project maintainers decide project roadmap, architecture, contribution progression, and release readiness. Security, release engineering, legal-compliance, community, and governance decide within their defined functional scopes. Organization owners decide platform and recovery matters that cannot be delegated.

Consensus is preferred. The accountable team may decide after affected contributors have had a reasonable opportunity to comment. A concrete security, legal, technical, community, or sustainability objection must be addressed or explicitly accepted as risk.

Emergency action must be limited to containment and followed by a durable incident or decision record appropriate to the sensitivity of the event.

## Policy suite

- [Access and Succession](docs/policies/ACCESS_AND_SUCCESSION.md)
- [Repository Lifecycle](docs/policies/REPOSITORY_LIFECYCLE.md)
- [Security and Releases](docs/policies/SECURITY_AND_RELEASES.md)
- [Decision Making](docs/policies/DECISION_MAKING.md)
- [Community and Moderation](docs/policies/COMMUNITY_AND_MODERATION.md)
- [Funding and Conflicts](docs/policies/FUNDING_AND_CONFLICTS.md)

Project policy may be stricter, but it must not silently weaken this baseline. When project and organization policy conflict, the accountable teams should resolve the conflict through the decision-making policy.

## Access and review cadence

Secure two-factor authentication is required. Fine-grained personal access tokens require approval and a bounded lifetime. GitHub Apps or OpenID Connect are preferred for automation. Classic tokens are temporary compatibility exceptions with a migration path.

Owners, members, outside collaborators, teams, applications, tokens, deploy keys, Actions secrets, and environments are reviewed at least annually during Stage 0 and quarterly from Stage 1. Material role changes, departures, incidents, and application installations trigger an additional review.

Greyfoundry's current single-owner state is a temporary Stage 0 risk. A second independent owner will be added only when a trusted person is qualified and accepts recovery responsibility. Shared accounts are prohibited.

## Amendments

Policy changes are made through a reviewed change to this repository when independent review capacity exists. During the current single-maintainer stage, direct changes must use factual commit messages and remain visible in repository history. Security-sensitive implementation details may stay private, but public policy must remain accurate.

The governance team reviews this model at least annually and after material security incidents, ownership changes, funding changes, or the addition of a production-critical project. Policies that create ceremony without accountability should be simplified or removed.

# Greyfoundry governance

This document defines the organization-wide governance baseline for Greyfoundry repositories. A repository may add stricter project-specific rules, but it must not weaken these access and security principles without a documented decision.

## Principles

- Use least privilege. Grant the smallest role that supports a person's current responsibilities.
- Separate organization administration, project maintenance, security response, release operations, and community moderation.
- Prefer teams over direct repository grants so access is reviewable and consistent.
- Keep technical decisions, role changes, and exceptions reviewable through issues, pull requests, or architecture decision records where appropriate.
- Maintain at least two independent organization owners when the contributor base makes that possible.
- Never use shared personal accounts, shared long-lived credentials, or owner access for routine project work.

## Organization roles

### Owners

Owners manage organization settings, billing relationships, emergency recovery, and destructive operations. Owner access is not a maintainer badge and should remain rare. Owners retain final authority for legal, security, and organization-continuity decisions.

### Security managers

Security managers review private vulnerability reports and organization-wide security alerts. Assign GitHub's Security manager role to the security team instead of granting owner access.

### Release engineering

Release engineering manages approved CI/CD and publishing systems. Assign GitHub's CI/CD role only when a team needs organization-wide Actions administration. Repository write or maintain access is granted separately and only where required.

### Community moderators

Moderators manage abusive content, interaction limits, and community safety. Assign GitHub's Moderator role without repository write access unless a project separately requires it.

### Members

Members receive read access by default. Additional access is granted through a project team. Repository creation, application installation, destructive repository changes, and organization-wide settings remain owner-controlled.

### Outside collaborators

Outside collaborators receive access only to the repositories and roles required for a bounded contribution. They are not a substitute for organization membership or teams.

## Team structure

Use visible teams unless membership itself is sensitive. Parent teams provide organization and mentions, not broad repository access.

- `engineering`: parent for project engineering teams, with no direct repository access.
  - `{project}-maintainers`: Maintain access for day-to-day project administration and review.
  - `{project}-triage`: Triage access for issues, discussions, labels, and pull request workflow.
- `security`: Security manager role and no owner access.
- `release-engineering`: CI/CD administration only when required.
- `community`: Moderator role and project-specific Triage access where needed.

Create additional divisions only when they own a distinct responsibility. Do not create teams merely to mirror job titles.

## Repository roles

- **Read**: discussion, review, and non-code participation.
- **Triage**: issue, discussion, label, and pull request stewardship without code write access.
- **Write**: active contributors who must push branches directly. Prefer fork-based contributions when practical.
- **Maintain**: trusted project maintainers who manage normal repository operations without destructive administration.
- **Admin**: exceptional repository administration. Prefer organization owners and avoid assigning Admin to broad teams.

Direct grants are temporary exceptions. Move recurring access into a team and record why the team needs that role.

## Decisions and reviews

Project maintainers own technical direction within published architecture and release constraints. Significant decisions should be recorded in public project artifacts unless security, privacy, or legal concerns require private handling.

A contributor must not approve their own security-sensitive or release-critical change when another qualified reviewer is available. Emergency owner action should be followed by a public or private incident record appropriate to the sensitivity of the event.

## Access lifecycle

- Require secure two-factor authentication for members and outside collaborators.
- Review organization members, outside collaborators, teams, installed applications, and active tokens at least quarterly.
- Remove access promptly when responsibilities end.
- Use fine-grained personal access tokens with administrator approval and short expirations.
- Prefer GitHub Apps or OpenID Connect over long-lived personal tokens for automation.
- Keep classic personal access tokens only for documented compatibility needs and retire them when the dependent workflow is migrated.
- Review audit-log events after material permission, application, or authentication changes.

## Amendments

Changes to this governance model are made through a reviewed pull request in this repository. Security-sensitive implementation details may be handled privately, but the public policy should remain accurate.
