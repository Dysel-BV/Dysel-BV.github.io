---
title: "Create Depreciation Lines"
parent: "Equipment Journal"
---

# **User Instructions: Creating Depreciation Lines Automatically**

This guide explains how to use the **Create Depreciation Lines** function to automatically generate depreciation journal lines for equipment objects in Dysel BC. The function calculates depreciation for all objects that have a depreciation setup configured and inserts the resulting lines into the Equipment Journal.

* * *

### **Step 1: Open the Equipment Journal**

Search for **Equipment Journal** in the Business Central search bar and open the **Equipment Journal** page.

* * *

### **Step 2: Select a Batch with a Number Series**

> **Prerequisite:** The active batch must have a **No. Series** configured. The report generates document numbers from this series. If no number series is set on the batch, the report will produce an error.

1. Verify the correct batch is selected at the top of the page.
2. To change the batch, click the **Batch Name** field and use the lookup.
3. To verify or configure the number series on a batch, open the batches page via the lookup and confirm that the **No. Series** field is filled in.

* * *

### **Step 3: Run Create Depreciation Lines**

1. Click **Create Depreciation Lines** (shortcut: Shift+F11), or use the ribbon: **Functions > Create Depreciation Lines**.
2. The **EX-Object Depr.** report dialog will open.

* * *

### **Step 4: Set the Report Parameters**

1. Set the desired **Posting Date**. The default value is the last day of the current month.
2. Optionally apply filters to limit the scope — for example, by **Equipment Category** or **Posting Status**.
3. To also receive an overview of the calculated lines in Excel format, enable the **Export to Excel** option.
4. Click **OK** to run the report.

> **Note:** Each time this function runs, any **existing journal lines for a given object in the current batch are deleted and replaced** with the newly calculated lines. Lines with a calculated amount of zero are not inserted. Run the function again at any time to recalculate, for example after changing a depreciation setup.

* * *

### **Step 5: Review the Generated Lines**

Once the report has completed, the depreciation lines appear in the journal. Review each line and verify:

1. The **Posting Date** is correct.
2. The **Equipment Journal Type** is as expected. The type is determined by the Cost Type's Posting Type:
   - **Depreciation** cost type → journal type **Depreciation**
   - **Fiscal Depreciation** or **Fiscal Difference Depreciation** → journal type **Fiscal Depreciation**
   - **Additional Depreciation** or **Additional Difference Depreciation** → journal type **Book3 Depreciation**
3. The **Amount** is correct for each object.
4. The **Cost Code**, **Account No.**, and **Bal. Account No.** are filled in where required.

Use **Object > Object Depreciation Setup** to review the depreciation configuration of a specific object if needed.

* * *

### **Step 6: Post the Journal**

1. Click **Post** (shortcut: F9) or use the ribbon: **Posting > Post**.
2. Confirm the prompt with **Yes**.
3. The system processes each line one by one and displays a progress window.
4. After successful posting, all journal lines are removed from the batch.
5. The resulting **Equipment Value Entries** can be reviewed via **Object > Entries** (Ctrl+F7) on the equipment object.

* * *

You have now successfully created and posted depreciation lines using the **Create Depreciation Lines** function!
