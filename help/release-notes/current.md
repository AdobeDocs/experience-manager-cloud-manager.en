---
title: Release Notes for 2024.5.0
description: These are the release notes for Cloud Manager release 2024.5.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2024.5.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2024.5.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2024.5.0 is 9 May 2024. The next release is planned for 6 June 2024.

## What's New {#what-is-new}

* The Content Audit step is now skipped when a pipeline is running in [emergency mode.](/help/using/code-deployment.md#emergency-pipeline)

## Early Adoption Program {#early-adoption}

Be a part of our early adoption program and have a chance to test some upcoming features

### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for staging-only and production-only pipelines has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

Check back soon for details on how to use this feature and how to join the early adoption program.

### Bring your own GitHub {#byo-github}

If you use GitHub to manage your repositories, [you can now validate code directly within your GitHub repositories through Cloud Manager.](/help/managing-code/byo-github.md) This integration eliminates the need to consistently sync code with the Adobe repository and allows you to verify pull requests before merging them into the main branches. This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available.

If you are interested in testing this new feature and sharing your feedback, please send an email to `Grp-CloudManager_BYOG@adobe.com` from your email address associated with your Adobe ID.

## Bug Fixes {#bug-fixes}

* A bug where Cloud Manager reused artifacts with the wrong commit hash has been addressed.
