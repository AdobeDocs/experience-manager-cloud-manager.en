---
title: Manage Access Tokens in Cloud Manager
description: Learn how to view, edit, and delete access tokens used for Bring Your Own Git in Cloud Manager on Adobe Managed Services.
badge: label="Early Adopter" type="Positive" url="/help/release-notes/current.md#access-tokens"
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
---
# Manage access tokens for external repositories {#manage-access-tokens}

Cloud Manager uses access tokens to manage repositories hosted on external Git platforms. Previously, if a token expired, the associated repository had to be re-onboarded to remain operational.

Now, the **Manage Access Tokens** feature lets you manage tokens more efficiently. You can view, rename, or remove tokens connected to supported external Git providers, including GitHub Enterprise, GitLab, Bitbucket, and Azure DevOps.

See also [Add External Repositories in Cloud Manager](/help/managing-code/external-repositories.md).

>[!NOTE]
>
>The features described in this article are only available through the early adoption program. For more details and to sign up as an early adopter, see [Manage Access Tokens](/help/release-notes/current.md#access-tokens).

## View access tokens {#view-access-tokens}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization.
1. On the **[My Programs](/help/getting-started/navigation.md#my-programs-console)** console, select the program whose Bring Your Own Git access token you want to manage.
1. In the side menu, under **Program**, click ![Folder outline icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositories**.
1. Near the upper-right corner of the page, click **Manage Access Tokens**.

   The **Manage Access Tokens** button is only visible if your program is using the Bring Your Own Git feature.

    ![Manage Access Tokens dialog box listing one token that is active and one token that is inactive](/help/managing-code/assets/access-tokens-manage.png)

1. In the **Manage Access Tokens** dialog box:
   * All access tokens are listed.
   * You can **edit** any token.
   * You can **delete** only those tokens that are *not currently in use*. If a token is in use, the ![Delete outline icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) button is disabled.

## Edit an access token {#edit-access-tokens}

1. In the **Manage Access Tokens** dialog box, to the right of a token name, click ![Edit icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. In the **Edit Access Token** dialog box, in the **Token Name** text field, update the token name.

    The Access Token secret itself cannot be modified.

    ![Edit Access Token dialog box](/help/managing-code/assets/access-tokens-edit.png)

1. If the token is in use, a notification warns you that all associated repositories are automatically revalidated.

1. Click **Update** to save the changes.

## Delete an access token {#delete-access-token}

1. In the **Manage Access Tokens** dialog box, to the right of a token name, click ![Delete icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)
 
    The icon is disabled (![Delete outline icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) for tokens that are currently in use.

1. In the **Delete Access Token** dialog box, click **Delete** to remove the token permanently.
