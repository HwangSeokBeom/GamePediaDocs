# Architecture Decisions

Use this document as the index and starter template for architecture decision records.

## How To Use This Section

- Add a new decision entry when a major technical choice changes system shape, ownership, or tradeoffs.
- Keep the title outcome-focused.
- Record the reason, the decision, and the consequences.
- Link to deeper documents or board zones where useful.

## Status Legend

- Proposed
- Accepted
- Superseded
- Deprecated

## Decision Index

| ID | Title | Status | Date | Related Area |
| --- | --- | --- | --- | --- |
| ADR-001 | [Placeholder: UIKit as primary client UI framework] | Proposed | [YYYY-MM-DD] | Client |
| ADR-002 | [Placeholder: Combine + MVI state model] | Proposed | [YYYY-MM-DD] | Client |
| ADR-003 | [Placeholder: Split backend into Auth / Core / Translation services] | Proposed | [YYYY-MM-DD] | Server |

## ADR Template

### ADR-[Number]: [Decision Title]

#### Status

[Proposed | Accepted | Superseded | Deprecated]

#### Date

[YYYY-MM-DD]

#### Context

[What problem or pressure led to this decision?]

#### Decision

[What was chosen?]

#### Rationale

[Why was this option selected over alternatives?]

#### Consequences

- [Positive impact]
- [Tradeoff or risk]
- [Follow-up work]

#### Related Documents

- [Placeholder: link to overview or architecture docs]
- [Placeholder: link to diagrams or board sections]

## Candidate Decisions To Capture Soon

- UIKit versus alternative UI approaches
- Combine + MVI as the client state architecture
- Coordinator pattern for navigation ownership
- UseCase / Repository layering in the iOS app
- Separate Auth, Core, and Translation servers
- Translation caching with Redis
