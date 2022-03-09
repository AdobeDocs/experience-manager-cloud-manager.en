---
title: Release Notes for 2022.3.0
description: These are the release notes for Cloud Manager release 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2022.3.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.3.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2022.3.0 is 10 March 2022. The next release is planned for 7 April 2022.

## What's New {#what-is-new}

* [The `reliability_rating` critical metric](understand-your-test-results.md) has been disabled.
* A user can now sort on the columns in the **Pipelines** page in Cloud Manager.

## Bug Fixes {#bug-fixes}

* [The **Skip Load Balancer changes** option](configuring-production-pipelines.md#adding-production-pipeline) can now be properly disabled.
* [The **Skip Load Balancer changes** option](configuring-production-pipelines.md#adding-production-pipeline) is now displayed for the edit deployment pipeline workflow. 
* A subset of manually-created git repositories had incorrect name values which affected [the build artifact reuse feature.](setting-up-project.md#build-artifact-reuse) The names of those repositories have been changed and users will see the corrected name in the Cloud Manager API/UI.
* [When adding or editing a code quality pipeline,](confiugring-non-production-pipelines.md) the options to handle metric failures is no longer displayed.
* Unexpected pipeline variable configurations no longer cause errors in the build step.
