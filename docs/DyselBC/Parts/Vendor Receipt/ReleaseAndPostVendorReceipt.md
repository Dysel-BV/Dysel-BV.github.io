---
title: "Release and Post a Vendor Receipt"
parent: "Vendor Receipts"
nav_order: 2
---

# Release and Post a Vendor Receipt

Once a Vendor Receipt reflects what physically arrived, release and post it to bring
the goods into stock. This guide also explains what happens when there is a shortage
or damage.

* * *

## Step 1: Release the Vendor Receipt

Releasing runs a set of pre-posting checks and locks the document for editing.

1. Open the Vendor Receipt you want to process.
2. Choose the **Release** action (or press **Ctrl+F9**).

The system checks that:

- A **Vendor Shipment No.** and **Receipt Date** are present.
- Every item line is linked to a Purchase Order.
- If anything is set to claim, a **Claim Vendor No.** has been entered.
- Equipment object lines have a **Serial No.**

If a check fails, the system tells you what to fix. Correct it and release again.

> You can skip this step and post directly. In that case, the system releases the
> document for you after a confirmation.

* * *

## Step 2: Post the Vendor Receipt

1. Choose the **Post** action (or press **F9**).
2. If the document is still **Open**, confirm when prompted to release and post it.

When you post, the system:

1. Receives each linked Purchase Order using the standard Business Central receipt
   process, but only for receipt purposes. It does not invoice.
2. Brings the goods into stock at the receipt location and creates the standard
   posted purchase receipt and item ledger entries.
3. Raises a claim for any shortages. See Step 3.
4. Sets the Vendor Receipt status to **Posted**.

> **Inventory is handled by the standard receipt process.** The Vendor Receipt is a
> worksheet that drives standard posting. It does not introduce its own inventory
> logic, so costing, general ledger, and item ledger entries behave the same as a
> normal purchase receipt.

* * *

## Step 3: Shortages and damage (claims)

If a line's **Qty. Actually Received** is less than its **Qty. on Packing Slip**, the
difference is recorded as **Qty. to Claim**. When you post:

1. The system creates a **Purchase Return Order** against the **Claim Vendor No.** on
   the header.
2. The return order is pre-filled with the claimed quantities and reference text for
   the shipment.

Use that return order to follow up the shortage or damaged goods with the supplier
through the normal returns process.

> **Set the Claim Vendor No. before releasing** if you expect to claim anything.
> Release stops you if a claim quantity exists without a claim vendor.

* * *

## Step 4: Find a posted Vendor Receipt

After posting, the receipt appears in the Posted Vendor Receipt view, which shows
receipts with a status of **Posted** or **Closed**. Open it there to review what was
received.

* * *

## Step 5: What's next

If the goods need to be moved from the receipt location to a bin, a work order, a
sales order, or onward via a transfer, continue to [Put-away List](PutAwayList.md).

When the receipt is fully handled, you can set its status to **Closed**.
