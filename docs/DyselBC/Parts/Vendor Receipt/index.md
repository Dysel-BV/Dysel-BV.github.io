---
title: "Vendor Receipts"
parent: "Parts"
---

# Vendor Receipts

A Vendor Receipt is a goods-inwards worksheet used when a delivery arrives from a
supplier. Warehouse staff use it to record what physically arrived, match it against
one or more open Purchase Orders, and post the receipt so the goods enter stock.

After the goods are received, an optional Put-away List helps staff move them from
the receipt location to their final destination, such as a bin, work order, sales
order, or transfer.

---

## Two posting steps

A Vendor Receipt uses two separate posting actions, and the order matters:

1. **Post the Vendor Receipt** to receive the goods into the receipt location.
2. **Post the Put-away Transfer** to move the received goods to their final
destination.

> **Always post the Vendor Receipt before the Put-away Transfer.** The put-away moves
> stock out of the receipt location, so the goods must already be there. Posting the
> put-away first can cause errors or, depending on your item and location settings,
> negative inventory that must be corrected later. See [Put-away List](PutAwayList.md)
> for details.

---

## Status lifecycle

A Vendor Receipt moves through four statuses:

| Status | Meaning |
|---|---|
| **Open** | The document is editable. You can add and change lines. |
| **Released** | Pre-posting checks have passed. The header and lines are now locked for editing. |
| **Posted** | The goods have been received into stock. The receipt appears in the posted history view. |
| **Closed** | A manual final state once the receipt is fully handled. |

You can post directly from **Open**. The system releases the document first after a
confirmation. If posting fails partway through, the document is reopened so you can
correct it.

---

## How it fits together

```mermaid
flowchart TD
    A["One or more open Purchase Orders"] --> B["Create Vendor Receipt<br/>and add lines"]
    B --> C["Enter received quantities"]
    C --> D["Release"]
    D --> E["Post Vendor Receipt<br/>goods enter the receipt location"]
    E --> F["(Optional) Open Put-away List"]
    F --> G["Post Transfer<br/>goods move to their destination"]
    G --> H["Close"]
```

---

## In this section

- **[Create a Vendor Receipt](CreateVendorReceipt.md)** — start the document and add
  the lines you are receiving.
- **[Release and Post a Vendor Receipt](ReleaseAndPostVendorReceipt.md)** — run the
  pre-posting checks, receive the goods, and handle shortages or damage as claims.
- **[Put-away List](PutAwayList.md)** — generate the put-away worklist and move the
  received goods to their destination.
- **[Field Reference](FieldReference.md)** — see what each field on the header and
  lines means.
