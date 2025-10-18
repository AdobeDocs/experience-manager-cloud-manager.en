---
title: Use the New Project Wizard
description: Follow this page to learn how to use the wizard to create an AEM Application Project.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
---

# Use the new project wizard {#using-the-wizard}

When you are onboarded to Cloud Manager as a new customer, you are provided with an empty Git repository. To help you get started, Cloud Manger offers a wizard to create a minimal AEM project based on the [AEM Project Archetype](https://github.com/adobe/aem-project-archetype) as a starting point.

Follow these steps to create an AEM project using the wizard.

1. Log into Cloud Manager at [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) and select the appropriate organization.

1. If you have not already, [create your program](program-setup.md). When the program is created, Cloud Manager detects that the repositories are not set up yet. A special call-to-action card then appears on the **Overview** screen.

   ![Create project CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Click **Create** to start the wizard and provide important values.

    * **Title** - The title of the project. By default, it is set to the name of the program.
    * **New Branch Name** - The initial branch of your Git repositories. By default, it is `main`. 

   ![Project values](/help/assets/screen_shot_2018-10-08at55825am.png)

1. The dialog box has a drawer that can be opened by clicking on the handle toward the bottom. In its expanded form, the dialog box shows all the configuration parameters for the AEM project archetype. These parameters have default values that are generated based on the **Title** you already provided and do not require modification. They are explained here for your information.

   ![Detailed archetype parameters](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Click **Create** to create the starter project by using the archetype and commit to the named Git branch. 

You now have a base project. It is time to set up your pipelines.

## Existing or migrating customers {#existing-migrating}

If you are a current Adobe Managed Services (AMS) customer or an on-premise AEM customer who is migrating, you are likely to have project code already in Git or another version control system.

In such cases, you can import your project into the Cloud Manager Git repository.
