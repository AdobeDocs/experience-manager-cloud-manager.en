---
title: Release Notes for 2020.8.0
seo-title: AEM Cloud Manager Release Notes for 2020.8.0
description: Follow this page to get information for Cloud Manager Release 2020.8.0
seo-description: Follow this page to get information for AEM Cloud Manager Release 2020.8.0
---
# Release Notes for 2020.8.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2020.8.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.8.0 is August 06, 2020.

## What's New {#whats-new}

* Sites Performance Testing now supports the optional use of authentication.

   Refer to [Authenticated Sites Performance Testing](configuring-pipeline.md#authenticated-sites-performance) to learn how to authenticate AEM Sites performance testing.

* Authentication-bound Private Maven Repositories are now supported.

## Bug Fixes {#bug-fixes}

* Some unnecessary and undesired SonarQube plugins were being executed as part of the Code Quality scanning. 

* On the pipeline execution page, the branch name was incorrectly formatted. 

* When deploying to topologies with a single publish, a single dispatcher and a cold standby author, the dispatcher was erroneously removed from the load balancer. 

* In some cases, completed pipeline executions were not successfully recorded as having been completed thereby preventing new executions of the pipeline.

* Pipeline executions would occasionally get *stuck* due to internal communication issues.

* The tooltip on the program cards were not consistently correct.

* There was a color mismatch on the overview page.

