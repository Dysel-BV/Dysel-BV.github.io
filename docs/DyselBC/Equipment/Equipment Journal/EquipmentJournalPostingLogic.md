---
title: "Equipment Journal Posting Logic"
parent: "Equipment Journal"
---

# Equipment Journal Posting Logic

This page describes the technical posting behaviour of the Equipment Journal. For each journal type it explains what entries are created, whether a G/L posting is made, and what prerequisites must be met. It also lists all field, object, and setup restrictions that are enforced at posting time.

For a guide on how to use the journal, see [Equipment Journal](EquipmentJournal.md).

---

## General Validations

The following checks are always performed before any journal line is posted, regardless of journal type:

- **Posting Date**, **Document No.**, and **Equipment Journal Type** must be filled in.
- The equipment object must have a valid owning location code and equipment posting group (when Owner Status = Own).
- The equipment model must be of type **Object Model**.
- The owner status and posting status of the object must be valid for the selected journal type.

---

## Posting Logic per Journal Type

| Journal Type | Purpose | G/L Posting | Key Requirements |
|---|---|---|---|
| **Depreciation** | Register standard commercial depreciation. Creates an Equipment Value Entry (Statistics Type = Depreciation) and updates the **Depreciation Posted** date on the object. | Optional — only when **Cost Code**, **Account No.**, and **Bal. Account No.** are all filled in and **Amount** ≠ 0. | Object must have at least one Object Depreciation Setup record. |
| **Fiscal Depreciation** | Record fiscal depreciation. Creates an Equipment Value Entry (Statistics Type = Fiscal Depreciation). | None. | **Cost Code** required; **Amount** must be ≥ 0. |
| **Book3 Depreciation** | Record alternative (book 3) depreciation. Creates an Equipment Value Entry (Statistics Type = Book3 Depreciation). | None. | **Cost Code** required; **Amount** must be ≥ 0. |
| **Fiscal Adjustment** | Record a fiscal value correction. Creates an Equipment Value Entry (Statistics Type = Fiscal Adjustment). | Yes, via source code ELC42. | **Account No.** and **Bal. Account No.** required. |
| **Conv. Bookvalue** | Transfer an object to a new owning location during conversion, including inventory and financial mutations. The **Location Code** on the line represents the **target** owning location. | Via item posting. | A conversion location must exist. The Inventory Posting Setup must have the correct inventory account for the location. |
| **>Scrap** | Permanently decommission an object as scrapped. Removes the item from inventory, reverses accumulated balance depreciation, and sets the object status to Scrapped. | Yes — debit Scraped Profit/Loss Account; credit depreciation contra accounts. | **Item No.**, **Serial No.**, and **Quantity = 1** required. Equipment Posting Setup must have `Scraped Profit/Loss Account` filled. |
| **>Stolen** | Administratively decommission an object as stolen. Identical to **>Scrap** except uses the Stolen Profit/Loss Account and sets the object status to Stolen. | Yes — debit Stolen Profit/Loss Account; credit depreciation contra accounts. | **Item No.**, **Serial No.**, and **Quantity = 1** required. Equipment Posting Setup must have `Stolen Profit/Loss Account` filled. |
| **Enhancement** | Record an investment or enhancement on the object. Creates an item journal line and an Equipment Value Entry (Statistics Type = Enhancement). | Via item posting. | **Item No.**, **Serial No.**, and **Location Code** required. Equipment Model must have an Item Charge configured. |
| **Cost** | Record a cost mutation on the object. Creates an item journal line and an Equipment Value Entry (Statistics Type = Cost). | Via item posting. | **Item No.**, **Serial No.**, and **Location Code** required. Equipment Model must have an Item Charge configured. |
| **Adjustment** | Record a positive or negative value correction. Statistics Type = Positive Adjmt. or Negative Adjmt. based on the sign of the amount. | Yes — via **Account No.** and **Bal. Account No.** | **Item No.**, **Serial No.**, **Location Code**, **Account No.**, and **Bal. Account No.** required. Equipment Model must have an Item Charge configured. |
| **Recognize** | Formally recognise an object's book value (e.g. during initial activation). Posting status validation is not applied for this type. | Only if both **Account No.** and **Bal. Account No.** are manually filled in. | None — posting status validation is exempt. |
| **After Sales** | Register costs incurred after the sale of the object. Creates an Equipment Value Entry (Statistics Type = After Sales Cost). | Yes — via **Account No.** and **Bal. Account No.** | Object must have Posting Status = Sold. **Account No.** and **Bal. Account No.** required. |
| **Deactivation Depreciation** | Record depreciation in the context of deactivation. Created automatically as part of a **>Scrap** or **>Stolen** posting; not intended for manual use. | Via quantity factor applied automatically. | Created automatically during **>Scrap** and **>Stolen** processing. |

---

## Restrictions Overview

### Object-Level Restrictions

| Restriction | Applies to |
|---|---|
| Equipment object must have an **Owning Location Code** | All types (when Owner Status = Own) |
| Equipment object must have an **Equipment Posting Group** | All types (when Owner Status = Own) |
| Equipment model must be of type **Object Model** | All types |
| Object **Posting Status** must be one of: Order, Stock, Rental, Used | All types except Recognize, Deactivation Depreciation, After Sales |
| Object **Owner Status** must be **Own** | All types except Recognize, Deactivation Depreciation, After Sales |
| Object must have at least one **Object Depreciation Setup** record | Depreciation only |
| Object **Posting Status** must be **Sold** | After Sales only |

### Journal Line Field Restrictions

| Restriction | Applies to |
|---|---|
| **Posting Date** must be filled | All types |
| **Document No.** must be filled | All types |
| **Equipment Journal Type** must be filled | All types |
| **Item No.** must be filled | Enhancement, Cost, Adjustment, Conv. Bookvalue, >Scrap, >Stolen |
| **Serial No.** must be filled | Enhancement, Cost, Adjustment, Conv. Bookvalue, >Scrap, >Stolen |
| **Location Code** must be filled | Enhancement, Cost, Adjustment |
| **Quantity** must equal **1** | >Scrap, >Stolen |
| **Account No.** must be filled | After Sales, Adjustment, Fiscal Adjustment |
| **Bal. Account No.** must be filled | After Sales, Adjustment, Fiscal Adjustment |
| **Cost Code** must be filled | Fiscal Depreciation, Book3 Depreciation |
| **Amount** must be ≥ 0 | Fiscal Depreciation, Book3 Depreciation |

### Setup Restrictions

| Setup requirement | Applies to |
|---|---|
| A conversion location (`Conversion W1 ELC = true`) must exist | Conv. Bookvalue |
| The Inventory Posting Setup for the object's location must have the correct inventory account (`Inventory Account Used W1 ELC`, `Invt. Acc. Rental W1 ELC`, or `Inventory Account` depending on posting status) | Conv. Bookvalue |
| The Equipment Posting Setup must have **Scraped Profit/Loss Account** filled | >Scrap |
| The Equipment Posting Setup must have **Stolen Profit/Loss Account** filled | >Stolen |
| The Equipment Model must have an **Item Charge** configured | Enhancement, Cost, Adjustment |
| The Dysel Setup must have a **Journal Template Name** configured | All types that create a G/L posting |
| Each Object Depreciation Setup record must have a **Depreciation Book Code** | Create Depreciation Lines |
| Each Object Depreciation Setup record must have a **Depreciation Ending Date** | Create Depreciation Lines |
| The **Account No.** and **Bal. Account No.** derived from the Cost Type must not be equal to each other | Create Depreciation Lines |

### Input Restrictions

| Restriction | Field |
|---|---|
| **Quantity** can only be set to 1; any other value is rejected immediately | Quantity |
| **Item No.** cannot be manually edited; any direct change is blocked with an error | Item No. |
| **After Sales** type can only be selected when the equipment object has Posting Status = Sold | Equipment Journal Type / Equipment Object |
| **Conv. Bookvalue** type can only be selected when a **G/L Account Conversion** is configured in Dysel Setup | Equipment Journal Type |
| **Create Depreciation Lines** requires the current batch to have a **No. Series** configured | Batch |

---

## Statistics Types per Journal Type

| Journal Type | Statistics Type in Equipment Value Entry |
|---|---|
| Depreciation | Depreciation |
| Fiscal Depreciation | Fiscal Depreciation |
| Book3 Depreciation | Book3 Depreciation |
| Fiscal Adjustment | Fiscal Adjustment |
| Conv. Bookvalue | *(via item posting; no direct Equipment Value Entry statistics type)* |
| >Scrap | Scrapped |
| >Stolen | Stolen |
| Enhancement | Enhancement |
| Cost | Cost |
| Adjustment | Positive Adjmt. or Negative Adjmt. (based on amount sign) |
| Recognize | *(inherited from journal line or blank)* |
| After Sales | After Sales Cost |
| Deactivation Depreciation | Deactivation Depreciation |
