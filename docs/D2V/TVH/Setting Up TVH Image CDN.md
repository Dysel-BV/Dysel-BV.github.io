---
title: "TVH-ImageCDN"
parent: "TVH"
nav_order: 60
published: false
---

# Setting Up TVH Image CDN in D2V

The TVH Image CDN feature displays a product image for each TVH part directly inside Business Central — on the **Price & Availability** worksheet and on the **Purchase Order** lines. Images are fetched on demand from the TVH content delivery network (`doc.tspaa.com`) using a key file that TVH provides on a regular refresh cycle.

---

## Prerequisites

Before enabling images you need:

| Item | Description |
|---|---|
| **Image key file** | A fixed-width text file supplied by TVH mapping each part number to an image key. TVH distributes this on a monthly (or agreed) refresh cycle. |
| **D2V TVH app** | Version with Image CDN support installed and licensed. |
| **Internet access** | Business Central must be able to reach `https://doc.tspaa.com`. Confirm with your IT team if the environment is behind an outbound firewall. |

---

## Understanding the Key File

TVH provides the image key file as a **fixed-width plain-text file**. Each line represents one part and contains three columns at fixed character positions:

| Column | Width | Content |
|---|---|---|
| **Image key** | 100 characters | The opaque key used to construct the CDN image URL |
| **TVH item number** | 50 characters | The TVH part number, typically prefixed, e.g. `TSA/` |
| **Description** | 50 characters | A short description of the part |

Lines are padded with spaces to the full column width. The import process trims all leading and trailing whitespace from each value, and automatically strips the prefix from part numbers before storing them.

> **Note:** The exact column widths may vary between TVH file generations. If TVH provides updated column positions with a new file, contact your implementation partner to confirm the widths are aligned in the configuration.

---

## Step 1: Import the Key File

1. Open the **TVH Image Key Import** page (search for *TVH Image Key Import* in the Tell Me bar).

2. On the action bar, choose **Import from File**.

3. A file picker opens. Select the key file provided by TVH and confirm.

4. The import reads every line, normalises the part numbers, and replaces **all existing** image key records in one operation. A confirmation message shows the number of records imported, for example:

   > *523,140 image keys imported successfully.*

5. Once the import completes, the list refreshes and shows the current key set.

> **Important:** Each import is a full replacement — the previous key set is deleted before the new one is written. This is intentional: it ensures stale keys for discontinued parts do not accumulate. Always use the latest file provided by TVH.

---

## Step 2: Verify the Import

After importing, the **TVH Image Key Import** list displays the current key set with the following columns:

| Column | Description |
|---|---|
| **TVH Item No.** | The normalised part number (no `TSA/` prefix) |
| **Image Key** | The CDN image key |
| **Description** | The part description from the file |
| **Valid From Date** | The date the file was imported |

Use this list to verify that expected part numbers are present before testing images in the workflow pages.

---

## Where Images Appear

Once the key file is imported, product images are displayed automatically in two places.

### Price & Availability Worksheet

When looking up parts on the **Price & Availability** page, the **TVH Image** factbox in the FactBox pane shows the image for the currently selected line. Scrolling to a different line loads the image for that part.

### Purchase Order Lines

On a **Purchase Order**, the **TVH Image** factbox in the FactBox pane shows the image for the currently selected purchase line. The image corresponds to the vendor item number on the line (the TVH part number as recorded when the order was created via the TVH integration).

---

## Image States

The factbox shows one of three states depending on the outcome of the lookup and retrieval:

| State | What you see | Cause |
|---|---|---|
| **Image found** | The product photo from the TVH CDN | A key was found for the part and the image was retrieved successfully |
| **No image registered** | A grey placeholder with the text "No TVH image registered for this part" | The part number is not present in the imported key set — either the part has no CDN image or the key file has not been imported yet |
| **Retrieval failed** | A grey placeholder with the text indicating a retrieval error | A key was found but the CDN request failed (e.g. network issue or CDN unavailability) |

Images are loaded on demand each time a line is selected and are not stored permanently. Closing and reopening a page always fetches a fresh copy from the CDN.

---

## Keeping Images Up to Date

TVH rotates the image key set periodically. When you receive a new key file from TVH:

1. Open **TVH Image Key Import**.
2. Choose **Import from File** and select the new file.
3. The new key set replaces the previous one immediately — no restart is required.

There is no need to clear old records manually before importing. The import always performs a full replacement.

---

## Troubleshooting

| Symptom | Likely cause | Action |
|---|---|---|
| All lines show "no image registered" | Key file has not been imported, or the import was interrupted | Check the **TVH Image Key Import** list — if it is empty, import the file again |
| Most lines show "no image registered" but some show images | Partial key file, or parts were added after the last import | Re-import the latest key file from TVH |
| Images show "retrieval failed" | Business Central cannot reach `doc.tspaa.com` | Confirm outbound internet access to `doc.tspaa.com` is allowed in the environment; retry after a few minutes if temporary CDN downtime is suspected |
| Import error: "Image CDN column widths have not been confirmed" | Column widths in the configuration need to be updated | Contact your implementation partner — the key file format has likely changed |
| Import count is 0 or unexpectedly low | Wrong file selected, or file encoding issue | Confirm the correct file was selected and that it is the plain-text fixed-width file from TVH (not a CSV or Excel export) |
