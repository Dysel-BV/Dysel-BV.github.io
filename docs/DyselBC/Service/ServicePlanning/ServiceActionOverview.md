---
title: "Service Action Overview"
parent: "Service Planning"
---

# Service Action Overview

This feature tracks maintenance jobs on **machines** (like forklifts or trucks) and ensures the system automatically keeps track of when each job needs to be done.
>
> This Feature is available as of **Release 27.5**. These changes do not impact older versions of Dysel BC.
>

---

## The Big Idea: Service Actions

A **Service Action** is just a job that needs to be done on a machine.
For example: *"Check the oil every 3 months"* or *"Change the filter every 1000 km"*.

The system keeps a list of all the jobs that need to happen for every machine.

---

## Work Orders

When it is time to do a job, someone creates a **Work Order** — think of it like a to-do note that says:
> *"Hey, please do these jobs on Machine A today."*

A Work Order can have many lines on it — one line for each job to do.

When you **Release** the Work Order, it means *"Yes, we are definitely going to do this today."*

---

## Service Action Entries

Every time a job is done (or is being planned), the system writes it down in a list called **Service Action Entries**. Each entry records:
- **Which machine** it belongs to.
- **Which job** (Action Code) it is for.
- **When** it was done (the date).
- **How many kilometres** the machine was at (M1), if relevant.
- **Which Work Order Line** or **Equipment Object** it came from (the Source Record ID).
- **Whether it should be ignored** when calculating planning dates.

---

## When Is an Entry Created?

A Service Action Entry is created in three situations:

| When | What happens |
|---|---|
| You **Release** a Work Order | An entry is created for each Job Code line on the Work Order |
| You **update M1** on a Work Order (if the switch is ON) | An entry is created or updated for each Job Code line |
| You **add a manual entry** via the Service Action Manual Entry page | An entry is created directly on the machine, not linked to a Work Order |

---

## What Is "Source Record ID"?

Each entry points back to **where the job came from**:
- If the entry came from a Work Order → it points to the exact **Work Order Line**.
- If someone added the entry by hand → it points to the **Equipment Object** (the machine card).

This pointing is called the **Source Record ID**. It is important because it lets you trace back every entry to its origin — you can always answer the question *"why does this entry exist?"*.

---

## Ignore in Calculation: "Don't Count This One"

Sometimes an entry should be **ignored**. This means: *"Yes, this entry is there, but please skip it when figuring out the next date."*

Why would you ignore an entry? Here are some examples:

| What Happened | What the System Does |
|---|---|
| Someone pressed the button to ignore it on purpose | Marks it as "Manually Changed" |
| The Work Order Line was deleted | Marks it as "Work Order Line Deleted" |
| Someone changed the type of work on the line | Marks it as "Work Order Line Type Changed" |
| Someone changed which job is on the line | Marks it as "Work Order Line Job Code Changed" |
| The Work Order was recreated from a return | Marks it as "Work Order Recreated" |

When an entry is ignored, the system skips it and looks at the other entries to figure out the planning dates.

If you later un-ignore it (toggle it back), the reason is cleared and the entry counts again.

---

## Planning: Figuring Out the Next Date

After a job is done, the system looks at the latest Service Action Entry and figures out:
> *"OK, if we did this job today, when is the NEXT time we need to do it?"*

For example:
- If the rule is "every 3 months", and the job was done today, the next date is in 3 months.
- If the rule is "every 500 km", and the machine is at 1000 km, the next date is at 1500 km.

This is called **Planning**. The system keeps a planning list that shows the next date for every job on every machine.

### When Does Planning Update?

The planning updates automatically whenever:
- You **Release** a Work Order (a job has been committed).
- You **Delete** a Work Order Line (a job was cancelled — the system recalculates when it should happen next).
- You **update M1** on a Work Order **and the "SA Entry on Meter Reading" switch is ON** — an entry is created or updated, which then triggers a planning recalculation.

---

## Meter Readings (M1): Counting Kilometres

Some machines need jobs based on **how far they have travelled** (or how many hours they have run), not just by date.

This number is called **M1** (Meter Reading 1). Think of it like the odometer in a car.

### The "SA Entry on Meter Reading" Switch

In the **ELC Setup** page, there is a switch called **"SA Entry on Meter Reading"**.

- **Switch OFF** (the default): entries are only created when you Release a Work Order.
- **Switch ON**: an entry is also created (or updated) the moment you type a new M1 value into a Work Order — before you even Release it.

### What Exactly Happens When You Update M1 on a Work Order?

Here is the step-by-step of what the system does behind the scenes the moment you save a new M1 value:

1. **For each Job Code line on the Work Order**, the system checks whether a Service Action Entry already exists for that line.
   - If **no entry exists yet** → a brand new entry is created with the M1 value and the date.
   - If an entry **already exists** → the existing entry is updated with the new M1 number.
2. **Planning is recalculated** — but only meaningfully if an entry was created or updated. Planning uses the entries to figure out the Next Planned Date, so if no entry was written, the recalculation will produce the same dates as before.
   - Switch **ON**: a new or updated entry exists → planning recalculates → Next Planned Date changes.
   - Switch **OFF**: no entry is written → planning recalculates → **Next Planned Date stays the same**.

### What If You Change M1 Again?

If you type a different M1 value on the same Work Order, the entry that was created earlier **gets updated** — it does not create a second one. The system always keeps just one entry per Work Order Line.

---

## The Service Action Manual Entry Page

The **SA Manual Entry** page is where someone can manually add an entry for a machine — recording that a job was done outside of a normal Work Order.

### How the Page Works

- **Direct insert/edit/delete via the grid is disabled.** You cannot accidentally type in the wrong row or press delete on a record. All changes go through the dedicated action buttons.
- The page shows a **subpage of existing entries** for the same machine and job, so you can see the full history at a glance.

### Actions on the Page

| Action | What It Does |
|---|---|
| **New Entry** | Creates one new manual entry for the machine/job. |
| **Clear Entry** | Clears the fields you have typed, without saving. |
| **Delete** | Deletes one or more entries that you have **selected in the list**. The system asks for confirmation first, then recalculates planning. |
| **Change Ignore in Calculation** | Toggles the "ignore" flag on one or more **selected entries** in the list. Works in bulk — select several entries and toggle them all at once. Planning recalculates afterwards. |

### Selecting Multiple Entries

In the entries subpage, you can select more than one row (just like a normal list in Business Central). The **Delete** and **Change Ignore in Calculation** actions will then act on everything you have selected.

---

## Bug Fix: Clearing the Job Code Now Correctly Ignores the Entry

There was a subtle bug: if someone cleared (blanked out) the **Job Code** on a Work Order Line, the system was supposed to mark the linked Service Action Entry as *"Work Order Line Job Code Changed"* and ignore it. But it was silently skipping that step and leaving the entry active.

This has been fixed. Now, whenever the Job Code on a line is cleared or changed, the system reliably ignores the old entry and recalculates the planning dates — just like it does for the other "something changed" scenarios described in the table above.

---

## Putting It All Together

1. A machine needs regular jobs — these are set up as **Service Actions**.
2. When it is time to do the jobs, a **Work Order** is created with lines for each job.
3. When the Work Order is Released, **Service Action Entries** are created automatically.
4. The system uses those entries to calculate the **Next Planned Date** for each job.
5. If something changes (a line is deleted, a job is swapped), the old entry is **Ignored** and the dates are recalculated.
6. For machines tracked by distance/hours, entries can also be created when the **M1 meter reading** is updated (if the switch is ON) — and planning recalculates whenever an entry is created or updated.
7. If a manual entry needs to be removed, the **Delete** action on the SA Manual Entry page lets you remove one or more entries and recalculates planning automatically.
