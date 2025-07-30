---
title: "Update the Dysel Mobile XML configuration"
parent: "Dysel Mobile Setup"
---

# Dysel Mobile XML Import and Update
The interface on the mobile device can be updated centrally. The update is done by importing XML configuration files into the Dysel Mobile app. This instruction will walk you through this process step by step.

## Importing the Configuration the First Time

### Obtain the XML File:
You will receive or can request the XML file from Dysel. When requesting an XML file, please include the version of the Dysel Mobile BC app (e.g. 26.3.202508.26303) from the [Extension Management](https://learn.microsoft.com/en-us/dynamics365/business-central/ui-extensions) page in Business Central.

### Install Required Extensions in Business Central (BC):
- Anvaigo Mobile App 
- DYSEL Mobile 

### Import the XML File:
1. Go to the Dysel App Technical Setup using the Find Me search in Business Central. 
2. Click on Import/Export in the ribbon. 
3. Click on Import Dysel Data.
4. You will see a checklist of aspects to update. On that page, ***deactivate*** the following settings:  
    1. Anvaigo Users 
    2. User Synch. Package Assignment 
    3. Charts 
    4. Anvaigo Setup (if present) 
5. Select the correct XML file when prompted. 
6. Wait for the import to complete (approximately 10 to 15 minutes). 
7. Activate Synchronization Packages: 
    1. Go to the Dysel App Synchronization Packages. 
    2. Activate the mandatory Synch Packages:  
        1. #ANVPKG#0001#ANVPKG# 
        2. DYSEL SERVICE APP 
        3. SYNC MGMT 
    3. Activate optional Synch Packages based on customer requirements and document these for future reference:  
        1. DYS SERVICE ACTIONS 
        2. DYS TRANSLATIONS 
        3. DYS_TASKS 
        4. DYS ATTENDANCE 
    4. Do not activate other Synch Packages as they are not used. 

## Updating an Existing Configuration

### Determine the Version:
1. Ensure you know the version of their original extension before upgrading. 
2. Ensure you know which Synchronization Packages are activated so they can be activated correctly during step 5

### Delete old functionality
If there are any components that need to be removed, a Word file noting these things will be put in the folder. Please follow those steps first and remove what needs to be removed before importing the new XML file. 

### Import the XML File:
1. If the version is 202505 or older, import the 202506 XML using the steps for a new customer. 
2. Import each subsequent version incrementally. For example, if upgrading from version 202506 to 202508, first import 202507 and then 202508. 

#### Importing the Full File
If you are importing the full xml file, you can follow steps 1 through 5 in the process for importing the first time.

#### Importing Partial XML Files
As of 26.2, we are able to import partial XML files. This is done to make updates more efficient since you only need to update the areas that have had changes. Those packeges cannot be imported from the Dysel App Technical Setup but must instead be imported through their corresponding setup pages. For example:
- *Pages*: **Import Dysel App Pages** on the Dysel App Pages list page
- *Actions*: **Import Action Codes** on the Dysel App Action Codes list page
- *Synchronization Packages*: **Import Synch. Package** on the Dysel App Synchronization Packages list page

### Import Hotfixes:
Import the base release and any previous hotfixes before the current one. For example, if importing hotfix 2, first import the base release (if not already present) and hotfix 1 before importing hotfix 2.

### Order of Importing Files
1. Dysel App Virtual App Tables 
2. Dysel App Synchronization Packages 
3. Dysel App Multilanguage Text Constants 
4. Dysel App Mobile No. Series Setup 
5. Dysel App Action Codes 
6. Dysel App Pages 
7. Dysel App Main Menu 
8. Dysel App Mobile App Table Trigger 
9. Dysel App Property Sets 

### Activate the Synchronization Packages
Activate the Synch Packages that the customer uses which you just imported during the Synchronization Packages import 

 

 
