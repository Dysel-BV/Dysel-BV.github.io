---
title: "Dynafields"
parent: "General"
grand_parent: "Dysel BC"
---

# Dynafields

**Dynafields** — short for "dynamic fields" — are a set of user-defined fields that can be added to several tables in Dysel BC, such as Items, Customers, and Equipment Objects. Rather than building a new field for every attribute a product line might need, each record gets a fixed set of general-purpose slots whose captions and allowed values are defined elsewhere.

Dynafields are grouped into **DynaGroups**. A DynaGroup names each slot (for example, Option 1 = `Color`) and can restrict it to a controlled list of values. When a DynaGroup is assigned to a record — say, an Equipment Object — the captions and picklists of that record's Dynafields update automatically to match the DynaGroup.