# Design System And References

## Document Purpose

Track the design sources of truth, component naming rules, handoff expectations, and architecture-to-design mapping used across GamePedia documentation and visual boards.

## Design Source Of Truth

| Artifact | Tool | Purpose | Owner |
| --- | --- | --- | --- |
| Wireframes | Pencil | Early structure, screen flow, low-fidelity validation | [Placeholder] |
| UI design | Figma | Final screen design and polished component references | [Placeholder] |
| Architecture board | FigJam / Figma | System relationships, flows, and interview visuals | [Placeholder] |

## Design Principles

- Keep visual artifacts aligned with documented architecture boundaries.
- Use the same naming for screens, features, and services across design and documentation.
- Prefer lightweight annotations and links over dense diagram text.

## Component Taxonomy

### Global Components

- Navigation shell
- Search input
- Game card
- Review card
- Profile summary
- Loading / empty / error states

### Feature-Level Components

- Discovery feed components
- Game detail sections
- Review composer elements
- Authentication entry points

[Placeholder: replace with the actual component inventory once design files are audited.]

## Screen Inventory Mapping

| Product Area | Primary Screens | Related Client Doc | Related Board Zone |
| --- | --- | --- | --- |
| Discovery | [Placeholder] | `docs/03-client-ios/client-architecture.md` | Product / User Flow |
| Authentication | [Placeholder] | `docs/04-server/server-architecture.md` | Product / User Flow, External Services |
| Reviews | [Placeholder] | `docs/03-client-ios/client-architecture.md` | Product / User Flow |
| Profile | [Placeholder] | `docs/03-client-ios/client-architecture.md` | Product / User Flow |

## Naming Conventions

- Screen names should match feature names used in client documentation.
- Service names should match backend documentation exactly.
- Environment labels should always use `dev`, `staging`, and `production`.
- Use one canonical label for each external integration across all artifacts.

## Architecture Board Inputs

When creating or updating the architecture board, gather:

- the latest product flow
- the current client architecture summary
- the current server/service boundary summary
- the current environment model
- the latest technical decision highlights

## Handoff Checklist

- Confirm current design links and owners.
- Confirm screen naming is still consistent with the iOS app.
- Confirm architecture board labels match the latest documentation.
- Export presentation-ready images to `assets/diagrams` as needed.

## Open Items

- [Placeholder: design file URLs]
- [Placeholder: design review cadence]
- [Placeholder: component ownership and review process]
