---
title: "Permissions"
parent: "Setup"
grand_parent: "Dysel Projects"
nav_order: 2
---

# 16. Permissions

Dysel Projects ships with two permission sets. Both are marked as `Assignable = true`, meaning they can be directly assigned to users or user groups in Business Central.

---

## 16.1 Permission sets overview

| Permission Set | ID | Caption | Purpose |
|---|---|---|---|
| **Perm. - All PRJ ELC** | 11021901 | Permissions - All | User-facing set; wraps all project permissions. Assign this to users. |
| **Proj. - Obj. PRJ ELC** | 11021900 | Project objects | Internal set; grants access to all project objects. Included by the set above. |

---

## 16.2 Perm. - All PRJ ELC (recommended for users)

**Caption**: Permissions - All  
**Assignable**: Yes

This is the set to assign to end users and project managers. It includes the `Proj. - Obj. PRJ ELC` set and acts as the single entry point for all project-related permissions.

To assign: Go to *Users* → select the user → *Permission Sets* → add **Perm. - All PRJ ELC**.

---

## 16.3 Proj. - Obj. PRJ ELC (object-level set)

**Caption**: Project objects  
**Assignable**: Yes (but assign `Perm. - All PRJ ELC` in preference)

This set grants:

### Table Data (RIMD — Read, Insert, Modify, Delete)

| Table |
|---|
| Project Header PRJ ELC |
| Project Task PRJ ELC |
| Project Budget Line PRJ ELC |
| Project Group PRJ ELC |
| Project Status PRJ ELC |
| Project Setup PRJ ELC |
| Project Delivery Hdr PRJ ELC |
| Proj.Task Inv Schedule PRJ ELC |
| Project Revision PRJ ELC |
| Proj.Purch. Requests PRJ ELC |
| Default Project Task PRJ ELC |

### Pages (Execute)

All project-related pages, including:
- Project Header List, Project Card, Project Task List/Sub, Project Budget Line
- Project Group, Project Status (list and card)
- Project Inv Schedule, Project Recognition (WIP worksheet)
- Project Revisions, Project Setup
- Project Statistics, Project Task Lookup
- Closed Project Headers
- Default Project Tasks

### Reports (Execute)

- **Project PRJ ELC** (Dysel Project — RDLC report)
- **EX-Project PRJ ELC** (Dysel EX-Project — Excel export)

### Codeunits (Execute)

All project integration and processing codeunits, including posting, dimension checks, equipment value posting, work order creation, WIP recognition, purchase request processing, and all event handler codeunits.

---

## 16.4 Who needs which permission set

| Role | Recommended permission set |
|---|---|
| Project manager | Perm. - All PRJ ELC |
| Project planner / estimator | Perm. - All PRJ ELC |
| Project finance / billing | Perm. - All PRJ ELC |
| Administrator configuring setup | Perm. - All PRJ ELC |
| Read-only viewer | No dedicated read-only set included; use standard BC read-only mechanisms or create a custom set based on `Proj. - Obj. PRJ ELC` with only `R` permissions. |

---

## 16.5 Required base permissions

Dysel Projects integrates with standard Business Central and Dysel W1 objects (customers, items, resources, G/L accounts, purchase orders, work orders, etc.). Users will also need appropriate permissions for those modules. Typically this means:

- Standard BC base app permissions for customers, vendors, items, dimensions.
- Dysel W1 permissions for work orders, equipment, time sheets, and other modules as required by the user's role.

Consult your Dysel partner for a recommended full permission set combination for each role in your organization.
