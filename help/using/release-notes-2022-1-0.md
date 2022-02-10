---
title: Release Notes for 2022.01.0
description: These are the release notes for Cloud Manager release 2022.01.0.
feature: Release Information
---
# Release Notes for Cloud Manager Release 2021.12.0 {#release-notes}

The following section outlines the general release notes for [!UICONTROL Cloud Manager] release 2022.01.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2022.01.0 is 20 January 2022. The next release is planned for 10 February 2022.

## What's New {#whats-new}

* Cloud Manager will [avoid rebuilding the code base when it detects that the same git commit is used](/help/using/setting-up-project.md#build-artifact-reuse) in multiple full stack pipeline executions.
* Upon generating a git password, the expiration date will be displayed.

## Bug Fixes {#bug-fixes}

* Infrequent occurrences of false positive pipeline failures have been addressed.
* For programs with only one repository, the pipeline execution screen will now display the repository name.
