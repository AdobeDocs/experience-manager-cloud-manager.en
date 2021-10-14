---
title: Release Notes for 2021.10.0
description: Follow this page to get information for Cloud Manager Release 2021.10.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---
# Release Notes for 2021.10.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.10.0.

>[!NOTE]
>Refer to [Current Release Notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) to see the latest release notes for Cloud Manager in AEM as a Cloud Service.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.10.0 is October 14, 2021.
The next release is planned for  November 04, 2021.

## What's New {#whats-new}

* Production pipelines can now be executed in an "emergency" mode, bypassing security and performance testing steps for emergency deployments.

* For consistency with Cloud Service, existing deployment pipelines will now be referenced and labelled in the UI as 'Full Stack' pipelines.

* Pipeline card has been refreshed to now display a single, integrated face that shows both production and non-production pipelines, and user can select Run/Pause/Resume directly from the action menu associated with each pipeline.

* Add and edit pipeline experiences have been refreshed to now use familiar, modern modals.

* Users of Cloud Manager can now submit feedback directly from the UI via the **Feedback** button on top right of the landing page.

* Yearly SLA Graphs can now be downloaded from the Cloud Manager user interface.

* Code quality and non-production pipeline executions will now use a more efficient shallow cloning process during the build step, leading to a faster build time for customers with especially large git repositories.

* The Cloud Manager API documentation now includes an interactive playground that allows logged-in users to experiment with the API from their browser. See [Cloud Manager API Playground](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) for more details.

* The tool tip on the Program card will be more descriptive if a selection option under 'Navigate To' is disabled. It will now say "A production environment does not exist."


## Bug Fixes {#bug-fixes}

* When data read from internal systems was not input correctly, it could cause unrelated data provided by CSEs to not be reflected properly in Cloud Manager. 

* In specific customer situations, invalid artifacts downloaded during the build step which should have caused a build failure were being ignored.
