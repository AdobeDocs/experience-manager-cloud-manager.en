---
title: Release Notes for 2021.6.0
description: Follow this page to get information for Cloud Manager Release 2021.6.0
feature: Release Information
exl-id: 01449ad2-4c5a-40d7-89ab-43b1a762fad3
---
# Release Notes for 2021.6.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.6.0.

>[!NOTE]
>Refer to [Current Release Notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) to see the latest release notes for Cloud Manager in AEM as a Cloud Service.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.6.0 is June 10, 2021.
The next release is planned for July 15, 2021.

## What's New {#whats-new}

* Assets and Sites tests will now run in parallel (when applicable), thereby reducing the total pipeline execution time. This feature will be enabled for customers over the next several weeks.

* Maven Dependencies downloaded during the build step will now be cached between pipeline executions. This feature will be enabled for customers over the next several weeks. 

* The default branch name used during both project creation and  in the default push command via manage git workflows has been changed to `main`. 

* Edit program experience in the UI has been refreshed. Refer to [Editing a Program](/help/using/setting-up-program.md#editing-program) to learn more.

* The quality rule `ImmutableMutableMixCheck` has been updated to classify `/oak:index` nodes as being immutable.

* The quality rules `CQBP-84` and `CQBP-84--dependencies` have been consolidated into a single rule. As part of this consolidation, the scanning of dependencies more accurately identifies issues in third party dependencies which are being deployed to the AEM runtime.

* In some situations, a failure to calculate the Skipped Tests metric would cause pipeline executions to fail.

## Bug Fixes {#bug-fixes}

* JCR node definitions containing a newline after the root element name were not correctly parsed.

* List repositories API would not filter deleted repositories.

* An incorrect error message was displayed when an invalid value was provided for the schedule step. 

* In some cases when the pipeline execution reached deploy to production step, and user stops execution, the deploy status  message in the UI did not correctly reflect what was actually happening.
