---
title: Using the New Project Wizard
description: Follow this page to learn how to use the wizard to create an AEM Application Project
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
---

# Using the New Project Wizard {#using-the-wizard}

When you are onboarded to Cloud Manager as a new customer, you are provided with an empty git repository. To help you get started, Cloud Manger offers a wizard to create a minimal AEM project based on the [AEM Project Archetype](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) as a starting point.

Follow these steps to create an AEM project using the wizard.

1. Log into Cloud Manager at [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) and select the appropriate organization.

1. If you have not already, [create your program](program-setup.md). When the program is created, Cloud Manager recognizes that the repositories are not yet set up and a special call-to-action card is shown on the **Overview** screen.

   ![Create project CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Click **Create** to start the wizard and provide important values.

    * **Title** - This is the title of the project and is by default set to the name of the program.
    * **New Branch Name** - This is the initial branch of your git repositories and by default will be `main`. 

   ![Project values](/help/assets/screen_shot_2018-10-08at55825am.png)

1. The dialog has a drawer which can be opened by clicking on the handle toward the bottom. In its expanded form, the dialog shows all of the configuration parameters for the AEM project archetype. These parameters have default values which are generated based on the **Title** you already provided and do not require modification. They are explained here for your information.

   ![Detailed archetype parameters](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Click **Create** to create the starter project by using the archetype and commit to the named git branch. 

You now have a base project! Now you can set up your pipelines.

## Existing or Migrating Customers {#existing-migrating}

If you are a current Adobe Managed Services (AMS) customer or an on-premise AEM customer who is migrating to, you likely already have project code in git or another version control system.

In such cases you will import your project into the Cloud Manager git repository.
