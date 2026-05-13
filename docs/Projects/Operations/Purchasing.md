---
title: "Purchasing"
parent: "Operations"
grand_parent: "Dysel Projects"
nav_order: 2
---

# 6. Purchasing

Purchase orders created for project-related materials and services are linked directly to a project and task. This allows procurement costs to flow through to the project's actual cost figures.

---

## 6.1 Linking a purchase line to a project

Any standard purchase order, purchase invoice, or purchase credit memo line can be linked to a project by filling in project fields on the line. Dysel Projects adds the following fields to purchase document lines:

| Field | Description |
|---|---|
| **Project No. PRJ ELC** | The project number this cost belongs to. |
| **Project Task PRJ ELC** | The task within the project. |
| **Project Task Line No. PRJ ELC** | The internal task line number (used to pinpoint the exact task row). |
| **Project Revision PRJ ELC** | The revision code, if this purchase relates to a change order revision. |
| **Project Budget Line PRJ ELC** | The specific budget line within the task that this purchase is matched against. |

These same fields are also available on:
- Purchase receipts (posted)
- Purchase invoices (posted)
- Purchase credit memos (posted)
- Return receipts (posted)
- Warehouse put-away lines

This means the project reference is preserved through the full procurement posting chain.

---

## 6.2 Project Status and purchase creation

The **Project Status** configuration (see [Section 2.3](02-setup-and-configuration.md)) controls whether purchase orders may be created for a project at any given stage:

- **Allowed to Create PO**: The user can manually create a purchase order linked to the project.
- **Create Purchase Order**: Purchase orders are created automatically when the project advances to this status.

If neither flag is enabled on the current project status, the create purchase order action is not available.

---

## 6.3 Purchase Requests

**Purpose**: Purchase Requests are an optional, lightweight planning list that records items or services the project team intends to purchase, before a formal purchase order is raised.

They are useful for collecting purchase needs from project managers and passing them to the purchasing department.

### Purchase Request fields

| Field | Description |
|---|---|
| **Project No.** | The project this request is for. |
| **Task Code** | The task within the project. |
| **Project Budget Line** | The budget line this request relates to. |
| **Description** | What needs to be purchased. |
| **Buy-from Vendor No.** | The preferred vendor (optional). |
| **Unit Cost (LCY)** | The expected cost. |
| **Vendor Item No.** | The vendor's own item reference. Supports a catalogue lookup via the Dysel W1 catalogue function. |

### Catalogue lookup

The **Vendor Item No.** field provides a lookup into the Dysel W1 parts catalogue. This allows the project team to search for standard items by vendor catalogue number rather than needing to know the internal item number.

---

## 6.4 Cost flow from purchasing to the project

When a purchase invoice is posted with a project reference on the lines, the posted cost entries carry the project and task information. These costs are then reflected in the **Actual Cost** figures shown on the Project Statistics page (see [Section 8](08-financial-postings-and-wip.md)).

The posting uses the **Gen. Bus. Posting Group** from the purchase header and the **Gen. Prod. Posting Group** from the purchase line. The Project Group's **Project Cost Account** or **WIP Project Cost Account** is the credit side destination, depending on whether final cost recognition has taken place.

---

## 6.5 Viewing project-related purchase documents

From the Project card, use:  
**Related → Purchase Orders** — to see all purchase orders linked to this project.  
**Related → Posted Purchase Invoices** — to see all posted purchase invoices linked to this project.

This gives the project manager a complete view of committed and actual procurement costs.
