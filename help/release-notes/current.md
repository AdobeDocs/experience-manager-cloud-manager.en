---
title: Release Notes for 2024.3.0
description: These are the release notes for Cloud Manager release 2024.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2024.3.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2024.3.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2024.3.0 is 14 March 2024. The next release is planned for 11 April 2024.

## What's New {#what-is-new}

* Details including IP/DNS (FQDN) information of green servers are now displayed in the Cloud Manager UI.

## Early Adoption Program {#early-adoption}

Be a part of our early adoption program and have a chance to test some upcoming features

### Bring your own GitHub {#byo-github}

If you use GitHub to manage your repositories, [you can now validate code directly within your GitHub repositories through Cloud Manager.](/help/managing-code/byo-github.md) This integration eliminates the need to consistently sync code with the Adobe repository and allows you to verify pull requests before merging them into the main branches. This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available.

If you are interested in testing this new feature and sharing your feedback, please send an email to `Grp-CloudManager_BYOG@adobe.com` from your email address associated with your Adobe ID.

## Bug Fixes {#bug-fixes}

* A bug was fixed when the appropriate logs were not generated during the performance test step when the error rate metric failed.
* Improved logic within the performance test service tasked with detecting the absence of a page on the site (404) now ensures smoother, uninterrupted deployment.
