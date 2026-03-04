---
title: "Dysel Setup"
parent: "DyselBC_Setup"
---

# Dysel Setup

The **Dysel Setup** page is the central configuration hub for your Dysel BC environment. It controls how key processes behave across the entire system — from work order handling and rental contracts to financial posting and time registration. You only need to configure this page once per company, though settings can be adjusted at any time.

To open the Dysel Setup page, search for **Dysel Setup** in the Business Central search bar.

---

## General

These settings control company-wide behavior that does not fall under a specific module.

| Field | Description |
|---|---|
| **Invoice Line Min. Amount** | The minimum amount that a work order or service line must have before it can be included on an invoice. Lines with a lower amount will be blocked from invoicing. Leave empty to allow any amount. |
| **Description in Customer Language** | When enabled, item and service descriptions on documents such as work orders and invoices will be shown in the customer's own language, provided translations have been set up. |
| **Responsibility Center Mandatory on Documents** | When enabled, every document (work order, sales order, etc.) must have a responsibility center before it can be posted or released. |
| **Branch Mandatory on Documents** | When enabled, every document must have a branch code filled in. Useful when your organization works across multiple locations or branches. |
| **Department Mandatory on Documents** | When enabled, every document must have a department code filled in. |
| **Time Zone** | The default time zone for your company. This is used to correctly interpret dates and times when working with mobile apps or integrations that process records from different time zones. |

---

## Number Series

Number series define the automatic numbering of documents and records created in Dysel BC. Each field points to a number series that has been set up under **Number Series** in Business Central.

### Rental

| Field | Description |
|---|---|
| **Rental Rate Nos.** | Controls the numbering of rental rate records. |
| **Manual Rental Rate Nos.** | Controls the numbering of manually created rental rate records. |
| **Rental Contract Nos.** | Controls the numbering of rental contracts. |
| **Rental Quote Nos.** | Controls the numbering of rental quotes. |
| **Rental Calculation Nos.** | Controls the numbering of rental calculation records. |
| **Lost Deal Nos.** | Controls the numbering of lost deal records, which are used to track rental contracts that were not converted into active rentals. |

### Equipment

| Field | Description |
|---|---|
| **Equipment Model Nos.** | Controls the numbering of equipment models. |
| **Equipment Object Nos.** | Controls the numbering of individual equipment objects (physical machines). |
| **Barcode Equipment Model Nos.** | Controls the numbering of barcodes generated for equipment models. |
| **Configuration Option Nos.** | Controls the numbering of equipment configuration options. |
| **Configuration Template Nos.** | Controls the numbering of equipment configuration templates. |
| **Configuration Nos.** | Controls the numbering of completed equipment configurations. |

### Service

| Field | Description |
|---|---|
| **Work Order Nos.** | Controls the numbering of work orders. |
| **Work Order Quote Nos.** | Controls the numbering of work order quotes. |
| **Job Code Nos.** | Controls the numbering of internal job codes used on work orders. |
| **Service Visit Nos.** | Controls the numbering of service visits (used in the mobile field service process). |
| **Maintenance Contract Nos.** | Controls the numbering of maintenance contracts. |
| **Maintenance Contract Quote Nos.** | Controls the numbering of maintenance contract quotes. |
| **Maintenance Price Nos.** | Controls the numbering of maintenance price records. |
| **Certificate Nos.** | Controls the numbering of equipment certificates. |

### Miscellaneous

| Field | Description |
|---|---|
| **Transport Order Nos.** | Controls the numbering of transport orders. |
| **Consolidated Order Nos.** | Controls the numbering of consolidated orders. |
| **Claim Nos.** | Controls the numbering of warranty or insurance claims. |
| **Financing Nos.** | Controls the numbering of financing records. |
| **Capex Nos.** | Controls the numbering of capital expenditure (CAPEX) records. |
| **Vendor Receipt Nos.** | Controls the numbering of vendor receipts. |
| **Cash Register Session Nos.** | Controls the numbering of cash register sessions. |
| **Cash Register Statement Nos.** | Controls the numbering of cash register statements. |
| **Work Type Schedule Nos.** | Controls the numbering of work type schedules. |
| **Payroll Schedule Nos.** | Controls the numbering of payroll schedules. |
| **Item No. Series From Catalogue** | Controls the numbering of items that are created from the equipment catalogue. |
| **Cylinder Nos.** | Controls the numbering of gas cylinder records. |

---

## Document Distribution

Document distribution controls how emails are sent from Dysel BC, for example when emailing invoices, rental contracts, or work order documents directly to customers.

> **Note:** The fields in this section are only visible when the Enhanced Email Handling feature has been enabled in Dysel Feature Management.

| Field | Description |
|---|---|
| **Main Email Account Address** | The email account used to send outgoing emails via document distribution. This account requires the appropriate permissions on your email server. Click the field to open a lookup and select the account. |
| **Account Connector** | Displays the connector (email provider) associated with the selected email account. This field is informational and cannot be edited directly. |
| **Open Email Before Sending** | When enabled, the email editor will open before each email is sent, giving you the opportunity to review and adjust the message. When disabled, emails are sent directly without review. |

You can use the **Clear Doc. Distribution Email** button on the action bar to remove the configured email account.

---

## Rental

These settings control the default behavior of rental contracts.

| Field | Description |
|---|---|
| **Default Start Time** | The default time of day that a rental contract starts when the contract type uses date-and-time calculation. |
| **Default Finishing Time** | The default time of day that a rental contract ends when the contract type uses date-and-time calculation. |
| **Show Configuration Subpage** | When enabled, a subpage showing the equipment configuration is displayed on the rental contract. |
| **Rental Deliver Return Posting Date** | Determines which date is used as the posting date when delivering or returning rental equipment. Options are: **Contract Header** (the date on the contract), **Work Date** (today's work date in Business Central), or **No Date** (no date is set automatically). |
| **Rental Availability Calculation** | Controls how the availability of rental equipment is calculated. When set to **Advanced**, the calculation method can be configured in further detail directly on this field. |

---

## Equipment

These settings control the behavior of equipment models and equipment objects throughout the system.

| Field | Description |
|---|---|
| **Equipment Serial Number Check** | Determines when the system checks for duplicate serial numbers. Choose **On Purchase Delivery** to check when receiving equipment from a vendor, **On Work Order Usage** to check at the point of usage, or **Never** to disable the check. It is strongly recommended to keep serial numbers unique. |
| **Duplicate Serial Nos.** | Defines what happens when a duplicate serial number is detected. The available options are configured via the **Duplicate Serial Nos.** enum. |
| **Replenishment System for Base Models** | Sets the default replenishment method used when creating purchase suggestions for base model equipment. |
| **Function Parent Object** | Determines which record type is treated as the parent in functional relationships between equipment objects. |
| **Object History Log** | Controls whether changes to equipment objects are logged. Select the level of detail you want recorded. |
| **Default Item Category for Parts** | The item category automatically assigned to items created from dealer options in the configurator. |
| **Apply Service Actions** | Controls how and when service actions are automatically applied to equipment objects. |
| **Create Service Action Entry** | Determines whether a service action entry is created automatically when relevant activity occurs. |
| **On Hold Duration (Equipment Objects)** | The default period for which an equipment object is placed on hold when a salesperson is assigned to the **On Hold Salesperson** field on the object card. Enter a date formula, such as `1M` for one month. |
| **Do Not Change Customer After Delivery** | When enabled, the customer on an equipment object cannot be changed once the equipment has been delivered. |
| **Recommended Caption** | A custom label used to identify "Recommended" options in the equipment configurator, so users see terminology that fits your business. |
| **Mandatory Caption** | A custom label used to identify "Mandatory" options in the equipment configurator. |
| **Equipment Model Item No. Series** | The number series used when automatically creating item numbers for equipment models. Must be different from the standard item number series, and a valid relationship between the two must be set up in the **No. Series Relationship** table. |
| **Depreciation Rounding Precision** | The rounding precision applied to equipment depreciation calculations. For example, entering `0.01` rounds depreciation amounts to the nearest cent. |

---

## Work Order

### Resource Handling

These settings control how resources, time sheets, and time registration interact with work orders.

| Field | Description |
|---|---|
| **Use Resource Skills** | When enabled, the system checks whether a resource has the required skill set before it can be assigned to a work order. |
| **Time Sheet Unit of Measure Code** | The unit of measure applied to hours transferred from time sheets to work order lines. Typically set to a unit representing hours (e.g. `HOUR`). |
| **Timesheet Work Type Code** | Determines whether a work type code is required when transferring time sheet lines to a work order. Choose **Normal** (optional), **Mandatory** (required), or **Warning** (a reminder is shown but it is not blocked). |
| **Post Usage from Timeline** | When enabled, work order usage is automatically posted when time sheet lines are transferred to the work order. |
| **Compress Hours on Work Order** | Controls whether multiple time registrations for the same resource and work type are combined into a single work order line. Options: **No**, **Per Day**, **Per Week**, or **Per Month**. |
| **Payroll Code on Work Order** | Determines whether lines with different payroll codes must be placed on separate work order lines during time sheet transfer. Choose **Ignore** to combine them, or **Always Use** to keep them separate. |
| **Travel Charge Code** | The charge code used to record chargeable travel (mileage) when transferring time sheet lines to a work order. |

### Default Values

These settings provide default values that are filled in automatically when a new work order is created.

| Field | Description |
|---|---|
| **Date Meter Reading** | Controls when meter readings on equipment objects are updated in relation to work order activity. |
| **Default Starting Date** | Determines the default starting date on new work orders. Choose **Fill Workdate** to automatically use today's work date, or **Leave Blank** to leave the field empty. |
| **Default Duration** | The default duration for a new work order. Together with the starting date, this determines the finishing date. Enter the duration as a time interval (e.g. 2 hours). |
| **Default Response Time** | The default response time for a work order, indicating how quickly a technician is expected to respond. |
| **Ship-to on Purchase Order** | Determines which ship-to address is automatically applied to purchase orders created from a work order. |

### Posting

These settings control financial posting behavior related to work orders.

| Field | Description |
|---|---|
| **Show Missing Unit Price Message** | When enabled, a warning is displayed when a work order line is missing a unit price at the time of posting. |
| **Service Type Internal Aftersales** | The service type code used for internal aftersales costs. Only relevant when **Invoice Aftersales Cost Internally** is enabled. |
| **Invoice Aftersales Cost Internally** | When enabled, the cost of aftersales work is invoiced as an internal transaction rather than charged externally to the customer. |
| **Service Type External Aftersales** | The service type code applied to external aftersales work. Only visible when **Invoice Aftersales Cost Internally** is enabled. |
| **Post Sublet on Purchase Order** | When enabled, the invoicing of subcontracted (outsourced) work that is received on linked purchase orders is handled from the purchase document rather than from the work order. |
| **Allow Profit on Internal Work Order** | When enabled, internal work orders can include a profit margin on the lines. |
| **Close Work Orders on Invoice** | Controls whether a work order is automatically set to **Closed** after it has been fully invoiced. Choose **Automatic** to close the work order or **No** to leave it open. Note that certain conditions (such as open service visits, outstanding claims, or unposted time sheet lines) may prevent automatic closing even when this option is enabled. |
| **Close Work Order at Invoice Claim** | When enabled, a work order is closed when the claim linked to it is invoiced. |
| **Allow Work Order Invoicing if Claim is Submitted** | When enabled, a work order where the service type is set to **Claim** can still be invoiced even if the claim line has been submitted but not yet finalised. |

### Reporting Codes

Work order reporting codes are free-text labels that appear on the work order as user-defined classification fields. They can be used for statistical analysis, grouping, or external reporting.

| Field | Description |
|---|---|
| **Caption Configuration RP1** | The label shown for the first reporting code field on the work order. Define this to reflect your internal terminology (e.g. *Project Type* or *Fault Category*). |
| **Caption Configuration RP2** | The label for the second reporting code field. |
| **Caption Configuration RP3** | The label for the third reporting code field. |
| **Caption Configuration RP4** | The label for the fourth reporting code field. |

> **Tip:** You can set up translated values for each reporting code caption using the **Translations** actions in the navigation bar.

### Automatic Behavior

These settings control how the system reacts automatically during work order processing.

| Field | Description |
|---|---|
| **Modify Service Type on Work Order Lines** | Determines under which circumstances the service type can be changed on existing work order lines. |
| **Object Reaction Method Service** | Controls how the system reacts when a service-related event occurs on an equipment object (for example, when a service action becomes due). |
| **Check Data on Line Transfer** | When enabled, the system validates required data on work order lines at the moment of transfer (for example from a quote to a work order). |
| **Hide Instructions on Work Order** | When enabled, the instructions section on the work order is hidden from view, keeping the work order screen cleaner for technicians who do not need it. |
| **Double Work Order Handling** | Determines how the system behaves when a duplicate work order is detected (for example, a second work order for the same equipment and fault type). |
| **Work Order Default Line Type** | The default type applied to new lines added to a work order (for example, *Item*, *Resource*, or *G/L Account*). |

---

## Time Sheet

These settings influence how time sheet data is processed and how it interacts with work orders and payroll.

| Field | Description |
|---|---|
| **Filter Parent Object in Timesheet** | When enabled, the equipment object lookup on a time sheet is filtered to show only objects that are linked to a parent object. Useful when technicians work on specific sub-equipment. |
| **Filter on Work Order in Timesheet** | Controls whether a filter is applied to work orders shown in the time sheet. Options include **No Filter** (all open work orders are shown), **Start/End Date** (only work orders within the relevant dates are shown), or **Assigned Resource** (only work orders to which the technician is assigned are shown). |
| **Use Schedule in Timesheet** | Determines whether work schedules are taken into account when processing time sheets. |
| **Credit Account Unproductive** | The general ledger account to which unproductive time (non-billable hours not linked to a work order) is posted. |

---

## Parts

These settings control the behavior of parts management, purchasing, and inventory.

| Field | Description |
|---|---|
| **UC Purchase Order** | Determines how the system handles items on a purchase order that are flagged as **Used and Certified** (UC). |
| **UC Work Order** | Determines how the system handles UC items on a work order. |
| **Block Substituted on Documents** | When enabled, items that have been substituted (replaced by an alternative part) are blocked from being added to new documents. |
| **Create Catalogue Item Manually** | When enabled, new catalogue items must be created manually; the system will not create them automatically. |
| **SKU Last Direct Cost Update** | When enabled, the **Last Direct Cost** on stockkeeping units (SKUs) is updated automatically when items are received. |
| **Job Queue Requisition Template** | The requisition template used when the automated planning process (calculate plan) is run via a job queue. Only templates of the type **Req.** are available. |
| **Job Queue Requisition Worksheet** | The specific worksheet within the requisition template used by the job queue planning process. This worksheet must belong to the template selected in the field above. |

---

## Financial

These settings control financial posting, journal usage, and general ledger accounts used by Dysel BC processes.

| Field | Description |
|---|---|
| **Overrule Check Invoice Amount** | When enabled, the system allows the posting of invoices with a negative amount and credit memos with a positive amount. Use with caution. |
| **Direct Transfers Allowed** | When enabled, direct stock transfers between locations are permitted without requiring a transit location. |
| **Journal Template Name** | The general journal template used for financial postings originating from Dysel BC processes (such as equipment depreciation and conversion entries). This field is required. |
| **Journal Batch Name** | The journal batch within the template above, used for financial postings. This field is required. |
| **Depreciation Journal Batch** | The specific journal batch used for equipment depreciation postings. This field is required. |
| **G/L Account Conversion** | The general ledger account used for equipment conversion entries (for example when converting a new machine from stock to a rental fleet asset). This field is required. |
| **G/L Account Applied Entries** | The general ledger account used when applied ledger entries are posted. This field is required. |
| **Depreciation Interim Account** | The interim general ledger account used during the depreciation posting process. This field is required. |

---

## Configurator

The configurator allows sales staff to build equipment configurations with optional and mandatory add-ons. The following fields let you customise the labels for four flexible data fields available on configuration templates.

| Field | Description |
|---|---|
| **Caption Configuration Dynadecimal 1** | Custom label for the first flexible decimal field on the configuration template (e.g. *Weight* or *Engine Capacity*). |
| **Caption Configuration Dynadecimal 2** | Custom label for the second flexible decimal field. |
| **Caption Configuration Dynacode 1** | Custom label for the flexible code field on the configuration template (e.g. *Color Code*). |
| **Caption Configuration Dynatext 1** | Custom label for the flexible text field on the configuration template (e.g. *Special Instructions*). |

---

## ODS

> **Note:** This section is currently hidden in the standard interface. The fields below are available for organizations that work with ODS (Ozone-Depleting Substances) regulations, such as companies handling refrigerants or gas cylinders.

| Field | Description |
|---|---|
| **ODS Start Weight Tolerance** | The accepted tolerance (in kilograms or your configured unit) when registering the starting weight of an ODS substance. |
| **Yearly Maximum Leakage %** | The maximum permitted annual leakage percentage for ODS equipment, as required by applicable regulations. |
| **2-Year Maximum Leakage %** | The maximum permitted leakage percentage measured over a two-year period. |

---

## Further Reading

- [Work Orders](../Service/Work%20Orders/)
- [Service Planning](../Service/ServicePlanning/)
- [Parts – SKUs](../Parts/SKUs/)
