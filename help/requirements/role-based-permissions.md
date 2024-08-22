---
title: Role-Based Permissions
description: Learn about Cloud Manager's pre-configured role-based permissions to manage access to your cloud resources.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
---

# Role-based permissions {#role-based-permissions}

[!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions. For example, a developer develops code and has the permission to push the code to the Git repository. A business owner has different permissions allowing them to define the key performance indicators (KPIs) and approve deployments.

>[!NOTE]
>
>This documentation describes role-based permissions for Cloud Manager for Adobe Managed Services (AMS).
>
>The equivalent documentation for AEM as a Cloud Service can be found in the document [Introduction to Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) in the AEM as a Cloud Service documentation.

## User roles {#user-roles}

Role management for [!UICONTROL Cloud Manager] is done using the [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Any user of [!UICONTROL Cloud Manager] must be a member of the customer's IMS organization and have the Adobe Managed Services Product Context. Specific role memberships are provided by adding the user to a [!UICONTROL Cloud Manager] product profile in the Admin Console.

To learn more about how to set up your roles, see [Setting Up Users and Roles](/help/requirements/users-and-roles.md).

The following table lists the roles that you can assign in the Admin Console.

| [!UICONTROL Cloud Manager] role | Description |
|---|---|
| Business Owner | The primary user who completes the initial [!UICONTROL Cloud Manager] setup and is responsible for defining KPIs, approving production deployments, and overriding important 3-tier failures when necessary. |
| Content Author | The user generally does not interact with Cloud Manager, but may use the Cloud Manager program switcher (having navigated from Experience Cloud) to access Adobe Experience Manager (AEM). |
| Customer Success Engineer | The user primarily supports AMS customer success and engages with [!UICONTROL Cloud Manager] to execute deployments. These deployments require oversight from an Adobe Customer Success Engineer (CSE). |
| Deployment Manager | The user manages the deployment operations using [!UICONTROL Cloud Manager] to execute stage and production deployments, may approve important 3-tier failures when necessary, and has access to the Git repository. |
| Developer | The user develops and tests custom application code, primarily uses [!UICONTROL Cloud Manager] to view deployment status, and has commit-access to the Git repository. |
| Program Manager | The user uses [!UICONTROL Cloud Manager] to perform team setup, review status, view KPIs, and may approve important 3-tier failures when necessary. |

## User permissions {#user-permissions}

Each of the roles has specific, associated preconfigured permissions. The following table lists the permissions available and the roles who can execute them.

|Permission|Description|Business Owner|Deployment Manager|Program Manager|Developer|CSE|
| --- | --- | --- | --- | --- | --- | --- |
|Read the Application | Read program KPIs | x | x | x | x | x |
| Write Application | Program set up or edit | x | | | | |
| Add Program | Add new program | x | | | | |
| Read Environment | See environment details | x | x | x | x | x |
| Create Execution | Start pipeline | x | x | x | | |
| Read Execution | See execution status | x | x | x | x | x |
| Resume Execution | Ability to resume execution when paused | x | x | x | | x |
| Execution Approve Deploy to Production | Provide go-live approval | x | x | x | | |
| Execution Schedule Deploy to Production | Schedule production deployment | x | x | x | | x |
| Execution Deploy to Production | Deploy application to production when paused for CSE oversight | | | | | x |
| Execution Cancel | Cancel current execution | | | x | | |
| Execution Override Quality Gate Failures | Approve important quality gate failures | x | x | x | | |
| Pipeline Create | Set up / edit pipeline | | x | | | |
| Pipeline Read | See pipeline details | x | x | x | x | x |
| Pipeline Write | Set up / edit pipeline | | x | | | |
| Pipeline Modify Approval | Allows editing the Business Owner option | | x | | | |
| Pipeline Modify Managed Deployment | Allows editing of the CSE oversight option | | x | | | |
| Pipeline Delete | Allows pipeline deletion | | x | | | |
| Step Read | See the step quality metrics results | x | x | x | x | x |
| Generate Personal Access Token | Access Git | | x | | x | |

To learn more about how to set up your users, see [Setting Up Users and Roles](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Custom permission profiles with configurable permissions are also available. See [Custom Permissions](/help/using/custom-permissions.md) for more details.
