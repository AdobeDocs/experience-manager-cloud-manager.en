---
title: Release Notes for Cloud Manager 2024.11.0
description: Learn about the release of Cloud Manager 2024.11.0.
feature: Release Information

---
# Release notes for Cloud Manager 2024.11.0 {#release-notes}

Learn about the release of [!UICONTROL Cloud Manager] 2024.11.0.

>[!NOTE]
>
>See the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

Release date for [!UICONTROL Cloud Manager] 2024.11.0 is November 7, 2024. 

The next planned release is December 5, 2024.

## What's new {#what-is-new}

* When pages redirect to another domain during performance testing, the test results for those pages are excluded, as they do not accurately represent the actual performance. <!-- (CMGR-5637) -->

## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

The **Bring Your Own Git** feature has been expanded to include support for external repositories such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure.

### Staging-only and production-only pipelines {#staging-production-only-pipelines}

Adobe announces the introduction of support for [staging-only and production-only pipelines](/help/using/stage-prod-only.md). This new feature lets you divide full-stack production deployment pipelines into smaller, more specialized deployments.

If you would like to test this feature and provide feedback, email [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) from your email address associated with your Adobe ID.

## Bug fixes

* A bug in AEM Cloud Manager that caused a "403" error during status updates for content copy operations is now resolved. This issue, attributed to a misconfigured ingress IP address, prevented status propagation and led to some content copy activities appearing stuck and running indefinitely, requiring manual cancellation. The fix now ensures proper status reporting and smoother execution of content copy tasks. <!-- (CMGR-62739) -->
* A recent update addressed an issue in SonarQube where hardcoded passwords were not detected in certain cases. The fix now includes an expanded pattern check, and aligns with default detection standards in SonarQube. <!-- CMGR-62682 -->

<!-- Known Issues {#known-issues}

* A -->
