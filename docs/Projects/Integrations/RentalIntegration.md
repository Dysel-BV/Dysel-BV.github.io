---
title: "Rental Integration"
parent: "Integrations"
grand_parent: "Dysel Projects"
nav_order: 1
---

# 10. Rental Integration

> **Prerequisite**: Rental integration requires the **Rental Management** module of Dysel W1. If your Dysel installation does not include this module, this section does not apply.

Projects can include rental items in their budgets and track the costs of rented equipment through to the project's actual cost figures. Rental items appear as specific budget line types, and rental contracts can be linked directly to a project task.

---

## 10.1 Rental budget line types

When building a task budget, three types relate specifically to rental (see [Section 4.4](04-tasks-and-budget.md#44-budget-lines)):

| Budget Line Type | Description |
|---|---|
| **Rental Model** | Plans a rental of equipment specified by model (any object of that model may be rented). |
| **Rental Object** | Plans a rental of a specific equipment object. |
| **Rental Contract** | Links directly to an existing rental contract (Orders only). The contract number is entered in the *No.* field. |

Using these types in the budget allows the project manager to communicate to the rental desk what equipment needs to be sourced for each task.

---

## 10.2 Rental contract linkage

When a rental contract exists and should be associated with a project task, it can be linked in two ways:

1. **Via a budget line** of type *Rental Contract* — entering the contract number directly on the budget line.
2. **Via the document relation mechanism** — Dysel Projects can detect rental contracts linked to a project and add them to the related documents list. The system checks budget lines of type *Object* and *Rental Object* to find associated rental contracts.

When a rental contract is linked to a project, the project fields (Project No., Project Task) are stamped on the rental contract, enabling rental charges to flow through to the project's cost totals.

---

## 10.3 Time sheets and rental

Time sheet lines with a **Document Type** of *Rental Contract* can carry project references (see [Section 9](09-time-sheets.md)). This allows time registered against a rental contract to be attributed to a specific project task.

---

## 10.4 Configurator integration (rental configuration)

If the Dysel W1 Configurator module is active, requested rental configurations can also carry project references. This extends the planning capability so that even the configuration phase of a rental is linked to the correct project task.

---

## 10.5 Cost flow from rental to the project

Rental charges (invoices from the rental contract) that carry a project reference are posted to the **WIP Project Cost Account** of the project's Project Group, in the same way as purchase or work order costs. They appear as **Actual Cost** on the project statistics.
