---
title: "Recurring Rental Charges"
parent: "Dysel BC"
---

# **User Instructions for Recurring Rental Charges**

This guide walks you through the steps to set up and use recurring rental
charges in Microsoft Dynamics 365 Business Central. Recurring charges are used
when a charge should be included again during normal rental invoicing.

* * *

### **Step 1:** Open the Charges List

  1. Find the **Charges List** by navigating to it using the search bar or the menu.
  2. Open the list and locate the charge you want to use as a recurring charge.
  3. If the charge does not exist yet, click **New** to create a new charge.

* * *

### **Step 2:** Open or Create the Charge

  1. Open the charge card for the charge you want to set up.
  2. Enter or review the normal charge details, such as **Code**, **Description**, **Unit Price**, posting groups, and tax group.
  3. Make sure the **Charge Type** is set to **Line Charge**.

**NOTE** Recurring charge behavior is only available for line charges.

* * *

### **Step 3:** Set Charge Invoicing to Recurring

  1. On the charge card, find the **Charge Invoicing** field in the rental section.
  2. Click the **Charge Invoicing** field.
  3. Select **Recurring**.

The available options are:

  1. **Blank** - the charge follows the standard invoicing behavior.
  2. **Postpone** - the charge is temporarily excluded from invoicing.
  3. **Recurring** - the charge can be included again on rental invoices.

* * *

### **Step 4:** Save and Close the Charge

  1. Review the charge setup.
  2. Close the charge card by clicking **Done** or **Close**.

The charge is now ready to be used as a recurring charge on rental quotes and
rental contracts.

* * *

### **Step 5:** Add the Charge to a Rental Quote or Rental Contract

  1. Open the rental quote or rental contract where the charge should be used.
  2. Go to the **Lines** section.
  3. Add a new line.
  4. Set **Type** to **Sale**.
  5. Set **Subtype** to **Charge**.
  6. Select the charge you set up earlier.
  7. Confirm that **Charge Invoicing** is set to **Recurring** on the line.

**NOTE** The recurring option is only available for rental lines where
**Type = Sale** and **Subtype = Charge**.

* * *

### **Step 6:** Review Quantity and Unit Price

  1. Check the **Quantity** on the rental line.
  2. Check the **Unit Price** on the rental line.
  3. Adjust these values before the charge is invoiced, if needed.

Recurring invoices use the current rental line quantity and unit price.

**NOTE** After a recurring charge line has been invoiced, the quantity and unit price may no longer be editable.

* * *

### **Step 7:** Invoice the Rental Contract

  1. Run the normal rental invoicing process for the rental contract.
  2. The recurring charge will be included when the invoice run creates normal invoiceable rental period lines.
  3. Review the created sales invoice before posting.
  4. Post the invoice when all lines are correct.

**NOTE** A recurring charge does not create a rental invoice by itself. It is included together with the normal rental invoice process.

* * *

### **Step 8:** Review Recurring Charge Behavior on Invoices

  1. If a new sales invoice is created for another invoice period, the recurring charge can appear again.
  2. If multiple invoice periods are combined on one sales invoice, the recurring charge appears once for each period on that sales invoice.
  3. If multiple sales invoices are created, each sales invoice can include the recurring charge when applicable.

* * *

### **Step 9:** Change a Line Back to Standard Invoicing

  1. Open the rental quote or rental contract line.
  2. Click the **Charge Invoicing** field.
  3. Change the value from **Recurring** to **Blank**.

The charge will then follow the standard charge invoicing behavior again.

* * *

### **Step 10:** Use Postpone When Needed

  1. Open the rental charge line.
  2. Click the **Charge Invoicing** field.
  3. Select **Postpone** if the charge should temporarily be excluded from invoicing.
  4. Enter a **Postpone Reason**, if required.
  5. Use **Clear Postponement** when the charge should become invoiceable again.

**NOTE** **Postpone Reason** and **Clear Postponement** only apply when **Charge Invoicing** is set to **Postpone**.

* * *

You have successfully set up and used a recurring rental charge. Repeat these steps for any other charges that should be included again during normal rental invoicing.
