---
title: Release Notes for 2022.11.0
description: These are the release notes for Cloud Manager release 2022.11.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2022.11.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.11.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2022.11.0 is 3 November 2022. The next release is planned for 29 November 2022.

## What's New {#what-is-new}

* Support for horizontal multi-region auto-scaling has been added to Cloud Manager.
* For users who only have the **Cloud Manager User** role, a new card on the welcome page has been customized to guide them through navigating to AEM environments and restricted program access.
* Users without any Cloud Manager roles will no longer be able to access program details. Such users can, however, navigate to author end points from the Cloud Manager landing page.
* Pipeline failures arising from retry failures have been eliminated by improving resiliency.

## Bug Fixes {#bug-fixes}

* The feedback provided to the user has been improved during AEM app build when Maven faces connectivity issues to private repos.
* Fixed the rare instances of auto-scale events triggering when the health check system was not able to retrieve a valid health score.
