---
title: "Dyna Group Value Worksheet"
parent: "Dynafields"
grand_parent: "General"
nav_order: 20
---

# Dyna Group Value Worksheet

## What is this page for?

Think of a **Dyna Group** as a template with "option" slots (Option 1,
Option 2, etc.). By itself, a Dyna Group doesn't know what choices should be
available in each slot — it just reserves the space.

The **Dyna Group Value Worksheet** is where you fill in the actual list of choices
("values") that people can pick from for each slot. It's like defining the options in a
dropdown menu, one row per option.

**Example:** Say your Dyna Group is called `COLOR` and Option 1 is meant to hold a paint
color. In the worksheet, you'd add rows like `RED`, `BLUE`, `GREEN` under Option 1. Those
are now the values someone can choose when that field shows up elsewhere in the system.

## How to use it

1. Open the **Dyna Group Value Worksheet** page.
2. In the **Dyna Group** field at the top, pick the Dyna Group you want to add values for.
   - As soon as you pick one, two panels on the right update automatically:
     - **DynaField Factbox** — shows which option slots (fields) are actually defined for
       this Dyna Group, so you know which ones you can add values to.
     - **DynaGroup - Where Used** — shows which tables in the system actually use this
       Dyna Group. Handy if you want to know what your changes will affect before you make them.
3. In the grid below, for each value you want to add:
   - **DynaOption** — pick which option slot this value belongs to (e.g. "Option 1").
   - **Caption** — read-only. This automatically shows you the real name of that option
     slot (e.g. "Color"), so you don't have to guess what "Option 1" actually means.
   - **Code** — type a short, unique code for this value (required — marked with a red
     asterisk).
   - **Description** — type a friendlier description. If you leave this blank, it's
     automatically filled in based on the Code you typed.

That's it — the row is saved as soon as you fill it in, no extra "save" step needed.

## Special case: Equipment Model fields

Equipment Model option fields use a separate, higher range of slot numbers behind the
scenes, but you don't need to worry about the numbers — they show up clearly labeled in
the **DynaOption** dropdown as, for example, "Equipment Model Option 1". Just pick the
one that matches what you're setting up.

## Things to know

- You must select a **Dyna Group** first — the grid stays locked (not editable) until you do.
- **Code** is mandatory for every value; **Description** is optional and will be
  auto-filled from the Code if you skip it.
- The **Caption** column is for reference only — you can't type into it, it just tells
  you what the selected option slot is called.
- The two side panels (DynaField Factbox and Where Used) are for information only —
  changing them has no effect on your data; they simply help you make the right choice.

## Frequently Asked Questions

**Q: I picked a Dyna Group but the grid is empty. Is that normal?**
Yes — the grid only shows values that have already been added for that Dyna Group. An
empty grid just means no values exist yet; start adding rows.

**Q: What happens if I pick the wrong option slot for a value?**
Change the **DynaOption** field on that row — the Caption updates automatically to
confirm you've picked the right one.

**Q: Can I see what happens if I remove a value that's currently in use somewhere?**
Check the **DynaGroup - Where Used** panel first to see which tables reference this
Dyna Group before removing values, so you understand the potential impact.
