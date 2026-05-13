---
title: "Tasks and Budget"
parent: "Project Management"
grand_parent: "Dysel Projects"
nav_order: 2
---

# 4. Tasks and Budget

Tasks are the structural backbone of a project. They define the work stages, hold the budget, control how revenue is invoiced, and drive the creation of work orders. Budget lines provide the detailed cost breakdown within each task.

---

## 4.1 Project Tasks

**Section on the Project card**: *Tasks* sub-page  
**Full page**: *Project Task List*

Each project contains one or more tasks. Tasks can be nested (indented) to form a hierarchy of up to six levels.

### Key task fields

| Field | Description |
|---|---|
| **Task** | A code identifying this task (up to 20 characters). If *Enforce Default Tasks* is enabled in setup, you must choose from the Default Project Tasks library. |
| **Description** | A readable label for the task. |
| **Indentation** | The nesting level (0 = top-level, 1 = child, etc.). Used to create hierarchy. |
| **Sorting** | Controls the display order within the same indentation level. |
| **Visible** | If unchecked, the task is hidden from the task list but still exists in the data. |
| **Revision Code** | Associates this task with a specific project revision. Leave blank for the base (unrevised) version. |
| **Invoicing Method** | Determines how the value of this task is billed to the customer. See [Section 7](07-invoicing-and-billing.md). |
| **Costing Method** | Determines how actual costs are recognized against the task budget. |
| **Quantity / Unit of Measure** | The deliverable quantity for this task (e.g., 1 unit, or a number of hours). |
| **Amount** | The agreed sales value for this task — i.e., what the customer pays for this stage. |
| **Amount to Invoice** | Calculated remaining amount that can still be invoiced. |

### Budget-related calculated fields

These are FlowFields computed from the budget lines:

| Field | Calculation |
|---|---|
| **Budget Amount** | Sum of sales amounts on budget lines where Revision = blank. |
| **Revision Budget Amount** | Sum of sales amounts on budget lines where Revision ≠ blank. |
| **Resource Hours** | Sum of quantities on budget lines of type *Resource* or *Group (Resource)* where Revision = blank. |

### Costing Methods

The **Costing Method** controls how costs are reported and compared against the budget for a task:

| Value | Description |
|---|---|
| *(blank)* | No specific costing method; costs are tracked but not compared against a method. |
| **Actual Cost** | Report actual posted costs against this task. |
| **Budget Cost** | Report budgeted cost as the reference. |
| **Complete % Actual Cost** | Uses completion percentage × actual cost as the recognized cost. |
| **Complete % Budget Cost** | Uses completion percentage × budget cost as the recognized cost. |

---

## 4.2 Task Hierarchy

Tasks can be arranged in a parent-child hierarchy using the **Indentation** field. The purpose is to group related sub-tasks under a parent stage.

**Rules**:
- The **Invoicing Method** must be set at the same level across all tasks that share a parent. You cannot mix different invoicing methods at different hierarchy depths within the same branch.
- Parent tasks aggregate budget amounts from their children automatically.

---

## 4.3 Task Dependencies

Task dependencies define the sequence in which tasks must be performed.

**Dependency types** (following standard project management notation):

| Type | Meaning |
|---|---|
| **Finish-to-Start** | Task B cannot start until Task A is finished. |
| **Start-to-Start** | Task B cannot start until Task A has started. |
| **Finish-to-Finish** | Task B cannot finish until Task A has finished. |
| **Start-to-Finish** | Task B cannot finish until Task A has started. |

---

## 4.4 Budget Lines

**Section on the Project card**: *Task Budget* sub-page (linked to the selected task)  
**Full page**: *Project Budget Lines*

Every task can have one or more budget lines. A budget line specifies a cost element: what it is, how many, and how much.

### Budget line types

| Type | What *No.* refers to |
|---|---|
| *(blank)* | Free text (Standard Text code). |
| **Item** | An inventory item. |
| **Resource** | A specific resource (person or machine). |
| **Charge** | A line charge — an additional cost or surcharge. |
| **Job Code** | A job code from Dysel W1. |
| **Purchase** | A purchase reference (links to a purchase order setup). |
| **Object** | A specific equipment object (Dysel W1). |
| **Model** | An equipment model (Dysel W1). |
| **Group (Resource)** | A resource group — any resource in the group can fulfil this budget line. |
| **Rental Model** | A rental item by model (Dysel W1 Rental required). |
| **Rental Object** | A rental item by specific object (Dysel W1 Rental required). |
| **Rental Contract** | Links directly to an existing rental contract (Dysel W1 Rental required). |

### Common budget line fields

| Field | Description |
|---|---|
| **Type** | The category of cost item (see table above). |
| **No.** | Polymorphic: an item no., resource no., charge no., etc. depending on Type. |
| **Description** | Free text or auto-populated from the No. |
| **Revision** | The revision code this budget line belongs to (blank = base budget). |
| **Quantity** | How many units are planned. |
| **Qty. per Unit of Measure** | Conversion factor if a secondary UoM is used. |
| **Unit of Measure Code** | The unit of measure for this budget line. |
| **Work Type Code** | For Resource-type lines: the work type (e.g., Regular, Overtime). |
| **Starting Date** | The planned date for this cost item. |

### Budget vs. Revision budget

The budget lines are separated by the **Revision** field:
- Lines with **Revision = blank** form the **Base Budget** — the original agreed scope and cost.
- Lines with a **Revision Code** form a **Revised Budget** — a formal change to the original scope. See [Section 4.5 – Revisions](#45-revisions) below.

This separation lets you track the delta between what was originally agreed and what was subsequently changed, and report them side by side.

---

## 4.5 Revisions

**Page**: *Project Revisions*  
**Navigation**: Project card → Related → Revisions

A Revision represents a formal change to the agreed budget of a project (a change order). Each revision can add, remove, or modify budget lines, and it carries its own approval status.

### Revision fields

| Field | Description |
|---|---|
| **Project No.** | The project this revision belongs to. |
| **Revision Code** | A short code identifying this revision (e.g., *REV001*). |
| **Description** | A description of the scope change. |
| **Status** | The approval state of the revision: **Draft**, **Final**, or **Agreed**. |
| **Revision Amount** | Calculated — the sum of all budget lines associated with this revision code. |

### Revision workflow

1. Create a new revision (Code + Description).
2. Add budget lines to the affected tasks, entering the Revision Code on each line.
3. Set Status to **Final** when the revision is ready for customer approval.
4. Set Status to **Agreed** when the customer formally accepts the change.

Only **Agreed** revisions are included in the *Revised Budget Amount* reported on project statistics.

---

## 4.6 Default Project Tasks

If **Enforce Default Tasks** is enabled in Project Setup, task codes must come from the Default Project Tasks library. See [Section 2.4](02-setup-and-configuration.md#24-default-project-tasks) for the configuration details.

When a default task is added to a project, the invoicing method, costing method, and posting groups are pre-populated from the template but can be adjusted on the project.
