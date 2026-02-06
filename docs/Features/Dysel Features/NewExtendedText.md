---
title: "New Extended Text"
parent: "Dysel Features"
---

# New Extended Text

The **New Extended Text** feature introduces a more robust way of storing and using extended text in Dysel BC. It is designed to be more stable and better suited for integrations with external systems, such as APIs and other applications.

## Overview

In many processes, you need to add longer descriptions or instructions to master data and documents (for example equipment, items, work orders, or sales documents). The New Extended Text feature replaces earlier extended text behavior with a more reliable model that:

- Reduces the risk of losing text due to changes or updates.
- Makes it easier to re-use text across multiple entities and documents.
- Aligns better with integrations, so external systems can read and write extended text in a predictable way.

## How it helps

With New Extended Text enabled, you can:

- Maintain longer, structured descriptions without impacting performance.
- Ensure that extended text is consistently applied when creating documents from master data.
- Expose extended text more reliably through APIs, making integrations less error-prone.

This is especially useful in environments with many integrations or where extended text is critical for instructions, legal wording, or customer-facing communication.

## Availability and enablement

- **Available from:** May 2026 (version 28.0.202605).
- The feature can be enabled from the Dysel feature management page.
- <span style="color:red">**Caution**</span>: Once enabled, this feature **_cannot_** be disabled due to the data migration that is taking place.