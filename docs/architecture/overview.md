# Architecture Overview

Kriterion-Engine is an evaluation engine focused on manipulating, evaluating,
ordering, and exporting tabular data.

The system is designed around a separation between the domain model, application
logic, input/output boundaries, and the terminal user interface.

## Architectural goals

- Keep domain logic independent from the TUI.
- Make table manipulation deterministic and testable.
- Separate data representation from presentation.
- Support multiple input and output formats.
- Keep infrastructure concerns isolated from the core domain.
- Allow the user interface to evolve without changing evaluation logic.

## High-level architecture

The application is organized into layers:

1. Domain
2. Application
3. Infrastructure
4. Presentation

The exact module boundaries are defined by the implementation and documented as
the architecture evolves.
