# 2. Setup and Configuration

Before projects can be created and used, an administrator must complete a one-time setup. The configuration is spread across five areas: Project Setup, Project Groups, Project Statuses, Default Project Tasks, and Source Codes.

---

## 2.1 Dysel Project Setup

**Page**: *Dysel Project Setup*  
**Navigation**: Search for "Dysel Project Setup"

This page contains global defaults for the entire Projects module.

### General tab

| Field | Description |
|---|---|
| **Default Equipment Object Status** | The equipment object status that is automatically assigned to a new equipment object that is created from a project. The status must be one that corresponds to the *Sold* posting status in the Equipment module. |
| **Enforce Default Tasks** | When enabled, users cannot define their own tasks on a project; they must use the tasks defined in the Default Project Tasks list. |
| **Allow Main Equipment Object Customer Change** | Controls whether the customer on the main equipment object linked to the project can be changed after the project is created. |

### No. Series tab

| Field | Description |
|---|---|
| **Project Nos.** | The number series used to automatically assign numbers to new projects. |
| **Project Delivery Nos.** | The number series used to automatically assign numbers to project delivery documents. |

### Finance tab

| Field | Description |
|---|---|
| **Pre-Recognize Basis** | Determines how pre-recognized (interim) revenue is calculated. Options: **Based on Cost** or **Based on Budget Amount**. See [Section 8 – Financial Postings and WIP](08-financial-postings-and-wip.md) for details. |
| **Mark-up % Rounding Precision** | The rounding increment applied when calculating mark-up percentages. Default is 1. |

---

## 2.2 Project Groups

**Page**: *Project Group*  
**Navigation**: Search for "Project Group"

A Project Group connects a category of projects to specific G/L accounts. Every project must be assigned to a Project Group, and that assignment drives all financial postings for the project.

### Fields

| Field | Description |
|---|---|
| **Code** | A unique code for the project group. |
| **Description** | A descriptive label for the group. |
| **Service Type** | Links this group to a specific work order service type in Dysel W1. This determines which type of work order is created when you create a work order from a project task. |

### G/L Accounts

| Field | Description |
|---|---|
| **WIP Project Cost Account** | Interim G/L account for work-in-progress costs. Posted to while the project is active and before the final cost recognition. |
| **WIP Project Sales Account** | Interim G/L account for work-in-progress sales. Posted to when revenue is pre-recognized. |
| **Project Cost Account** | Final G/L account where project costs are recognized. |
| **Project Sales Account** | Final G/L account where project sales revenue is recognized. |
| **Project Expected Cost Account** | G/L account used to record expected (budgeted) costs for reporting purposes. |
| **Project Pre-recognize Sales Acc** | G/L account used when pre-recognizing sales revenue before the final invoice. |
| **Project Interim Account** | Clearing/interim account used during the invoicing process. |

> **Tip**: At a minimum, configure one Project Group for each distinct type of project in your business (e.g., one for equipment builds, one for conversions). Each type may have different revenue and cost accounts.

---

## 2.3 Project Statuses

**Page**: *Project Statuses*  
**Navigation**: Search for "Project Statuses"

Project Statuses are user-defined workflow stages. They are distinct from the fixed *Posting Status* (see [Section 3](03-project-lifecycle.md)). A Project Status tells you *where in your internal process* a project is, and it controls which actions can be taken.

### Fields

| Field | Description |
|---|---|
| **Code** | A unique code for the status (up to 10 characters). |
| **Description** | A readable label shown on the project card. |
| **Sorting** | Controls the display order of statuses in lists. |
| **Posting Status** | The fixed system posting status that this project status maps to (Enquiry, Quote, Active Project, etc.). |
| **Next Project Status Code** | The code of the status that follows this one in the process. Used to advance the project to the next stage. |
| **Reverse Project Status Allowed** | Whether the project can be moved back to a previous status. |

### Permitted actions per status

Each status has a set of flags that determine what is allowed when the project carries that status:

| Flag | Effect when enabled |
|---|---|
| **Allowed to Create Work Order** | Users may manually create a work order for the project. |
| **Create Work Order** | Work orders are created automatically when the status is assigned. |
| **Allowed to Create PO** | Users may create purchase orders linked to the project. |
| **Create Purchase Order** | Purchase orders are created automatically. |
| **Post Time Sheet** | Time sheet lines may be posted against the project. |
| **Dimension Check** | Dimensions are validated when posting. |
| **Release all Work Orders** | All open work orders on the project are released automatically. |
| **Allowed to Invoice** | Users may generate sales invoices for the project. |
| **Allowed to Deactivate** | Users may deactivate (reverse pre-recognition of) the project. |
| **Allowed to Create Equipment Objects** | Users may create new equipment objects linked to the project. |
| **Check To be Approved by** | The project must be approved before posting is allowed. |

> **Design guidance**: Define statuses that match your internal project stages (e.g., *Enquiry*, *Quotation*, *Approved*, *In Production*, *Ready for Delivery*, *Invoiced*, *Closed*). Map each status to the appropriate Posting Status and configure the permission flags carefully — this is the primary way to enforce your business process.

---

## 2.4 Default Project Tasks

**Page**: *Default Project Tasks*  
**Navigation**: Search for "Default Project Tasks"

Default Project Tasks are a library of reusable task templates. When **Enforce Default Tasks** is enabled in the Project Setup, users must choose tasks from this list rather than creating ad-hoc tasks.

### Fields

| Field | Description |
|---|---|
| **Code** | A unique task code (up to 20 characters). |
| **Sorting** | Controls the order tasks appear when selected. |
| **Description** | A label describing the task or phase. |
| **Invoicing Method** | The default invoicing method pre-filled when this task is used on a project. See [Section 7 – Invoicing and Billing](07-invoicing-and-billing.md). |
| **Costing Method** | The default costing method for this task type. |
| **Gen. Prod. Posting Group** | Default general product posting group for cost lines generated from this task. |
| **VAT Prod. Posting Group** | Default VAT product posting group. |
| **Tax Group Code** | Default tax group (used in tax area-based tax setups). |
| **Blocked** | Prevents this task from being selected on new projects. |

---

## 2.5 Source Codes

**Page**: *Source Code Setup* (extended by Projects)  
**Navigation**: General Ledger → Setup → Source Code Setup

Dysel Projects adds project-specific source codes to the standard Source Code Setup page. Source codes appear on ledger entries and allow you to identify which process generated a specific posting.

No special action is required for source codes unless your organization wants to assign specific codes to differentiate project postings in reports and analyses.

---

## 2.6 User Setup

The standard Dysel W1 User Setup is extended with project-relevant per-user or per-branch settings. These control branch-level access and defaults for individual users. Consult your system administrator if you need to restrict which branches a user can post to or create projects for.
