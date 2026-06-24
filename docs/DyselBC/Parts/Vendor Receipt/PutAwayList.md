---
title: "Put-away List"
parent: "Vendor Receipts"
nav_order: 3
---

# Put-away List

After a Vendor Receipt is posted, the goods sit at the **receipt location**. The
**Put-away List** is a worklist that tells staff where each received quantity should
go and lets you move it there.

> **Post the Vendor Receipt first.** The put-away moves stock *out of* the receipt
> location, so the goods have to be received before you can put them away. See the
> warning in [Step 3](#step-3-post-the-put-away-transfer).

* * *

## **Step 1:** Open the Put-away List

1. Open the Vendor Receipt.
2. Choose the **Put-Away List** action (or press **F11**).

The system generates the put-away lines for the receipt. Each time you open or refresh
the list, the lines are **rebuilt** from the latest received quantities and the demand
linked to them — so the list is always current, and any unposted lines are recreated.

* * *

## **Step 2:** Understand the put-away lines

Each line shows where a received quantity should move **from** and **to**, and which
demand it is fulfilling:

| Destination type | What it means |
|---|---|
| **Work Order** | The goods are earmarked for a work order; they move to that work order's location. |
| **Sales Order** | The goods are earmarked for a sales order; they move to that sales order's location. |
| **Transfer To** | The goods feed a transfer order; they move to the transfer's from-location. |
| **Requisition** | The goods are earmarked against planned demand from the requisition worksheet. |
| **Purchase** | The goods are linked to purchase demand. |

Anything not earmarked to a specific demand becomes a **remainder line** that simply
puts the goods on the shelf — to the item's fixed bin at the receipt location.

> **Why a line might point at a transfer:** when replenishment is planned through the
> requisition worksheet for an item supplied by transfer, carrying out the plan
> creates a transfer order. The received goods are then earmarked to feed that
> transfer, and show on the put-away list as **Transfer To**.

* * *

## **Step 3:** Post the put-away transfer

1. On the **Put-away List**, select the lines you want to move.
2. Choose **Post Transfer of Selected Lines**.

For each selected line, the system moves the quantity from the **receipt location** to
the line's destination location and marks the line as **Posted**.

> ### ⚠️ Post the receipt before the put-away
>
> The put-away takes stock **from the receipt location**, which only holds stock once
> the Vendor Receipt has been **posted**. If you post a put-away transfer **before**
> the receipt (or for a quantity that was never actually received):
>
> - If the item/location has **Prevent Negative Inventory** switched on, the posting
>   is **blocked** with an error.
> - If it does not, the posting **succeeds and creates negative inventory** at the
>   receipt location, which then has to be corrected.
>
> **Always post the Vendor Receipt first, then post the put-away transfer.**

> **Note:** Lines whose destination is already the receipt location (from and to are
> the same) are **not** posted — there is nothing to move. They stay on the list and
> reappear the next time it is regenerated.

* * *

## **Step 4:** Confirm the moves

Review the put-away list after posting. Posted lines are marked **Posted**; any line
that was skipped (same from/to location, or not selected) remains for you to handle or
regenerate.

* * *

You have now received the goods and put them away. When the Vendor Receipt is fully
handled, set its status to **Closed**.
