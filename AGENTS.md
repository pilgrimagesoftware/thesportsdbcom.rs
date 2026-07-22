# AGENTS.md

This file provides guidance to Claude Code (claude.ai/code), Codex (openai.com/codex/), GitHub
Copilot (copilot.github.com), and other models when working with code in this repository.

## About This Project

This is a Rust client library for the [TheSportsDB API](https://www.thesportsdb.com/api.php),
which surfaces data about sports leagues, teams, players, and events across a wide range of
sports.

The crate is published to [crates.io](https://crates.io/crates/thesportsdbcom) and documented on
[docs.rs](https://docs.rs/thesportsdbcom).

## Repository

- **GitHub**: https://github.com/pilgrimagesoftware/thesportsdbcom.rs
- **Crate name**: `thesportsdbcom`
- **Minimum Rust version**: pinned in `Cargo.toml`'s `rust-version`; toolchain version resolved
  via `rust-toolchain.toml` (`stable` + `rustfmt`/`clippy`)

## Branches and Workflow

- `develop` is the source of truth for active development (Git Flow).
- Feature branches are cut from `develop` and merged back via pull request.
- `master` tracks released, published versions; nothing is committed here directly.
- Releases are automated via `git-cliff` and Conventional Commits — see
  [RELEASING.md](RELEASING.md). **Squash-merging a PR must preserve the original commit's
  Conventional Commits type/breaking marker** (`gh pr merge <n> --squash --subject "feat!:
  ..."`), or the release automation silently under-bumps the version.

## Coding Conventions

- All public items **must** have doc comments (`///`). The crate enables `#![warn(missing_docs)]`.
- Follow `#![warn(rust_2018_idioms)]`; avoid deprecated Rust 2015 idioms.
- Clippy is configured via `clippy.toml`. Run `cargo clippy` before committing and resolve all
  warnings that are not explicitly suppressed in `lib.rs`.
- YAML files use the `.yaml` extension (not `.yml`).
- Commit messages follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
  format, e.g. `feat(team): add get-by-id endpoint` — `git-cliff` reads these to generate the
  changelog and compute the release version; see [RELEASING.md](RELEASING.md).

## Implementation Status

This crate is scaffolding only — no API client has been implemented yet. See
`src/lib.rs` for the crate root; new modules should follow the pattern established by sibling
SDK crates in the org (e.g. `openligadb`), one model per file under `src/models/`, with query
functions returning `Result` and doc comments on every public item.

## Running Checks Locally

```bash
# Build
cargo build

# Run tests
cargo test --all-features --workspace

# Lint
cargo clippy --all-targets --all-features -- -D warnings

# Format
cargo fmt --check

# Test without default features
cargo test --no-default-features

# Doc tests and doc build
cargo test --doc
RUSTDOCFLAGS="-D warnings" cargo doc --no-deps
```
