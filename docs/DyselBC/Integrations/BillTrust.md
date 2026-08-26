---
title: "BillTrust Connector"
parent: "Integrations"
grand_parent: "Dysel BC"
---

# BillTrust Connector

## Overview

The **BillTrust Connector** integrates BillTrust cash application and lockbox services with Dysel Business Central. The connector automates three primary workflows:

- **PDF Document Export** — Automatic PDF generation of invoices and credit memos for BillTrust distribution
- **Cash App File Import** — Ingest payment and cash application data from BillTrust Cash App into Business Central
- **Bank Deposit Integration** — Automatically create bank deposit and general journal entries from imported Cash App data, with support for deductions, short payments, overages, and discounts

**Core Objects:**

| Object | Purpose |
|--------|---------|
| **Billtrust Setup Card** | Configure connector settings (access, document filters, distribution rules) |
| **Billtrust Logs** | View audit trail of all imports and document processing |
| **Billtrust Log Details** | Drill into individual documents processed in each import run |
| **Cash App Files** | Imported Cash App line items; used to create bank deposits |
| **Import Cash App Data in Bank Deposit** | Report that creates journal entries from Cash App files |
| **Billtrust UDF File** | Report to export customer account data to BillTrust in UDF format |

---

## System Requirements

| Requirement | Details |
|---|---|
| **Business Central Version** | 28.0 or later |
| **Base App** | Microsoft Dynamics 365 Business Central |
| **Bank Deposits Module** | Required for bank deposit integration workflows |
| **Admin Setup Access** | `BillTrust Setup` permission set |
| **Daily Operations** | `BillTrust` permission set |
| **Import Users** | Require `Create` and `Modify` permissions on `Cash App File` and `General Journal Line` tables |

---

## Setup

### BillTrust Setup Card

Open the **Billtrust Setup Card** from the Business Central search bar. This is the single configuration record for your connector.

#### General Settings

| Field | Purpose | Default |
|-------|---------|---------|
| **Username** | The BillTrust user account name used for logging and audit purposes | — |
| **Default Language** | Default language code for PDF generation (e.g., `ENG` for English) | ENG |
| **Use Extended Currency** | Enable extended currency code support (use if multi-currency with 3+ char codes) | Off |
| **Doc Distribution Code** | Links to the Document Distribution W1 ELC record; controls PDF routing rules | — |
| **Allow Journal Entries** | When enabled, permits Cash App imports to create general journal entries | Off |

#### Advanced Filters

Use these drill-down fields to restrict which data BillTrust can access. Leave blank to include all data.

| Filter | Purpose | Example |
|--------|---------|----------|
| **Customer View** | Restrict which customers appear in PDF exports and Cash App matching | `Customer Posting Group = "DOMESTIC"` |
| **Cust. Ledger Entry View** | Restrict which ledger entries are eligible for Cash App matching | `Remaining Amt. (LCY) <> 0` |
| **Posted Sales Invoices View** | Restrict which invoices generate PDFs | Filter by date, customer, document status |
| **Posted Sales Cr. Memo View** | Restrict which credit memos generate PDFs | Filter by date, customer, document status |

### Configure Document Distribution

If using PDF export:

1. Open **Document Distribution W1 ELC** setup
2. Create or select the distribution code referenced in the **Doc Distribution Code** field
3. Configure PDF routing (folder, email, or BillTrust endpoint)
4. Return to **Billtrust Setup Card** and save

### Assign Permissions

Grant users the appropriate permission sets based on their role:

| Permission Set | Access Level |
|---|---|
| **BillTrust** | Standard daily operations: run Cash App imports, view logs |
| **BillTrust Internal** | Internal administrative access |

---

## Common Workflows

### Export Invoices and Credit Memos as PDFs

This workflow is typically run by finance or collections staff, and can be automated to run nightly.

**Steps:**

1. Search for **Billtrust UDF File** report
2. Click **Preview & Print**
3. Set optional filters (date range, customer, etc.)
4. Click **Send to** and choose output format:
   - **PDF** — Download for manual upload
   - **Email** — Send to distribution list
   - **Schedule** — Set up recurring runs (recommended: nightly)

**Output:** Plain-text UDF file (`BilltrustData_[Date].txt`) containing customer data and all open invoices, ready to upload to BillTrust.

---

### Import Cash App Payment Files

This workflow consists of two steps: (1) import the raw Cash App file, then (2) create bank deposits from the imported data.

**Step 1: Import Cash App Data File**

1. Obtain the Cash App export file from BillTrust (CSV or XML format)
2. Search for **Import Cash App Data BT ELC** (XMLPort)
3. Click **Import** and select the file
4. The system parses the file, creates records in **Cash App File BT ELC**, validates amounts, and logs errors

**Imported data includes:** Export/Job IDs, bank details, customer info, invoice amounts, deduction codes (SHORT, DISC, TAX, FLEET, OTH, etc.), and batch identifiers.

**Step 2: Create Bank Deposit from Imported Data**

1. Navigate to **Bank Deposits**
2. Create a new bank deposit or open one for the import date
3. Search for **Import Cash App Data in Bank Deposit** report
4. Set filters:
   - **Journal Template/Batch Name** — Select deposit template (e.g., `BANK`)
   - **Batch Import Date** — Filter by date range (optional)
   - **Import ID** — Filter by specific BillTrust run (optional)
5. Click **OK** to create journal lines
6. The system creates separate lines for payments and deductions, validates amounts, and updates Cash App File records to "InJournal"
7. Review lines in **General Journal** for accuracy
8. Post the journal to complete the deposit

**Validation formula:** Payment amount + Total deductions = Total remittance. The report errors if amounts do not balance.

---

### View and Audit Import History

1. Search for **Billtrust Logs** list page
2. View all import runs in reverse chronological order (newest first)
3. Each row shows:
   - **Entry No.** — Unique identifier
   - **Run Date/Time** — When executed
   - **Run By** — User who initiated
   - **Total Documents** — Count of documents processed
   - **Total Errors** — Count of failed documents (highlighted in red if > 0)
4. Click any row to drill into **Billtrust Log Details** for document-level information

#### Log Detail Fields

| Field | Description |
|-------|-------------| 
| **Customer** | Customer number from the invoice |
| **Document Type** | Invoice or Credit Memo |
| **Document No.** | Sales document number |
| **PDF Exported** | True = success; False = error |
| **Print Status** | Success, Error, or Pending |
| **Print Error** | Error message if Print Status = Error |

#### Print Status Meanings

| Status | Meaning |
|--------|---------|
| **Success** | Document processed without issues |
| **Error** | Document failed; check Print Error message |
| **Pending** | Document queued but not yet processed |

### Common Error Messages & Causes

| Error Message | Cause | Solution |
|---------------|-------|----------|
| "Missing customer address" | Invoice customer has no address on file | Update customer master with billing address |
| "Invalid document type" | Document type is not Invoice or Credit Memo | Verify source document type; may be journal entry or other |
| "PDF generation failed" | PDF print layout is broken or missing | Check DYSEL system PDF setup; verify print layout assigned to document |
| "Customer excluded from Billtrust" | Customer record has "Exclude from Billtrust BT ELC" checkbox enabled | Uncheck the exclusion flag on the customer card if intended for BillTrust |
| "Date filter excluded document" | Document posting date is outside the configured filter | Adjust the As of Date or date filter when running the report |

---

## Troubleshooting & Common Issues

### Amount Mismatches

**Error:** `Amounts Do Not Match: AmountPaid + TotalDeductionAmt <> OpenAmount`

**Cause:**  The Cash App file contains a mismatch between:
- `AmountPaid` (the actual payment received)
- `TotalDeductionAmt` (total deductions: short payments, discounts, fees, tax adjustments)
- `OpenAmount` (the remaining invoice balance after deductions)

**Formula that should hold:**  
`AmountPaid + TotalDeductionAmt = OpenAmount`

**Resolution:**

1. Obtain the original Cash App export file from BillTrust
2. Verify the payment amount, deduction codes, and invoice balance in the file
3. Check the **Deduction Info** field on the Cash App File record; it may contain parsing errors
4. Contact BillTrust support if the data is corrupted in the source system
5. If the discrepancy is small (rounding), work with your finance team to decide if a manual adjustment entry is warranted

### Import Files Not Processing

**Symptom:** Cash App file was imported but no records appear in **Cash App Files** table, or import seems to hang

**Causes & Solutions:**

| Cause | Solution |
|-------|----------|
| File is in wrong format (not CSV or XML that BillTrust exports) | Verify the file comes from BillTrust Cash App exports; check file extension and header |
| File is empty or has only a header row | Confirm the export from BillTrust includes data rows; check date range in BillTrust export |
| User running import lacks permissions | Verify user has `BillTrust` permission set and `Create` permission on Cash App File table |
| Parsing error in XMLPort (field mapping mismatch) | Check the import log for field-level errors; escalate to development if field structure changed |
| Date/Time is outside active import window | Some BillTrust configurations have time-window restrictions; confirm with BillTrust timing |

**Diagnostic Steps:**

1. Check **Cash App Files** table (`Ctrl+Alt+I` to open table directly) — do records exist?
2. Review the import report output — does it show errors?
3. Check **Event Log** (if enabled in DYSEL system) for XML parsing errors
4. Try importing a small test file to isolate the issue

### PDF Export Not Running

**Symptom:** Billtrust UDF File report runs but produces no output, or output is empty

**Causes & Solutions:**

| Cause | Solution |
|-------|----------|
| No customers match the active filters | Remove or broaden customer filters; check Customer View setting in Billtrust Setup |
| All customers are marked "Exclude from Billtrust" | Review the exclusion flag on customer cards; uncheck if intended for export |
| No open invoices exist for the date range | Verify invoices are posted and have remaining balance; check date filter |
| Posted Sales Invoices View filter is too restrictive | Click the drill-down in Billtrust Setup Card and review the filter; may be excluding all documents |
| Report permissions are missing | Confirm user has `Run Report` permission for "Billtrust UDF File" report (check Billtrust permission set) |

**Diagnostic Steps:**

1. Run the report without filters first (remove all filters)
2. Check the customer count — do customers exist in your system?
3. Open a customer card and verify no "Exclude from Billtrust" flag is set
4. Manually query: Go to **Sales Invoice Header** > search for a recent invoice > verify it is posted and not archived
5. If still failing, try a simplified filter (e.g., date = today only) to narrow scope

### Users Can't Access Billtrust Logs

**Symptom:** User receives "You do not have permission to read the Billtrust Logs table"

**Solution:**

1. Open **Permission Sets** (in Business Central Administration area)
2. Find or create `BillTrust` permission set
3. Ensure the user (or the user's role) is assigned the `BillTrust` permission set
4. Verify the permission set grants at least `Read` access to tables:
   - Billtrust Log BT ELC
   - Billtrust Log Detail BT ELC
   - Cash App File BT ELC
5. Assign the permission set to the user
6. User logs out and back in for permissions to take effect

### Bank Deposit Journal Lines Not Posting

**Symptom:** Journal lines are created by the import report, but posting fails with errors

**Common Errors & Fixes:**

| Error | Fix |
|-------|-----|
| "Account does not exist" | Verify deduction codes map to valid GL accounts; check GL Account setup for deduction codes (COA, DISC, TAX, FLEET, etc.) |
| "Customer does not exist" | Ensure the customer number in Cash App file matches a customer in Business Central |
| "Bank account not found" | Verify the bank account on the bank deposit header is valid and active |
| "Document already exists" | A journal line with this document number was already posted; check for duplicate imports |
| "Dimensions do not match" | Verify dimension codes on the journal line match the customer's default dimensions |

**Prevention:**

1. Always preview the generated journal lines before posting
2. Run a pilot import with test data first
3. Use a separate batch name for each import to avoid accidental overwrites
4. Reconcile total Cash App amounts to bank deposit amounts before posting

---

## Best Practices

### 1. Schedule Regular PDF Exports

- **Frequency:** Daily or at least 3x per week
- **Timing:** Run at off-peak hours (e.g., 10 PM)
- **Method:** Schedule the **Billtrust UDF File** report using the **Schedule** option
- **Why:** Keeps BillTrust synchronized with current customer and invoice data, improving match rates and reducing manual rework

### 2. Validate Before Bank Deposit Posting

1. Import Cash App file
2. Generate journal lines (report)
3. **Stop and review:** Open the **General Journal** batch
4. Spot-check 5–10 lines for:
   - Correct customer
   - Correct amounts
   - Correct GL accounts for deductions
5. Only after validation → **Post** the journal

### 3. Monitor Error Logs Weekly

- Schedule a 15-minute review of **Billtrust Logs** each Monday
- Filter for runs with `Total Errors > 0`
- Investigate and document root causes
- Track trends (e.g., "every Tuesday we see 5 PDF failures" → may indicate a process issue)

### 4. Keep Setup Documentation Updated

Maintain a record (spreadsheet or wiki) of:
- Which customer segments are included/excluded
- Document distribution code and routing rules
- Deduction codes and their GL account mappings
- Date ranges for regular exports (e.g., "export all invoices from last 90 days")
- Contact info for BillTrust support liaison

### 5. Archive Old Log Data Periodically

- **Billtrust Logs** records grow over time (hundreds per year)
- Every 6–12 months, export old logs to archive storage (CSV/Excel) and delete from production
- Retention policy: typically keep 2–3 years of detail logs for audit

### 6. Test Deduction Mappings Carefully

Deductions (SHORT, DISC, TAX, FLEET, PORTAL, WOF, OTH, DISC, COA) must map to valid GL accounts:
- Create a GL account naming convention for deductions (e.g., `DEDUCT-DISCOUNT`, `DEDUCT-SHORT`)
- Test a sample Cash App import with each deduction code present
- Verify that all expected deduction GL accounts exist and accept postings

### 7. Align with BillTrust Cadence

- Coordinate import frequency with BillTrust's export schedule
- If BillTrust exports twice daily, arrange for BC imports to occur shortly after
- Document the SLA: "We import within 2 hours of BillTrust export"
- Communicate any outages to BillTrust operations

---

## FAQ

**Q: Can I edit a Billtrust Log Detail record after it's been created?**  
A: No. Log detail records are read-only; they are audit records. If you need to re-process a document, re-run the import with updated source data.

**Q: What happens if I import the same Cash App file twice?**  
A: The system will create duplicate records in the **Cash App File** table. You must manually delete duplicates or use a filtered import (by Export Detail ID or Batch Import Date) to avoid re-processing.

**Q: Can I manually exclude a customer from PDF export without using filters?**  
A: Yes. On the **Customer Card**, there is a checkbox: **Exclude from Billtrust BT ELC**. Check this box to exclude that customer from all BillTrust exports.

**Q: How do I handle partial/short payments from a customer?**  
A: The Cash App file includes deduction codes. Short payments are coded as `SHORT` in the **Deduction Info** field. When the import report runs, it automatically creates a separate journal line for the short amount, which you can reconcile against the customer's account.

**Q: What's the difference between "PDF Exported" and "Print Status" in the logs?**  
A: **PDF Exported** = Boolean flag indicating if a PDF file was successfully created. **Print Status** = Enum (Success, Error, Pending) indicating the overall document processing status. A document can have PDF Exported = TRUE and Print Status = Success (ideal), or PDF Exported = FALSE and Print Status = Error (problem to fix).

**Q: Can I re-export PDFs for a document that already has PDF Exported = TRUE?**  
A: Yes. Use the **Force** option in the Billtrust UDF File report to re-export all documents, even if they have already been exported. This is useful if you need to regenerate PDFs due to address updates or other corrections.

**Q: Where do the generated PDF files go?**  
A: This depends on the **Document Distribution Code** configured in the Billtrust Setup Card. The document distribution settings control whether PDFs are:
   - Saved to a file share or OneDrive
   - Emailed to a distribution list
   - Sent to a print queue
   - Forwarded to an external system (e.g., BillTrust API)  
   
   Contact your system administrator if you are unsure where PDFs are routed.

---

## Support & Escalation

**For Configuration Questions:**  
Contact your Dysel system administrator or implementation consultant.

**For BillTrust Integration Issues:**  
Provide the following information when contacting BillTrust support:
- Cash App File Export Detail ID(s)
- Import Date/Time (from Billtrust Log Entry No.)
- Error message (from Billtrust Log Detail **Print Error** field)
- Sample record data (export to Excel for review)

**For Bugs or Development Requests:**  
Submit to the Dysel development team with:
- Clear description of the issue or feature request
- Steps to reproduce (if a bug)
- Screenshot or log entry evidence