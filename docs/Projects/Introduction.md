---
title: "Introduction"
parent: "Dysel Projects"
nav_order: 1
---

# 1. Introduction

## What is Dysel Projects?

**Dysel Projects** is a project management extension for the Dysel BC ERP solution. It is designed for companies that carry out large, multi-stage work engagements — typically involving the build, conversion, or delivery of equipment — where the work is performed over an extended period and billed to the customer in stages rather than line by line.

A **project** is the central organizing record in this module. It acts as the umbrella under which all related activities are grouped: service work orders, purchase orders, time registrations, rental contracts, and equipment transactions. None of these activities are invoiced to the customer independently; instead, their costs and revenue are accumulated on the project and invoiced according to a schedule that you control.

## Who is this module for?

Dysel Projects is aimed at:

- **Project managers** who need to plan work phases, assign tasks, set budgets, and track progress.
- **Service coordinators** who create and manage work orders that execute the physical work on a project.
- **Finance staff** who handle invoicing, revenue recognition (including WIP accounting), and project profitability analysis.
- **Purchasing staff** who procure materials and services charged to a project.
- **System administrators** who configure the module before it is used.

## Core concepts

| Concept | Description |
|---|---|
| **Project** | The top-level record. Links a customer, an equipment object, and all related activities. |
| **Project Group** | Determines the G/L accounts used for project postings (WIP, cost, sales, interim). |
| **Project Status** | A user-configured workflow code that determines which actions are permitted on the project at any given stage. |
| **Posting Status** | A fixed system-level status that tracks the project through its formal lifecycle stages: Enquiry → Quote → Active → Inactive → Off Site → Closed. |
| **Project Task** | A phase or stage within a project. Tasks are arranged in a hierarchy and each can be budgeted, assigned an invoicing method, and used to drive work order creation. |
| **Budget Line** | A detailed cost estimate within a task, specifying the type of resource (item, labour, charge, rental, etc.) and the expected quantity and amount. |
| **Invoice Schedule** | A per-task table of billing milestones (terms), each with an amount, due date, and readiness flag. |

## Relationship to Dysel W1

Dysel Projects is built on top of **Dysel W1**, the base Dysel application. Several features of Dysel Projects are integrations with Dysel W1 modules:

| Feature used by Projects | Dysel W1 module required |
|---|---|
| Work Orders | Work Order Management |
| Equipment Objects | Equipment Management |
| Rental lines in budget | Rental Management |
| Time Sheet registration | Time Sheet |
| Consolidated Orders | Consolidated Orders |

These integrations are clearly marked in the relevant sections of this documentation.

## Dependencies

- **Platform**: Microsoft Dynamics 365 Business Central, version 28.0 or later.
- **Base app**: Dysel (DYSEL), version 28.0 or later.
