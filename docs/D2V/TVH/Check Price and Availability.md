---
title: "TVH-P&A"
parent: "TVH"
published: false
nav_order: 30
---

# Check Price and Availability

The **Check Price and Availability** feature sends the item lines on a purchase order to TVH and retrieves current stock levels, account pricing, and item details. The results appear in a worksheet where you can review what TVH has on offer and optionally write prices and descriptions back to the purchase order.

---

> 
> ### <span style="color:CornflowerBlue">Note: this functionality is still being developed and is expected to become available in 2026 release wave 1 (May - October)</span>
> #### <span style="color:CornflowerBlue">This is an estimated release and is subject to change.</span>
> 

---

## Before You Start

Before using Check Price and Availability, make sure:

- The TVH interface has been set up and the connection has been tested. See [Setting Up the TVH Connection](Setting Up the TVH Connection.md).
- Each location code used on the purchase order has been mapped to a TVH warehouse. This is done in Step 3 of the setup guide.
- Each purchase line has a **Vendor Item No.** filled in with the TVH part number. If a line does not have one, TVH will not be able to identify that part and will return an item error for that line.

---

## Opening the Check

### From the ribbon[text](<../../../../../Additional Apps/D2VSuite/D2V TVH/App/docs/Setting Up Carrier Codes for TVH Warehouses.md>)

On the Purchase Order card, go to the **Prepare** tab in the ribbon. You will see a **D2V** button.

- **Left-click** the D2V button to run Check Price & Availability directly.
- Click the **dropdown arrow** on the right side of the button to access other D2V actions such as Submit Order.

### Keyboard shortcut

Press **Ctrl+Shift+P** anywhere on the Purchase Order card to run the check without opening any menus.

> **Note:** The D2V button and keyboard shortcut are only available on Parts purchase orders with a status of blank (open) or Draft, and only when a TVH interface is configured for the vendor on the order. If the button does not appear, ask your administrator to verify the interface setup.

---

## The Results Page

When the check completes, the **Price and Availability** page opens and shows one row per item line that TVH responded to.

### Result columns

| Column | What it shows |
|---|---|
| **TVH Item No.** | The part number as TVH identifies it. |
| **Description** | The item description returned by TVH. |
| **Total Inventory Qty.** | The total stock quantity across all TVH warehouses. Select the row to see the per-warehouse breakdown in the **Warehouse Inventory** factbox on the right. |
| **Item Price** | Your account price for this item. |
| **List Price** | The standard TVH list price. |
| **Core Price** | The core charge for this item, if one applies. |
| **Currency Code** | The currency the prices are quoted in. If this differs from your purchase order currency, review the pricing before applying. |
| **Backorderable** | Checked if TVH can fulfil this item on backorder when it is out of stock. |
| **Is HazMat** | Checked if TVH classifies this item as hazardous material. |
| **Is Non-Returnable** | Checked if this item cannot be returned to TVH. |
| **Item Error** | If TVH could not price this item, the error message from TVH appears here and the row is highlighted in orange. |

### Row highlighting

Rows shown in **orange** mean TVH returned an error for that specific item — for example, the part number was not recognised. The **Item Error** column explains what went wrong. All other rows in the same result are still valid and can be applied normally.

### Factboxes

| Factbox | What it shows |
|---|---|
| **Warehouse Inventory** | Stock quantities per individual TVH warehouse for the selected row. |
| **Quantity Breaks** | Price tiers for the selected item. TVH may offer a lower unit price when ordering larger quantities. |

---

## Update Options

At the top of the results page you will find three options. All three are off by default. Switch on the ones you want **before** clicking OK.

| Option | What it does when you click OK |
|---|---|
| **Update Unit Price** | Copies the **Item Price** from TVH into the **Direct Unit Cost** on the matching purchase line. |
| **Update Description** | Copies the **Description** from TVH into the **Description** on the matching purchase line. |
| **Update Non-Returnable** | Updates the returnable flag on the purchase line to match the **Is Non-Returnable** value returned by TVH. |

> **Tip:** If you only want to check stock levels without changing anything on the purchase order, leave all three options off and click **Cancel** — no lines will be touched.

---

## Applying the Results

- Click **OK** to write the selected updates back to the purchase order. Lines that have an item error in the results are skipped automatically.
- Click **Cancel** to close the page without making any changes to the purchase order.

---

## When TVH Reports an Error

### Item error (one or more rows highlighted in orange)

An item error means TVH could not find or price a specific part. The row is highlighted orange and the **Item Error** column shows the message from TVH, which may include a TVH error code in brackets, for example: *Item not found (TVH error code: 200)*.

The rest of the results are unaffected. You can still apply updates to the rows that did not have an error — highlighted rows are simply skipped.

If you see item errors, check the **Vendor Item No.** on those purchase lines. Common causes are a missing or incorrect vendor item number, or a part that TVH no longer stocks.

### Request error (the check fails before any results appear)

If TVH rejects the entire request — for example because of an authentication problem or an account issue — an error message is shown immediately and no results page opens.

Contact your administrator and ask them to run the **Test Connection** action on the TVH Account setup page to confirm the connection is working.

---

## Further Reading

- [Setting Up the TVH Connection](Setting Up the TVH Connection.md)
