---
title: Release Notes for 2020.10.0
seo-title: AEM Cloud Manager Release Notes for 2020.10.0
description: Follow this page to get information for Cloud Manager Release 2020.10.0
seo-description: Follow this page to get information for AEM Cloud Manager Release 2020.10.0
---
# Release Notes for 2020.10.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2020.10.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.10.0 is October 01, 2020.

## Bug Fixes {#bug-fixes}

* The crawler used for performance testing was incorrectly considering certain resource types as valid web links.

* In some situations, the completion step in performance testing was not correctly handled leading to long-running steps.

* When dispatcher cache invalidation was configured for production deployments, the invalidation was sometimes executed twice.