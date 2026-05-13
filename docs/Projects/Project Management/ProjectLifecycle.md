---
title: "Project Lifecycle"
parent: "Project Management"
grand_parent: "Dysel Projects"
nav_order: 1
---

# 3. The Project Lifecycle

This section describes how a project moves through its stages from creation to closure, and how the two status systems — **Posting Status** and **Project Status** — work together.

---

## 3.1 Understanding the two status fields

A project carries two status values simultaneously:

| Status | Controlled by | Purpose |
|---|---|---|
| **Posting Status** | System (fixed enum) | Records the formal, system-level stage of the project. Determines what kinds of financial transactions are allowed. |
| **Project Status** | Administrator (configurable) | Records where the project is in your *internal process*. Controls day-to-day permitted actions (create WO, invoice, etc.). |
| **Status** | System | A simple technical lock: **Open**, **Released**, or **Closed**. Set by the Release and Close actions. |

Think of it this way: the Posting Status is the legal/accounting lifecycle, the Project Status is your operational workflow, and Status is the document lock.

---

## 3.2 Posting Status — fixed lifecycle stages

The Posting Status follows a fixed progression. It cannot be skipped, and moving backwards requires an explicit action.

```
Enquiry → Quote → Active Project → Inactive Project → Off Site → Closed Project
```

| Value | Meaning |
|---|---|
| **Enquiry** | A potential project, no commitment yet. |
| **Quote** | A formal quotation has been issued to the customer. |
| **Active Project** | Work is in progress. Costs and time can be posted. |
| **Inactive Project** | Work is temporarily suspended. |
| **Off Site** | The project output (typically an equipment object) has left the premises, but the project is not yet financially closed. |
| **Closed Project** | The project is fully complete. No further postings are allowed. |

The Posting Status is linked to your **Project Statuses** (see [Section 2.3](02-setup-and-configuration.md)). Each Project Status maps to one Posting Status, so when a user advances the project's Project Status, the Posting Status is updated automatically.

---

## 3.3 Creating a project

**Page**: *Dysel Project*  
**Navigation**: Open Projects list → New

### Required information

When creating a new project, the following fields must be completed:

| Field | Description |
|---|---|
| **No.** | Assigned automatically from the Project Nos. number series, or enter manually. |
| **Sell-to Customer No.** | The customer who receives the work. Their address and payment details are copied automatically. |
| **Bill-to Customer No.** | The customer who receives the invoice (defaults to the sell-to customer, but can differ). |
| **Project Group** | Determines the G/L accounts for all financial postings on this project. **Required before releasing.** |
| **Project Status** | The initial workflow status. |
| **Equipment Object** | The main equipment object that is the subject of the project (e.g., the machine being built or converted). Referred to as the "parent" or "main" object. |

### Additional header fields

| Field | Description |
|---|---|
| **Description** | Free-text description of the project. |
| **Branch** | The branch responsible for the project. May be mandatory depending on setup. |
| **Department** | The department responsible. |
| **Location Code** | The inventory location from which materials will be issued. |
| **Customer Reference** | The customer's own reference number for this project. |
| **Project Manager** | The salesperson/purchaser responsible for the project. |
| **Starting Date / Finishing Date** | Planned project dates. |
| **Order Date** | The date the customer placed the order. |
| **Consolidated Order No.** | Links this project to a consolidated order (optional). |

### Customer tab

The project stores three customer addresses:

- **Sell-to Customer**: Who is receiving the work.
- **Bill-to Customer**: Who will be invoiced (can be a different legal entity).
- **Ship-to Customer / Address**: Where the finished product or delivery is sent. Can be set via a ship-to code or entered manually.

### Invoicing tab

| Field | Description |
|---|---|
| **Customer Price Group** | General price group for this customer. |
| **Customer Price Group Parts** | Overrides the general price group for item/parts pricing. |
| **Customer Price Group Resource** | Overrides the general price group for resource/labour pricing. |
| **Customer Price Group Charges** | Overrides the general price group for charge pricing. |
| **Default Mark-up %** | Default margin percentage applied to costs when generating sales amounts. |
| **Default Profit %** | Alternative margin expression (profit-based). |
| **Payment Terms Code** | Payment terms applied to invoices generated from this project. |
| **Currency Code** | The currency for all transactions on this project. |
| **VAT Bus. Posting Group** | VAT business posting group for this customer. |

---

## 3.4 Releasing a project

Releasing a project moves its **Status** from *Open* to *Released*. This is a prerequisite for many downstream actions (posting, invoicing).

**Action**: *Release* button on the Project card.

### Prerequisites for release

- **Project Status** must be filled in (cannot be blank).
- **Branch** and **Department** must be filled in if they are mandatory in your setup.

### What release does

- Sets **Status** = *Released*.
- The project card becomes read-only for most fields (protected from accidental editing during active work).

### Reopening a released project

If corrections are needed, the project can be reopened (Status back to *Open*) using the **Reopen** action, subject to your Project Status configuration allowing reversal.

---

## 3.5 Advancing the Project Status

To move the project to the next workflow stage, use the **Advance Status** action on the project card. The system moves the Project Status to the value configured in the **Next Project Status Code** field of the current status.

The corresponding **Posting Status** is also updated automatically.

---

## 3.6 Closing a project

When all work is complete, all costs are posted, and all invoices have been issued, the project can be closed.

Closing a project:
- Sets **Status** = *Closed*.
- Sets **Posting Status** = *Closed Project*.
- Prevents any further postings to the project. Attempting to post to a closed project results in an error: *"Posting is not allowed on project [No.] because its status is Closed."*

Closed projects are removed from the **Open Dysel Projects** list and appear only in the **Closed Projects** list.

---

## 3.7 Open Projects list

**Page**: *Open Dysel Projects*  
**Navigation**: Search for "Open Dysel Projects" or "Dysel Projects"

This is the main working list. It shows all projects with a **Status** other than *Closed*. Use column filters to narrow by Project Status, customer, branch, or date.
