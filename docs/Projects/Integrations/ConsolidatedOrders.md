---
title: "Consolidated Orders"
parent: "Integrations"
grand_parent: "Dysel Projects"
nav_order: 3
---

# 13. Consolidated Orders

> **Prerequisite**: Consolidated Order integration requires the **Consolidated Orders** module of Dysel W1. If your Dysel installation does not include this module, this section does not apply.

A **Consolidated Order** in Dysel W1 is a sales order that groups multiple items and transactions together, often representing the commercial view of what needs to be sold to a customer. Dysel Projects links a project to a consolidated order so that both the project cost tracking and the commercial order management are aligned on the same customer transaction.

---

## 13.1 Project and Consolidated Order relationship

The link between a project and a consolidated order is bidirectional:

- **On the Project Header**: The field **Consolidated Order No.** stores the number of the associated consolidated order. This is visible on the project card.
- **On the Consolidated Order**: The field **Project No.** (added by Dysel Projects) links back to the project.

This means a single project can be associated with one consolidated order, and a consolidated order can be associated with one project.

---

## 13.2 Linking a project to a consolidated order

**From the Consolidated Order card:**

1. Open the consolidated order.
2. In the **Project No.** field, select the relevant project.
   - The lookup is filtered to open projects belonging to the same sell-to customer.
3. On selection, the system automatically updates the project header's **Consolidated Order No.** field.
4. If the project has an equipment object and the consolidated order does not yet have one, the equipment object is also copied to the consolidated order.

**From the Project Header:**

1. Open the project.
2. In the **Consolidated Order No.** field, enter or look up the consolidated order number.

---

## 13.3 Effect of linking

Once a consolidated order is linked to a project:

- Both documents carry a cross-reference to each other, enabling navigation between them.
- The **Equipment Object** on the consolidated order is synchronized from the project if not already set.
- Sales and invoicing triggered from the consolidated order will be traceable back to the project.

---

## 13.4 Use case

The typical scenario for using consolidated orders together with projects is:

1. A customer places an order for a machine (commercial order → Consolidated Order).
2. The machine needs to be built or converted (production/engineering → Project).
3. By linking both, the company can manage the commercial commitment and the project execution in parallel, using the consolidated order for customer-facing communications and the project for internal cost and planning purposes.
