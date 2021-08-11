---
title: Release Notes for 2021.8.0
description: Follow this page to get information for Cloud Manager Release 2021.8.0
feature: Release Information
---
# Release Notes for 2021.8.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.8.0.

>[!NOTE]
>Refer to [Current Release Notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) to see the latest release notes for Cloud Manager in AEM as a Cloud Service.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.8.0 is August 12, 2021.
The next release is planned for September 09, 2021.

## What's New {#whats-new}

* Self-service capability to allow users to create and manage multiple repositories via Cloud Manager UI.

* SonarQube was unnecessarily reading git history data. On large code bases, this could lead to an unnecessary build performance penalty.

* There is now an API available to invalidate the Maven dependency cache per pipeline.

* The flow and task related to assets testing should happen in the region of the pipeline execution. 

* As a Deployment Manager, you can add or edit a non-Production Pipeline from the pipeline card.

## Bug Fixes {#bug-fixes}

* *Update Available* status should not be displayed when the latest release is less than the current release.

* Occasionally, when a pipeline is triggered twice for some reason, it results in one of the executions failing with *cannot update pipeline execution status* error. 
