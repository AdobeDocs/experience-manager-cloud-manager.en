---
title: Release Notes for 2024.6.0
description: These are the release notes for Cloud Manager release 2024.6.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2024.6.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2024.6.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2024.6.0 is 6 June 2024. The next release is planned for 11 July 2024.

## What's New {#what-is-new}

* You can now [use your own GitHub repositories](/help/managing-code/private-repositories.md) as sources for both full-stack and frontend pipelines.
  * Additionally, you can take advantage of GitHub repositories with [git submodules,](/help/managing-code/git-submodules.md) providing you with enhanced control over the auto-generated pipelines used for pull request validation and allowing you to define behaviors for crucial metrics during the code scanning phase.
  * [You also have the choice](/help/managing-code/github-check-config.md) to preserve the report history on GitHub, name the pipeline, and set pipeline variables to suit your needs.
* New OakPal rules were added to the [Cloud Manager Code Quality scan.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
  * Every new rule added as of June 2024 is a non-breaking change.
  * You are urged to address these as soon as possible since these new rules will cause pipelines to fail starting with the Cloud Manager August 2024 release.

## Early Adoption Program {#early-adoption}

Be a part of our early adoption program and have a chance to test some upcoming features

### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md) has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, please send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. 
