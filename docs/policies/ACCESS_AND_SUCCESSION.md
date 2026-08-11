# Access and Succession Policy

Status: Adopted

## Purpose

This policy prevents unnecessary access, single-account dependency, and undocumented transfer of authority.

## Rules

1. Access is granted to teams, not individuals, unless GitHub provides no suitable team mechanism or the access is temporary and documented.
2. Organization Owner is reserved for platform administration, billing, recovery, and emergencies. Routine project work must use lower privileges.
3. The target is two to five independent, trusted owners. Shared accounts are prohibited.
4. Every owner must use phishing-resistant or otherwise secure two-factor authentication, retain recovery material, and be able to perform organization recovery.
5. Repository administration belongs to project maintainer teams. Triage, write, maintain, and admin are granted separately according to the work required.
6. GitHub Apps are preferred over long-lived personal tokens for automation. Fine-grained tokens require approval and a bounded lifetime. Classic tokens remain exceptional and must have a documented migration path.
7. Outside collaborators are used only for narrow repository access and reviewed with the same cadence as members.
8. No workflow, application, deploy key, or token receives organization-wide write access merely for convenience.

## Joiner, mover, leaver process

### Joiner

- Verify the GitHub identity and two-factor-authentication status.
- Add the person to the minimum teams needed.
- Record the accountable maintainer for each grant.
- Do not grant Owner during onboarding.

### Mover

- Remove obsolete team memberships before or at the time new access is granted.
- Re-evaluate access when a contributor changes project, employment, contract, or moderation duties.
- Review tokens and application installations connected to the former role.

### Leaver

- Remove organization and team access promptly.
- Revoke or rotate credentials, keys, secrets, and environment access that could have been retained.
- Transfer issue, release, package, domain, and incident responsibilities.
- Preserve audit records and public attribution.

## Reviews

- Stage 0: quarterly owner-risk review and at least annual full access review.
- Stage 1 and above: quarterly review of owners, members, outside collaborators, teams, roles, tokens, applications, deploy keys, Actions secrets, and environments.
- High or critical repositories: review after every maintainer departure or security incident.

Each review records reviewer, date, scope, exceptions, and due dates. The reviewer should not be the sole approver of their own exceptional access once another qualified person exists.

## Succession

The organization must maintain a private recovery record covering:

- owners and emergency contacts;
- billing and legal-account continuity;
- domains, package registries, signing identities, and distribution accounts;
- release secrets and recovery procedures;
- how to transfer organization, repository, package, and trademark stewardship;
- the conditions under which an inactive owner may be removed.

An owner is considered unavailable when the documented emergency contact process has failed for 30 days, or sooner where a confirmed compromise requires immediate action. Removal must preserve at least one verified recovery path.

## Current exception

Greyfoundry currently has one organization owner. This is an accepted temporary Stage 0 risk, not the target state. A second owner will be added only when an independent, trusted person is qualified and accepts recovery responsibility.

