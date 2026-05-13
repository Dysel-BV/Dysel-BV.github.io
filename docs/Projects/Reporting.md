# 14. Reporting

Dysel Projects includes two dedicated reports, as well as extending several existing Dysel W1 and standard Business Central reports with project-related columns. All reports are accessible from the project list or project card via the **Reports** action group.

---

## 14.1 Dysel Project (report)

**Report name**: *Dysel Project*  
**Type**: RDLC layout (printed / PDF output)

This is the standard project document report. It prints the full project overview, and is suitable for customer-facing or internal communication.

### Content

- **Project header information**: Project no., description, status, sell-to customer, bill-to customer, shortcut dimensions.
- **Project tasks**: All tasks in sort order.
- **Budget lines** (optional): Can be shown or hidden using the **Show Budget Lines** option.

### Filters

The report request page allows filtering by:

- **Project No.**
- **Status**
- **Archive Version** — use this to print historical versions of a project (see [Section 15](15-archiving-and-closed-projects.md)).

---

## 14.2 Dysel EX-Project (report)

**Report name**: *Dysel EX-Project*  
**Type**: Excel export (processing-only, outputs to Excel workbook)

This report exports project data to Excel for further analysis, planning, or reporting outside of Business Central. It is the primary tool for ad hoc analysis of project content.

### Output

The output is a structured Excel workbook with rows for project headers, tasks, and budget lines, depending on the selected **Print Level**.

### Print Level options

| Print Level | Content |
|---|---|
| **Project** | One row per project header with key project information. |
| **Project Task** | One row per task, including task amounts, resource hours, and status. Also includes equipment-calculated values per task. |
| **Project Detail** | One row per budget line, with full detail including type, item/resource no., unit price, unit cost, quantity, amount, and cost. |

### Filters

- **Project No.** — Filter to specific projects.
- **Task** (when Print Level ≥ Project Task) — Optionally restrict to specific task codes.

---

## 14.3 Project Statistics

The **Project Statistics** page (accessible from the project card via *Statistics*) provides a real-time financial summary of a project without printing. Key figures shown:

| Field | Description |
|---|---|
| Budget Amount | Total invoicing-side budget across all tasks |
| Revised Budget Amount | Budget amount as per the active revision |
| Budget Cost | Total cost budget across all tasks |
| Revised Budget Cost | Cost budget as per the active revision |
| Total Budget Profit | Budget Amount minus Budget Cost |
| Invoiced Amount | Amount already invoiced to the customer |
| Actual Cost | Total posted actual cost |
| Actual Profit | Invoiced Amount minus Actual Cost |
| Pre Recognized Sales | Revenue recognized via WIP before invoicing |
| Deactivated Invoice Amount | Invoice amounts on deactivated/closed tasks |
| Deactivated Cost | Costs on deactivated/closed tasks |
| Posted Profit | Net financial result posted to G/L |

---

## 14.4 Report extensions

### Purchase Put-Away List / Put-Away Lines

When purchase orders carry project references, those project fields are included in the **Put-Away List** and **Put-Away Lines** reports, allowing warehouse staff to see which project a received item belongs to.

### Change Model

The **Change Model** report (Dysel W1) is extended to include project context when a model change is related to a project conversion (see [Section 11.7](11-equipment-integration.md#117-change-model-report)).
