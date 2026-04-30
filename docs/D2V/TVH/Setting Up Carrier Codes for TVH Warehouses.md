---
title: "TVH-CarrierCodes"
parent: "TVH"
---

# Setting Up Carrier Codes for TVH Warehouses

Each TVH warehouse mapping in D2V requires a **Default Carrier Code** — the transport carrier code that is sent to TVH when a purchase order is submitted for that warehouse. This guide explains how to retrieve the available carrier codes directly from TVH and assign the correct one to each warehouse row.

---

>
> ### <span style="color:CornflowerBlue">**Note: this functionality will become available in version 28.3.202607**</span>
>

---

## Before You Start

Before fetching carrier codes:

- The TVH interface must be set up and the connection must have been tested successfully. See [Setting Up the TVH Connection](Setting Up the TVH Connection.md).
- At least one warehouse mapping must exist on the **TVH Warehouses** page, with a **Warehouse ID** filled in.

> **Note:** Carrier codes are specific to each warehouse. A carrier available at one TVH warehouse may not be available at another. Always fetch codes for each warehouse row individually.

---

## Opening TVH Warehouses

1. Open the **Interfaces** page (search for *Interfaces* in the Tell Me bar).
2. Select the TVH interface.
3. In the action bar, choose **TVH > TVH Warehouses**.

The **TVH Warehouses** page lists all location-to-warehouse mappings for this interface.

---

## Fetching and Selecting a Carrier Code

You can fetch carrier codes in two ways. Both do the same thing — choose whichever is more convenient.

### Option A: Using the action bar

1. On the **TVH Warehouses** page, select the row for the warehouse you want to configure.
2. In the action bar, choose **Fetch Carrier Codes**.

### Option B: Using the assist-edit button on the field

1. On the **TVH Warehouses** page, select the row for the warehouse you want to configure.
2. Click the **Default Carrier Code** field to put focus on it.
3. Click the **...** (assist-edit) button that appears at the right side of the field.

### What happens next

Both options contact the TVH API and retrieve the carrier codes available for the warehouse on the selected row. If the call succeeds, the **TVH Carriers** lookup page opens.

| Column | What it shows |
|---|---|
| **Code** | The carrier code to be stored on the warehouse row and sent in order requests |
| **Description** | The carrier name as TVH identifies it |
| **Level** | Service level — `1` = standard ground, `2` = express |
| **Warehouse ID** | The TVH warehouse identifier this carrier belongs to |
| **Warehouse Name** | The TVH warehouse name |

4. Select the carrier you want to use for this warehouse.
5. Choose **OK** (or press Enter on the selected row).

The selected carrier code is written to the **Default Carrier Code** field on the warehouse row and saved automatically.

> **Tip:** If you want to review the available carriers without making a change, choose **Cancel** — no changes are made.

---

## When the Fetch Fails

If TVH returns an error or the connection cannot be reached, a message is shown with the error text from TVH. No changes are made to the warehouse row.

| Symptom | Likely Cause | Action |
|---|---|---|
| *Could not retrieve carrier codes from TVH: …* | TVH returned an API error — the message includes the TVH error description | Check the TVH account credentials and run **Test Connection** from the Interfaces page |
| Message shown but carrier list does not open | The fetch succeeded but TVH returned no carriers for this warehouse | Verify the **Warehouse ID** is correct with your TVH account manager |
| No message, page does not respond | Network or authentication issue before the API could respond | Ask your administrator to run **Test Connection** and check the interface setup |

---

## Where the Carrier Code Is Used

The **Default Carrier Code** stored on a warehouse row is included in every Submit Order request that D2V sends to TVH for purchase lines mapped to that warehouse. TVH uses it to assign a transport carrier when processing the order.

If the carrier code is missing or invalid when a Submit Order is run, the order for that warehouse will be rejected by TVH.

---

## Further Reading

- [Setting Up the TVH Connection](Setting Up the TVH Connection.md)
- [Check Price and Availability](Check Price and Availability.md)