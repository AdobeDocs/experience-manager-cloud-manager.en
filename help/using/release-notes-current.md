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

* Outbounds HTTP requests from asset tests will now come from a Fixed IP range.


## Bug Fixes {#bug-fixes}

* The **Skip Load Balancer changes** option was not able to be disabled.
*The **Skip Load Balancer changes** option was not displayed on the AMS Dev Deploy **Edit Pipeline Workflow**. 
* A subset of git repositories created manually had an incorrect name value which prevented the build artifact reuse feature from being effective. The names of those repositories have been changed and users will see the corrected name in the Cloud Manager API/UI.
* Build artifacts from non-production pipelines were inappropriately reused on production full stack pipelines.
 * When adding or editing a code quality pipeline, the options to handle metric failures is no longer displayed.
* Some unexpected pipeline variable configurations could cause in the build step.
