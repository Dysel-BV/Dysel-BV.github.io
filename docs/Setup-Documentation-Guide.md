---
title: "Setup Documentation Guide"
nav_order: 4
---

# Setup Documentation Guide

This guide provides templates and methodology for documenting static functionalities like setups in the Dysel ecosystem. It helps ensure consistency and clarity across all setup documentation.

## Overview

Setup documentation differs from process documentation as it focuses on configuration rather than workflows. We categorize setups into two main types:

### Card Setups
Single configuration pages where users fill in multiple fields on one form or card. These typically involve:
- Configuration pages with multiple settings
- Color selections
- Preference settings
- System-wide configurations

**Examples:**
- Dysel Setup
- Graphical Dispatch Board Setup
- System preferences and configurations

### List Setups
Processes that involve creating, managing, or applying lists, templates, or multiple related items. These typically involve:
- Template creation
- Bulk operations
- Multi-step processes that result in lists or collections
- Applying configurations to multiple items

**Examples:**
- SKU Template creation
- Posting setups
- User permission setups
- Location configurations

## Documentation Standards

### Common Elements for All Setup Documentation

1. **YAML Frontmatter**
   ```yaml
   ---
   title: "Descriptive Title"
   parent: "Parent Section"
   ---
   ```

2. **Header Structure**
   - Use descriptive titles that clearly indicate the setup being documented
   - Include a brief introduction explaining the purpose and scope

3. **Consistent Formatting**
   - Use **bold** for field names, buttons, and UI elements
   - Use *italics* for example values
   - Use `code formatting` for specific values that should be entered exactly
   - Separate major sections with horizontal rules (`* * *`)

4. **Step Numbering**
   - Use nested numbering for sub-steps
   - Keep steps focused and actionable
   - Include verification steps where appropriate

5. **Completion Section**
   - Include a congratulations or completion message
   - Provide references for additional help
   - Mention any follow-up actions if needed

### Writing Guidelines

- **Be Specific**: Use exact field names and button labels as they appear in the interface
- **Be Clear**: Write for non-technical users; explain what will happen before they take action
- **Be Complete**: Include all necessary steps, but avoid overwhelming detail
- **Be Consistent**: Follow the same pattern throughout the document

## Templates

### For Card Setup Documentation
Use the [Card Setup Template](Card-Setup-Template.md) when documenting:
- Single-page configurations
- Settings with multiple fields on one form
- System preferences
- Color or display configurations

### For List Setup Documentation  
Use the [List Setup Template](List-Setup-Template.md) when documenting:
- Template creation processes
- Multi-step configurations
- Processes that create or manage lists
- Bulk operations or configurations

## Quality Checklist

Before publishing setup documentation, verify:

- [ ] Title clearly describes the setup being documented
- [ ] Introduction explains the purpose and scope
- [ ] All steps are numbered and in logical order
- [ ] Field names match exactly what appears in the interface
- [ ] Examples are provided for complex fields
- [ ] Navigation instructions are clear
- [ ] Completion section provides closure and next steps
- [ ] Document follows the appropriate template structure
- [ ] YAML frontmatter is correct with proper parent hierarchy

## Getting Help

For questions about documentation standards or templates:
- Consult existing documentation for examples
- Reference the [Contribution Guide](Contribute.md)
- Follow the standard GitHub issue process for suggestions or improvements

---

*This guide ensures consistent, high-quality documentation across all Dysel setup procedures.*