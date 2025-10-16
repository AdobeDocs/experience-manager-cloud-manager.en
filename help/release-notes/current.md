---
title: Release Notes for Cloud Manager 2025.10.0
description: Learn about the release of Cloud Manager 2025.10.0 on Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
---
# Release notes for Cloud Manager 2025.10.0 on Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2025.10.0 on Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2025.10.0 is Thursday, October 2, 2025. 

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, November 6, 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## What's new {#what-is-new}

There are no significant new features in the October Cloud Manager release.


## Beta programs {#beta-program}

Participate in Cloud Manager's Beta programs to get exclusive access to upcoming features before their general release.

The following opportunities are currently available:

### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.

### Faster builds with module caching {#quick-build-cm-pipelines}

A new build model compiles only changed modules (rather than the entire repo) using module-level caching to shorten build times. It applies to code-quality, full-stack, and stage-only pipelines.

![Edit Non-Production Pipeline dialog box showing the two Build Strategy options which are Full Build and Smart Build](/help/release-notes/assets/non-production-pipeline-edit.png) *Edit Non-Production Pipeline dialog box showing the two Build Strategy options which are Full Build and Smart Build.*

In the **Add/Edit Pipeline** dialog box, under the **Source Code** tab, a new **Build Strategy** section lets you choose one of the following build options:

* **Full Build** — builds all modules in the repository on every run.
* **Smart Build** — builds only modules that changed since the last commit, which shortens overall build time.

You control which pipelines use **Smart build**. During the beta, this option appears only for **Code Quality** and **Dev Deployment** pipelines.

Interested? Email [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) with your Adobe OrgID and Program ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


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

There are no significant bug fixes in the October Cloud Manager release. 

<!--
Known Issues {#known-issues}

* A -->
