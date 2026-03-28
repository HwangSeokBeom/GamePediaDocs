# Environment Overview

## Document Purpose

Document how GamePedia is separated across `dev`, `staging`, and `production`, including expected usage, deployment flow, configuration boundaries, and operational considerations.

## Environment Summary

| Environment | Primary Purpose | Primary Users | Stability Expectation |
| --- | --- | --- | --- |
| dev | Active development and rapid validation | Developers | Low to medium |
| staging | Integrated verification before release | Internal QA, reviewers, stakeholders | Medium to high |
| production | Live service for end users | Public users | Highest |

## Stack Per Environment

Each environment should contain its own logical stack:

- iOS app build or target configuration
- Auth Server instance
- Core Server instance
- Translation Server instance
- database
- Redis

## Endpoint Matrix

| Component | dev | staging | production |
| --- | --- | --- | --- |
| iOS bundle / build config | [Placeholder] | [Placeholder] | [Placeholder] |
| Auth Server base URL | [Placeholder] | [Placeholder] | [Placeholder] |
| Core Server base URL | [Placeholder] | [Placeholder] | [Placeholder] |
| Translation Server base URL | [Placeholder] | [Placeholder] | [Placeholder] |
| Database identifier | [Placeholder] | [Placeholder] | [Placeholder] |
| Redis identifier | [Placeholder] | [Placeholder] | [Placeholder] |

## Promotion Flow

1. Validate changes in `dev`.
2. Promote tested builds and deployments to `staging`.
3. Run integrated QA and release checks in `staging`.
4. Release approved artifacts to `production`.

## Configuration Rules

- Do not share production secrets with lower environments.
- Keep environment naming consistent across app config, servers, CI, and diagrams.
- Document all environment-specific values in one maintained location.
- Record ownership for secret rotation and deployment approval.

## Operational Concerns

### Monitoring

- [Placeholder: log aggregation]
- [Placeholder: metrics and uptime checks]
- [Placeholder: alerting path]

### Release Safety

- [Placeholder: rollback strategy]
- [Placeholder: canary or phased rollout if applicable]
- [Placeholder: post-deploy smoke tests]

### Data Management

- [Placeholder: database backup policy]
- [Placeholder: staging data policy]
- [Placeholder: Redis persistence or eviction expectations]

## Environment Risks

- Drift between staging and production configuration
- Shared credentials across environments
- Missing ownership for deployment approval
- Incomplete smoke tests before production release

## Related Documents

- [Project Overview](../00-overview/project-overview.md)
- [System Diagrams](../00-overview/system-diagrams.md)
- [Release Checklist](../06-quality/release-checklist.md)
