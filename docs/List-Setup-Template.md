---
title: "List Setup Template"
parent: "Setup Documentation Guide"
---

# List Setup Template

Use this template for documenting setup processes that involve creating, managing, or applying lists, templates, or multiple related items.

---

## Template Structure

```markdown
---
title: "[Action] [Item Type]"
parent: "[Parent Section]"
---

# **User Instructions: [Action] [Item Type]**

This guide walks you through the steps to [action description] in Microsoft Dynamics 365 Business Central. [Brief explanation of the purpose and end result.]

* * *

## **Step 1: Navigate to [Starting Location]**

1. Navigate to the **[Page/Section Name]** page.
2. You can use the search bar to find it or select it from the main menu.
3. [Any additional navigation notes if needed.]

* * *

## **Step 2: Start [Action Process]**

1. On the **[Page Name]** page, click **New** to begin creating a new [item type].
2. [Description of what appears - e.g., "A new screen will appear titled **[Screen Name]**."]
3. [Any immediate orientation information.]

* * *

## **Step 3: Enter Basic Information**

1. Click into the **[Field Name]** field and [action description].
   - Example: *[example value]*
2. Click into the **[Field Name]** field and [action description].
   - Example: *[example value]*
3. [Any validation or additional notes.]

* * *

## **Step 4: [Configure Main Content/Items]**

1. [Navigate to the main content area - e.g., "Scroll down to the **Lines** section."]
2. In the **[Field Name]** field, [specific action instructions].
3. [Description of system behavior - e.g., "This feature will suggest and filter options as you type."]
4. [Selection instruction - e.g., "Select the desired item from the list that appears."]
5. [Any additional tips or notes for complex selections.]

* * *

## **Step 5: [Specify Settings/Values]**

1. In the same **[Section Name]** section:
2. Find the field labeled **[Field Name]**.
3. Click into the field and enter [description]. Example: *[example value]*.
4. [Any additional configuration notes.]

* * *

## **Step 6: [Additional Configuration]**

1. [Location instruction - e.g., "In the **Lines** section:"]
2. Locate the **[Field Name]** field.
3. [Action instruction with any conditional logic.]
4. [Default behavior or optional nature of this step.]

* * *

## **Step 7: [Handle Multiple Items/Repetition]**

1. If you have [additional items] to add, repeat steps **[X]** to **[Y]** for each:
   - [Brief summary of repeated actions]
   - [Brief summary of repeated actions]
   - [Brief summary of repeated actions]
2. [Any notes about managing multiple items.]

* * *

## **Step 8: [Finalize and Apply/Save]**

1. When finished, [specific completion action - e.g., "click the **Close** button to finalize the template."]
2. [Description of what happens - e.g., "The **[Screen Name]** will close, and you're returned to the previous screen."]
3. [Any automatic saving or additional steps needed.]

* * *

## **Step 9: [Apply/Use the Setup] (if applicable)**

1. [Instructions for applying the created setup to other items/locations]
2. [Any selection or configuration needed during application]
3. [Verification that the application was successful]

* * *

### **Congratulations!**

You've successfully [completed action description]. You can now [description of what this enables or next steps].

* * *

This guide simplifies the process to make it easy for non-technical users. For additional help, consult your administrator or refer to the official Business Central documentation.
```

---

## Key Elements for List Setups

### Process Flow
List setups typically follow this flow:
1. **Navigate** to starting location
2. **Create** new item/template
3. **Configure** basic information
4. **Add/Define** list items or content
5. **Set** properties for each item
6. **Repeat** for multiple items
7. **Save/Finalize** the setup
8. **Apply** (if needed to other locations/items)

### List/Table Interaction Patterns

#### Adding Items to Lists
```markdown
1. Scroll down to the **[Section Name]** section (a list).
2. In the **[Field Name]** field, click and begin typing [description].
3. This feature will suggest and filter options as you type.
4. Select the desired item from the list that appears.
5. [Any additional selection tips.]
```

#### Setting Properties for List Items
```markdown
1. In the same **[Section Name]** section:
2. Find the field labeled **[Property Name]**.
3. Click into the field and enter [description]. Example: *[value]*.
```

#### Managing Multiple Items
```markdown
1. If you have other [items] to add, repeat steps **[X]** to **[Y]** for each:
   - [Action 1]
   - [Action 2]
   - [Action 3]
```

### Template/Configuration Application

For setups that create templates to be applied elsewhere:
```markdown
## **Step [X]: Apply [Template] to [Target]**

1. Navigate to the **[Target Location]** where you want to apply the template.
2. [Selection instruction for target items]
3. Look for the **Apply [Template Type]** action or button.
4. In the popup window that appears, select your created template.
5. Configure any application-specific settings.
6. Click **OK** to apply the template.
```

---

## Examples of List Setup Documentation

- [Create Stockkeeping Unit Template](DyselBC/Parts/SKUs/CreateSKUTemplate.md) - Template creation example
- [Apply SKU to Location](DyselBC/Parts/SKUs/ApplySKUtoLocation.md) - Template application example
- [Set Up SKU Replenishment](DyselBC/Parts/SKUs/ReplenishmentSetup.md) - List-based configuration example

---

Use this template to ensure consistency across all list setup documentation. The template is flexible - not all steps may be needed for every setup, and some setups may require additional steps. Adapt as needed while maintaining the overall structure and formatting standards.