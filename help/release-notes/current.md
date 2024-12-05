---
title: Release Notes for Cloud Manager 2024.12.0
description: Learn about the release of Cloud Manager 2024.12.0 on Adobe Managed Services.
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
---
# Release notes for Cloud Manager 2024.12.0 on Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2024.12.0 on Adobe Managed Services.

>[!NOTE]
>
>See the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

The release date for [!UICONTROL Cloud Manager] 2024.12.0 is December 5, 2024. 

The next planned release is January 23, 2025.

<!-- ## What's new {#what-is-new} -->

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
