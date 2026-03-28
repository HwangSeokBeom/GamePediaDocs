# Architecture Board Blueprint

## Purpose

This blueprint defines a single architecture board that can be recreated in Figma, FigJam, or Pencil. It is optimized for fast system explanation, interview walkthroughs, and ongoing documentation updates.

## Recommended Board Order

Lay out the board from left to right in this order:

1. Product / User Flow
2. iOS Client Architecture
3. Server Architecture
4. External Services
5. Environment Separation
6. Deployment Flow
7. Design References
8. Key Technical Decisions

Keep overview zones in the top half and supporting or reference zones in the bottom half.

## Zone 1: Product / User Flow

### Boxes To Include

- User personas or user entry point
- Launch / onboarding
- Authentication
- Game discovery
- Game detail
- Review creation / management
- Profile or account management

### Grouping

- Group user-facing flows in a single horizontal sequence.
- Keep optional paths, such as sign-in or review creation, as side branches.

### Arrows

- Use primary arrows for the main happy path from app launch to game interaction.
- Use secondary arrows for optional or gated actions such as login before review submission.

### Relationships To Visualize

- Which product actions require authentication
- Which screens are read-only versus user-owned content
- Where translated content or third-party data affects user experience

### Visual Emphasis

- Emphasize the two or three most important user journeys only.
- Make the sign-in boundary visually obvious because it connects product flow to backend auth architecture.

## Zone 2: iOS Client Architecture

### Boxes To Include

- App entry
- Coordinator layer
- Feature modules or scenes
- UIKit views / view controllers
- MVI state flow
- UseCase layer
- Repository layer
- Network layer
- Cache layer

### Grouping

- Group by architectural layer from top to bottom: presentation, domain, data.
- Place Coordinator beside or above feature scenes to show navigation ownership.

### Arrows

- Show navigation flow from Coordinator to feature scenes.
- Show unidirectional MVI flow from user input to action, reducer/store, state, and rendered view.
- Show request flow from UseCase to Repository to Network / Cache.

### Relationships To Visualize

- Coordinator owns navigation, not business logic.
- UseCases orchestrate domain logic.
- Repositories abstract remote and local data access.
- Cache short-circuits repeated reads where applicable.

### Visual Emphasis

- Highlight separation of concerns.
- Highlight the unidirectional state loop because it explains why the client remains maintainable at scale.

## Zone 3: Server Architecture

### Boxes To Include

- Auth Server
- Core Server
- Translation Server
- Shared or logical database boundary
- Redis cache
- Internal server-to-server communication

### Grouping

- Group services together under a "Backend Services" frame.
- Keep data stores beneath the services they support.

### Arrows

- App to Auth Server
- App to Core Server
- Core Server to Translation Server
- Services to database and Redis

### Relationships To Visualize

- Auth handles identity and token issuance.
- Core owns domain data and user-facing APIs.
- Translation supports localization concerns and caching.

### Visual Emphasis

- Make service boundaries clear.
- Keep responsibilities short and explicit inside or below each service box.

## Zone 4: External Services

### Boxes To Include

- IGDB API
- Twitch OAuth
- Apple Login
- Google Login

### Grouping

- Separate authentication providers from content/data providers.
- Place them to the right of internal servers so dependency direction remains obvious.

### Arrows

- Auth Server to Apple, Google, and Twitch OAuth
- Core Server to IGDB API

### Relationships To Visualize

- Which internal service owns each external dependency
- Which dependencies are on the critical path for login or data freshness

### Visual Emphasis

- Use a distinct visual style for third-party systems so they are never mistaken for internal services.

## Zone 5: Environment Separation

### Boxes To Include

- dev stack
- staging stack
- production stack
- iOS build variant or app target per environment
- service instances per environment
- database and Redis per environment

### Grouping

- Use three parallel columns or swimlanes, one per environment.
- Keep the same internal structure in each lane so comparisons are easy.

### Arrows

- Show promotion flow from dev to staging to production.
- Show environment-specific app builds talking only to matching backend stacks.

### Relationships To Visualize

- Isolation between environments
- Promotion path and validation path
- Which environment is used by developers, QA, and end users

### Visual Emphasis

- Emphasize production stability and staging parity.
- Avoid clutter by collapsing repeated infrastructure labels where possible.

## Zone 6: Deployment Flow

### Boxes To Include

- Source repositories
- CI or build pipeline
- Test / verification gate
- Deployment target per environment
- Release checkpoint or approval note

### Grouping

- Keep this as a simple linear pipeline below the environment zone.
- Separate client release flow from server deployment flow only if the board gets crowded.

### Arrows

- Repository to CI
- CI to dev
- dev validated to staging
- staging approved to production

### Relationships To Visualize

- Which artifacts are promoted
- Where approvals or manual checks exist
- Where rollout or rollback decisions happen

### Visual Emphasis

- Emphasize that production release is a controlled promotion, not a direct jump from development.

## Zone 7: Design References

### Boxes To Include

- Pencil wireframes
- Figma screens
- FigJam board
- Design system / component notes

### Grouping

- Keep design references in a compact support zone, not the main architecture path.
- Group sources of truth together with short descriptions.

### Arrows

- Link design references to the product flow and iOS client zones.

### Relationships To Visualize

- Which design artifact is used for wireframing versus final presentation versus collaborative system mapping

### Visual Emphasis

- Emphasize traceability from design artifacts to implementation docs without overpowering the technical architecture.

## Zone 8: Key Technical Decisions

### Boxes To Include

- UIKit over SwiftUI
- Combine + MVI
- Coordinator pattern
- UseCase / Repository layering
- Multi-service backend split
- Translation caching strategy

### Grouping

- Use small note cards or decision tiles in a dedicated row.
- Keep each decision to one line of rationale and one line of tradeoff.

### Arrows

- Link decisions back to the client or server zone they affect.

### Relationships To Visualize

- Why the architecture looks the way it does
- Which choices improve maintainability, testing, or separation of concerns

### Visual Emphasis

- Make rationale more prominent than implementation detail.
- This zone should read like a fast interview aid rather than a deep ADR index.
