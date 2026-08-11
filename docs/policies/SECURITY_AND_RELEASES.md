# Security and Release Policy

Status: Adopted baseline

## Security ownership

The security team owns vulnerability intake, severity coordination, disclosure timing, incident coordination, and security-policy exceptions. Project maintainers own remediation in their code. Release engineering owns trusted build and distribution infrastructure.

## Baseline controls

- Secure two-factor authentication is required for organization access.
- Default member privileges are minimal.
- OAuth applications and GitHub App installation are restricted.
- Fine-grained personal access tokens require approval and expire within the organization maximum.
- Workflow tokens are read-only by default and cannot approve pull requests.
- Actions are restricted and must be pinned to immutable revisions where supported.
- Self-hosted runners are not used without a documented isolation and lifecycle design.
- Secrets are scoped to the smallest repository, environment, and workflow surface.
- Private vulnerability reporting is preferred for security disclosures.

## Repository controls by criticality

### Low and moderate

- protect the default branch from deletion and force push where recovery remains possible;
- run deterministic tests and license checks appropriate to the project;
- keep dependencies and supported versions documented;
- publish releases from a repeatable process.

### High

All lower-tier controls, plus:

- two-person maintainer continuity;
- independent pull-request approval when reviewer capacity exists;
- required status checks with no unreviewed bypass path;
- dependency review, secret scanning, and static analysis appropriate to the stack;
- protected release environments and provenance-bearing builds when the plan supports them;
- documented restore and compromise response.

### Critical

All high-tier controls, plus:

- two independent release authorizers;
- isolated, ephemeral build infrastructure;
- verifiable provenance and signing identities protected from source maintainers acting alone;
- rehearsed incident response and recovery;
- an independent security review at least annually and after material trust-boundary change.

## Vulnerability handling

1. Acknowledge confidential reports without requiring public disclosure.
2. Limit details to people needed for triage and remediation.
3. Record affected versions, severity, exploitability, owners, decisions, and target dates.
4. Coordinate fixes, advisories, releases, and downstream notice.
5. Preserve reporter credit unless anonymity is requested or credit creates risk.
6. Publish a factual advisory when users need to act.
7. Review the incident for control improvements without blaming reporters or contributors.

## Release integrity

- Releases are produced from reviewed, version-controlled inputs.
- The release commit or tag is identifiable and immutable.
- Generated artifacts are reproducible or accompanied by provenance sufficient to identify the builder and inputs.
- Signing keys and publishing credentials are not stored in repositories or ordinary workflow logs.
- Release notes identify supported versions, security relevance, compatibility changes, and known limitations.
- Packages and containers are retired or marked unsupported when their source repository is deprecated or archived.

## Exceptions

An exception records scope, owner, reason, compensating controls, expiry, and reviewer. Security exceptions require security-team approval. Release-infrastructure exceptions require release-engineering approval. No exception is permanent by default.

