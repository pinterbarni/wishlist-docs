# Writing docs

Conventions that keep the documentation consistent and easy to read for both people and AI tools.

## Text

- No manual line breaks inside paragraphs or list items; each paragraph is a single line.
- No numbered lists for sections; use `###` headers instead.
- No arrow characters (such as `→` or `->`) in prose; describe the relationship in words. Arrows are allowed only inside Mermaid diagrams and code.
- No em dashes; use a colon, comma, parentheses or a new sentence instead.

## File names and codes

- **ASDs:** files are named `NNN-name.md` (e.g. `001-auth-sso.md`), the code is `ASD-NNN`.
- **ADRs:** files are named `NNNN-name.md` (e.g. `0001-documentation-approach.md`), the code is `ADR-NNNN`.
- Numbers are never reused or changed. The code appears in the page header and in commit messages.

## Page header

Every ASD and ADR starts with the same header, taken from its template in `templates/`:

```markdown
# 0001 - Documentation approach

**Date:** 2026-10-08  
**Code:** `ADR-0001`  
**Status:** Accepted
```

## Index pages

- Entries are grouped under date headers in the format `## YYYY.MM.DD`.
- Newer dates appear on top.
- Within a date, entries are listed in ascending order by number.

```markdown
## 2026.10.12

[0002 - Evaluate Zensical](./0002-evaluate-zensical.md)

## 2026.10.08

[0001 - Documentation approach](./0001-documentation-approach.md)
```

## Diagrams and tables

- Tables are used only to explain flow diagrams and are placed directly below the diagram they describe. Everything else uses `###` headers and bullet points.
- Each diagram node is numbered in bold in its label (e.g. `<b>1:</b> Push to dev or main`), and the table has exactly one row per node, in the same order.
- The first column (`#`) holds the step number in bold, matching the number in the diagram. Branching steps use letter suffixes (e.g. **4a**, **4b**).
- The second column holds the step name in bold; the remaining columns hold plain-text detail.
- Table cells contain a single line of text: no line breaks, no nested lists.
- Diagram labels use a colon after the number (`1:`), not a period, because Mermaid can misread `1.` as a Markdown list.

## Callouts

Callouts (admonitions) highlight information that should stand out from the surrounding text. Each callout has a type, which sets its color and icon, and an optional title in quotes. The content must be indented by 4 spaces, or it renders outside the box.

### note

General remarks that are useful but not critical.

!!! note
    The API reference is generated from the backend's OpenAPI file.

```markdown
!!! note
    The API reference is generated from the backend's OpenAPI file.
```

### abstract

A short summary at the top of a long page. Aliases: `summary`, `tldr`.

!!! abstract "Summary"
    Shared wishlists let invited users see items and reserve gifts without the owner knowing.

```markdown
!!! abstract "Summary"
    Shared wishlists let invited users see items and reserve gifts without the owner knowing.
```

### info

Neutral background information or context.

!!! info
    Sign-in currently supports Google and Apple accounts.

```markdown
!!! info
    Sign-in currently supports Google and Apple accounts.
```

### todo

Marks a page or section that is not finalized. Alias of `info`.

!!! todo "Not finalized"
    This page is a draft and may change.

```markdown
!!! todo "Not finalized"
    This page is a draft and may change.
```

### tip

Advice that makes something easier. Aliases: `hint`, `important`.

!!! tip
    Run `mkdocs serve` while writing to see changes live.

```markdown
!!! tip
    Run `mkdocs serve` while writing to see changes live.
```

### success

Something that is done, confirmed or working. Aliases: `check`, `done`.

!!! success "Done"
    Google sign-in is implemented and deployed.

```markdown
!!! success "Done"
    Google sign-in is implemented and deployed.
```

### question

An open question that still needs an answer. Aliases: `help`, `faq`.

!!! question "Open question"
    Should reservations expire after the event date?

```markdown
!!! question "Open question"
    Should reservations expire after the event date?
```

### warning

Something the reader must be careful about. Aliases: `caution`, `attention`.

!!! warning
    Changing the database schema requires a new Drizzle migration.

```markdown
!!! warning
    Changing the database schema requires a new Drizzle migration.
```

### failure

Something that does not work or is not supported. Aliases: `fail`, `missing`.

!!! failure "Not supported"
    LinkedIn sign-in is not available yet.

```markdown
!!! failure "Not supported"
    LinkedIn sign-in is not available yet.
```

### danger

A risk of data loss, security issues or breaking production. Alias: `error`.

!!! danger
    Never run seed scripts against the production database.

```markdown
!!! danger
    Never run seed scripts against the production database.
```

### bug

A known issue and its workaround.

!!! bug "Known issue"
    The share link is not refreshed after renaming a wishlist. Reload the page as a workaround.

```markdown
!!! bug "Known issue"
    The share link is not refreshed after renaming a wishlist. Reload the page as a workaround.
```

### example

A concrete example of a rule or concept.

!!! example
    `ASD-002: hide reservations from list owner` is a correctly formatted commit message.

```markdown
!!! example
    `ASD-002: hide reservations from list owner` is a correctly formatted commit message.
```

### quote

A quotation from a person, a document or an external source. Alias: `cite`.

!!! quote
    Docs that drift from the code stop being read.

```markdown
!!! quote
    Docs that drift from the code stop being read.
```

## Callout variations

### Collapsible, closed by default

Use `???` instead of `!!!`. Good for long details most readers can skip. Requires `pymdownx.details` in `mkdocs.yml`.

??? info "Full error log"
    The complete output is kept here so it does not clutter the page.

```markdown
??? info "Full error log"
    The complete output is kept here so it does not clutter the page.
```

### Collapsible, open by default

Use `???+`.

???+ tip "Shortcut"
    Press `/` to jump to the search box.

```markdown
???+ tip "Shortcut"
    Press `/` to jump to the search box.
```

### Without a title

Use an empty title to show only the content.

!!! note ""
    A callout without a title bar.

```markdown
!!! note ""
    A callout without a title bar.
```

## When to use which callout

- **todo:** at the top of every unfinished page; remove it when the page is complete.
- **abstract:** a one or two sentence summary at the top of long ASDs and ADRs.
- **question:** open questions in ASDs, one callout per question.
- **warning:** steps that can go wrong if done carelessly.
- **danger:** anything that can lose data, leak secrets or break production.
- **bug:** known issues in the runbook, each with its workaround.
- **success:** confirmed, completed states, such as a feature that is implemented and deployed.
- **example:** concrete examples next to a rule or convention.
- Do not stack more than two callouts in a row; if everything stands out, nothing does.
