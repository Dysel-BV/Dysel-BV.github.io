---
title: "Field Reference"
parent: "Vendor Receipts"
nav_order: 4
---

# Field Reference

This page explains the main fields on the Vendor Receipt header and lines. Fields
related to features that are not currently in use are omitted.

* * *

## Header fields

| Field | Description |
|---|---|
| **No.** | The unique number of the Vendor Receipt, assigned automatically from the number series. |
| **Vendor No.** | The supplier the goods were received from. |
| **Location Code** | The location or warehouse where the goods are received. This is the receipt location where stock enters on posting and from which the put-away moves it out. |
| **Receipt Date** | The date the goods physically arrived. |
| **Posting Date** | The date the receipt is posted to the ledger. By default, it follows the receipt date; change it to post into a different period. |
| **Vendor Shipment No.** | The supplier's shipment or packing-slip number. This is required before posting. |
| **Purchase Order No.** | An optional anchor Purchase Order. Selecting one automatically creates receipt lines from that order's receivable lines. Lines can also come from several orders via **Select Order Lines**. |
| **Claim Vendor No.** | The vendor a claim for shortage or damage is raised against. This is required if any line has a quantity to claim. |
| **Branch** | The branch the receipt belongs to, if used. |
| **Department** | The department the receipt belongs to, if used. |
| **Status** | The document status: **Open**, **Released**, **Posted**, or **Closed**. See [Status lifecycle](index.md#status-lifecycle). |

* * *

## Line fields

| Field | Description |
|---|---|
| **No.** | The item or object being received. |
| **Description** | The description of the item or object. |
| **Purchase Order No.** | The Purchase Order this line is received against. |
| **Purchase Order Line** | The specific Purchase Order line this receipt line links to. |
| **Qty. on Packing Slip** | The quantity the supplier says they sent. |
| **Qty. Actually Received** | The quantity you physically counted. This drives what is received into stock. |
| **Qty. to Receive** | The quantity that will be received when the document is posted. |
| **Qty. to Claim** | The shortfall between the packing slip and the quantity actually received. This raises a claim to the **Claim Vendor No.** on posting. |
| **Serial No.** | The serial number for an equipment object line. This is required before object lines can be posted. |

* * *

## Put-away line fields

| Field | Description |
|---|---|
| **From Location** | The location the goods move from, which is the receipt location. |
| **From Fixed Bin** | The bin the goods move from, where applicable. |
| **Location Code** | The destination location the goods move to. |
| **Fixed Bin** | The destination bin, where applicable. |
| **Quantity** | The quantity to move. |
| **Document** | The type of demand the goods are earmarked for: **Work Order**, **Sales Order**, **Transfer To**, **Purchase**, or **Requisition**. |
| **Posted** | Indicates that the put-away transfer for this line has been posted. |
