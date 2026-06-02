---
title: "Add Multiple Objects"
parent: "Equipment Journal"
---

# **User Instructions: Adding Multiple Objects to the Equipment Journal**

This guide explains how to use the **Select Objects** action to quickly add journal lines for multiple equipment objects at once in Dysel BC. This is useful when the same journal type and settings apply to a group of objects.

* * *

### **Step 1: Open the Equipment Journal**

Search for **Equipment Journal** in the Business Central search bar and open the **Equipment Journal** page.

* * *

### **Step 2: Select or Create a Batch**

1. Verify the correct batch is selected at the top of the page.
2. To change the batch, click the **Batch Name** field and use the lookup.

* * *

### **Step 3: Create a Template Line**

Before using **Select Objects**, create one journal line with all the shared settings that should apply to each object:

1. Enter the **Document Date** and **Posting Date**.
2. Fill in the **Document No.** — or leave it blank to have it assigned automatically from the batch number series.
3. Select the applicable **Equipment Journal Type**.
4. Enter the **Amount**, **Cost Code**, **Account No.**, and **Bal. Account No.** as required for the selected journal type.

> **Note:** The **Equipment Object** does not need to be filled in on the template line. The object will be set automatically for each line that is created by **Select Objects**. All other settings from this line are copied to each new line.

* * *

### **Step 4: Open Select Objects**

1. With the template line selected, click the **Object** menu in the ribbon.
2. Select **Select Objects**. A list of available equipment objects will open.

* * *

### **Step 5: Select the Objects**

1. Browse or search for the equipment objects you want to add.
2. Select multiple objects using Ctrl+Click or by using the mark button.
3. Click **OK** to confirm your selection.

A new journal line is automatically created for each selected object, with the **Equipment Object** filled in from the selection and all other fields copied from the template line. If a line for a given object already exists in the current batch, no duplicate line is created for that object.

* * *

### **Step 6: Adjust Lines as Needed**

Review the newly created lines and adjust the **Amount**, **Cost Code**, or other fields per line where needed.

* * *

### **Step 7: Review and Post**

1. Go through all lines and verify the amounts, accounts, and dimensions are correct.
2. Click **Post** (shortcut: F9) or use the ribbon: **Posting > Post**.
3. Confirm the prompt with **Yes**.
4. After successful posting, all journal lines are removed from the batch.
5. The resulting **Equipment Value Entries** can be reviewed via **Object > Entries** (Ctrl+F7) on the equipment object.

* * *

You have now successfully added multiple objects to the Equipment Journal and posted the lines!
