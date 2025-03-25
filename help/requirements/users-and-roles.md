---
title: Add Users and Roles
description: Learn how to use the Admin Console to add users and roles, and create profiles.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
---

# Add users and roles {#add-users-and-roles}

Many features in [!UICONTROL Cloud Manager] require specific permissions to use. For example, only certain users are allowed to set the key performance indicators (KPIs) for a program. These permissions are logically grouped into roles.

[!UICONTROL Cloud Manager] currently defines four roles for users, which govern the availability of specific features:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

>[!NOTE]
>
>To use [!UICONTROL Cloud Manager], you must have an Adobe ID and the Adobe Managed Services Product Context.

## Role definitions {#role-definitions}

The following table summarizes the roles in Cloud Manager.

|[!UICONTROL Cloud Manager] role | Description |
| --- | --- |
| Business Owner | Responsible for defining KPIs, approving production deployments, and overriding important 3-tier failures when necessary. |
| Program Manager | They use [!UICONTROL Cloud Manager] to perform team setup, review status, view KPIs, and can approve important 3-tier failures when necessary. |
| Deployment Manager | Manages deployment operations and uses [!UICONTROL Cloud Manager] to execute staging and production deployments, edit CI/CD pipelines, and approve critical 3-tier failures when necessary. They also have access to the Git repository. |
| Developer | Develops and tests custom application code and primarily uses [!UICONTROL Cloud Manager] to view deployment status and can access the Git repository for code commits. |
| Customer Success Engineer | The CSE generally supports customer success for AMS customers. They interact with [!UICONTROL Cloud Manager] for the purpose of executing deployments that require CSE oversight. |
| Content Author | They generally do not interact with [!UICONTROL Cloud Manager] but may use the [!UICONTROL Cloud Manager] program switcher to access AEM. |

>[!NOTE]
>
>The Developer persona in the Admin Console is unrelated to the Developer role in [!UICONTROL Cloud Manager].

## Create a profile using the Admin Console {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] roles are managed from the Admin Console. Specific role memberships are provided by adding the user to a [!UICONTROL Cloud Manager] product profile.

The Admin Console is a central location for managing your Adobe entitlements across your entire organization. To learn more about the Adobe Admin Console, see [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

An administrator must create new product profiles under the [!UICONTROL AEM Managed Services] Product Context to assign role-based permissions for [!UICONTROL Cloud Manager] users, corresponding to each of the four [!UICONTROL Cloud Manager] roles.

* Business Owner
* Deployment Manager
* Developer
* Program Manager

You can create or add users or groups to these product profiles with the Admin Console.

1. Log in to the Admin Console at [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Click the **Overview** tab, then click the product you want to edit on the **Products and Services** card. If it is not listed there, use the **Products** tab to locate the product and click it.

   ![Admin console overview tab](/help/assets/admin-console-overview.png)

1. On the **Products** tab, click the environment for which you want to add users/groups to product profiles.

   ![Admin console products tab](/help/assets/admin-console-product.png)

1. On the **Product Profile** tab of the product, click **New Profile** to add a new profile.

   ![New profile](/help/assets/admin-console-product-profiles.png)

1. Provide the information to set up a new role for [!UICONTROL Cloud Manager].

   * **Profile Name** - The **Profile Name** can be anything, although to avoid confusion it is recommended to use the values in the **Recommended Profile Name** column.
   * **Display Name** -  The **Display Name** must be the technical value defined by [!UICONTROL Cloud Manager] (see the following table).
   * **Permission Group** - You may choose a permission group for the profile (not always available).

   ![Creating a new profile](/help/assets/screen_shot_2018-05-04at171819.png)

   |Role|Display Name (Required)|Recommended Profile Name|
   |---|---|---|
   | Business Owner |`CM_BUSINESS_OWNER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Business Owner Role |
   | Deployment Manager |`CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Deployment Manager Role |
   | Developer |`CM_DEVELOPER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Developer Role |
   | Program Manager |`CM_PROGRAM_MANAGER_ROLE_PROFILE` |[!UICONTROL Cloud Manager] - Program Manager Role |


1. Click **Done** to save the new profile.

## Assign profiles to users or user groups {#assign-profiles}

Once you have created product profiles, you can assign users or user groups to them.

1. Log in to the Admin Console at [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. In the Admin Console, choose the **Users** tab.

   ![Users tab](/help/assets/admin-console-users.png)

1. Click **Users** in the left navigation panel and then click a user to modify it.

1. Click ![More icon, ellipsis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) in the **Products** section and click **Edit**.

   ![Edit user](/help/assets/admin-console-edit-user.png)

1. In the **Edit products and user groups** dialog box, click ![Add icon, plus sign](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) and select the profiles to assign to the user.

   * If the user already is assigned to the roles, the ![Add icon, plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) button is an edit button (a pencil), but works the same way.

   ![Edit products and user groups](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Click **Save** to save the profiles to the user.

Repeat the same steps to assign profiles to user groups, but select **User Groups** from the left navigation panel on the **Users** tab. Click a user group and select the **Assigned Product Profiles** click **Assign Product Profile** to assign profiles.

![Assign profiles to group](/help/assets/admin-console-edit-user-groups.png)
