---
title: User Journey
description: Learn about the different onboarding scenarios and getting started with Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
---

# User journey {#user-journey}

As an AEM (Adobe Experience Manager) user, you likely fit one of the following scenarios:

* You are new to AEM. 
* You are currently using AEM 6.x.
* You need to upgrade to AEM 6.5 to use [!UICONTROL Cloud Manager].

This document lays out these three scenarios and explains your journey to get started with [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] is only available to Adobe Managed Services (AMS) customers using AEM 6.4 or above.

## Onboarding {#onboarding}

The onboarding process differs depending on if you are new to AMS or are an existing AMS customer.

### New to Adobe Managed Services {#new-to-ams}

As a new customer, you are going to be onboarded to [!UICONTROL Cloud Manager] as part of the onboarding process to Adobe Managed Services.

As part of the onboarding process, you receive a welcome email that includes the following:

* The URL to access [!UICONTROL Cloud Manager].
* Instructions to log in to [!UICONTROL Experience Cloud].
* Instructions to use the Admin Console for managing your users and their respective permissions so they can access [!UICONTROL Cloud Manager] if required.

### Current Adobe Managed Services customer {#existing-customer}

As an existing AMS customer, you must first upgrade your existing production and non-production environments to AEM 6.4 or higher.

During the upgrade, you are onboarded to Cloud Manager and provided with the URL to access [!UICONTROL Cloud Manager]. Additionally, for those users who need to access [!UICONTROL Cloud Manager], you must start using the Admin Console to manage them and their respective permissions.

Your existing AEM project also needs to conform to the recommended best practices, because you begin to start using [!UICONTROL Cloud Manager] for deploying new code changes to your AEM environments.

To get additional information on the benefits of upgrading to AEM 6.5, see [Upgrading to AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Access [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Log into the [!UICONTROL Experience Cloud] landing page using your Adobe Identity Management credentials. From there, select AEM from the solution switcher to access [!UICONTROL Cloud Manager] and your AEM environments.

After logging in to [!UICONTROL Cloud Manager] for the first time, you have access to your AEM environments directly from the [!UICONTROL Cloud Manager] UI. At this point, you are ready to explore all the possibilities of [!UICONTROL Cloud Manager] and prepare your first code branch to be deployed to your stage and production environments.

To get started with [!UICONTROL Cloud Manager], see [First Time Login](/help/getting-started/first-time-login.md).

For additional information about AEM, see [Deploying and Maintaining](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Get started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

After you log in to [!UICONTROL Cloud Manager], you can get started with your AEM project by doing the following:

1. Set up your code repository environment.
1. Set up your team and roles. Role memberships are assigned by adding the user to a [!UICONTROL Cloud Manager] profile using the Admin Console.
1. Set up your source code branches in the Git repository.
1. Define your goals in terms of load and performance KPIs (Key Performance Indicators).
1. Define test scenarios to deploy your code successfully to your stage and production environments after all the quality checks have passed.

## End-to-end journey {#end-to-end-journey}

This diagram illustrates the customer journey at a high level when using the [!UICONTROL Cloud Manager] CI/CD pipeline for deploying your code changes to your staging and production environments.

![End-to-end journey](/help/assets/screen_shot_2018-05-15at124004pm.png)
