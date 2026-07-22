# Security Policy

## Supported Versions

This crate is pre-1.0. Only the latest version published on
[crates.io](https://crates.io/crates/thesportsdbcom) receives security fixes. Please upgrade before
reporting an issue to confirm it still reproduces.

## Reporting a Vulnerability

Do not open a public issue for security vulnerabilities.

Report privately via GitHub's
[Security Advisories](https://github.com/pilgrimagesoftware/thesportsdbcom.rs/security/advisories/new).
This keeps the report confidential until a fix is released.

Include, where possible:

- Affected version(s)
- A minimal reproduction or proof of concept
- Impact (e.g. what an attacker can do, what data or systems are exposed)

You should receive an initial response as soon as possible. If the report is confirmed, we'll work with
you on a fix and coordinate a disclosure timeline before any public advisory is published. Reporters are
credited in the advisory unless they ask to remain anonymous.

## Scope

This policy covers the `thesportsdbcom` crate: the TheSportsDB API client and its response model
types/`serde` impls.

Note what this crate explicitly does *not* cover, since a report against these is really about a
different part of the chain:

- The TheSportsDB API service itself (`www.thesportsdb.com`) — that's operated by TheSportsDB,
  not this org.
- Consumers that supply their own transport instead of this crate's HTTP client — this crate
  only validates the shape of the bytes it's handed via `serde`; transport security is the
  consumer's responsibility.

Vulnerabilities in dependencies should be reported upstream; if a dependency issue affects this crate
directly (e.g. no fix available, requires a workaround here), report it here as well.
