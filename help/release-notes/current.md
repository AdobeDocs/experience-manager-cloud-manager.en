---
title: Release Notes for 2023.9.0
description: These are the release notes for Cloud Manager release 2023.9.0.
feature: Release Information
---

# Release Notes for Cloud Manager Release 2023.9.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2023.9.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2023.9.0 is 14 September 2023. The next release is planned for 5 October 2023.

## What's New {#what-is-new}

* This release consists of bug fixes only for Cloud Manager.

## Bug Fixes {#bug-fixes}

* When a program is deleted, any associated, running pipeline is now also deleted.
* An occasional error has been fixed where all steps of a pipeline execution were marked as completed, but the status of the pipeline was still running, giving the appearance of a stuck state.
* An error was corrected when CI/CD pipelines failed for repository branches generated the archetype.
