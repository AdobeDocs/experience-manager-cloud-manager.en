---
title: Release Notes for Cloud Manager 2026.11.0
description: Learn about the release of Cloud Manager 2026.11.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
---

# Release notes for Cloud Manager 2026.11.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Learn about the release of [!UICONTROL Cloud Manager] 2026.11.0 in Adobe Managed Services.

See also the [current release notes for Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Release dates {#release-date}

The release date for [!UICONTROL Cloud Manager] 2026.11.0 is Thursday, November 5, 2026. 
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

The next planned release is Thursday, December 3, 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## New features {#new-features}

### Web Tier Pipelines for AEM Managed Services {#web-tier-pipelines}

Cloud Manager now supports dedicated Web Tier Pipelines for AMS programs, allowing teams to deploy Dispatcher and web tier configurations independently from full stack deployments. This enables faster iteration on web tier changes while reducing unnecessary full pipeline executions. 

When a Web Tier Pipeline is configured, full stack pipelines automatically skip web tier deployment for that environment to prevent deployment conflicts. Removing the Web Tier Pipeline restores the default deployment behavior automatically. <!-- CMGR-27553 -->

See [Web tier config pipelines](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines).

## Beta programs {#beta-program}

There are no beta program opportunities currently available.

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## Bug fixes {#bug-fixes}


* Code quality scan fails on large projects. The code quality (SonarQube) scan generates multi-gigabyte debug logs and is killed when scanning certain bundled libraries, failing the build. The scan has been corrected so it completes normally on affected projects. (CMGR-80025)

* Sites usage CSV export showed month labels shifted by one month. On the License > Sites Usage Details page, the CSV export shows month labels shifted one month earlier for users in time zones behind UTC. The export now shows the correct month labels regardless of the user's time zone. (CMGR-80903)

* Reusing an access token name no longer overwrites the existing token. Reusing an existing access token name within a program overwrites the shared token and creates duplicate access secrets. Cloud Manager now handles token name reuse correctly, preventing accidental overwrites and duplicates. (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
