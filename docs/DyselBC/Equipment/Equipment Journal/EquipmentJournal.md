---
title: "Equipment Journal Reference"
parent: "Equipment Journal"
---

# Equipment Journal

The Equipment Journal allows you to register and post financial and physical mutations on equipment objects without source documents. It is comparable to a standard Business Central general journal but is specifically designed for equipment administration in Dysel BC.

To open the Equipment Journal, search for **Equipment Journal** in the Business Central search bar.

> **Note:** Posting equipment objects through the standard Business Central **General Journal** does **not** create Equipment Value Entries. Always use the Equipment Journal when mutations on equipment objects must be reflected in the equipment administration.

---

## Journal Batch

Journal lines are organised into batches. A batch logically groups lines by period, posting type, or department. When posting, only the lines of the currently active batch are processed.

To manage batches, click the **Batch Name** field at the top of the journal page and use the lookup to select or create a batch.

| Field | Description |
|---|---|
| **Name** | Unique code for the batch (max. 10 characters). |
| **Description** | Description of the batch. |
| **Source Code** | Source code assigned to postings from this batch. |
| **Recurring** | Indicates whether the batch is a recurring journal. A number series cannot be configured when this is enabled. |
| **No. Series** | Number series used to automatically assign a document number when a line is created. Required when using the **Create Depreciation Lines** function. |
| **Posting No. Series** | Separate number series for the document number at the time of posting. Must differ from **No. Series**. |

## Journal Line Fields

The following fields are visible by default on the **Equipment Journal** page.

| Field | Required | Description |
|---|---|---|
| **Batch Name** | Yes | Name of the batch the line belongs to. Displayed at the top of the page as the batch selector. |
| **Document Date** | Yes | Document date of the journal line. |
| **Posting Date** | Yes | Determines on which date the resulting entries are inserted into the ledgers. |
| **Document No.** | Yes | Document number of the journal line. Can be assigned automatically from the batch number series. |
| **Equipment Journal Type** | Yes | Type of posting. Drives the complete posting logic. See [Posting Logic per Journal Type](EquipmentJournalPostingLogic.md#posting-logic-per-journal-type). |
| **Equipment Category** | No | Category of the equipment object. Automatically populated from the object; can be used as a search filter. |
| **Equipment Group** | No | Group of the equipment object. Automatically populated from the object. |
| **Equipment Model** | No | Model of the equipment object. Automatically populated from the object. |
| **Equipment Object** | Yes | The equipment object to which the mutation applies. When filled in, category, group, model, location, branch, department, and description are automatically copied from the object. |
| **Object Serial No.** | No | Serial number of the equipment object. Read-only; sourced from the object. |
| **Item No.** | No | Item number of the serialised item linked to the object. Read-only; automatically populated. |
| **Branch** | No | Branch to which the posting is attributed. Also automatically determines the location code. |
| **Department** | No | Department code; affects the dimensions on the line. |
| **Location Code** | No | Location code of the posting. Read-only; automatically sourced from the object or branch. |
| **Description** | No | Description of the line. Automatically populated from the object. |
| **Quantity** | Yes | Quantity. For most journal types this is always 1, which the system enforces automatically. |
| **Unit Amount** | No | Amount per unit. When filled in, **Amount** is automatically recalculated. |
| **Amount** | Yes | Total amount of the journal line. A negative value creates a credit posting. |
| **Adjustment** | No | Flag indicating whether the line is a corrective posting. Does not affect the posting logic itself. |
| **Cost Code** | Conditional | Cost type used for depreciation posting. Required for **Fiscal Depreciation** and **Book3 Depreciation**, and for **Depreciation** when a G/L posting must be made. |
| **Account No.** | Conditional | G/L account number for the debit side of the posting. Required for **After Sales**, **Adjustment**, and **Fiscal Adjustment**; optional for **Depreciation**. |
| **Bal. Account No.** | Conditional | G/L balancing account number (credit side). Required for **After Sales**, **Adjustment**, **Fiscal Adjustment**, and for **Depreciation** when a G/L posting must be made. |

### Background Fields

The following fields are not visible by default but are relevant for understanding the posting results.

| Field | Description |
|---|---|
| **Statistics Type** | Statistics type stored in the resulting Equipment Value Entry. Automatically determined based on the journal type. |
| **Process** | Process type (e.g. Equipment, Rental). Automatically determined. |
| **Source Code** | Source code of the posting. Automatically populated from the batch or journal type. |
| **Equipment Posting Group** | Posting group of the object; determines which G/L accounts are used. |
| **Gen. Prod. Posting Group** | General product posting group, inherited from the object or model. |
| **Dimension Set ID** | Dimension set of the line. Automatically populated from the object, model, branch, department, etc. |
| **Reversed by Entry No.** | Indicates which Equipment Value Entry reverses this depreciation line. Read-only; cannot be filled manually. |
| **ELC Doc. Type / No. / Line No.** | Link to an ELC source document (e.g. a rental contract). Automatically populated when used programmatically. |

## Page Actions

### Line

| Action | Shortcut | Description |
|---|---|---|
| **Dimensions** | Shift+Ctrl+D | Opens the dimension editing window for the selected journal line. Allows dimension values to be manually adjusted or supplemented. |

### Object

| Action | Shortcut | Description |
|---|---|---|
| **Card** | Shift+F7 | Opens the Equipment Object Card for the object on the current line. |
| **Object Depreciation Setup** | – | Opens the depreciation setup for the object on the current line. |
| **Entries** | Ctrl+F7 | Shows all Equipment Value Entries for the object on the current line. |
| **Select Objects** | – | Opens a selectable object list. A new journal line is automatically created for each selected object, using the current line as a template. No duplicate line is created if a line for that object already exists in the current batch. |

### Functions

| Action | Shortcut | Description |
|---|---|---|
| **Create Depreciation Lines** | Shift+F11 | Opens the **EX-Object Depr.** report, which automatically generates depreciation lines for all equipment objects that have a depreciation setup configured. Any existing lines for a given object in the current batch are deleted and replaced each time the report runs. Lines with a calculated amount of zero are not inserted. Requires a **No. Series** on the current batch. |

### Posting

| Action | Shortcut | Description |
|---|---|---|
| **Post** | F9 | Posts all journal lines in the current batch. Prompts for confirmation and shows a progress window per line. After successful posting, the lines are deleted from the batch. |

For a detailed overview of what each journal type posts, which G/L entries are created, and what restrictions apply, see [Equipment Journal Posting Logic](EquipmentJournalPostingLogic.md).

