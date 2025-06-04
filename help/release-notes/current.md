---
title: Release Notes for Cloud Manager 2025.6.0
description: Learn about the release of Cloud Manager 2025.5.0 on Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
---
# Release notes for Cloud Manager 2025.6.0 on Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2025.6.0 on Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2025.6.0 is Thursday, June 5, 2025. 

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, July 10, 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## What's new {#what-is-new}

* **(UI) Pipeline favorites**

    In this release, Cloud Manager introduces the ability to pin favorite pipelines, letting you mark specific pipelines as favorites so they appear at the top of the list on the **Pipelines** page. This enhancement makes frequently accessed pipelines easier to find and run. <!-- CMGR-68293 -->

    ![Pipelines marked as favorites](/help/release-notes/assets/pipeline-favorites.png) *Two pipelines marked as favorites.*

    See [Mark pipeline favorites](/help/using/managing-pipelines.md#pipeline-favorites).


## Early adoption program {#early-adoption}

Participate in Cloud Manager's Early Adoption Program to get exclusive access to upcoming features before their general release.

The following early adoption opportunities are currently available:

### Manage Access Tokens{#access-tokens}

Use the **Manage Access Tokens** feature in Cloud Manager to view, rename, and delete access tokens associated with external Bring Your Own Git repositories, such as GitHub Enterprise, GitLab, Bitbucket, and Azure DevOps.

See [Manage Access Tokens](/help/managing-code/manage-access-tokens.md).

If you are interested in testing this new feature and sharing your feedback, send an email to from your email address associated with your Adobe ID.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure.

### Staging-only and production-only pipelines {#staging-production-only-pipelines}

Adobe announces the introduction of support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md). This new feature lets you divide full-stack production deployment pipelines into smaller, more specialized deployments.

If you would like to test this feature and provide feedback, email [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) from your email address associated with your Adobe ID.


## Bug fix {#bug-fixes}

* AEM Cloud Manager now correctly maps Maven build failures caused by 409 errors (conflicts) when fetching customer artifacts to a customer-caused failure. This change improves error messaging by distinguishing between internal errors and issues related to customer environment setup. <!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
