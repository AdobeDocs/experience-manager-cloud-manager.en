---
title: Release Notes for 2024.7.0
description: Learn about the release notes for Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager 2024.7.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, see [Cloud Manager in AEM as a Cloud Service's current release notes](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Release date {#release-date}

The release date for [!UICONTROL Cloud Manager] 2024.7.0 is July 18, 2024. The next release is planned for August 13, 2024.

## What's new {#what-is-new}

* The [production pipeline](/help/using/production-pipelines.md#adding-production-pipeline) and [non-production pipeline](/help/using/non-production-pipelines.md#adding-non-production-pipeline) trigger **On Git Changes** to start the pipeline on a commit is now available for [private repositories](/help/managing-code/private-repositories.md).
* A pre-production pipeline is only triggerable manually and cannot be configured as **On Git Changes**.
* For production-only pipelines, the list of promotable executions includes executions with an artifact version greater than the artifact version deployed on the production environment.
* [The AEM Project Archetype](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview) has been updated to [version 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49).

## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test some upcoming features

### Staging-only and Production-only pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md) is now introduced, letting you split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. 
