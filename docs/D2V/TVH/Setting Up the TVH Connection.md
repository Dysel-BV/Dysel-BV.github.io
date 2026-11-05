---
title: "TVH-Setup"
parent: "TVH"
grand_parent: "D2V"
nav_order: 10
---

# Setting Up the TVH Connection in D2V

This guide walks you through the full configuration needed to connect Business Central to the TVH API using the D2V TVH integration app.

---

## Prerequisites

Before you start, make sure you have the following from TVH:

| Item | Description |
|---|---|
| **Account number** | Your TVH account number, formatted as `[number]/[company]`, e.g. `1234567/1` |
| **Access key** | The API access key issued by TVH for your account |
| **Base URL** | The TVH production REST API base URL: `https://rest.irmn.com` |

You also need:
- The **D2V** base app installed and licensed.
- The **D2V TVH** extension app installed on top of D2V.
- A Business Central user with administration rights.

## TVH User Permissions

Assign permission sets from **Users > Permission Sets** to control which users can run each TVH operation:

| Permission set | Assign to |
|---|---|
| **TVH Base Read** | Every user who needs to view TVH images or read TVH configuration. Assign this to all intended image viewers. |
| **TVH Price Avail** | Users who may run Price & Availability. |
| **TVH Submit Order** | Users who may submit orders to TVH. |
| **TVH Get List** | Users who may retrieve carrier lists or test the TVH connection. |
| **TVH Punchout** | Users who may start a TVH Punchout session. |
| **TVH Image Import** | Only users responsible for importing or replacing the TVH image key file. |

Each functional permission set includes **TVH Base Read**. Assign the base set directly to every intended image viewer, and assign each user the functional set matching the TVH operations they are authorized to perform. Give **TVH Image Import** only to image-key importers; image viewing does not require it.

---

## Step 1: Create an Interface

The Interface is the central configuration record that links a TVH connection to a vendor and item category.

1. Open the **Interfaces** page (search for *Interfaces* in the Tell Me bar).
2. Choose **New** to create a new line.
3. Fill in the fields:

| Field | Value |
|---|---|
| **Code** | A short code to identify this interface, e.g. `TVH` |
| **Description** | A readable description, e.g. `TVH Parts` |
| **Sub System** | Select `TVH` |
| **Base Request URL** | Enter the TVH production REST API base URL: `https://rest.irmn.com`. This field must be non-empty. Per-method API URLs are pre-populated in the TVH Method Setup and normally do not need to be changed. |
| **Authentication Method** | Select `Access Key` |
| **Vendor No.** | The BC vendor card linked to TVH (used when processing orders) |
| **Item Category Code** | Optional — the item category for parts sourced from TVH |
| **Debug Enabled** | Leave off in production; enables detailed HTTP request logging when troubleshooting |

4. Close or save the line.

> Note: when first implementing the interface, it is recommended to keep 'Debug Enabled' turned on until you have verified all integrations work as expected for a period of time.

---

## Step 2: Configure the TVH Account

The TVH Account record holds your credentials and connection settings for this interface.

1. On the **Interfaces** page, select the interface you just created.
2. In the action bar, choose **TVH > TVH Accounts**.
3. A new TVH Account line is created automatically for your interface. Fill in the fields:

| Field | Description |
|---|---|
| **Account** | Your TVH account number in the format `[number]/[company]`, e.g. `1234567/1` |
| **Request Key** | Optional — a correlation key that TVH echoes back in responses. Leave blank if not required. |
| **Use Test Environment** | Enable only when connecting to the TVH sandbox. When enabled, the sandbox URLs from TVH Method Setup are used instead of the production URLs. Leave off for production. |

In Business Central SaaS, every environment whose name is not `Production` is forced to use the TVH test URLs at runtime, regardless of the stored **Use Test Environment** value. OnPrem deployments keep using the stored setting; if OnPrem refresh processes copy production setup into a test database, handle any required disarming with environment-specific operational scripts before users test integrations.

4. To store the access key securely:
   - Scroll down to the **Access Key** section.
   - In the **New Access Key** field, type or paste your TVH access key.
   - Press **Enter** or tab away from the field. The key is encrypted and stored immediately.
   - The **Access Key Configured** indicator turns on. The key itself is never shown again for security reasons.

> **Important:** The access key is stored in BC's IsolatedStorage, scoped per company. If you switch to a different company, you must enter the key again for that company.

> **Punchout:** If you use Punchout, the signing secret must match the value configured for the Punchback Connector. Connector deployment and callback setup are outside this guide; contact your D2V administrator for those details.

> **API URLs:** Each integration method has its own base URL and test base URL, pre-populated automatically. If you ever need to override them — for example, if TVH changes an endpoint — go to **TVH > TVH Method Setup** from the Interfaces page.

---

## Step 3: Map Locations to TVH Warehouses

If your purchase orders use BC **locations**, you must map each location to a TVH warehouse ID. This controls which TVH warehouse receives an order line and which carrier is used.

1. On the **Interfaces** page, select your interface.
2. In the action bar, choose **TVH > TVH Warehouses**.
3. Add one line per location:

| Field | Description |
|---|---|
| **Location Code** | The BC location code, e.g. `MAIN` |
| **Warehouse ID** | The TVH warehouse identifier. Use the lookup (click **...** on the field or press F4) to select from the list of known TVH warehouses. The **Warehouse Name** column fills in automatically when you select an ID. If the lookup is empty, ask your administrator — the warehouse reference list may need to be populated first. |
| **Default Carrier Code** | The carrier code sent in order requests for this warehouse, e.g. `UPS`. Use the **Fetch Carrier Codes** action on the row to retrieve valid codes directly from TVH. See [Setting Up Carrier Codes for TVH Warehouses](Setting Up Carrier Codes for TVH Warehouses.md). |

---

## Step 4: Test the Connection

Once the account and access key are configured, verify the connection before using it in production.

1. On the **Interfaces** page, select your interface.
2. In the action bar, choose **TVH > Test Connection**.
3. Business Central sends a carrier list request to the TVH API.
   - If it succeeds, a message reads: *TVH connection successful.*
   - If it fails, the error returned by the API is shown. Common causes:
     - Incorrect access key — clear it and re-enter.
     - Wrong base URL — verify the URL with TVH.
     - Account number format wrong — must be `[number]/[company]`.

---

## Step 5: Clear or Rotate the Access Key

If you need to replace an expired or compromised access key:

1. Open **TVH > TVH Accounts** from the **Interfaces** page.
2. In the action bar, choose **Security > Clear Access Key**.
3. Confirm the prompt. The key is deleted from storage.
4. Re-enter the new access key in the **New Access Key** field as described in Step 2.

---

## Available Integration Methods

Once connected, the following TVH API operations are supported through D2V:

| Method | Description |
|---|---|
| **Price & Availability** | Queries TVH for current pricing and stock levels for items on a purchase order |
| **Submit Order** | Sends a purchase order to TVH grouped by warehouse and carrier |
| **Get Carrier List** | Retrieves available carriers from TVH for a warehouse. See [Setting Up Carrier Codes for TVH Warehouses](Setting Up Carrier Codes for TVH Warehouses.md). Also used for connection testing. |
| **Punchout** | Punchout catalogue flow — lets users browse the TVH catalogue from within a BC document and return selected items through the configured Punchback Connector. Contact your D2V administrator for connector setup details. |

---

## Troubleshooting

| Symptom | Likely Cause | Action |
|---|---|---|
| *Access key is not configured* error | Access key was never entered, or entered in a different company | Open TVH Accounts, re-enter the access key |
| *Authentication Method* validation error | Interface Authentication Method is not set to `Access Key` | Update the Interface record |
| *Base Request URL* validation error | The Base Request URL field is empty | Enter the TVH production URL |
| *TVH Warehouse is not configured* error on order submit | A purchase line uses a location that has no warehouse mapping | Add the missing line in TVH Warehouses |
| Connection test succeeds but orders fail | Carrier code on a warehouse line is invalid | Use Get Carrier List output to verify valid carrier codes |
| Unexpected API responses | Debug mode needed | Enable **Debug Enabled** on the Interface — responses are logged and can be inspected in the HTTP request log |
