# ADR-001: Use Rust as the Primary Programming Language

- Status: Accepted
- Date: 2026-10-01

## Context

The project requires rebuilding an item evaluation, ranking, and export CLI application from scratch. The system must support flexible dynamic attributes, custom weighted scoring models, and multi-format export capability (JSON, Markdown, Excel). 

Key technical requirements for the new architecture include:
1. High execution performance and low memory footprint for instant startup times.
2. Rich interactive Terminal User Interface (TUI) capabilities.
3. Easy cross-platform distribution without requiring heavy runtime environments (e.g., JRE).
4. Long-term architectural flexibility to target desktop GUIs (via Tauri) or web platforms (via WebAssembly) while sharing a single core domain codebase.

## Decision

The project use **Rust** as the core programming language for the application, combined with **Ratatui** + **Crossterm** for the TUI layer and an embedded database (e.g., Redb / SQLite with JSON) for local storage.

The application core will follow Hexagonal Architecture principles to strictly separate the evaluation engine, sorting logic, and export formats from the UI presentation and storage adapters.

## Alternatives Considered

### Alternative A: Java (Pure / Maven) or Quarkus + Picocli
* **Pros:** Reuses existing knowledge from the previous project iteration; strong ecosystem for file parsing and JSON manipulation. Quarkus allows GraalVM native compilation to reduce startup latency.
* **Cons:** JVM memory consumption is relatively high. Building rich, interactive TUI interfaces in Java is limited compared to modern terminal ecosystems. Desktop GUI options (JavaFX) carry high memory overhead and are cumbersome to distribute across modern operating systems like ChromeOS.

### Alternative B: Go (Golang) + Bubbletea
* **Pros:** Fast execution speed, quick compilation times, simple concurrency model, and strong cross-platform native binary compilation. Excellent TUI ecosystem with `bubbletea`.
* **Cons:** Dynamic typing features rely heavily on `interface{}` or reflection, making complex domain models with heterogeneous attribute types less type-safe compared to Rust's pattern matching and algebraic data types (`enum`). Reusability targeting WebAssembly for browser deployment is less mature than Rust's Wasm ecosystem.

## Consequences

### Positive

- **Performance & Zero-Cost Abstractions:** Sub-millisecond startup times and negligible RAM usage (<20MB baseline for TUI).
- **Type Safety & Data Integrity:** Rust's strict compiler, ownership model, and rich algebraic enum types simplify handling heterogeneous item attributes without dynamic runtime errors.
- **Modern TUI Ecosystem:** Direct access to `ratatui` for building responsive, visually engaging terminal interfaces.
- **Future-Proof Reusability:** The hexagonal core domain written in Rust can be reused without modification for a desktop GUI (Tauri) or compiled to WebAssembly (Wasm) for a browser/PWA deployment.
- **Self-Contained Binaries:** Easy cross-compilation into small native executables with no external runtime dependencies.

### Negative

- **Steeper Learning Curve:** Development velocity may initially be slower due to strict borrow checker rules and lifetime management during domain modeling.
- **Compilation Overhead:** Long initial compilation times compared to dynamic or simple compiled languages.
- **Ecosystem Specifics:** Handling dynamic data schemas requires careful usage of `serde` attributes and custom serialization traits.

## References
- [The Rust Programming Language](https://doc.rust-lang.org/book/title-page.html)
- [Ratatui Framework Documentation](https://docs.rs/ratatui/latest/ratatui/)
- [Serde](https://docs.rs/serde/latest/serde/)
- [Hexagonal Architecture (Ports & Adapters) by Alistair Cockburn](https://alistair.cockburn.us/hexagonal-architecture/)
