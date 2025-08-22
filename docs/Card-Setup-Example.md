---
title: "Card Setup Example"
parent: "Setup Documentation Guide"
---

# Card Setup Example: Dysel System Preferences

This is an example of documentation following the [Card Setup Template](Card-Setup-Template.md). Use this as a reference when creating similar setup documentation.

---

```markdown
---
title: "Setup Dysel System Preferences"
parent: "Dysel BC"
---

# **User Instructions for Dysel System Preferences Setup**

This guide walks you through the steps to configure system preferences in Microsoft Dynamics 365 Business Central. The settings configured here will be applied globally to all users with access to the Dysel system.

* * *

## **Step 1: Navigate to the Dysel System Preferences Setup Page**

1. Navigate to **Dysel System Preferences** in the search field and select the corresponding option to navigate to the setup page.

* * *

## **Step 2: Configure Display Settings**

### **Default Theme**

1. Locate the **Default Theme** field.
2. Select your preferred theme from the dropdown (e.g., *Light*, *Dark*, or *Auto*).
3. This setting determines the default appearance for new users.

### **Date Format**

1. Find the **Date Format** field.
2. Select the preferred date format (e.g., *MM/DD/YYYY* for US format or *DD/MM/YYYY* for European format).

### **Time Zone**

1. Locate the **Default Time Zone** field.
2. Input your organization's primary time zone (e.g., `EST` for Eastern Standard Time).

* * *

## **Step 3: Configure Notification Settings**

### **Email Notifications**

1. Locate the **Enable Email Notifications** field.
2. Toggle the setting as needed:
   - Set it to **Yes** to enable automatic email notifications
   - Set it to **No** to disable email notifications

### **Notification Frequency**

1. Find the **Notification Frequency (hours)** field.
2. Input the number of hours between notifications (e.g., enter `24` for daily notifications).

* * *

## **Step 4: Set System Colors**

### **Primary Brand Color**

1. Click on the field labeled **Primary Brand Color**.
2. A color selection window will appear.
3. Choose your organization's primary brand color and click **OK**.

### **Alert Color**

1. Click on the field labeled **Alert Color**.
2. When the color selection window opens, select a color for system alerts and click **OK**.

### **Success Color**

1. Click on the field labeled **Success Color**.
2. Choose a color for success messages and click **OK**.

* * *

## **Step 5: Configure Security Settings**

### **Session Timeout**

1. Locate the **Session Timeout (minutes)** field.
2. Enter the number of minutes before an inactive session times out (e.g., `30` for 30 minutes).

### **Password Complexity**

1. Find the **Require Complex Passwords** field.
2. Set to **Yes** to enforce complex password requirements or **No** to allow simple passwords.

* * *

## **Step 6: Save Your Changes**

1. Return to the top of the setup page.
2. Ensure all fields are updated as needed.
3. Close the page to save your changes. The system will save your configuration automatically.
4. A confirmation message will appear indicating that the settings have been saved successfully.

* * *

The Dysel System Preferences are now configured according to your organization's requirements. These settings will be applied to all users and will take effect immediately.

* * *

For additional assistance, consult your administrator or reference the official Business Central documentation.
```

---

## Key Features Demonstrated

This example shows:

### 1. **Proper Structure**
- Clear YAML frontmatter
- Descriptive title with "Setup" prefix
- Introduction explaining scope and impact

### 2. **Logical Grouping**
- Related settings grouped under meaningful headings
- Each group has a clear purpose (Display, Notifications, Colors, Security)

### 3. **Consistent Field Instructions**
- Location instructions ("Locate the..." or "Find the...")
- Clear action descriptions
- Example values where helpful
- Explanations of setting effects

### 4. **Different Field Types**
- Dropdown selections (Theme, Date Format)
- Text input fields (Time Zone, Session Timeout)
- Toggle/Boolean fields (Email Notifications, Password Complexity)
- Color selection fields (Brand Colors)

### 5. **Professional Completion**
- Clear save instructions
- Expected confirmation message
- Statement of when changes take effect
- Reference to additional help

---

Use this example as a guide when creating your own card setup documentation. Adapt the sections and field types as needed while maintaining the overall structure and formatting standards.