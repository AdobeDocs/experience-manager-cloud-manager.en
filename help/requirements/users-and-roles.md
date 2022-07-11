---
title: Add Users and Roles
description: Learn how to use the Admin Console to add users and roles and create profiles.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
---

# Add Users and Roles {#add-users-and-roles}

Many features in [!UICONTROL Cloud Manager] require specific permissions to use. For example, only certain users are allowed to set the key performance indicators (KPIs) for a program. These permissions are logically grouped into roles.

[!UICONTROL Cloud Manager] currently defines four roles for users which govern the availability of specific features:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

>[!NOTE]
>
>To use [!UICONTROL Cloud Manager], you must have an Adobe ID and the Adobe Managed Services Product Context.

## Role Definitions {#role-definitions}

This table summarizes the roles.

|[!UICONTROL Cloud Manager] Role|Description|
|--- |--- |
|Business Owner|This user is responsible for defining KPIs, approving production deployments, and overriding important 3-tier failures when necessary.|
|Program Manager|This user uses [!UICONTROL Cloud Manager] to perform team setup, review status, view KPIs, and can approve important 3-tier failures when necessary.|
|Deployment Manager|This user manages deployment operations and uses [!UICONTROL Cloud Manager] to execute staging/production deployments, edit CI/CD pipelines, approve important 3-tier failures when necessary, and can access the git repository.|
|Developer|This user develops and tests custom application code and primarily uses [!UICONTROL Cloud Manager] to view deployment status and can access the git repository for code commits.|
|Customer Success Engineer|This user generally supports customer success for AMS customers and interacts with [!UICONTROL Cloud Manager] for the purpose of executing deployments which require CSE oversight.|
|Content Author|This user generally does not interact with [!UICONTROL Cloud Manager] but may use the [!UICONTROL Cloud Manager] program switcher to access AEM.|

>[!NOTE]
>
>The Developer persona in the Admin Console is unrelated to the Developer role in [!UICONTROL Cloud Manager].

## Using Admin Console to Create a Profile {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] roles are managed from the Admin Console. Specific role memberships are provided by adding the user to a [!UICONTROL Cloud Manager] product profile.

The Admin Console is a central location for managing your Adobe entitlements across your entire organization. To learn more about the Adobe Admin Console, see the documentation for [Admin Console.](https://helpx.adobe.com/enterprise/using/admin-console.html)

>[!NOTE]
>
>To access the admin console and set up your team (users and roles), visit [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

In order to provide the appropriate role-based permissions to [!UICONTROL Cloud Manager] users, an administrator in the customer's organization must create new product profiles under the [!UICONTROL AEM Managed Services] product context corresponding to each of the four [!UICONTROL Cloud Manager] roles:

* Business Owner
* Deployment Manager
* Developer
* Program Manager

You can create or add users/groups to these product profiles with the Admin Console.

1. Log in to the Admin Console and click **New Profile** to add a new profile.

   ![New profile](/help/assets/admin_console_roles-1.png)

1. Provide the information to set up a new role for [!UICONTROL Cloud Manager].

   * **Profile Name**
   * **Display Name**
   * **Permission Group**

1. Click **Done** to complete the profile creation step.

When creating product profiles, the **Display Name** must be the technical value defined by [!UICONTROL Cloud Manager] (see the following table). The **Profile Name** can be anything, although to avoid confusion it is recommended to use the values in the **Recommended Profile Name** column. To do this, when creating the Product Profile, uncheck the **Same as Profile Name** and specify the corresponding value as the **Display Name**.

| **Role** |**Display Name (Required)** |**Recommended Profile Name** |
|---|---|---|
| Business Owner |`CM_BUSINESS_OWNER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Business Owner Role |
| Deployment Manager |`CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Deployment Manager Role |
| Developer |`CM_DEVELOPER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Developer Role |
| Program Manager |`CM_PROGRAM_MANAGER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Program Manager Role |

![Creating a new profile](/help/assets/screen_shot_2018-05-04at171819.png)

Once you create product profile, you can add users (or groups) to these product profiles.

![Editing user](/help/assets/image2018-4-9_15-19-26.png)
   
![User groups](/help/assets/image2018-4-9_15-16-47.png)
