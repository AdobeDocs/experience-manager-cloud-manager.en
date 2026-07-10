---
title: Release Notes for Cloud Manager 2026.7.0
description: Learn about the release of Cloud Manager 2026.7.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
---

# Release notes for Cloud Manager 2026.7.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2026.6.0 in Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2026.7.0 is Thursday, July 9, 2026. 
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, August 6, 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## What's new {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **Improved build performance with module caching**
    A new build model compiles only changed modules (rather than the entire repository) using module-level caching to improve build performance. It applies to production pipelines. You control which production pipelines use **Smart Build**.

    For more information, see the following:

    * [About using Smart Build in a production pipeline](/help/using/production-pipelines.md#about-smart-build) and [About using Smart Build in a non-production pipeline](/help/using/non-production-pipelines.md#about-smart-build) 
    * [Add a production pipeline](/help/using/production-pipelines.md##adding-production-pipeline) and [Add a non-production pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline).

## Beta programs {#beta-program}

Participate in Cloud Manager's beta programs to get exclusive access to upcoming features before their general release.

>[!IMPORTANT]
>
>Beta releases contain defects and are provided "AS IS" without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (by way of Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk and should not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunities are currently available:

### Web Tier Pipelines for AEM Managed Services {#web-tier-pipelines}

Cloud Manager now supports dedicated Web Tier Pipelines for AMS programs, allowing teams to deploy Dispatcher and web tier configurations independently from full stack deployments. This enables faster iteration on web tier changes while reducing unnecessary full pipeline executions. When a Web Tier Pipeline is configured, full stack pipelines automatically skip web tier deployment for that environment to prevent deployment conflicts. Removing the Web Tier Pipeline restores the default deployment behavior automatically. 

To join the Beta, contact your Adobe Customer Success Engineer to learn more. 




## Bug fixes {#bug-fixes}

There are no significant bug fixes in the June 2026 Cloud Manager on AMS release. 

<!--
Known Issues {#known-issues}

* A 
-->
