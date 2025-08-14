---
title: "Localization"
parent: "Dysel Mobile Setup"
---

# Localization
By default, the mobile app is available with US English (en-US) and Dutch (nl-NL) as the base languages. However, it is possible to implement other languages for your users. This article will go into how the multilanguage functionality in the Dysel Mobile App is structured and how to update the various captions. 

## Language Sources
Before setting up languages, it is important to understand where the various translations come from. Translation in the app is necessarily a multi-layered approach. We will go through each layer and explain where the translations are stored and how they can be updated.

### Business Central Captions
For field captions of Business Central fields, such as Ship-to Name, Serial No., or Customer No., the app will use the captions that are present in Business Central. These captions are stored in [xliff](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-work-with-translation-files) files. Xliff is an industry standard in application translations and is widely used for multi-language functionalities. The xliff files are embedded in the various Business Central apps (e.g. the Microsoft Base App, Dysel W1, Dysel Projects) and can therefore only be changed by accessing the source. This can only be done by Microsoft and ISVs/VARs.

### Business Central Data Translations
Another layer of translations are **data translations**. Data translations are not applied to field captions, but to actual field values like document line description fields (such as work order line descriptions), measurements and more. Microsoft has a limited data multi-language functionality, and Dysel has expanded on that and has applied data translations to various fields. This data translation can be accessed on pages like the equipment object card, item card, resource card, and many others. These translations can be added manually by a user with sufficient Business Central permissions and can be exported and imported using tools like [configuration packages](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/administration/set-up-standard-company-configuration-packages).

> Currently, the Data Translations support one extra language in addition to the one the data is written in in Business Central. This may change in future versions.

### App Fields and Actions
Finally, there are two multilanguage layers on the app setup in Business Central. These can be accessed through the Business Central search by looking for **Dysel App Multilanguage** and **Dysel App Multilanguage Text Constants**. Both can be manually created by users with sufficient permissions in Business Central and can be exported using the export and import action buttons on their respective pages.

#### Dysel App Multilanguage
The Dysel App Multilanguage handles most of the native app UI, like buttons, headings, menu items, and page names. It also handles the translations for any field captions for fields that are unique to the app and thus not present in Business Central.

#### Dysel App Multilanguage Text Constants
The Dysel App Multilanguage Text Constants functionality handles translations for dialog UI, such as confirmation questions, errors, messages, progress dialogs and other process-related UI elements.

### Brief Overview
In short, we can summarize the language functionality in this table.

| Layer | User-Changeable | Extra Languages |
| --- | --- | --- |
| BC Captions | No | Multiple |
| Data Translations | Yes | One |
| App Multilanguage | Yes | Multiple |
| App Multilanguage Text Constants | Yes | Multiple |

## Assigning a Language to a User
In order to display the correct language, the app will need to know which language the user prefers. That can be done by entering the User Language field in the Dysel App User card. The Dysel App User can be found through the Business Central search by looking for "Dysel App Users".
