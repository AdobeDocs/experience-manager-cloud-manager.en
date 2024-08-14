---
title: Program Setup
description: After onboarding, the business owner will need to do some initial setup of the program.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
---

# Program setup {#program-setup}

After onboarding, the business owner completes the initial setup of the program including setting the program description and defining the key performance indicators (KPIs), which are used for performance testing.

## Program setup with [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Follow these steps to set up the program and define KPIs.

1. Log into Cloud Manager at [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) and select the appropriate organization.

1. Click **Setup Program** to start the setup process.

   ![Set up program](/help/assets/set-up-program/setup1.png)

1. In the **Setup Program** dialog you can enter program information across three tabs:

   * **General**
   * **KPI**
   * **Provisioning**

1. On the **General** tab, add a description for your program and optionally upload a thumbnail by clicking on **Change Photo**.

   ![General tab](/help/assets/Setup_Program-General.png)

1. On the **KPI** tab, define your KPIs. In this example, separate KPIs are defined for **AEM Sites** and **AEM Assets**. You will be able to specify the KPIs for the products you have licensed.

   * See the section [KPIs](#kpis) for more details on how KPIs are measured in Cloud Manager.

   ![Defining KPIs](/help/assets/Setup_Program-KPIs.png)

1. On the **Provisioning** tab, you can define the on-demand scaling options for your environments if autoscaling is enabled for your program.

   * Autoscaling is applicable to production environment only and may not be available for all customer programs.

   ![Provisioning options](/help/assets/Setup_Program-Provisioning.png)

1. Click **Save** to complete the setup wizard.

Your program will be created. It may take several minutes for resources to be provisioned before the program is ready for use.

## Edit a program {#editing-program}

You can edit programs after they are set up. Follow these steps to edit a program.

1. Log into Cloud Manager at [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) and select the appropriate organization.

1. Navigate to the program from the Cloud Manager home screen.

1. Click **Edit program** to update or modify your program from the **Overview** page.

   ![Edit program option](/help/assets/set-up-program/edit-program1.png) 

1. The **Edit Program** dialog displays, allowing you to update your program. See the section [Program Setup with Cloud Manager](#program-setup-cloud-manager) for details on the fields available.

   ![Edit program dialog](/help/assets/set-up-program/edit-program-general.png)

1. Click **Update** to save your changes.

Note that the changes are saved immediately to Cloud Manager, but will not be reflected in your environments until the next pipeline run.

If you have have not yet created a pipeline see the documents [Configuring Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md).

## Switch between programs {#swithing-programs}

When working on a program, you can quickly switch to another program without returning to the Cloud Manager overview page.

Use the action bar to switch to another program, edit the current program, or add a new program.

![Program switcher](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Sites KPIs are measured on tests run on the staging environment. Typically, these KPIs are scaled down to fit the capabilities of the staging environment.

For example, a user expecting an average of 1000 page views per minute in their production environment and has four dispatcher/publishing servers in production should scale this to 250 page views per minute. This assumes that their staging environment consists of only a single dispatcher/publish server pair.

Assets performance testing is done by uploading assets repeatedly during a 30 minute test period and measuring the processing time for each asset and various system-level metrics.

You may have a content delivery network (CDN) such as Akamai or CloudFront in front of your production environment. Since [!UICONTROL Cloud Manager] tests against the staging environment directly, the KPI should reflect only the traffic expected to pass through the CDN, that is, the cache misses. Typically this will be a relatively small subset of the total production traffic.

## Video overview {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
