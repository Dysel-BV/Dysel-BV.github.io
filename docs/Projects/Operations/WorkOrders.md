# 5. Work Orders

> **Prerequisite**: Work Orders in Dysel Projects depend on the **Work Order Management** module of Dysel W1. The Project Group must have a **Service Type** configured that corresponds to the project's service domain.

Work orders are the mechanism through which physical work on a project is organised, tracked, and costed. Each work order is linked back to the project and to a specific task, ensuring that all labour, materials, and other costs incurred during execution are captured against the correct budget line.

---

## 5.1 How work orders relate to projects

When a work order is created from a project task:

- The work order header is stamped with the **Project No.**, **Project Task**, and **Project Task Line No.**
- The **Equipment Object** from the project header is copied to the work order.
- Costs posted via the work order (items, resources, job codes, etc.) flow through to project cost ledger entries, making them visible in the project statistics.

The relationship is one-to-many: a single project task can have multiple work orders if the work is carried out in separate phases or by different teams.

---

## 5.2 Creating a work order from a project

**Action**: *Create Work Order* on the Project card.

### Prerequisites

Before a work order can be created:

1. The project's **Project Status** must have the **Allowed to Create Work Order** flag enabled.
2. The **Project Group** on the project must have a **Service Type** assigned that is configured for project-type work orders.
3. The project must not be closed.

### Process

1. Open the project and choose **Create Work Order** from the actions.
2. A dialog presents the project tasks as options. Select one or more tasks for which the work order should be created.
3. The system checks whether budget lines exist for the selected task. If none exist, the work order can still be created, but no cost lines will be pre-populated.
4. **Duplicate check**: if a non-closed work order already exists for the same project and task, the system warns you. You can either:
   - Open the existing work order and add lines to it.
   - Confirm that a second work order should be created anyway.
5. The work order is created and the work order card opens automatically.

---

## 5.3 Work Order header fields set by the project

When a work order is created from a project task, these fields are copied or set automatically:

| Work Order Field | Source |
|---|---|
| **Project No. PRJ ELC** | Project header — No. |
| **Project Task PRJ ELC** | Selected task — Task code |
| **Project Task Line No. PRJ ELC** | Selected task — Line No. |
| **Equipment Object** | Project header — Equipment Object |
| **Customer** | Project header — Sell-to Customer No. |
| **Service Type** | Project Group — Service Type |

---

## 5.4 Work order lines and project cost

Work order lines (items, resources, charges, job codes) are posted through the standard Dysel W1 work order posting process. Because the work order header carries the project references, the posted cost entries are automatically tagged with:

- **Project No.**
- **Project Task**
- **Project Task Line No.**

These tags cause the costs to appear in the project statistics as **Actual Cost**, where they can be compared against the budgeted cost.

---

## 5.5 Multiple work orders per task

A task may have several work orders across its lifetime (for example, one work order per visit to a site). All costs from all associated work orders accumulate on the same task, giving a single consolidated actual cost figure per task.

---

## 5.6 Releasing work orders from the project

Depending on the **Project Status** configuration (the **Release all Work Orders** flag), work orders linked to a project can be released automatically when the project advances to a particular status. This ensures work orders are in the correct state for posting without requiring a user to release each one manually.

---

## 5.7 Viewing work orders from the project

**Action**: *Related → Work Orders* on the Project card.

This opens a filtered list of all work orders linked to the current project, across all tasks.
