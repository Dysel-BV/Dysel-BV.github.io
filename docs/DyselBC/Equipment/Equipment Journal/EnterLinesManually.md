---
title: "Enter Lines Manually"
parent: "Equipment Journal"
---

# **User Instructions: Entering and Posting Equipment Journal Lines Manually**

This guide walks you through the steps to manually enter journal lines in the Equipment Journal and post them in Dysel BC.

* * *

### **Step 1: Open the Equipment Journal**

Search for **Equipment Journal** in the Business Central search bar and open the **Equipment Journal** page.

* * *

### **Step 2: Select or Create a Batch**

1. The active batch name is displayed at the top of the page.
2. If only one batch exists, it is selected automatically.
3. To select a different batch, click the **Batch Name** field and use the lookup to choose from the available batches.
4. To create a new batch, open the lookup and select **New**.

* * *

### **Step 3: Enter Journal Lines**

On a new journal line, fill in the following fields:

1. Enter the **Document Date** and **Posting Date**.
2. Fill in the **Document No.** — or leave it blank to have it assigned automatically from the batch number series.
3. Select the applicable **Equipment Journal Type** from the dropdown.
4. Fill in the **Equipment Object**. The **Equipment Category**, **Equipment Group**, **Equipment Model**, **Location Code**, **Branch**, **Department**, and **Description** are automatically copied from the object record.
5. Enter the **Amount** (and optionally the **Unit Amount** if needed).
6. For depreciation postings, fill in a **Cost Code** if applicable.
7. For journal types that require a G/L posting (such as **After Sales**, **Adjustment**, or **Depreciation** with a G/L entry), fill in the **Account No.** and **Bal. Account No.**.
8. To review or adjust dimensions, click **Line** in the ribbon and select **Dimensions** (Shift+Ctrl+D).
9. Repeat for each additional journal line.

* * *

### **Step 4: Review the Journal Lines**

Before posting, go through all lines and verify:

1. All required fields are filled in (fields with missing required values are highlighted in red).
2. The amounts are correct.
3. The correct G/L accounts are filled in for journal types that require a G/L posting.
4. The dimensions are correct.

Use **Object > Entries** (Ctrl+F7) to view existing Equipment Value Entries for a specific object if needed.

* * *

### **Step 5: Post the Journal**

1. Click **Post** (shortcut: F9) or use the ribbon: **Posting > Post**.
2. Confirm the prompt with **Yes**.
3. The system processes each line one by one and displays a progress window.
4. After successful posting, all journal lines are removed from the batch.
5. The resulting **Equipment Value Entries** can be reviewed via **Object > Entries** (Ctrl+F7) on the equipment object.

* * *

You have now successfully entered and posted Equipment Journal lines manually!
