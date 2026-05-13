# 12. Project Deliveries

A **Project Delivery** is a shipping document that records the physical delivery of project output (typically an equipment object or finished goods) to the customer. It is separate from a sales invoice: the delivery records that the goods have been shipped, while invoicing records the financial claim on the customer.

---

## 12.1 When to use Project Deliveries

Project Deliveries are appropriate when:

- The project produces a tangible output (e.g., a built or converted machine) that is physically shipped to the customer.
- You want to record a formal delivery document with ship-to address and shipment date, independent of the invoicing timeline.
- The delivery may need to be released and closed as a separate workflow step before or after invoicing.

---

## 12.2 Project Delivery document

**Page**: Navigate from the project card using *Related → Project Deliveries*, or search for Project Deliveries.

### Header fields

| Field | Description |
|---|---|
| **No.** | Assigned from the *Project Delivery Nos.* number series in Project Setup. |
| **Status** | The current lifecycle status of the delivery. See [Section 12.3](#123-delivery-status) below. |
| **Project No.** | The project this delivery belongs to. |
| **Sell-to Customer No.** | The customer to whom the goods are sold. Required. |
| **Ship-to Customer No.** | The customer record used to derive the ship-to address. Required. May differ from the sell-to customer. |
| **Ship-to Code** | A specific ship-to address code for the ship-to customer. Populates the address fields automatically. |
| **Ship-to Name / Name 2 / Address / Address 2 / City / Contact** | The full delivery address. Can be edited after selection. |
| **Posting Date** | The date the delivery is posted/recorded. |
| **Shipment Method Code** | The delivery method (e.g., own delivery, courier). |

---

## 12.3 Delivery Status

Project Deliveries follow a three-stage lifecycle:

| Status | Meaning |
|---|---|
| **Open** | The delivery document has been created and is being prepared. Details can still be edited. |
| **Released** | The delivery has been confirmed and is ready for dispatch. Editing is restricted. |
| **Closed** | The delivery has been completed and is fully recorded. No further changes are allowed. |

---

## 12.4 Delivery numbering

Delivery numbers are assigned from the **Project Delivery Nos.** number series configured in Project Setup (see [Section 2.1](02-setup-and-configuration.md)). If no number series is configured, numbers must be entered manually.

---

## 12.5 Relationship between deliveries and invoicing

Project Deliveries are informational/logistical documents. They do not directly trigger invoicing. The decision of when to invoice is controlled by the invoice schedule or the invoicing method on the project task. However, a delivery document provides important evidence for when billing milestones are met (e.g., "invoice upon delivery").

A common process flow is:
1. Create the project delivery when goods are ready for shipment.
2. Release the delivery when the goods leave the premises.
3. Mark the relevant invoice schedule term as *Ready to Invoice*.
4. Generate the sales invoice from the project.
5. Close the delivery once delivery is confirmed by the customer.
