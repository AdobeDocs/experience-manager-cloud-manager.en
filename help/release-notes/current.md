---
title: Release Notes for Cloud Manager 2025.7.0
description: Learn about the release of Cloud Manager 2025.7.0 on Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
---
# Release notes for Cloud Manager 2025.7.0 on Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2025.7.0 on Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2025.7.0 is Thursday, July 10, 2025. 

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, August 7, 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## What's new {#what-is-new}

* **Staging-only and production-only pipelines**

    Cloud Manager now supports staging-only and production-only pipelines. This feature lets you split full-stack production deployments into smaller, purpose-specific pipelines. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

    ![Add non-production pipeline dialog box with Full Stack Code radio button selected and Stage environment selected](/help/release-notes/assets/add-non-production-pipeline.png)

    See [Stage-Only and Prod-Only Pipelines](/help/using/stage-prod-only.md).

* **Pipeline favorites**

    In this release, Cloud Manager introduces the ability to pin favorite pipelines, letting you mark specific pipelines as favorites so they appear at the top of the list on the **Pipelines** page. This enhancement makes frequently accessed pipelines easier to find and run. <!-- CMGR-68293 -->

    ![Pipelines marked as favorites](/help/release-notes/assets/pipeline-favorites.png) *Two pipelines marked as favorites.*

    See [Mark pipeline favorites](/help/using/managing-pipelines.md#pipeline-favorites).


## Early adopter program {#beta-program}

Participate in Cloud Manager's alpha and beta programs to get exclusive early access to upcoming features before their general release.

The following opportunities are currently available:


### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** (BYOG) feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure.

#### Manage Access Tokens{#access-tokens}

Use **Manage Access Tokens** with BYOG, to view, rename, and delete access tokens associated with external Bring Your Own Git repositories, such as GitHub Enterprise, GitLab, Bitbucket, and Azure DevOps.

See [Manage Access Tokens](/help/managing-code/manage-access-tokens.md).

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure.


## Bug fixes {#bug-fixes}

There are no significant bug fixes in the July Cloud Manager release.

<!--
Known Issues {#known-issues}

* A -->
