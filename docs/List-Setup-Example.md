---
title: "List Setup Example"
parent: "Setup Documentation Guide"
---

# List Setup Example: User Permission Template

This is an example of documentation following the [List Setup Template](List-Setup-Template.md). Use this as a reference when creating similar setup documentation.

---

```markdown
---
title: "Create User Permission Template"
parent: "User Management"
---

# **User Instructions: Create User Permission Template**

This guide walks you through the steps to create a User Permission Template in Microsoft Dynamics 365 Business Central. This template can be applied to multiple users to ensure consistent permission settings across your organization.

* * *

## **Step 1: Navigate to User Permission Templates**

1. Navigate to the **User Permission Templates** page.
2. You can use the search bar to find it or select it from the administration menu.
3. The page will display a list of existing templates if any have been created.

* * *

## **Step 2: Start Template Creation**

1. On the **User Permission Templates** page, click **New** to begin creating a new template.
2. A new screen will appear titled **User Permission Template Card**. This is where you will define the template details.
3. The card will be empty and ready for you to configure.

* * *

## **Step 3: Enter Basic Template Information**

1. Click into the **Template Code** field and enter a unique identifier for your template.
   - Example: *SALES_BASIC*
2. Click into the **Template Name** field and enter a descriptive name.
   - Example: *Basic Sales User Permissions*
3. In the **Description** field, provide additional details about the template's purpose.
   - Example: *Standard permissions for sales team members*

* * *

## **Step 4: Add Permission Sets**

1. Scroll down to the **Permission Sets** section (a list).
2. In the **Permission Set ID** field, click and begin typing the permission set name.
3. The system will suggest and filter available permission sets as you type.
4. Select the desired permission set from the list that appears.
5. You may need to click several times to refine your search if permission sets have similar names.

* * *

## **Step 5: Configure Permission Level**

1. In the same **Permission Sets** section:
2. Find the field labeled **Permission Level**.
3. Click into the field and select the appropriate level. Example: *Full Access*, *Read Only*, or *Limited*.
4. This determines what level of access this permission set grants.

* * *

## **Step 6: Set Effective Dates**

1. In the **Permission Sets** section:
2. Locate the **Start Date** field.
3. Click and select when this permission should become active (leave blank for immediate effect).
4. In the **End Date** field, optionally set when this permission should expire.

* * *

## **Step 7: Add Additional Permission Sets**

1. If you have other permission sets to add, repeat steps **4** to **6** for each:
   - Add the permission set ID
   - Configure the permission level
   - Set effective dates if needed
2. Each row represents one permission set that will be granted to users using this template.

* * *

## **Step 8: Review and Save Template**

1. When finished adding all permission sets, review the template configuration for accuracy.
2. Click the **Close** button to finalize the template.
3. The **User Permission Template Card** will close, and you're returned to the templates list.
4. Your new template will appear in the list and is now ready for use.

* * *

## **Step 9: Apply Template to Users**

1. Navigate to the **Users** page to apply your template.
2. Select the user who should receive these permissions.
3. Look for the **Apply Permission Template** action or button.
4. In the popup window that appears, select your newly created template.
5. Configure any user-specific settings if prompted.
6. Click **OK** to apply the template to the selected user.

* * *

### **Congratulations!**

You've successfully created a User Permission Template. You can now apply this template to multiple users to ensure consistent permission settings across your organization.

* * *

This guide simplifies the process to make it easy for non-technical users. For additional help, consult your administrator or refer to the official Business Central documentation.
```

---

## Key Features Demonstrated

This example shows:

### 1. **Process Flow Management**
- Clear progression from creation to application
- Logical step sequence that builds on previous steps
- Separate creation and application phases

### 2. **List Management Patterns**
- Adding items to a list/table structure
- Configuring properties for each list item
- Managing multiple related items

### 3. **Template Methodology**
- Creating reusable configurations
- Applying templates to multiple targets
- Consistent configuration across items

### 4. **Complex Field Interactions**
- Auto-complete/filtering fields (Permission Set ID)
- Dependent field relationships (Permission Level affects access)
- Optional vs. required fields (Effective Dates)

### 5. **Multi-step Process**
- Template creation phase
- Template application phase
- Clear separation of concerns

### 6. **Repetitive Actions**
- Clear guidance on repeating steps for multiple items
- Summary of repeated actions
- Management of multiple list entries

---

Use this example as a guide when creating your own list setup documentation. This pattern works well for:
- Template creation processes
- Bulk configuration operations
- Multi-item setup procedures
- Configuration processes that are later applied to other objects

Adapt the sections and field types as needed while maintaining the overall structure and formatting standards.