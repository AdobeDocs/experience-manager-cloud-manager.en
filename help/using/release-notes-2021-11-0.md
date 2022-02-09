---
title: Release Notes for 2021.11.0
description: Follow this page to get information for Cloud Manager Release 2021.11.0
feature: Release Information
---
# Release Notes for 2021.11.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.11.0.

>[!NOTE]
>Refer to [Current Release Notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) to see the latest release notes for Cloud Manager in AEM as a Cloud Service.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.11.0 is November 04, 2021.
The next release is planned for  December 16, 2021.

## What's New {#whats-new}

* The Git Commit ID will now be displayed in the pipeline execution details making it easier to track the code that was built. 

* The `x-request-id` response header is now visible in the API Playground on [www.adobe.io](https://www.adobe.io/). This header is useful when submitting customer care issues for troubleshooting.

* As a user, I see Pipeline card with zero pipelines provide me with appropriate guidance. 

* A new Activity Page is now available where activities such as pipeline and code executions can be viewed along with their associated details. Over time, the activities listed in this page will expand in scope along with the details provided.

* A new Pipelines page with an on-hover, status popover for easy view of the summary of details is now available. Pipeline executions can be viewed along with their associated details.

* The Edit Pipeline API now supports setting the dispatcher invalidation and flush paths. 

* The Edit Pipeline API now supports changing the environment used in the deploy phases. 

* An optimization in the OakPal scanning process has been introduced for large packages.

* The quality issue CSV file will now contain the timestamp for each quality issue.

* Manage button in the Environments page will no longer be visible in the UI.

## Bug Fixes {#bug-fixes}

* Certain unorthodox build configurations resulted in unnecessary files being stored in the pipeline's Maven artifact cache which resulted in extraneous network I/O when starting and stopping the build container.

* Pipeline PATCH API fails if deploy phase does not exist.

* The `ClientlibProxyResourceCheck` quality rule was producing false positive issues when there were client libraries with common base paths.

* Error message when max number of repositories has been reached did not specify the reason for the error.

* In rare cases, pipelines were failing due to inappropriate retry handling of certain response codes. 
