---
title: Release Notes for 2022.8.0
description: These are the release notes for Cloud Manager release 2022.8.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2022.8.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.8.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2022.8.0 is 11 August 2022. The next release is planned for 9 September 2022.

## What's New {#what-is-new}

* Under certain scenarios, a silent re-try mechanism will help ensure that the deployment pipeline does not result in an error state.
* [The AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) included in Cloud Manager was updated to version 37.

## Bug Fixes {#bug-fixes}

* Certain cases of infrequent repository creation failures have been made more resilient.
* Rare occurrences of VSTS org set up errors are now reduced due to retries introduced.
