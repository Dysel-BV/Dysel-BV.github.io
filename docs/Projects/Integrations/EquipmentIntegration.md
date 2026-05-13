# 11. Equipment Integration

> **Prerequisite**: Equipment integration requires the **Equipment Management** module of Dysel W1. If your Dysel installation does not include this module, this section does not apply.

Projects are typically built around an equipment object — the machine or asset being built, converted, or maintained. Dysel Projects has deep integration with Dysel W1's Equipment module to track the equipment throughout the project lifecycle and to record the financial impact on the equipment object's value.

---

## 11.1 Equipment object on the project header

Every project can have one main **Equipment Object** linked on the project header. This is the primary asset that the project concerns — for example, the machine being built or overhauled.

When a work order is created from a project task, the equipment object is automatically copied from the project header to the work order, linking all work performed to both the project and the equipment object.

---

## 11.2 Equipment Object fields added by Projects

Dysel Projects adds the following fields to the Equipment Object record:

| Field | Description |
|---|---|
| **Project No. PRJ ELC** | The project currently associated with this equipment object (read-only; set by the system). |
| **Project Task PRJ ELC** | The task within that project (read-only; set by the system). |

These fields are informational and allow navigating from an equipment object back to its project. They are set automatically when the equipment object becomes the subject of a project.

---

## 11.3 New equipment object status

When a new equipment object is created as an output of a project, the **Default Equipment Object Status** from the Project Setup (see [Section 2.1](02-setup-and-configuration.md)) is automatically applied to it. This status must be one that corresponds to the *Sold* posting status in the Equipment module, representing a customer-owned asset.

The **Allowed to Create Equipment Objects** flag on the Project Status controls whether users may create new equipment objects at a given project stage.

---

## 11.4 Equipment budget line types

Budget lines of the following types relate specifically to equipment (see [Section 4.4](04-tasks-and-budget.md#44-budget-lines)):

| Budget Line Type | Description |
|---|---|
| **Object** | A specific existing equipment object. Use when the work involves an existing asset already in the system. |
| **Model** | An equipment model. Use when planning costs for a type of machine without specifying the individual object yet. |

---

## 11.5 Equipment value entries and project sales

When a sales invoice is posted for a project that involves an equipment object (doc type = *Project*), Dysel Projects posts equipment value entries alongside the standard G/L entries. This records the financial movement on the equipment object's value ledger:

- **Sales WIP** entries are created when a project invoice is posted.
- **COGS** entries are created when the cost of the equipment is recognized.

Both types of entries carry the project number, task, and budget line references, preserving full traceability from the equipment's financial history back to the project.

---

## 11.6 Equipment dispatch

The **Equipment Dispatch** page in Dysel W1 is extended to show project information. This allows dispatchers to see which projects are associated with the equipment objects being scheduled.

---

## 11.7 Change Model report

A **Change Model** report extension is included. This is used when the model of an equipment object needs to be updated as part of a project (for example, after a conversion that results in a different model classification).
