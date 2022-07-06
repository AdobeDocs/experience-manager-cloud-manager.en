---
title: Role-Based Permissions
description: Learn about Cloud Manager's pre-configured role-based permissions to manage access to your cloud resources.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
---

# Role Based Permissions {#role-based-permissions}

[!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions. For example, a developer develops code and has the permission to push the code to the git repository. A business owner has different permissions allowing them to define the key performance indicators (KPIs) and approve deployments.

## User Roles {#user-roles}

Role management for [!UICONTROL Cloud Manager] is done using the [Admin Console.](https://helpx.adobe.com/enterprise/using/admin-console.html) Any user of [!UICONTROL Cloud Manager] must be a member of the customer's IMS organization and have the Adobe Managed Services Product Context. Specific role memberships are provided by adding the user to a [!UICONTROL Cloud Manager] product profile in the Admin Console.

To learn more about how to setup your roles see the document [Setting Up Users and Roles.](setting-up-users-and-roles.md)

This table lists the roles you can assign in the Admin Console.

| [!UICONTROL Cloud Manager] Role |Description |
|---|---|
| Business Owner |This is the primary user who completes the initial [!UICONTROL Cloud Manager] setup and is responsible for defining KPIs, approving production deployments, and overriding important 3-tier failures when necessary. |
| Program Manager |This user uses [!UICONTROL Cloud Manager] to perform team setup, review status, view KPIs, and may approve important 3-tier failures when necessary. |
| Deployment Manager |This user manages the deployment operations using [!UICONTROL Cloud Manager] to execute stage and production deployments, may approve important 3-tier failures when necessary, and has access to the git repository. |
| Developer |This user develops and tests custom application code, primarily uses [!UICONTROL Cloud Manager] to view deployment status, and has commit access to the git repository. |
| Customer Success Engineer |This user generally supports customer success for AMS customers and interacts with [!UICONTROL Cloud Manager] for the purpose of executing deployments which require Customer Success Engineer (CSE) oversight. |
| Content Author |This user generally does not interact with [!UICONTROL Cloud Manager], but may use the [!UICONTROL Cloud Manager] program wwitcher (having navigated from [!UICONTROL Experience Cloud]) to access Adobe Experience Manager (AEM).|

## User Permissions {#user-permissions}

Each of the roles have specific associated preconfigured permissions. This table lists the permissions available and the roles who can execute them.


|Permission|Description|Business Owner|Deployment Manager|Program Manager|Developer|CSE|
|--- |--- |--- |--- |--- |--- |--- |
|Read Application|Read program KPIs|x|x|x|x|x|
|Write Application|Program setup or edit|x|||||
|Add Program|Add new program|x|||||
|Read Environment|See environment details|x|x|x|x|x|
|Create Execution|Start pipeline|x|x|x|||
|Read Execution|See execution status|x|x|x|x|x|
|Resume Execution|Can resume execution when paused|x|x|x||x|
|Execution Approve Deploy to Production|Provide go-live approval|x|x|x|||
|Execution Schedule Deploy to Production|Schedule production deployment|x|x|x||x|
|Execution Deploy to Production|Deploy application to production when paused for CSE oversight|||||x|
|Execution Cancel|Cancel current execution|||x|||
|Execution Override Quality Gate Failures|Approve important quality gate failures|x|x|x|||
|Pipeline Create|Set up / edit pipeline||x||||
|Pipeline Read|See pipeline details|x|x|x|x|x|
|Pipeline Write|Set up / edit pipeline.||x||||
|Pipeline Modify Approval|Allows editing the Business Owner option||x||||
|Pipeline Modify Managed Deployment|Allows editing of the CSE oversight option||x||||
|Pipeline Delete|Allows pipeline deletion||x||||
|Step Read|See the step quality metrics results|x|x|x|x|x|
|Generate Personal Access Token|Access git||x||x||

To learn more about how to setup your users see the document [Setting Up Users and Roles.](setting-up-users-and-roles.md)
