---
title: Release Notes for 2024.7.0
description: These are the release notes for Cloud Manager release 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2024.7.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2024.7.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2024.7.0 is 18 July 2024. The next release is planned for 8 August 2024.

## What's New {#what-is-new}

* The [production pipeline](/help/using/production-pipelines.md#adding-production-pipeline) and [non-production pipeline](/help/using/non-production-pipelines.md#adding-non-production-pipeline) trigger **On Git Changes** to start the pipeline on a commit is now available for [private repositories.](/help/managing-code/private-repositories.md)
* A pre-production pipeline is only triggerable manually and can not be configured as **On Git Changes**.
* For production-only pipelines, the list of promotable executions includes those that have the artifact version greater than the artifact version deployed on the production environment.

## Early Adoption Program {#early-adoption}

Be a part of our early adoption program and have a chance to test some upcoming features

### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md) has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, please send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. 
