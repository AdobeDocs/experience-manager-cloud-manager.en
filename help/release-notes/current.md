---
title: Release Notes for Cloud Manager 2026.5.0
description: Learn about the release of Cloud Manager 2026.5.0 in Adobe Managed Services.
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

# Release notes for Cloud Manager 2026.5.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2026.5.0 in Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2026.5.0 is Thursday, May 7, 2026. 
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, June 4, 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## What's new {#what-is-new}

There are no significant new features in the May 2026 Cloud Manager on AMS release.

## Beta programs {#beta-program}

Participate in Cloud Manager's beta programs to get exclusive access to upcoming features before their general release.

>[!IMPORTANT]
>
>Beta releases may contain defects and are provided "AS IS" without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (by way of Adobe Support Services or otherwise) the beta releases. Adobe advises customers to use caution and not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Accordingly, any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunities are currently available:

### Web Tier Pipelines for AEM Managed Services {#web-tier-pipelines}

Cloud Manager now supports dedicated Web Tier Pipelines for AMS programs, allowing teams to deploy Dispatcher and web tier configurations independently from full stack deployments. This enables faster iteration on web tier changes while reducing unnecessary full pipeline executions. When a Web Tier Pipeline is configured, full stack pipelines automatically skip web tier deployment for that environment to prevent deployment conflicts. Removing the Web Tier Pipeline restores the default deployment behavior automatically. 

To join the Beta, contact your Adobe Customer Success Engineer to learn more. 

### Faster builds with module caching {#quick-build-cm-pipelines}

A new build model compiles only changed modules (rather than the entire repo) using module-level caching to shorten build times. It applies to Code Quality and Full Stack pipelines.

![Edit Non-Production Pipeline dialog box showing the two Build Strategy options which are Full Build and Smart Build](/help/release-notes/assets/non-production-pipeline-edit.png)
*Edit Non-Production Pipeline dialog box showing the two Build Strategy options which are Full Build and Smart Build.* 

In the **Add/Edit Pipeline** dialog box, under the **Source Code** tab, a new **Build Strategy** section lets you choose one of the following build options:

* **Full Build** — builds all modules in the repository on every run.
* **Smart Build** — builds only modules that changed since the last commit, which shortens overall build time.

See [Add a non-production pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline) and [About using Smart Build in a non-production pipeline](/help/using/non-production-pipelines.md#about-smart-build).

You control which pipelines use **Smart Build**. During the beta, this option appears only for **Code Quality** and **Dev Full Stack Code Deployment** pipelines.

To join the Beta, email [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) with your Adobe Organization ID and Program ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Bug fixes {#bug-fixes}

There are no significant bug fixes in the May 2026 Cloud Manager on AMS release. 

<!--
Known Issues {#known-issues}

* A 
-->
