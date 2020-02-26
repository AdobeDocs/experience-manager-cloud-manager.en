---
title: Role Based Permissions
description: Follow this page to learn about Role Based Permissions.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
---

# Role Based Permissions {#role-based-permissions}

[!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions. For example, a developer develops code and has the permission to push the code to the **Git Repository**. Alternatively, a business owner has different permissions allowing them to define the Key Performance Indicators (KPIs) and approve deployments.

## User Roles {#user-roles}

Role management for [!UICONTROL Cloud Manager] is done inside the [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Any user of [!UICONTROL Cloud Manager] must be a member of the customer's IMS Organization and have the Adobe Managed Services Product Context. Specific role memberships are provided by adding the user to a [!UICONTROL Cloud Manager] Product Profile in the Admin Console.

To learn more about how to setup your roles see [Setting up Users and Roles](setting-up-users-and-roles.md).

The following table list defines the possible roles you can assign in the Admin Console.

| **[!UICONTROL Cloud Manager] Role** |**Description** |
|---|---|
| Business Owner |Primary user who completes the initial [!UICONTROL Cloud Manager] setup. Responsible for defining KPIs, approving production deployments and overriding important 3-tier failures. |
| Program Manager |Uses [!UICONTROL Cloud Manager] to perform team setup, review status and view KPIs. May approve important 3-tier failures. |
| Deployment Manager |Manages the deployment operations. Uses [!UICONTROL Cloud Manager] to execute stage and production deployments. May approve important 3-tier failures. Has access to Git repository. |
| Developer |Develops and tests custom application code. Primarily uses [!UICONTROL Cloud Manager] to view status. Has commit access to Git repository. |
| Customer Success Engineer |Generally supports customer success for AMS customers. Interacts with [!UICONTROL Cloud Manager] for the purpose of executing deployments which require Customer Success Engineer (CSE) oversight. |
| Content Author |Generally does not interact with [!UICONTROL Cloud Manager]. This user may use the [!UICONTROL Cloud Manager] Program Switcher (having navigated from [!UICONTROL Experience Cloud]) to access Adobe Experience Manager (AEM). |

## User Permissions {#user-permissions}

Each of the roles have specific permissions, preconfigured tasks, or permissions, associated with each role. This table lists the functions available and the roles who can execute the function.

To learn more about how to setup your Users see [Setting up Users and Roles](setting-up-users-and-roles.md).

|Permission|Description|Business Owner|Deployment Manager|Program Manager|Developer|CSE|
|--- |--- |--- |--- |--- |--- |--- |
|Read Application|Read Program KPIs.|x|x|x|x|x|
|Write Application|Program setup or edit.|x|||||
|Read Environment|See Environment details.|x|x|x|x|x|
|Create Execution|Start Pipeline.|x|x|x|||
|Read Execution|See execution status.|x|x|x|x|x|
|Resume Execution|Can resume execution when paused.|x|x|x||x|
|Execution Approve Deploy to Production|Provide GoLive Approval.|x|x|x|||
|Execution Schedule Deploy to Production|Schedule Production Deployment.|x|x|x||x|
|Execution Deploy to Production|Deploy application to production when paused for CSE Oversight.|||||x|
|Execution Cancel|Cancel current execution.|x|x|x|||
|Execution Override Quality Gate Failures|Approve Important Quality Gate Failures.|x|x|x|||
|Pipeline Create|Setup / Edit Pipeline.||x||||
|Pipeline Read|See Pipeline details.|x|x|x|x|x|
|Pipeline Write|Setup / Edit Pipeline.||x||||
|Pipeline Modify Approval|Allows editing the Business Owner option.||x||||
|Pipeline Modify Managed Deployment|Allows editing of the CSE Oversight option.||x||||
|Step Read|See the step quality metrics results.|x|x|x|x|x|
