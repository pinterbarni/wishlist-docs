# Wishlist Docs

Specs, architecture, and decision records for [Wishlist app]: a shared wishlist and gift-coordination platform. This repository is the single source of truth for documentation that spans the backend API and the web client.

## Read the docs

- **Live:**  [documentation for the current release](https://pinterbarni.github.io/wishlist-docs/)
- **Dev:** [work in progress for the upcoming release](https://pinterbarni.github.io/wishlist-docs/dev/)

## What's inside

- **Product:** vision and glossary
- **ASDs:** Application Specification Documents, describing what each feature does
<!-- - **Architecture:** system overview, data model, authentication and internationalization -->
- **ADRs:** Architecture Decision Records, explaining why key decisions were made
<!-- - **Operations:** environments, deployment and runbook
- **Contributing:** workflow and writing conventions -->

## Run locally

Requires Python 3. (obv.)

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Preview the latest version

```bash
mkdocs serve
```

Shows the site as it looks on **latest**: standard header, no banner.

### Preview the dev version

```bash
DOCS_ENV=dev mkdocs serve
```

Shows the site as it looks on **dev**: orange header, `[DEV]` before the title and the development banner.

In both cases the site is available at `http://127.0.0.1:8000` and reloads automatically when files change. Stop the server with `Ctrl+C`.

### Preview both versions together

clone the gh-pages branch.

## Contributing

Changes are committed to the `dev` branch. Releases are made by merging `dev` into `main`, which updates the live docs. Commits that relate to a feature reference its ASD code (e.g. `ASD-001: add Google sign-in flow`).

Writing conventions and templates are described in [Writing docs](docs/contributing/writing-docs.md). The documentation approach itself is recorded in [ADR-0001](docs/adr/0001-documentation-approach.md).

## Built with

[MkDocs](https://www.mkdocs.org), [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/), [mike](https://github.com/jimporter/mike) and [Mermaid](https://mermaid.js.org).
