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

- 'engineering': parent for project engineering teams, with no direct repository access.
  - '<project>-maintainers': Maintain access for day-to-day project administration and review.
  - '<project>-triage': Triage access for issues, discussions, labels, and pull request workflow.
- 'security': Security manager role and no owner access.
- 'release-engineering': CI/CD administration only when required.
- 'community': Moderator role and project-specific Triage access where needed.

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
