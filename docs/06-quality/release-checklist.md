# Release Checklist

Use this checklist before promoting GamePedia changes into production. Keep it short, operational, and reusable.

## Release Metadata

- Release name:
- Release date:
- Release owner:
- Included repositories:
- Related tickets / issues:

## Pre-Release Readiness

- [ ] Scope is confirmed and frozen for this release.
- [ ] Related docs are updated in `GamePediaDocs`.
- [ ] Known risks are documented.
- [ ] Rollback owner is identified.

## iOS Client Checks

- [ ] Target build configuration is correct.
- [ ] Authentication flow is smoke-tested.
- [ ] Core user flows are validated on target devices.
- [ ] Error, loading, and empty states were reviewed for impacted screens.
- [ ] App versioning / release notes are prepared.

## Server Checks

- [ ] Auth Server changes are deployed to the correct environment.
- [ ] Core Server changes are deployed to the correct environment.
- [ ] Translation Server changes are deployed to the correct environment.
- [ ] Backward compatibility risks are reviewed.
- [ ] External dependency changes are verified.

## Infrastructure Checks

- [ ] Environment variables and secrets are correct.
- [ ] Database migration status is confirmed.
- [ ] Redis or cache behavior is verified if relevant.
- [ ] Monitoring and alerts are enabled for changed paths.

## QA Validation

- [ ] dev validation completed.
- [ ] staging validation completed.
- [ ] Regression checklist completed.
- [ ] Release blocker list reviewed with stakeholders.

## Production Release Gate

- [ ] Final approval received.
- [ ] Release window confirmed.
- [ ] Rollback steps reviewed and accessible.
- [ ] On-call or responsible engineer is available during rollout.

## Post-Release Checks

- [ ] Production smoke tests completed.
- [ ] Authentication verified in production.
- [ ] Critical user flows verified in production.
- [ ] Error monitoring reviewed after release.
- [ ] Release outcome documented.

## Rollback Notes

- Rollback trigger:
- Rollback owner:
- Rollback steps:
- Communication channel:
