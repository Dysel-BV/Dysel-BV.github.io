# GitHub Copilot instructions for DyselBC documentation

## Repository purpose and stack
- This repo hosts the Dysel Learn documentation site for the Dysel BC ERP solution, published as a GitHub Pages site using the `just-the-docs` remote Jekyll theme.
- The rendered site root is the `docs/` folder; all user-facing content is Markdown (`.md`) with YAML front matter.
- There is no custom application code or tests here; the primary task is adding and maintaining documentation pages.
- The result of the site can be seen at https://learn.dysel.com/ and the source code is in this repo.

## Where to edit / add content
- General site configuration lives in `docs/_config.yml` (theme, title, colors, search, logo, favicon). Avoid changing it unless explicitly asked.
- Product documentation lives under `docs/DyselBC/` by functional area (for example `Service/Work Orders/`, `Parts/`, `Service/Work Order Quotes/`). New Business Central process docs should be placed in the appropriate subfolder.
- Feature documentation (new and deprecated product capabilities) lives under `docs/Features/`; use `docs/Features/Dysel Features/` for active features and `docs/Features/Deprecated Features/` for retired ones.
- GDB (Graphical Dispatch Board) documentation lives under `docs/GDB/`.
- Mobile documentation lives under `docs/Dysel Mobile/`.
- Module-level hubs (for example `docs/GDB/index.md`, `docs/DyselBC/index.md`, `docs/Dysel Mobile/index.md`) introduce a domain; keep them short and descriptive.
- Release notes live in `docs/ReleaseNotes/` with one file per version (for example `27.3.202602.md`), plus an index page.
- Images and static assets go in `docs/assets/images/`. Reference them from Markdown using a root-relative path (for example `![Alt text](/assets/images/filename.png)`).
- `docs/About.md` and `docs/Contribute.md` are standalone informational pages; edit them in place and do not restructure their front matter or headings unless explicitly asked.

## Front matter and navigation conventions
- Every page starts with YAML front matter using at least `title` (or `Title`) and often `parent` and/or `nav_order`.
- **Important**: front matter keys are case-sensitive in Jekyll. The casing of the `title`/`Title` key follows the page type: top-level section hubs and release notes use `Title` (capital T); content leaf pages use `title` (lowercase). Mirror the casing used in existing pages of the same type.
- **Critical**: `parent` keys must be lowercase and `parent` values must match the parent page's `title`/`Title` value exactly, in a case-sensitive way, to nest correctly in the left-hand nav (for example, if the parent has `Title: "Work Orders"`, child pages must use `parent: "Work Orders"`). When creating new pages, reuse existing `parent` values or add new ones as needed.
- **Three-level nesting**: When a page sits under a subfolder that is itself under a top-level section (for example `Allocations` inside `GDB`), the page must declare both `parent` and `grand_parent` — for example `parent: "Allocations"` and `grand_parent: "GDB"`. Without `grand_parent` the page will not appear correctly in the left-hand nav.
- Top-level sections (for example `Release Notes`, `GDB`) use `nav_order` in their front matter to control left-hand navigation order. Do not add `nav_order` to every child page unless you have a clear ordering requirement.
- Child pages use `parent` to attach to their section (for example a Work Orders article uses `parent: "Work Orders"`; release notes files use `parent: "Release Notes"`). When creating new pages, follow existing `parent` values exactly so they appear under the right node.
- Some pages (for example `docs/index.md`) use `nav_exclude: true` to hide them from the nav while still being landing pages; keep this pattern when editing those files.

## Release notes pattern
- Version files in `docs/ReleaseNotes/` are named `{major}.{minor}.{build}.md` and have front matter like `Title: "27.3.202602"` and `parent: "Release Notes"`.
- The H1 heading follows the pattern `# Dysel BC {version}`.
- Content is a Markdown table with columns `Case No.`, `Module`, and `Comment`; each row describes a single change for that release.
- Many releases end with a `## Notes` section for upgrade or compatibility warnings; keep using this section name when adding additional notes.
- Release note files do not carry a `nav_order` value; the just-the-docs theme sorts them alphabetically by title, which works naturally for numeric version strings. Do not add `nav_order` to individual release note files.
- Use `<span style="color:red">**Important**</span>:` before any critical upgrade warning in the `## Notes` section, consistent with existing release files.

## Style of user instruction pages
- Most how-to pages (for example `AllocateResourcefromGDB.md`) are generated from Business Central page scripts and have:
  - An H1 in the format `# **User Instructions: {Task Description}**` — note the bold wrapping and colon separator (for example `# **User Instructions: Allocating Resources from Graphical Dispatch Board**`).
  - A short introductory paragraph after the H1 that summarises what the guide covers.
  - Sequential sections named `### **Step N: {description}**` (H3, not H2) describing each step.
  - UI text and field names in **bold** (for example `**Work Orders**`, `**Sell-to Customer No.**`).
  - Horizontal rules written as `* * *` between steps.
  - A closing success sentence after the last step (for example `You have now successfully allocated resources using the **Graphical Dispatch Board**!`).
- When editing or generating new instructions, preserve this structure: keep the numbered H3 step sections, bold UI labels, the horizontal rules, and the closing sentence.
- Prefer clear, neutral, second-person language ("you") and avoid changing domain terminology already used in existing docs.

## Style of feature pages
- Feature pages live under `docs/Features/Dysel Features/` or `docs/Features/Deprecated Features/` and describe a product capability rather than a step-by-step procedure.
- Front matter uses `title` (lowercase) and `parent` matching the subfolder title (for example `parent: "Dysel Features"`).
- Structure: H1 with the feature name, then `## Overview`, `## How it helps`, `## Availability and enablement` (use these exact section names for consistency).
- Availability should state the version and release date (for example `**Available from:** May 2026 (version 28.0.202605)`).
- Use `<span style="color:red">**Caution**</span>:` to flag irreversible actions or significant prerequisites, consistent with existing feature pages.

## Contribution and workflow expectations
- Contribution flow is issue-first, PR-second as described in `README.md` and `docs/Contribute.md`: issues should describe the requested documentation and, when possible, link to the PR implementing it.
- Branch names on this repo typically reference work items or features (for example `29-new-documentation-release-notes-273202602`); follow this convention when suggesting branch names.
- Assume that GitHub Pages (with the Just-the-docs theme) will build the site automatically; focus on creating valid Markdown with correct front matter rather than introducing custom plugins or theme changes.
- When in doubt about structure or wording, look for a similar existing page in the same folder and mirror its front matter, headings, and formatting.

## Front matter templates

Use these as starting points. Match the casing and keys exactly.

**Top-level section hub** (`index.md` at the root of a module folder):
```yaml
---
title: "Module Name"
nav_order: N
---
```

**Sub-section hub** (`index.md` inside a subfolder with its own children):
```yaml
---
title: "Sub-section Name"
parent: "Module Name"
---
```

**Content leaf page** (instruction, setup, or reference page):
```yaml
---
title: "Page Title"
parent: "Direct Parent Title"
grand_parent: "Top-level Section Title"  # only if three levels deep
---
```

**Feature page** (under `docs/Features/Dysel Features/` or `docs/Features/Deprecated Features/`):
```yaml
---
title: "Feature Name"
parent: "Dysel Features"
---
```

**Release note file** (under `docs/ReleaseNotes/`):
```yaml
---
Title: "27.3.202602"
parent: "Release Notes"
---
```
