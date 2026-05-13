---
title: "Archiving and Closed Projects"
parent: "Dysel Projects"
nav_order: 8
---

# 15. Archiving and Closed Projects

Dysel Projects maintains a full history of every project through a versioning mechanism. Each project header, task, and budget line carries an **Archive Version** integer field. The live (active) record always has `Archive Version = 0`. When a snapshot is taken, a copy is created with a higher archive version number, preserving the state of the project at that point in time.

---

## 15.1 Archive Version

| Archive Version | Meaning |
|---|---|
| **0** | Live record — the current working version of the project. |
| **1, 2, 3, ...** | Historical snapshots — read-only copies taken at meaningful points (e.g., on revision approval, on project close). |

The archive version propagates to all child records:
- **Project Header** → Archive Version
- **Project Tasks** → Archive Version
- **Project Budget Lines** → Archive Version

All lookups and relationships in the system filter to `Archive Version = 0` to avoid accidental access to historical data.

---

## 15.2 Viewing archived versions

From the project card, you can navigate to previous versions through the **Archive** action. Each archived version shows the project header, tasks, and budget lines exactly as they were at the moment of archiving.

The **Dysel Project** report (see [Section 14.1](14-reporting.md#141-dysel-project-report)) accepts an **Archive Version** filter, allowing you to print or review a historical snapshot of a project.

---

## 15.3 Closed projects

When a project's **Posting Status** is advanced to **Closed Project** (step 5 in the posting status progression), the project moves to the *Closed* state. Closed projects:

- Are read-only — no further changes, invoices, or postings are allowed.
- Remain in the database for historical and financial reference.
- Are accessible from the **Closed Dysel Projects** page (search for *Closed Dysel Projects* or use the navigation from the project list).

### Closed Projects page

The **Closed Dysel Projects** page shows all project headers with `Status = Closed` and `Archive Version = 0` (i.e., the final state of each closed project). The page is read-only — insert, modify, and delete are not permitted.

You can open the project card from the list to review full detail.

---

## 15.4 Closing process summary

1. **Complete all invoicing**: Ensure all invoice schedule terms are marked as invoiced and no open amounts remain.
2. **Pre-recognize remaining WIP**: If any pre-recognized sales need to be reversed before closing, run the WIP recognition worksheet with *Post Pre-Recognized Back* selected (see [Section 8](08-financial-postings-and-wip.md)).
3. **Advance Posting Status to Closed Project**: Use the **Change Posting Status** action on the project card or the posting status change codeunit.
4. **Confirm**: The project is now in Closed status. It will appear in the *Closed Dysel Projects* list and will no longer appear on the active project list.

---

## 15.5 Related archived records

When a project is involved with other documents that support archiving, those archived documents also carry the project reference:

- **Purchase order archives** — purchase lines carry `Project No. PRJ ELC`, `Project Task PRJ ELC`, and related fields, so archived purchase orders retain the project link.
- **Sales order archives** — sales lines carry the equivalent project fields.
- **Equipment object archives** — the archived equipment object record carries the project fields.
- **Configurator header archives** — configurator archives carry project references when applicable.
