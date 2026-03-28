# iOS Client Architecture

## Document Purpose

Describe the internal structure of the GamePedia iOS client so readers can understand navigation, state flow, business logic boundaries, data access, and integration points without reading source code.

## Technology Summary

| Area | Current Approach |
| --- | --- |
| UI framework | UIKit |
| State handling | Combine + MVI |
| Navigation | Coordinator pattern |
| Domain organization | UseCase layer |
| Data access | Repository layer |
| Platforms | [Placeholder: iOS version support] |

## Architectural Goals

- Keep navigation separate from feature logic.
- Keep state flow explicit and traceable.
- Isolate domain logic from transport and persistence details.
- Make remote and cached data access replaceable behind repositories.

## Layer Overview

### Presentation Layer

- UIKit views and view controllers
- View state rendering
- User intents or actions
- MVI store / reducer / view model responsibilities

### Navigation Layer

- App coordinator
- Feature coordinators
- Route ownership and screen transitions

### Domain Layer

- UseCases for feature-specific business rules
- Input / output contracts for feature orchestration

### Data Layer

- Repositories as the abstraction boundary
- Network layer for server communication
- Cache layer for local or temporary data reuse

## Typical Request Flow

1. A user action occurs in a UIKit screen.
2. The action is transformed into an MVI intent.
3. The store or view model updates state and triggers a UseCase if needed.
4. The UseCase calls the relevant Repository.
5. The Repository resolves data through Network and/or Cache.
6. The resulting domain data is converted into view state.
7. The screen renders the updated state.

## Navigation Model

| Concern | Expected Owner |
| --- | --- |
| App launch routing | App coordinator |
| Authentication flow | [Placeholder: auth coordinator or equivalent] |
| Main tab or root navigation | [Placeholder] |
| Feature detail flow | Feature-specific coordinator |
| Modal presentation rules | Coordinator-owned where possible |

## MVI State Flow

### Inputs

- User interaction
- Lifecycle events
- Async completion from UseCases

### Processing

- Intent mapping
- State reduction
- Side-effect triggering through UseCases

### Outputs

- View state updates
- Loading / error / empty states
- Navigation events delegated to coordinators

## Data Boundaries

| Dependency | Typical Responsibility |
| --- | --- |
| Auth Server | Login, token refresh, authenticated identity |
| Core Server | Game data, reviews, profile-related features |
| Translation Server | Multi-language content support |
| Local cache | Reused responses, temporary persistence, performance support |

## Feature Inventory

| Feature | Coordinator | UseCase | Repository | Notes |
| --- | --- | --- | --- | --- |
| Authentication | [Placeholder] | [Placeholder] | [Placeholder] | [Placeholder] |
| Discovery | [Placeholder] | [Placeholder] | [Placeholder] | [Placeholder] |
| Game Detail | [Placeholder] | [Placeholder] | [Placeholder] | [Placeholder] |
| Review Flow | [Placeholder] | [Placeholder] | [Placeholder] | [Placeholder] |
| Profile | [Placeholder] | [Placeholder] | [Placeholder] | [Placeholder] |

## Error Handling And Resilience

- Define where transport errors are converted into user-facing states.
- Document token expiration handling.
- Document retry rules and offline behavior.
- Document fallback behavior when translation is unavailable.

## Observability Hooks

- [Placeholder: analytics events]
- [Placeholder: logging strategy]
- [Placeholder: crash reporting]

## Open Questions

- [Placeholder: module boundaries still under discussion]
- [Placeholder: cache persistence strategy]
- [Placeholder: feature ownership map]
