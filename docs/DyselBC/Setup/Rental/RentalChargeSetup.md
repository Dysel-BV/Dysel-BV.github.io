---
title: "Rental Charge Setup"
parent: "Rental Setup"
---


### **User Instructions for Setting Up Rental Charges**

This guide walks you through the steps to set up a rental charge in Microsoft Dynamics 365 Business Central. Follow these simple instructions to complete the setup.

* * *

### **Step 1:** Open the Charges List

  1. Find the **Charges List** by navigating to it using the search bar or the menu. 
  2. Once you open the page, you will see a list of charges.

* * *

### **Step 2:** Create a New Charge

  1. Click **New** to create a new charge. 
  2. A new form will appear for you to fill out the details of the charge.

* * *

### **Step 3:** Fill in the Charge Details

#### **a. Enter the Code**

  1. Click in the **Code** box. 
  2. Type the unique identifier for the charge (e.g., "Rent"). 

#### **b. Enter the Description**

  1. Click in the **Description** box. 
  2. Type a short description of the charge (e.g., "Rent"). 

#### **c. Specify Unit Price**

  1. Click in the **Unit Price** box. 
  2. Enter the price for the charge (e.g., "300"). 

#### **d. Select Charge Type**

  1. Click in the **Charge Type** box. 
  2. Choose the appropriate type related to your charge.

**NOTE** Recurring charge behavior is only available when the **Charge Type**
is set to **Line Charge**.

* * *

### **Step 4:** Set General Product Posting Group

  1. Click in the **General Product Posting Group** field to open a list. 
  2. Select the appropriate group for the charge from the list that appears. 
  3. Click **Ok** to confirm the selection.

* * *

### **Step 5:** Set Tax Group Code

  1. Click in the **Tax Group Code** field to open a list. 
  2. Select the appropriate tax group for the charge from the list that appears. 
  3. Click **Ok** to confirm the selection.

* * *

### **Step 6:** Specify Account Details

#### **a. Set G/L Account Sales**

  1. Click in the **G/L Account Sales** field. 
  2. Choose the correct account from the list. 
  3. If the account does not apply to this charge, simply close the list.

#### **b. Set G/L Account Purchase**

  1. Click in the **G/L Account Purchase** field. 
  2. Choose the correct account from the list. 
  3. If the account does not apply to this charge, simply close the list.

* * *

### **Step 7:** Configure Charge Invoicing

  1. Click in the **Charge Invoicing** field.
  2. Select how the charge should be handled during rental invoicing:
     1. **Blank** - the charge follows the standard invoicing behavior.
     2. **Postpone** - the charge is temporarily excluded from invoicing.
     3. **Recurring** - the charge can be included again during normal rental invoicing.

**NOTE** The **Recurring** option is used for charges that should appear again on rental invoices. The recurring charge will only be included when the normal rental invoicing process creates invoiceable rental period lines.

* * *

### **Step 8:** Configure Postponement Settings

#### **a. Set Charge Invoicing to Postpone**

  1. In the **Charge Invoicing** field, select **Postpone** to enable postponing.

#### **b. Set Postpone Reason**

  1. Click in the **Postpone Reason** box. 
  2. Type the reason (e.g., "Postpone"). 

#### **c. Clear Postponement**

  1. Click in the **Clear Postponement** box. 
  2. Enter the number of days to delay clearing (e.g., "2").

**NOTE** **Postpone Reason** and **Clear Postponement** only apply when
**Charge Invoicing** is set to **Postpone**. Postponement is an option to use
with charges and not a required setup.

* * *

### **Step 9:** Save and Close

  1. Once you’ve entered all the information, close the charge setup form by clicking **Done** or **Close**. 

* * *

Your new rental charge is now set up and ready to use. If the charge was set to **Recurring**, it can be used on rental quote or rental contract lines where **Type = Sale** and **Subtype = Charge**. Repeat the steps for other charges as needed.

