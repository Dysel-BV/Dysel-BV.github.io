# GitHub Copilot instructions for DyselBC documentation

## Repository purpose and stack
- This repo hosts the Dysel Learn documentation site for the Dysel BC ERP solution, published as a GitHub Pages site using the `just-the-docs` remote Jekyll theme.
- The rendered site root is the `docs/` folder; all user-facing content is Markdown (`.md`) with YAML front matter.
- There is no custom application code or tests here; the primary task is adding and maintaining documentation pages.

## Where to edit / add content
- General site configuration lives in `docs/_config.yml` (theme, title, colors, search, logo, favicon). Avoid changing it unless explicitly asked.
- Product documentation lives under `docs/DyselBC/` by functional area (for example `Service/Work Orders/`, `Parts/`, `Service/Work Order Quotes/`). New Business Central process docs should be placed in the appropriate subfolder.
- Module-level hubs (for example `docs/GDB/index.md`, `docs/DyselBC/index.md`, `docs/Dysel Mobile/index.md`) introduce a domain; keep them short and descriptive.
- Release notes live in `docs/ReleaseNotes/` with one file per version (for example `27.3.202602.md`), plus an index page.

## Front matter and navigation conventions
- Every page starts with YAML front matter using at least `title` (or `Title`) and often `parent` and/or `nav_order`.
- **Important**: front matter keys are case-sensitive in Jekyll; use `title` or `Title` consistently as seen in existing files.
- **Critical**: `parent` keys must be lowercase and values must match existing section titles exactly to nest correctly in the left-hand nav (for example `parent: "Work Orders"`). When creating new pages, reuse existing `parent` values or add new ones as needed.
- Top-level sections (for example `Release Notes`, `GDB`) use `nav_order` in their front matter to control left-hand navigation order. Do not add `nav_order` to every child page unless you have a clear ordering requirement.
- Child pages use `parent` to attach to their section (for example a Work Orders article uses `parent: "Work Orders"`; release notes files use `parent: "Release Notes"`). When creating new pages, follow existing `parent` values exactly so they appear under the right node.
- Some pages (for example `docs/index.md`) use `nav_exclude: true` to hide them from the nav while still being landing pages; keep this pattern when editing those files.

## Release notes pattern
- Version files in `docs/ReleaseNotes/` are named `{major}.{minor}.{build}.md` and have front matter like `Title: "27.3.202602"` and `parent: "Release Notes"`.
- The H1 heading follows the pattern `# Dysel BC {version}`.
- Content is a Markdown table with columns `Case No.`, `Module`, and `Comment`; each row describes a single change for that release.
- Many releases end with a `## Notes` section for upgrade or compatibility warnings; keep using this section name when adding additional notes.

## Style of user instruction pages
- Most how-to pages (for example `CreateWorkOrderManually.md`) are generated from Business Central page scripts and have:
  - An H1 describing the task (for example `# User Instructions for Creating a Work Order Manually`).
  - Sequential sections named `## **Step N:** ...` describing each step.
  - UI text and field names in **bold** (for example `**Work Orders**`, `**Sell-to Customer No.**`).
  - Horizontal rules written as `* * *` between steps.
- When editing or generating new instructions, preserve this structure: keep the numbered step sections, bold UI labels, and the detailed step-by-step bullets.
- Prefer clear, neutral, second-person language ("you") and avoid changing domain terminology already used in existing docs.

## Contribution and workflow expectations
- Contribution flow is issue-first, PR-second as described in `README.md` and `docs/Contribute.md`: issues should describe the requested documentation and, when possible, link to the PR implementing it.
- Branch names on this repo typically reference work items or features (for example `29-new-documentation-release-notes-273202602`); follow this convention when suggesting branch names.
- Assume that GitHub Pages (with the Just-the-docs theme) will build the site automatically; focus on creating valid Markdown with correct front matter rather than introducing custom plugins or theme changes.
- When in doubt about structure or wording, look for a similar existing page in the same folder and mirror its front matter, headings, and formatting.
