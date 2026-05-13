# 8. Financial Postings and WIP (Work in Progress)

This section describes how the financial side of a project is structured, how costs and revenue flow through G/L accounts, and how to use pre-recognition (WIP accounting) to recognize revenue before invoicing.

---

## 8.1 The role of the Project Group

All financial postings for a project are routed through the **Project Group** assigned to the project header. The Project Group maps to seven G/L accounts that form the accounting skeleton of the project.

### Project Group G/L account matrix

| Account field | Purpose |
|---|---|
| **WIP Project Cost Account** | Costs are posted here while the project is in progress and before final cost recognition. This is the cost-side WIP account. |
| **WIP Project Sales Account** | Pre-recognized (interim) revenue is posted here. This is the sales-side WIP account. |
| **Project Cost Account** | The final destination for project costs after recognition. |
| **Project Sales Account** | The final destination for project revenue after recognition (typically invoiced sales). |
| **Project Expected Cost Account** | Used to record expected (budgeted) costs, providing a balance-sheet view of what has been committed but not yet spent. |
| **Project Pre-recognize Sales Acc** | Used specifically during the pre-recognition journal entries to capture revenue that is being recognized ahead of invoicing. |
| **Project Interim Account** | A clearing account used during the invoicing process. Debited when an invoice is posted, credited when the final recognition is completed. |

---

## 8.2 Cost posting flow

When a work order, purchase invoice, or time sheet line is posted against a project, the cost follows this path:

```
Source document (WO, PO, time sheet)
        ↓
  Item / Resource / Job Code ledger entries
  (stamped with Project No. + Task)
        ↓
  G/L Entries
  WIP Project Cost Account  (debit)
  Inventory / Payables / ...  (credit)
```

The WIP Project Cost Account accumulates all un-recognized costs. They stay there until a cost recognition or deactivation posting moves them to the **Project Cost Account**.

---

## 8.3 Revenue posting flow (invoicing)

When a sales invoice is posted for a project task:

```
Sales Invoice (project line)
        ↓
  Customer Ledger Entry
  G/L Entries
  Customer Receivables  (debit)
  Project Interim Account  (credit)
```

The **Project Interim Account** captures the gross invoice amount. The final recognition step (see [Section 8.5](#85-pre-recognition-wip-accounting)) then moves the balance to **Project Sales Account**.

---

## 8.4 Project Statistics

**Page**: *Dysel Project Statistics*  
**Navigation**: Project card → *Statistics* action, or search for "Dysel Project Statistics"

The Statistics page is a read-only financial dashboard for a single project. It summarises all financial figures in one place.

| Field | Description |
|---|---|
| **Budget Amount** | The total sales amount from base budget lines (Revision = blank). |
| **Revised Budget Amount** | The total sales amount from revision budget lines (Revision ≠ blank). |
| **Budget Cost** | The total cost from base budget lines. |
| **Revised Budget Cost** | The total cost from revision budget lines. |
| **Total Budget Profit** | (Budget Amount + Revised Budget Amount) – (Budget Cost + Revised Budget Cost). |
| **Invoiced Amount** | Total amount posted via sales invoices. |
| **Actual Cost** | Total costs posted via work orders, purchase invoices, time sheets, etc. |
| **Actual Profit** | Invoiced Amount – Actual Cost. |
| **Deactivated Invoice Amount** | Total invoiced amount after the deactivation/recognition process. |
| **Pre Recognized Sales** | Total revenue recognized ahead of invoicing via the WIP recognition process. |
| **Deactivated Cost** | Total costs after the deactivation/recognition process. |
| **Posted Profit** | Deactivated Invoice Amount + Pre Recognized Sales – Deactivated Cost. |
| **Starting Date / Finishing Date / Order Date** | Dates from the project header. |

---

## 8.5 Pre-recognition (WIP accounting)

**Page**: *Dysel Project Recognition*  
**Navigation**: Project card → *Pre-recognize* action

Pre-recognition is the process of recognizing revenue (and costs) in the accounting period in which work is performed, even if the customer has not yet been invoiced. This is required by accrual accounting standards for long-running projects.

### Setup: Pre-recognize basis

The **Pre-recognize Basis** in Project Setup determines how the recognition amount is calculated:

| Basis | Calculation |
|---|---|
| **Based on Cost** | Pre-recognized sales = Actual Cost as a proportion of Budget Cost × Budget Amount. |
| **Based on Budget Amount** | Pre-recognized sales = Budget Amount × completion percentage entered by the user. |

### The recognition page

The recognition page shows all tasks on the project. For each task, you can:

1. Review the **Budget Amount**, **Pre Recognised Sales** to date, and **Sales Amount to Pre Recognise** (proposed new recognition amount).
2. Adjust the **Sales % to Pre Recognise** — the percentage of the task's value to recognize in this run.
3. Enter a **Posting Date**, **Posting Description**, and **Document No.** for the resulting journal entries.
4. Optionally enable **Post Pre-Recognized Back (Deactivate)** — this reverses all existing pre-recognized entries, effectively deactivating the WIP recognition. Use this when the project has been completed and final invoices have been posted.

### G/L entries created by recognition

A recognition posting creates two G/L journal entries:

```
WIP Project Sales Account  (debit)       ← reversal of previous WIP
Project Pre-recognize Sales Acc  (credit) ← new recognized revenue
```

When deactivating:
```
Project Pre-recognize Sales Acc  (debit) ← reversal of recognized revenue
WIP Project Sales Account  (credit)      ← restores WIP balance
```

---

## 8.6 Dimension integration

Projects support Business Central's standard **dimension** system. Dimensions can be inherited from the project header onto all sub-documents (work orders, purchase orders, sales invoices). A dedicated dimension check flag on the Project Status can enforce that dimensions are validated before posting is allowed.

The project header carries **Shortcut Dimension 1** and **Shortcut Dimension 2** (Global Dimensions 1 and 2 from your company setup), as well as a full dimension set for additional dimensions. These are copied to document lines when the project reference is applied.
