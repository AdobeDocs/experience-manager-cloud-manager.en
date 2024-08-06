---
title: Release Notes for Cloud Manager 2024.8.0
description: Learn about the release notes for Cloud Manager 2024.8.0.
feature: Release Information

---

# Release notes for Cloud Manager 2024.8.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] 2024.8.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Release date {#release-date}

The release date for [!UICONTROL Cloud Manager] 2024.8.0 is July 18, 2024. The next release is planned for August 8, 2024.

## What's new {#what-is-new}

* The `sonar-maven-plugin` is now upgraded to work with Java 17 to Java 21. The plug-in is used to integrate SonarQube, a tool for continuous inspection of code quality, into the build process. <!-- CMGR-58634 -->
* A documentation update was made to the current list of [Copy Content tool limitations](/help/using/content-copy.md#limitations). See the last four bullets in the list. <!-- CQDOC-21876 -->
* If the `authorizeEmergencyExecutionMode` flag is set to true, you can start a classic production pipeline in *emergency mode*, skipping stage testing. You can now enable this *emergency mode* from directly in the user interface for stage and pre-production pipelines. <!-- CMGR-58091 -->


## Early adoption program {#early-adoption}

Be a part of Adobe's early adoption program and have a chance to test some upcoming features.

### Staging-only and production-only pipelines {#staging-production-only-pipelines}

Adobe is excited to announce the introduction of support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md). This new feature lets you divide full-stack production deployment pipelines into smaller, more specialized deployments.

If you would like to test this feature and provide feedback, email `Grp-cloudmanager_splitpipelines@adobe.com` using the email address associated with your Adobe ID.


## Bug fixes

* In rare cases, the pipeline step was found to be running even after the pipeline was deleted. <!-- CMGR-58614 -->
* In rare instances, when customers tried to re-run the pipeline multiple times, only the first attempt functioned correctly.
* You create a full stack pipeline with the schedule step enabled, then start the deployment and proceed to the schedule step. After selecting any date, then waiting a few seconds, the **[!UICONTROL Now]** option was getting selected automatically, and the date was resetting to the default value. <!-- CMGR-58318 -->
* In rare cases, performing a [copy content ](/help/using/content-copy.md#copy-content) task incorrectly displayed an *In progress* status even though it failed. <!-- CMGR-58297 -->