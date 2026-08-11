# Repository Lifecycle Policy

Status: Adopted

## Required classification

Every repository must have `lifecycle`, `criticality`, `support`, and `owner_team` organization properties before it is treated as active work.

## Lifecycle states

### Incubating

The purpose and architecture are still being validated. Compatibility and support are not promised unless a repository says otherwise.

Minimum requirements:

- named accountable team;
- license and public description;
- security and support routes;
- contribution and conduct expectations;
- no unsupported claim of production readiness.

### Active

The project accepts planned development and has an active roadmap.

Additional requirements:

- documented maintainer authority;
- protected default branch appropriate to current reviewer capacity;
- automated validation for release-relevant changes;
- dependency and vulnerability update process;
- release and deprecation policy.

### Maintenance

The project accepts security fixes and bounded corrective work, but not general feature development. The README and support guidance must state the maintenance scope.

### Deprecated

The project should not be selected for new deployments. The repository must identify the replacement or explain why none exists, state the final support date, and provide migration guidance where practical.

### Archived

The repository is read-only. Outstanding security, package, release, documentation, and transfer obligations must be resolved or explicitly recorded before archival.

## Criticality

- `low`: limited impact and easy replacement.
- `moderate`: meaningful user or contributor impact, but bounded recovery.
- `high`: important distribution, infrastructure, security, or downstream dependency.
- `critical`: compromise or prolonged failure could cause severe security, legal, financial, or ecosystem harm.

Criticality controls the required review, recovery, release, and incident practices. A repository must not reduce criticality merely to avoid a control.

## Support commitments

- `experimental`: evaluation only; no stability or response commitment.
- `community`: best-effort community maintenance without a guaranteed response time.
- `supported`: named maintainers, documented supported versions, security response process, release integrity controls, and at least two-person continuity.

## Transitions

The accountable project maintainers propose transitions. Governance confirms organization-wide metadata and minimum evidence. Security and legal-compliance must be consulted when their obligations are affected.

Promotion to `active` or `supported` requires evidence that the applicable controls exist. Demotion is allowed whenever capacity or risk changes and should be preferred over silently missing a commitment.

## Intake checklist

Before a new repository is made public or active, record:

- purpose, audience, and accountable team;
- original, forked, generated, or imported provenance;
- license, notices, trademarks, and dependency policy;
- data handled and security boundaries;
- build, test, release, package, and archival plan;
- support level and contributor path;
- naming collision, impersonation, and domain concerns;
- initial lifecycle and criticality.

## Staleness review

An active repository with no substantive maintainer activity for 90 days must be reviewed. The outcome can be continued active status with a recorded reason, maintenance, deprecation, transfer, or archival. Automated commits alone do not prove maintainer availability.

