---
title: Release Notes for 2021.3.0
description: Follow this page to get information for Cloud Manager Release 2021.3.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea,e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
---
# Release Notes for 2021.3.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.3.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.3.0 is March 11, 2021.
The next release is planned for April 08, 2021.

## What's New {#whats-new}

* A new code quality tool [Dispatcher Optimization Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) has been introduced to validate customer dispatcher configuration.

* Users can now see their Cloud Manager role(s) by selecting the **View Cloud Manager Role(s)** option after navigating to the User Profile icon (top right) of Unified Shell. 

* The label **Application for Approval** has been relabeled to **Production Approval** for greater clarity.

* The **Version** label has been relabeled to **Git Tag** in the Production pipeline execution screen.

* The labels which define the behavior when important metrics do not meet the defined threshold have been relabeled to reflect their true behavior – **Cancel Immediately** and **Approve Immediately**. Refer  to [Configuring the Pipeline Settings](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) for more details.

* The class and method deprecation lists have been updated based on version `2021.3.4997.20210303T022849Z-210225` of the AEM Cloud Service SDK.

## Bug Fixes {#bug-fixes}

* Some quality issues were not properly discovered when packages were embedded in other packages. 

* On occasion, if user navigates away from pipeline execution page immediately after starting a pipeline, an error message is displayed stating that the action failed, although the execution actually starts.
