---
title: User Journey
description: This document lays out the different onboarding scenarios and explains your getting started journey with Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
---

# User Journey {#user-journey}

As an Adobe Experience Manager user, you may:

* Be new to AEM.
* Be currently using AEM 6.x.
* Need to upgrade to AEM 6.5 release in order to use [!UICONTROL Cloud Manager].

This document lays out these scenarios and explains your journey to get started with [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] is only available to Adobe Managed Services (AMS) customers using AEM 6.4 or above.

## Onboarding {#onboarding}

The onboarding process differs depending on if you are new to AMS or are an existing AMS customer.

### New to Adobe Managed Services {#new-to-ams}

As a new customer, you will be onboarded to [!UICONTROL Cloud Manager] as part of the onboarding process to Adobe Managed Services.

As part of the onboarding process, you will receive a welcome email that includes:

* The URL to access [!UICONTROL Cloud Manager]
* Instructions to login to [!UICONTROL Experience Cloud] 
* Instructions to use the Admin Console for managing your users and their respective permissions so they can access [!UICONTROL Cloud Manager] if required.

### Existing Adobe Managed Services Customer {#existing-customer}

As an existing AMS customer, you will first need to upgrade your existing production and non-production environments to AEM 6.4 or higher.

As you perform the upgrade, you will be onboarded to Cloud Manager and provided with the URL to access [!UICONTROL Cloud Manager]. Additionally, for those users who need to access [!UICONTROL Cloud Manager], you will need to start using the Admin Console to manage them and their respective permissions.

Your existing AEM project will also need to conform to the recommended best practices, as you will start using [!UICONTROL Cloud Manager] for deploying new code changes to your AEM environments.

To get additional information on the benefits of upgrading to AEM 6.5, see the document [Upgrading to AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html).

## Accessing [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

You will get access to [!UICONTROL Cloud Manager] and your AEM environments by simply logging in to the [!UICONTROL Experience Cloud] landing page using your Adobe Identity Management credentials and selecting AEM from the solution switcher interface.

After logging in [!UICONTROL Cloud Manager] for the first time, you will have access to your AEM environments directly from the [!UICONTROL Cloud Manager] UI. At this point, you are ready to explore all the possibilities of [!UICONTROL Cloud Manager] and prepare your first code branch to be deployed to your stage and production environments.

To get started with [!UICONTROL Cloud Manager], see the document [First Time Login](/help/getting-started/first-time-login.md).

For additional information about AEM, see the document [Deploying and Maintaining](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html).

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Once you are logged in to [!UICONTROL Cloud Manager] you can get started with your AEM project by:

1. Setting up your code repository environment.
1. Setting up your team and roles.
   * Role memberships are assigned by adding the user to a [!UICONTROL Cloud Manager] profile using the Admin Console.
1. Setting up your source code branches in the git repository.
1. Defining your goals in terms of load and performance KPIs.
1. Defining test scenarios to successfully deploy your code to your stage and production environments once all the quality checks have passed successfully.

## End-to-End Journey {#end-to-end-journey}

This diagram illustrates the customer journey at a high level when using [!UICONTROL Cloud Manager] CI/CD pipeline for deploying your code changes to your staging and production environments.

![End-to-end journey](/help/assets/screen_shot_2018-05-15at124004pm.png)
