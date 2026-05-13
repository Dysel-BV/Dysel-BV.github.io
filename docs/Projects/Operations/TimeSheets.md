---
title: "Time Sheets"
parent: "Operations"
grand_parent: "Dysel Projects"
nav_order: 3
---

# 9. Time Sheets

> **Prerequisite**: Time sheet functionality requires the **Time Sheet** module of Dysel W1. If your Dysel installation does not include this module, this section does not apply.

Time sheets in Dysel W1 are extended by Dysel Projects to allow employees to register their hours directly against a project and task. Posted time sheet lines are then reflected in the project's actual cost figures.

---

## 9.1 How time sheets relate to projects

When a time sheet line is linked to a project, the following fields are stamped on the line:

| Field | Description |
|---|---|
| **Project No. PRJ ELC** | The project the hours belong to. |
| **Project Task PRJ ELC** | The specific task within the project. |
| **Project Task Line No. PRJ ELC** | The internal line number of the task. |
| **Project Revision PRJ ELC** | The revision code if this time relates to a change order revision. |

These references ensure that when the time sheet line is posted, the resulting resource ledger entries carry the project and task information, making them visible as actual cost on the project statistics.

---

## 9.2 Eligible document types

Project references can only be set on time sheet lines where:

1. The **Activity Code** has a reporting hour type of **Work**, **Travel**, or **Billable Allowance**.
2. The **Document Type** is either **Work Order** or **Rental Contract**.

If the activity code or document type does not meet these conditions, the project fields are automatically cleared.

---

## 9.3 Project Status and time posting

The **Project Status** configuration (see [Section 2.3](02-setup-and-configuration.md)) includes a **Post Time Sheet** flag. When this flag is disabled on the project's current status, time sheet lines cannot be posted against the project.

---

## 9.4 Entering project information on a time sheet line

1. Open or create a **Time Sheet** line in Dysel W1.
2. Set the **Document Type** to *Work Order* or *Rental Contract*.
3. Set the **Activity Code** to one with a qualifying hour type (Work, Travel, or Billable Allowance).
4. Populate **Project No. PRJ ELC** — use the lookup to find and select the project.
5. Populate **Project Task PRJ ELC** — the lookup filters to tasks on the selected project.
6. Optionally, populate **Project Revision PRJ ELC** if the hours relate to a specific change order.

---

## 9.5 Cost flow from time sheets to the project

When a time sheet is posted:

- A resource ledger entry is created carrying the project and task references.
- A G/L entry is posted to the **WIP Project Cost Account** of the project's Project Group.
- The amount appears as **Actual Cost** on the project statistics.

The calculation of the cost uses the resource's cost rate (from the resource card or work type), multiplied by the number of hours entered.
