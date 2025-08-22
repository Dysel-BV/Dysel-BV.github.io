---
title: "Card Setup Template"
parent: "Setup Documentation Guide"
---

# Card Setup Template

Use this template for documenting single-page configuration setups where users fill in multiple fields on one form or card.

---

## Template Structure

```markdown
---
title: "Setup [Feature Name]"
parent: "[Parent Section]"
---

# **User Instructions for [Feature Name] Setup**

This guide walks you through the steps to configure [feature description] in Microsoft Dynamics 365 Business Central. [Brief explanation of what this setup affects and who can see the changes.]

* * *

## **Step 1: Navigate to the [Setup Page Name]**

1. Navigate to **[Setup Page Name]** in the search field and select the corresponding option to navigate to the setup page.

* * *

## **Step 2: Configure [Category Name]**

### **[Setting Name 1]**

1. Locate the **[Field Name]** field.
2. Enter/select your preferred value (e.g., *example value*).
3. [Any additional explanation if needed.]

### **[Setting Name 2]**

1. Find the **[Field Name]** field.
2. Input [description of what should be entered] (e.g., enter `specific value` for [purpose]).
3. [Any verification or additional notes.]

* * *

## **Step 3: Configure [Another Category]**

[Repeat the pattern above for each logical grouping of settings]

### **[Setting Name]**

1. Click on the field labeled **[Field Name]**.
2. [Description of what happens - e.g., "A color selection window will appear."]
3. [Action to take - e.g., "Choose your preferred color and click **OK**."]

* * *

## **Step 4: [Additional Configuration Sections]**

[Continue with additional steps as needed, maintaining the same pattern]

* * *

## **Step 5: Save Your Changes**

1. Return to the top of the setup page.
2. Ensure all fields are updated as needed.
3. [Specific save instruction - either explicit save action or automatic save on close.]
4. [Any confirmation message or result that should be expected.]

* * *

[Feature description] is now configured according to your preferences. [Brief statement about what this enables or how it affects the system.]

* * *

For additional assistance, consult your administrator or reference the official Business Central documentation.
```

---

## Key Elements for Card Setups

### Navigation
- Always start with clear navigation to the setup page
- Use the exact page name as it appears in Business Central

### Field Organization
- Group related fields under logical subheadings
- Use the exact field names as they appear in the interface
- Provide examples for fields that might be unclear

### Setting Patterns
For each setting, follow this pattern:
1. **Location**: "Locate/Find/Click on the field labeled..."
2. **Action**: Clear description of what to do
3. **Example**: Provide example values when helpful
4. **Explanation**: Brief explanation of purpose if not obvious

### Color Settings
For color selection fields:
```markdown
### **[Color Setting Name]**

1. Click on the field labeled **[Field Name]**.
2. A color selection window will appear.
3. Choose your preferred color and click **OK**.
```

### Toggle/Boolean Settings
For yes/no or checkbox fields:
```markdown
### **[Setting Name]**

1. Locate the **[Field Name]** field.
2. Toggle the setting as needed:
   - Set it to **No** to [disable/prevent action]
   - Set it to **Yes** to [enable/allow action]
```

### Dropdown/List Settings
For fields with predefined options:
```markdown
### **[Setting Name]**

1. Click on the **[Field Name]** field to open the dropdown.
2. Select [description of what to select] from the available options.
3. [Any additional notes about the selection.]
```

---

## Examples of Card Setup Documentation

- [GDB Setup Page](GDB/Setup/GDBsetup.md) - Comprehensive example with multiple setting categories
- [Dysel Mobile Localization](Dysel Mobile/Setup/Localization.md) - Configuration with explanatory content

---

Use this template to ensure consistency across all card setup documentation. Adapt the sections as needed while maintaining the overall structure and formatting standards.