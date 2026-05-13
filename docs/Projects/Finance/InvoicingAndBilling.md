---
title: "Invoicing and Billing"
parent: "Finance"
grand_parent: "Dysel Projects"
nav_order: 1
---

# 7. Invoicing and Billing

Projects are not invoiced line by line as in a standard sales order. Instead, invoicing is controlled at the task level through **Invoicing Methods** and, for the *Schedule* method, through a per-task **Invoice Schedule** (billing milestones).

---

## 7.1 Invoicing Methods

Each task has an **Invoicing Method** that determines how the system calculates how much can be invoiced for that task. The method is set on the task and — when *Enforce Default Tasks* is enabled — defaults from the Default Project Task template.

> **Important constraint**: All tasks at the same hierarchy level within the same parent must use the same invoicing method. The system enforces this rule. You cannot, for example, have one sibling task using *Budget* and another using *Schedule*.

| Invoicing Method | Description |
|---|---|
| *(blank)* | No invoicing method assigned. This task is not independently invoiceable. Typically used for summary/heading tasks. |
| **Budget** | The invoiceable amount equals the budgeted amount on the task. |
| **Actual Cost** | The invoiceable amount is based on actual costs posted to the task (cost-plus billing). |
| **Completion Budget %** | A percentage of completion is applied to the budgeted amount to derive the invoiceable amount. |
| **Amount** | A fixed amount is set directly on the task. |
| **Completion % Amount** | A percentage of completion is applied to the fixed Amount on the task. |
| **Schedule** | Invoicing is driven by a separate **Invoice Schedule** table. See [Section 7.3](#73-invoice-schedule) below. |

---

## 7.2 Creating a sales invoice from a project

**Action**: *Create Invoice* on the Project card (available when the Project Status flag **Allowed to Invoice** is enabled).

The system evaluates all tasks on the project and determines the invoiceable amount for each based on the task's invoicing method and current state. Sales invoice lines are generated for the tasks and amounts that are ready to invoice.

The resulting invoice is a standard Business Central sales invoice. Once posted, the invoiced amount is reflected in the **Invoiced Amount** figure on the project statistics.

---

## 7.3 Invoice Schedule

**Page**: *Dysel Project Invoice Schedule*  
**Navigation**: Project card → Task → *Invoice Schedule* action, or search for "Dysel Project Invoice Schedule"

When a task uses the **Schedule** invoicing method, all billing milestones for that task are defined in the Invoice Schedule. Instead of the system calculating the invoiceable amount from budget or actuals, the user defines explicit billing terms.

### Invoice Schedule fields

The page shows a header with task summary information:

| Header Field | Description |
|---|---|
| **Project Task** | The task code for which the schedule applies. |
| **Task Description** | The description of the task. |
| **Amount** | The total agreed amount on the task. |
| **Amount Inv. Schedule** | The sum of all term amounts defined in the schedule so far. |
| **Remaining Amount** | Amount – Amount Inv. Schedule. Should reach zero once all terms are defined. |

Each row in the schedule is a billing **Term**:

| Term Field | Description |
|---|---|
| **Term No.** | Sequential term number (e.g., 1, 2, 3). |
| **Description** | A descriptive label for the billing milestone (e.g., "30% on delivery of frame"). |
| **Amount Term** | The total amount allocated to this term. |
| **Ready to Invoice** | When checked, this term is included in the next invoice run. This field is editable only while the term has not been fully invoiced. |
| **Amount to Invoice** | The amount to actually post on the next invoice for this term (can be less than Amount Term to allow partial invoicing). |
| **Due Date Term** | The planned date by which this term should be invoiced. |
| **Advice at % Completion** | Optional: the percentage of project completion at which this term should be advised to the customer. |
| **Amount open Invoice** | Read-only: amount currently on unposted sales invoices for this term. |
| **Invoiced Amount** | Read-only: the amount already posted via sales invoices. |
| **Amount Cr.Memo** | Read-only: the amount credited back via credit memos. |

### Invoicing a term

1. Open the Invoice Schedule for the relevant task.
2. Set **Ready to Invoice** = Yes on the term(s) to be billed.
3. Set **Amount to Invoice** if you want to post less than the full term amount.
4. Run the **Create Invoice** action from the project card.

The term remains available for further partial invoicing until `Invoiced Amount – Amount Cr.Memo = Amount Term`. At that point, **Ready to Invoice** becomes read-only (fully invoiced) and cannot be ticked again.

---

## 7.4 Sales documents and project references

Sales invoice and credit memo lines are extended with project fields in the same way as purchase lines (see [Section 6.1](06-purchasing.md)). This ensures that every invoice line carries:

- **Project No.**
- **Project Task**
- **Project Revision** (if applicable)

These references allow posted sales entries to be traced back to the project and contribute to the **Invoiced Amount** and **Deactivated Invoice Amount** figures in the project statistics.

---

## 7.5 Credit notes

If a credit memo is posted for an invoiced project amount, the **Amount Cr.Memo** field on the invoice schedule term is updated accordingly. The term can then be re-invoiced up to the original Amount Term less the net invoiced amount.

---

## 7.6 Customer Price Groups

The project header carries three customer price group fields that override standard pricing at the line level when invoices are generated:

| Price Group Field | Applies to |
|---|---|
| **Customer Price Group** | General default. |
| **Customer Price Group Parts** | Items / spare parts lines. |
| **Customer Price Group Resource** | Resource / labour lines. |
| **Customer Price Group Charges** | Charge lines. |

This allows the project to use pricing agreements that differ from the customer's default price group — for example, if a project has a special fixed-price agreement for labour.
