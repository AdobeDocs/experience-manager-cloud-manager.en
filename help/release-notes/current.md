---
title: Release Notes for Cloud Manager 2025.9.0
description: Learn about the release of Cloud Manager 2025.9.0 on Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
---
# Release notes for Cloud Manager 2025.9.0 on Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2025.9.0 on Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2025.9.0 is Thursday, September 4, 2025. 

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, October 2, 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## What's new {#what-is-new}

* **Config pipelines with private respositories**

    Cloud Manager now supports config pipelines with private repositories across GitHub, Bitbucket, Azure DevOps, and GitLab.

* **Support now added for Azure DevOps private repositories** 

    Documentation updates include configuration steps for Bring Your Own Git with Azure DevOps and pull request validation. See [Add External Repositories in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).


* **Supoort now added for Azure DevOps private repositories** 

    Documentation updates include configuration steps for Bring Your Own Git with Azure DevOps and pull request validation. See [Add External Repositories in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

* **Adobe Experience Hub now available**

    Experience Hub is a unified starting point that delivers personalized, contextual experiences to help users achieve goals faster. The rollout concludes by August 26, 2025 making it available to all users. The new Experience Hub is accessible directly at [experience.adobe.com](https://experience.adobe.com/). To learn more, see [Adobe Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub).

* **Staging-only and production-only pipelines**

    Cloud Manager now supports staging-only and production-only pipelines. This feature lets you split full-stack production deployments into smaller, purpose-specific pipelines. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release --

    ![Add non-production pipeline dialog box with Full Stack Code radio button selected and Stage environment selected](/help/release-notes/assets/add-non-production-pipeline.png)

    See [Stage-Only and Prod-Only Pipelines](/help/using/stage-prod-only.md).

## Beta programs {#beta-program}

Participate in Cloud Manager's Beta programs to get exclusive access to upcoming features before their general release.

The following opportunities are currently available:


### Bring Your Own Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Customers can now onboard their Azure DevOps Git repositories into Cloud Manager, with support for both modern Azure DevOps and legacy VSTS (Visual Studio Team Services) repositories.

* For Edge Delivery Services users, the onboarded repository can be used to sync and deploy site code.
* For AEM as a Cloud Service and Adobe Managed Services (AMS) users, the repository can be linked to both full-stack and frontend pipelines.

Support for additional pipeline types and pull request validation through code quality pipelines is coming soon.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/azure-repo.png)

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. 

#### Manage Access Tokens{#manage-access-tokens}

Use **Manage Access Tokens** in Cloud Manager to view, rename, and delete access tokens associated with external BYOG repositories, such as GitHub Enterprise, GitLab, Bitbucket, and Azure DevOps.

See [Manage Access Tokens](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. --> 

## Bug fixes {#bug-fixes}

There are no significant bug fixes in the August Cloud Manager release.

<!--
Known Issues {#known-issues}

* A -->
