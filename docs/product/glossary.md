# Glossary

Terms used across the Wishlist documentation.

## Documentation

### ADR (Architecture Decision Record)

A short, append-only record of _why_ a significant technical decision was made: its context, the decision and its consequences. A changed decision gets a new ADR that supersedes the old one. Stored in `adr/` as `NNNN-name.md`.

### ASD (Application Specification Document)

A living document that describes _what_ a single feature should do: the problem, user stories, acceptance criteria and flows. Changes through pull requests. Stored in `asd/` as `ASD-NNN-name.md`.

### Acceptance criteria

Testable conditions a feature must meet to be considered done, written as _Given / When / Then_.

## Versions & tooling

### latest

The production version of the docs, built from the `main` branch. The default version of the site.

### dev

The work-in-progress version of the docs, built from the `dev` branch.

### mike

The tool that publishes multiple versions (`latest`, `dev`) of the MKDocs docs side by side.
