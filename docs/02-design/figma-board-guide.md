# Figma / FigJam / Pencil Board Guide

## Recommended Frame Layout

Use one main board frame with a wide horizontal layout.

- Top row: Product / User Flow, iOS Client Architecture, Server Architecture, External Services
- Bottom row: Environment Separation, Deployment Flow, Design References, Key Technical Decisions
- Keep a small title and legend area in the upper-left corner

## Left-To-Right Structure

Build the board so the story reads left to right:

1. What the user does
2. How the iOS app is structured
3. Which backend services handle the work
4. Which external systems the platform depends on
5. How environments are separated
6. How changes move toward release

This order works well for both interviews and engineering onboarding because the viewer starts with product value before diving into implementation detail.

## Color Grouping Suggestions

| Group | Suggested Color Direction | Notes |
| --- | --- | --- |
| Client | Blue | Use for iOS app, client layers, and navigation/state flow |
| Server | Green | Use for Auth, Core, Translation, and internal server notes |
| External | Orange | Use for third-party APIs and login providers |
| Infra | Gray | Use for environments, deployment paths, database, Redis, and operational notes |
| Design | Pink | Use for Figma, FigJam, Pencil, and design-system references |

Keep fills muted and rely on strong headers so the board remains readable when exported.

## Shape Suggestions

| Element Type | Recommended Shape |
| --- | --- |
| Service | Rounded rectangle |
| Database | Cylinder |
| Redis / cache | Rounded rectangle with dashed border or cache icon |
| External API / provider | Hexagon or outlined rectangle |
| User / actor | Circle or avatar card |
| Decision note | Sticky note or callout card |
| Group / zone | Large frame with labeled header |

## Readability Rules

- Keep each box to a short title and one supporting line at most.
- Avoid crossing arrows when a zone can be repositioned instead.
- Use consistent iconography only if it adds clarity.
- Repeat patterns between environments so comparison is instant.
- Split a crowded zone into a linked detail board rather than shrinking everything.

## Linking Strategy

Use the architecture board as an entry point, not the full knowledge base.

- Link each major zone to its detailed markdown document.
- Put long explanations in docs, not inside boxes.
- Use callout notes only for high-value context such as tradeoffs or warnings.
- Export clean board snapshots to `assets/diagrams` and keep edit-heavy work in the design tool.

## Suggested Legend

- Solid arrow: primary request or dependency flow
- Dashed arrow: optional, indirect, or validation flow
- Thick border: current focus area
- Neutral note: explanation
- Highlight note: decision or risk
