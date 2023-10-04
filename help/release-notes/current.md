---
title: Release Notes for 2023.10.0
description: These are the release notes for Cloud Manager release 2023.10.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2023.10.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2023.10.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2023.10.0 is 5 October 2023. The next release is planned for 2 November 2023.

## What's New {#what-is-new}

* The **Deployment Manager** role can [configure a set of content paths which will either be invalidated or flushed from the AEM Dispatcher cache when a non-production pipeline is run.](/help/using/non-production-pipelines.md)
  * These cache actions will be performed as part of the deployment pipeline step, just after any content packages are deployed.
  * These settings use standard AEM Dispatcher behavior.
* With the October 2023 release of Cloud Manager, Java versions are being updated via a phased roll-out.
    * The Java versions are being updated to Oracle JDK 8u371 and Oracle JDK 11.0.20.
    * [See the OpenJDK advisory](https://openjdk.org/groups/vulnerability/advisories/) for details on the security and bugfixes in these JDK updates.

## Bug Fixes {#bug-fixes}
