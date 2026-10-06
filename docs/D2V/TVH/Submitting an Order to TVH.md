---
title: "TVH-SubmitOrder"
parent: "TVH"
nav_order: 40
published: false
---

# Submitting an Order to TVH

The **Submit Order** action sends a released purchase order to TVH and confirms it as a live order. TVH responds with a vendor order number and confirmed pricing, which are written directly back to the purchase order and its lines.

---

> 
> ### <span style="color:CornflowerBlue">Note: this functionality is still being developed and is expected to become available in 2026 release wave 1 (May - October)</span>
> #### <span style="color:CornflowerBlue">This is an estimated release and is subject to change.</span>
> 

---

## Before You Start

Before submitting an order, make sure:

- The TVH interface has been set up and the connection has been tested. See [Setting Up the TVH Connection](Setting Up the TVH Connection.md).
- Each location code used on the purchase order has been mapped to a TVH warehouse, and each warehouse mapping has a **Default Carrier Code** set. See Step 3 of the setup guide.
- Each item line has a **Vendor Item No.** filled in with the TVH part number.
- The purchase order is not pending approval.

> **Note:** If you want to check pricing and stock levels before placing the order, run **Check Price and Availability** first. See [Check Price and Availability](Check Price and Availability.md).

---

## Running the Action

### From the ribbon

On the Purchase Order card, go to the **Prepare** tab. Click the **dropdown arrow** on the right side of the **D2V** button and choose **Submit Order**.

> **Note:** The D2V button and its dropdown are only available on Parts purchase orders where a TVH interface is configured for the vendor. If the action does not appear, ask your administrator to verify the interface and vendor setup.

---

## Release Confirmation

If the purchase order has not yet been released, D2V will ask:

> *Purchase order [No.] has not yet been released. Do you want to release it now?*

- Choose **Yes** to release the order and continue with the submission.
- Choose **No** to cancel. The order is not released and nothing is sent to TVH.

A purchase order that is **Pending Approval** cannot be submitted. You will see an error and must wait for the approval to be resolved first.

---

## What Is Sent to TVH

When you confirm the submission, D2V sends the following to TVH:

| Data | Source on Purchase Order |
|---|---|
| Item lines | All lines of type **Item** with a quantity greater than zero and a **Vendor Item No.** filled in |
| Ship date | **Expected Receipt Date**; if blank, today's date is used |
| Ship-to address | **Ship-to Name**, **Address**, **City**, **Post Code**, **Country**, **Contact** |
| Comments | **Posting Description** |
| Carrier | **TVH Carrier Code** on the order; if blank, the **Default Carrier Code** from the warehouse mapping is used |
| Ship complete | **TVH Ship Complete** on the order |

Each group of lines belonging to the same location is sent as a separate delivery to the corresponding TVH warehouse.

---

## What Is Written Back

After a successful submission, D2V updates the purchase order automatically:

| Field | What is written |
|---|---|
| **Vendor Order No.** | The TVH order number |
| **TVH Order Status** | Set to **Submitted** |
| **Direct Unit Cost** (per line) | The confirmed price returned by TVH, if TVH confirmed a price for that line |
| **TVH Submit Error** (per line) | If TVH returned an item-level error for a line, the error message is stored here |

---

## Item Errors vs. Order Errors

TVH distinguishes between two types of errors in the response:

### Item-level errors (non-blocking)

If TVH cannot process a specific item — for example, because the part number is no longer orderable — it returns an error for that line only. The order is still submitted for all other lines. The error message is written to the **TVH Submit Error** field on the affected purchase line. The **Direct Unit Cost** for that line is not changed.

Review lines with a **TVH Submit Error** after submission and decide whether to remove them, replace the part number, or source the part elsewhere.

### Order-level errors (blocking)

If TVH rejects the entire order — for example, due to an account or authorisation issue — submission fails and no changes are made to the purchase order. The error message from TVH is shown on screen. Contact your TVH account manager if the error is not self-explanatory.

---

## Preventing Duplicate Submissions

D2V checks the **TVH Order Status** before sending. If the order has already been submitted, the action is blocked and an error is shown. This prevents the same order from being placed twice in TVH.

If you need to resubmit an order that has already been sent — for example, because the original submission was lost in transit — contact your administrator. Resubmission requires a deliberate override.

---

## After Submission

Once submitted:

- The **Vendor Order No.** field on the purchase header holds the TVH order reference. Use this when communicating with TVH about the order.
- Lines where TVH confirmed a price now have an updated **Direct Unit Cost**.
- Lines where TVH returned an item error have a note in **TVH Submit Error** — review these before receiving or posting.
- The order status in TVH reflects a live order. Changes to the purchase order in Business Central after submission are **not** automatically sent to TVH. Contact TVH directly to change or cancel a submitted order.
