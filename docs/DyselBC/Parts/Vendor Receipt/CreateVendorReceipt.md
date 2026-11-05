---
title: "Create a Vendor Receipt"
parent: "Vendor Receipts"
nav_order: 1
---

# Create a Vendor Receipt

Use this guide to create a Vendor Receipt and add the lines you are receiving against
one or more Purchase Orders.

* * *

## Step 1: Open the Vendor Receipts list

Go to the Vendor Receipts page. You can open it from the menu or by searching for
"Vendor Receipts".

* * *

## Step 2: Start a new Vendor Receipt

1. On the Vendor Receipts page, choose **New**.
2. The system opens a new Vendor Receipt card and assigns a number automatically.

* * *

## Step 3: Fill in the header

Enter the details of the delivery:

1. **Vendor No.** — select the vendor the goods were received from.
2. **Location Code** — the location or warehouse where the goods are being received.
3. **Receipt Date** — the date the goods physically arrived.
4. **Vendor Shipment No.** — the supplier's shipment or packing-slip number. This is
   required before you can post.
5. **Branch** and **Department** — complete these if your organisation uses them.

> **Tip:** The **Posting Date** controls the date the receipt is posted to the ledger.
> By default, it follows the receipt date. Change it if you need to post into a
> different period.

* * *

## Step 4: Add lines — choose the right method

There are two ways to add the lines you are receiving. Use the option that best fits
the delivery.

### Option A — Receive from a single Purchase Order

1. In the **Purchase Order No.** field on the header, select the Purchase Order the
   delivery relates to.
2. The system automatically creates a receipt line for each receivable item or
   object line on that Purchase Order.

This is the quickest route when the whole delivery belongs to one order.

### Option B — Combine lines from several Purchase Orders

When one delivery covers items from more than one order:

1. Choose the **Select Order Lines** action.
2. The **Select PO Lines** page opens, showing open Purchase Order lines for the
   vendor.
3. Tick the lines that arrived in this delivery.
4. Confirm. The selected lines are added to the receipt, each keeping its link back
   to its own Purchase Order.

> One Purchase Order can also be received across **several** Vendor Receipts (partial
> deliveries). Each receipt records only the quantities that arrived in that
> delivery.

* * *

## Step 5: Enter the received quantities

For each line, record what actually arrived:

1. **Qty. on Packing Slip** — the quantity the supplier says they sent.
2. **Qty. Actually Received** — the quantity you physically counted.

If **Qty. Actually Received** is less than **Qty. on Packing Slip**, the shortfall is
recorded as **Qty. to Claim**. This is a shortage or damage that will raise a claim
when you post. See [Release and Post a Vendor Receipt](ReleaseAndPostVendorReceipt.md).

* * *

## Step 6: Item tracking and equipment objects

- **Item tracking** — for items that use serial or lot numbers, open the **Item
  Tracking Lines** action on a line and enter the tracking details.
- **Equipment objects** — lines that receive an equipment object must have a **Serial
  No.** before the receipt can be posted. The system checks this during the
  pre-posting checks.

* * *

## Step 7: Review and continue

Check the lines and quantities carefully. When the receipt reflects what actually
arrived, you are ready to release and post it.

Continue to [Release and Post a Vendor Receipt](ReleaseAndPostVendorReceipt.md).
