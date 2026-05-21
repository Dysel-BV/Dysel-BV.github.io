---
applyTo: "docs/ReleaseNotes/**"
---

# Release notes style guide

## File structure

Release notes are organized in two levels under `docs/ReleaseNotes/`:

- `docs/ReleaseNotes/Version {major}/index.md` — version hub page
- `docs/ReleaseNotes/Version {major}/{major}.{minor}.{build}.md` — individual release file (for example `27.3.202602.md`)

## Front matter

**Version hub (`index.md`):**
```yaml
---
title: "Version 27"
parent: "Release Notes"
---
```
- `title` uses lowercase t.
- `parent` must be `"Release Notes"` exactly.
- No `nav_order`.

**Version release file:**
```yaml
---
Title: "27.3.202602"
parent: "Version 27"
---
```
- `Title` uses capital T.
- `parent` must match the version hub's `title` value exactly (for example `"Version 27"`), not `"Release Notes"`.
- No `nav_order` — the just-the-docs theme sorts these alphabetically by title, which works naturally for numeric version strings.

## Version hub content

H1 follows the pattern: `# Version {major} (BC {wave name})`

For example: `# Version 27 (BC 2025 Release Wave 2)`

Follow with two sentences: (1) which version number this covers and which BC wave it aligns with; (2) what each page in this section contains.

## Version release file content

**H1:** `# Dysel BC {version}` — no bold wrapping, no prefix.

Immediately after the H1, a three-column change table:

```markdown
| Case No. | Module | Comment |
| --- | --- | --- |
| 12345 | Module | Description of the change. |
```

### Table conventions

- Column order must be `Case No.`, `Module`, `Comment` exactly.
- Header separator uses `| --- | --- | --- |`.
- Use **bold** for UI element names and page names within comment text.
- Use *italic* for technical terms within comment text.
- Descriptions should be written in plain English. Explain the change clearly enough that an implementer or end user can understand the impact without opening the case.
- Do not reference internal systems beyond the Case No. column.

### Module values

Use consistent module names. Existing values (use these, do not invent new ones unless a new module is genuinely introduced):

`General`, `Equipment`, `Service`, `Rental`, `Mobile Field Service`, `Integration`, `Parts`, `Finance`, `Purchase`, `Localization`, `Transport`, `Credit Management`, `Time Sheet Scanning`

## Notes section

Add `## Notes` only when the release contains upgrade warnings, minimum version requirements, or breaking changes that implementers must act on.

- Prefix every critical warning with `<span style="color:red">**Important**</span>:`.
- A typical use case is stating a minimum Business Central version requirement: `Dysel 27.3.202602 requires a Business Central version of 27.3 or higher.`
- Omit the `## Notes` section entirely when there is nothing critical to communicate; do not add it as a placeholder.
