# System Diagrams

Starter diagrams for architecture communication. These are intentionally lightweight drafts that can be refined later in Figma, FigJam, or Pencil.

## Overall System Architecture

```mermaid
flowchart LR
    User[User] --> App[iOS App]

    subgraph Backend[GamePedia Backend]
        Auth[Auth Server]
        Core[Core Server]
        Translation[Translation Server]
    end

    subgraph Data[Data Layer]
        DB[(Database)]
        Redis[(Redis)]
    end

    subgraph External[External Services]
        IGDB[IGDB API]
        Twitch[Twitch OAuth]
        Apple[Apple Login]
        Google[Google Login]
    end

    App --> Auth
    App --> Core
    Core --> Translation

    Auth --> DB
    Core --> DB
    Translation --> Redis

    Core --> IGDB
    Auth --> Twitch
    Auth --> Apple
    Auth --> Google
```

This view is the fastest way to explain the system boundary. The iOS app talks to the Auth Server for identity, the Core Server for domain features, and the Core Server can depend on the Translation Server and external providers as needed.

## iOS Client Architecture

```mermaid
flowchart TD
    User[User Interaction] --> View[UIKit View / ViewController]

    subgraph Navigation[Navigation]
        Coordinator[Coordinator]
    end

    subgraph Presentation[Presentation Layer]
        Intent[Intent / Action]
        Store[Store / Reducer / ViewModel]
        State[View State]
    end

    subgraph Domain[Domain Layer]
        UseCase[UseCase]
    end

    subgraph Data[Data Layer]
        Repository[Repository]
        Network[Network Layer]
        Cache[Cache Layer]
    end

    subgraph Remote[Remote Services]
        Auth[Auth Server]
        Core[Core Server]
        Translation[Translation Server]
    end

    Coordinator --> View
    View --> Intent
    Intent --> Store
    Store --> State
    State --> View

    Store --> UseCase
    UseCase --> Repository
    Repository --> Network
    Repository <-->|read / write| Cache

    Network --> Auth
    Network --> Core
    Network --> Translation
```

This diagram shows the client as layered and unidirectional. Coordinators own navigation, MVI handles state flow, UseCases hold app-specific business logic, and Repositories hide the details of remote and cached data access.

## Environment Separation

```mermaid
flowchart LR
    Repo[Source Repositories] --> CI[CI / Build Pipeline]
    CI --> DevGate[Deploy to dev]
    DevGate --> StageGate[Promote to staging]
    StageGate --> ProdGate[Release to production]

    subgraph Dev[dev]
        DevApp[iOS Dev Build]
        DevAuth[Auth Server]
        DevCore[Core Server]
        DevTranslation[Translation Server]
        DevDB[(Database)]
        DevRedis[(Redis)]
        DevApp --> DevAuth
        DevApp --> DevCore
        DevCore --> DevTranslation
        DevAuth --> DevDB
        DevCore --> DevDB
        DevTranslation --> DevRedis
    end

    subgraph Staging[staging]
        StageApp[iOS Staging Build]
        StageAuth[Auth Server]
        StageCore[Core Server]
        StageTranslation[Translation Server]
        StageDB[(Database)]
        StageRedis[(Redis)]
        StageApp --> StageAuth
        StageApp --> StageCore
        StageCore --> StageTranslation
        StageAuth --> StageDB
        StageCore --> StageDB
        StageTranslation --> StageRedis
    end

    subgraph Production[production]
        ProdApp[iOS Production Build]
        ProdAuth[Auth Server]
        ProdCore[Core Server]
        ProdTranslation[Translation Server]
        ProdDB[(Database)]
        ProdRedis[(Redis)]
        ProdApp --> ProdAuth
        ProdApp --> ProdCore
        ProdCore --> ProdTranslation
        ProdAuth --> ProdDB
        ProdCore --> ProdDB
        ProdTranslation --> ProdRedis
    end

    DevGate --> DevApp
    DevGate --> DevAuth
    DevGate --> DevCore
    DevGate --> DevTranslation

    StageGate --> StageApp
    StageGate --> StageAuth
    StageGate --> StageCore
    StageGate --> StageTranslation

    ProdGate --> ProdApp
    ProdGate --> ProdAuth
    ProdGate --> ProdCore
    ProdGate --> ProdTranslation
```

This draft makes the environment boundary explicit. Each environment has its own app build and backend stack, while promotion flows move in one direction from dev to staging to production.

## Authentication Flow

```mermaid
sequenceDiagram
    actor User
    participant App as iOS App
    participant Auth as Auth Server
    participant Provider as Apple / Google / Twitch
    participant DB as Database
    participant Core as Core Server

    User->>App: Tap sign in
    App->>Auth: Start login request
    Auth->>Provider: OAuth / identity exchange
    Provider-->>Auth: Identity payload
    Auth->>DB: Find or create user
    DB-->>Auth: User record
    Auth-->>App: JWT + refresh token
    App->>Core: Authorized API request with JWT
    Core->>Auth: Verify token or claims
    Auth-->>Core: Token validation result
    Core-->>App: User-scoped response
```

This flow explains the separation between authentication and application data. The Auth Server owns login and token issuance, while the Core Server trusts verified identity to serve user-specific features.
