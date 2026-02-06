---
title: "Work Order Shipment Posting"
parent: "Dysel Features"
---

# Work Order Shipment Posting

The **Work Order Shipment Posting** feature introduces a shipment-based flow for posting work order usage. Instead of posting all usage directly from the work order, you can handle item consumption through shipment documents.

## Overview

In some scenarios, especially when working with items that use non-standard costing methods, direct posting of usage from work orders can be limiting. With Work Order Shipment Posting enabled, Dysel BC will handle usage through a shipment process closer to the standard sales posting process.

## How it helps

This feature is valuable when:

- You use costing methods that require more detailed control over how and when inventory is relieved, like FIFO, LIFO, and Average.
- You want a posting flow for work orders that is closer to standard shipment handling.
- You need better insight into shipped quantities and their relation to work order usage.

By posting usage via shipments, you improve transparency and control over inventory and costing, while still keeping the link to the underlying work order.

## Availability and enablement

- **Available from:** November 2026 (version 29.0.202611).
- The feature can be enabled from the Dysel feature management page.
- <span style="color:red">**Caution**</span>: Once enabled, this feature **_cannot_** be disabled due to the data migration that is taking place.