---
title: Release Notes for 2021.12.0
description: These are the release notes for Cloud Manager release 2021.12.0.
feature: Release Information
---
# Release Notes for Cloud Manager Release 2021.12.0 {#release-notes}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] release 2021.12.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2021.12.0 is 16 December 2021. The next release is planned for January 2022.

## What's New {#whats-new}

* The commit hash, which is already visible in the UI, is now also provided in the API.
* The Activity page now includes a pop-over for running pipelines that provides a summary of pipeline details at-a-glance.
* Updates to include additional details presented in the Activities page were added.
* The Learn tab in Cloud Manager now includes quick access to API guides and associated resources.
* A user with the Deployment Manager role can now initiate the Project/Branch creation wizard for a repository with no branches from the action menu on the repositories page.
* The Deployment Manager, who is in the add or edit pipeline workflow, is now informed on how to create a branch or project if the selected repository has no branches.
* In the Edit Production Pipeline window, when there is more than one stage environment for production, a dropdown for environment selection is available.
* The version of the AEM Project Archetype used by Cloud Manager has been updated to version 32.

## Bug Fixes {#bug-fixes}

* Full stack production pipelines remain named "Production Pipeline" even when the user inputs a different name in the name field.
