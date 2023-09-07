---
title: Release Notes for 2023.9.0
description: These are the release notes for Cloud Manager release 2023.9.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2023.9.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2023.9.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2023.9.0 is 7 September 2023. The next release is planned for 5 October 2023.

## What's New {#what-is-new}

This release contains bug fixes.

## Bug Fixes {#bug-fixes}

* When a program is deleted, any associated, running pipeline is also deleted, ensuring that the pipeline is not incorrectly designated as failed status.
* Occasionally, when all steps of a pipeline execution are 'completed',  status of the pipeline is seen as "running", making it seem to be in a stuck state. It is now seen as 'Complete'.
* For repository branches generated using code generator archetype, CI/CD pipeline fails.
