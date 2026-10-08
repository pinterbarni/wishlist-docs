# Workflow

How changes to the documentation are made, published and released.

## Branches

- **`main`:** the released documentation, published as **latest**. Only updated by merging `dev`.
- **`dev`:** work in progress for the upcoming release, published as **dev**.

Pull requests are not used yet; changes are committed directly to `dev`.

## Making a change

- Switch to `dev` and pull the latest changes: `git checkout dev && git pull`.
- Start the local preview with `mkdocs serve` and edit the files in `docs/`.
- Commit with a message that follows the commit conventions below.
- Push to `dev`. CI publishes the dev version automatically.

## Commit messages

- **Feature work:** start with the ASD code, e.g. `ASD-001: add SSO flow`.
- **Decisions:** start with the ADR code, e.g. `ADR-0002: evaluate Zensical`.
- **Everything else:** start with `docs:`, e.g. `docs: fix typo in glossary`.

Commits in the code repositories that change behavior reference the related ASD code the same way, and the matching docs change is committed to `dev` at the same time.

## Adding an ASD or ADR


!!! failure "Not supported"
    Don't modify already published ADRs.

- Copy the template from `docs/contributing/templates/` (`asd.md` or `adr.md`) into `docs/asd/` or `docs/adr/`.
- Give it the next free number: `NNN-name.md` for ASDs, `NNNN-name.md` for ADRs.
- Fill in the header (title, date, code, status).
- Add it to the section's `index.md` under today's date.
- Add it to `nav:` in `mkdocs.yml`.



## Releasing

- Make sure `dev` contains everything for the release and builds without warnings.
- Merge `dev` into `main` and push: `git checkout main && git merge dev && git push`.
- Tag the release with the application version: `git tag vX.Y.Z && git push --tags`.
- CI publishes the new **latest** version.
