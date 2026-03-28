# GamePediaDocs

System-level documentation for the GamePedia platform.

This repository is intentionally documentation-only. It exists to explain the product, architecture, design references, infrastructure boundaries, quality process, and technical decisions across the GamePedia ecosystem without mixing in application source code.

## Goals

- Understand the entire system architecture at a glance.
- Support portfolio and interview walkthroughs with clear, visual documentation.
- Keep client, server, design, infrastructure, and quality docs separated by concern.
- Provide a stable source of truth for Figma, FigJam, and Pencil architecture boards.

## Recommended Reading Order

1. [Project Overview](docs/00-overview/project-overview.md)
2. [System Diagrams](docs/00-overview/system-diagrams.md)
3. [Architecture Board Blueprint](docs/00-overview/architecture-board-blueprint.md)
4. [Client Architecture](docs/03-client-ios/client-architecture.md)
5. [Server Architecture](docs/04-server/server-architecture.md)
6. [Environment Overview](docs/05-infra/environment-overview.md)
7. [Architecture Decisions](docs/07-decisions/architecture-decisions.md)

## Repository Map

| Path | Purpose |
| --- | --- |
| `docs/00-overview` | Entry-point material for system summary, diagrams, and execution plan. |
| `docs/01-product` | Product scope, user journeys, and feature-level documentation. |
| `docs/02-design` | Design references, board-building rules, and handoff documentation. |
| `docs/03-client-ios` | iOS app architecture, module boundaries, and client-side flows. |
| `docs/04-server` | Server responsibilities, service interactions, and integration boundaries. |
| `docs/05-infra` | Environments, deployment paths, configuration, and operational view. |
| `docs/06-quality` | Release checklists, QA process, and verification standards. |
| `docs/07-decisions` | Architecture decision records and major tradeoff history. |
| `assets/diagrams` | Exported diagrams, board snapshots, and presentation-ready visuals. |
| `assets/images` | Screenshots, supporting visuals, and reference images. |
| `references` | Cross-repository references and external documentation pointers. |

## Folder Tree

```text
.
├── README.md
├── assets
│   ├── diagrams
│   └── images
├── docs
│   ├── 00-overview
│   │   ├── architecture-board-blueprint.md
│   │   ├── execution-plan.md
│   │   ├── project-overview.md
│   │   └── system-diagrams.md
│   ├── 01-product
│   │   └── product-scope.md
│   ├── 02-design
│   │   ├── design-system.md
│   │   └── figma-board-guide.md
│   ├── 03-client-ios
│   │   └── client-architecture.md
│   ├── 04-server
│   │   └── server-architecture.md
│   ├── 05-infra
│   │   └── environment-overview.md
│   ├── 06-quality
│   │   └── release-checklist.md
│   └── 07-decisions
│       └── architecture-decisions.md
└── references
    └── repositories.md
```

## Documentation Principles

- Keep one primary concern per document.
- Prefer links to deeper docs instead of growing overview pages indefinitely.
- Store rendered diagram exports in `assets/diagrams` and keep source board files in the design tool.
- Record major architecture choices in `docs/07-decisions`.
- Use placeholders until a detail is confirmed rather than guessing.

## Related Repositories

See [references/repositories.md](references/repositories.md) for the current repository map across the GamePedia system.

## Board Resources

- [Architecture Board Blueprint](docs/00-overview/architecture-board-blueprint.md)
- [Figma / FigJam / Pencil Board Guide](docs/02-design/figma-board-guide.md)
- [System Diagrams](docs/00-overview/system-diagrams.md)
