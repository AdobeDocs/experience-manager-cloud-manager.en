---
title: Release Notes for Cloud Manager 2026.3.0
description: Learn about the release of Cloud Manager 2026.3.0 on Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
---
# Release notes for Cloud Manager 2026.3.0 on Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2026.3.0 on Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2026.3.0 is Thursday, March 5, 2026. 
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, April 2, 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## What's new {#what-is-new}

* **Support for UI extensibility in AEM Experience Hub**
    Support for UI Extensions in [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) is now enabled, letting developers extend the interface with custom functionality and widgets built using Adobe App Builder. 

    To learn more, see [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Configuration pipelines now support managed secrets**

    Users can now add and manage secrets directly in Cloud Manager configuration pipelines. These secrets securely override values in the pipeline configuration spec and support flexible, environment-specific deployments.

    ![View/Edit variables option on the drop-down menu for a selected pipeline](/help/release-notes/assets/view-edit-variables-option.png) 
    *View/Edit variables option on the drop-down menu for a selected pipeline.* 

    ![Variables Configuration dialog box](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Variables Configuration dialog box.*

* **Improved stability, performance, and reliability**

    This release includes optimization and maintenance updates that improved the stability, performance, and reliability of Cloud Manager.


## Beta programs {#beta-program}

Participate in Cloud Manager's Beta programs to get exclusive access to upcoming features before their general release.

The following opportunities are currently available:

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Faster builds with module caching {#quick-build-cm-pipelines}

A new build model compiles only changed modules (rather than the entire repo) using module-level caching to shorten build times. It applies to Code Quality and Full Stack pipelines.

![Edit Non-Production Pipeline dialog box showing the two Build Strategy options which are Full Build and Smart Build](/help/release-notes/assets/non-production-pipeline-edit.png)
*Edit Non-Production Pipeline dialog box showing the two Build Strategy options which are Full Build and Smart Build.* 

In the **Add/Edit Pipeline** dialog box, under the **Source Code** tab, a new **Build Strategy** section lets you choose one of the following build options:

* **Full Build** — builds all modules in the repository on every run.
* **Smart Build** — builds only modules that changed since the last commit, which shortens overall build time.

See [Add a non-production pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline) and [About using Smart Build in a non-production pipeline](/help/using/non-production-pipelines.md#about-smart-build).

You control which pipelines use **Smart build**. During the beta, this option appears only for **Code Quality** and **Dev Full Stack Code Deployment** pipelines.

Interested? Email [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) with your Adobe OrgID and Program ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Bug fixes {#bug-fixes}

There are no significant bug fixes in the March 2026 Cloud Manager on AMS release. 

<!--
Known Issues {#known-issues}

* A 
-->
