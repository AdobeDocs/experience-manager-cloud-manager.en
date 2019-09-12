---
title: Release Notes for 2019.9.0
seo-title: AEM Cloud Manager Release Notes for 2019.9.0
description: Follow this page to get information for Cloud Manager Release 2019.9.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.9.0.
---
# Release Notes for 2019.9.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.9.0 Release updates the security test criteria, adds downloadable monitoring graphs, and fixes some customer-reported usability issues.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.9.0 is September 12, 2019.

## What's New {#whats-new}

* The categorization of the Sling Referrer Filter health check has been changed from Critical to Important.
* The categorization of the HTML Library Manager Config health check has been changed from Critical to Important.
* Monitoring graphs can now be downloaded. Refer to [Monitor your Environments](monitor-your-environments.md) for more details.
* If a program does not have a production AEM environment, clicking on the program card from the landing page will navigate to the Cloud Manager overview page, not produce an error dialog.
* The **Pipeline Settings** Card on the **Overview** page has been retitled to **Production Pipeline Settings**.
* The Important Failure Behavior radio buttons have been removed from code-quality only pipelines.
* The **Activity** page now displays the name of the pipeline for each execution.
* The execution page now displays the name of the pipeline.
* The Code Quality summary dialog now shows a description for each rating.

## Bug Fixes {#bug-fixes}

* Some users could not view an execution details when it was waiting for approval.
* On **Overview** page, the right margin was not consistent.
* The build container could run out of memory in large projects.
* Under certain circumstances, the BannedPaths OakPAL rule did not identify installed content under /libs.
* When a quality gate was rejected, the dialog heading still showed *Partially Passed*.

## Known Issues {#known-issues}

* Downloading of monitoring graphs is not available in Safari.
