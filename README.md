<div align="center">

# Kriterion Engine ⚙️📊
<!--<picture>
    <source media="(prefers-color-scheme: dark)"
            srcset="./docs/img/kriterion-dark.png">
    <source media="(prefers-color-scheme: light)"
            srcset="./docs/img/kriterion-light.png">
    <img src="./docs/img/kriterion-light.png"
        alt="Kriterion Banners">
        </picture> -->
  <br>
  <p>
    <a href="https://github.com/dnbsammie/kriterion-engine/issues">
      <img src="https://img.shields.io/github/issues/dnbsammie/kriterion-engine" alt="Issues">
    </a>
    <a href="https://github.com/dnbsammie/kriterion-engine/stargazers">
      <img src="https://img.shields.io/github/stars/dnbsammie/kriterion-engine" alt="Stars">
    </a>
    <a href="https://github.com/dnbsammie/kriterion-engine/blob/main/LICENSE">
      <img src="https://img.shields.io/github/license/dnbsammie/kriterion-engine" alt="License">
    </a>
  </p>
</div>

## About The Project

<blockquote style="border-left: 4px solid #00c8ff; padding-left: 10px; color: #fafafa;">
    Kriterion Engine is an open-source Rust engine for working with structured
    evaluation tables.
</blockquote>

### Tech Stack

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=bash,github,githubactions,md,html,rust,&theme=dark" alt="icons"/>
  </a>
</p>

## Status

Early development.

## Goals

- Load evaluation tables
- Edit table items
- Sort and organize data
- Apply evaluation rules
- Export tables to different formats

## Key Features

- **Dynamic Schema Validation:** No hardcoded fields. Define your entities, properties, grading scales, and weights dynamically via configuration files.

- **Multi-Format Ingestion & Export:** Read from and export to JSON, Markdown, and Excel (.xlsx) effortlessly.

- **Multi-Modal Interfaces:** Consume the engine locally via a desktop client (JavaFX), through a modern web interface (Vite/React), or programmatically via a REST API.

- **AI Agent Ready (MCP):** Expose tools natively so Large Language Models (like Claude or custom agents via Google AI Studio) can query, rank, and organize your matrices on the fly.

- **Advanced Scoring Engine:** Configurable weighting algorithms to generate precise tier lists and decision matrices based on custom multidimensional criteria.

## Requirements:

- Rust stable
- Cargo

Run:
```sh
cargo run
```
Test:
```sh
cargo test
```
Check:
```sh
cargo check
```
Lint:
```sh
cargo clippy --all-targets --all-features -- -D warnings
```
Format:
```sh
cargo fmt
```
---
