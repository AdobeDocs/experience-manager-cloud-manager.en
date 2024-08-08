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

The release date for [!UICONTROL Cloud Manager] 2024.8.0 is August 13, 2024. The next release is planned for September 14, 2024.

## What's new {#what-is-new}

* For stage-only and production-only pipelines (available as part of the [early adopter program](#staging-production-only-pipelines)), you can now execute them in [emergency mode,](/help/using/stage-prod-only.md#emergency-mode) skipping stage testing.

## Early adoption program {#early-adoption}

Be a part of Adobe's early adoption program and have a chance to test some upcoming features.

### Staging-only and production-only pipelines {#staging-production-only-pipelines}

Adobe is excited to announce the introduction of support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md). This new feature lets you divide full-stack production deployment pipelines into smaller, more specialized deployments.

If you would like to test this feature and provide feedback, email `Grp-cloudmanager_splitpipelines@adobe.com` using the email address associated with your Adobe ID.

## Bug fixes

* A rare issue was corrected where pipeline steps were found to be running after the pipeline was deleted.
* Re-running the pipeline now works on the first attempt, correcting a rare issue where a rerun had to be started multiple times.
* Scheduled deployment steps for full-stack pipelines now respect the selected scheduled date and do not revert to **Now**.
* The statuses of failed copy content tasks are now properly reflected and no longer incorrectly show an `In Progress` status in rare circumstances.
