---
title: Repository Access Information
description: Learn how to access and manage your Adobe-managed git repositories using the self-service git account management from Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
---
# Repository Access Information {#accessing-repos}

Learn how to access and manage your Adobe-managed git repositories using the self-service git account management from Cloud Manager.

## Accessing Repository Info from the Overview Page {#overview-page}

Cloud Manager makes it easy to retrieve your repository access information for Adobe-managed repositories by using the **Access Repo Info** button available prominently on the pipeline card.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to **Pipelines** card from your **Program Overview** page.

   ![Access Repo Info button on Environments card](assets/pipelines-card.png)

1. Click the **Access Repo Info** button to open the **Repository Info** dialog and view:

   * The git username.
   * The git password.
   * The URL to the Cloud Manager git repository.
   * Prebuilt git commands to quickly add a remote to your git repo and push code.

   ![Repository Info window](assets/access-repo-info.png)

1. To access the password, a new password must be generated. To do so, click the **Generate password** button.

1. Confirm password generation in the **Are you sure...** dialog box by clicking **Generate password**.

   ![Confirm password generation](assets/confirm-password-generation.png)

1. The password is generated and is visible for copying in the **Password** field.

   * Generating a password will invalidate the previous password.
   * Cloud Manager will not save the password. It is your responsibility to save this password securely.
   * Because Cloud Manager does not save the password, if you loose the password, you must regenerate a new one.

   ![Example of a generated password](assets/generated-password.png)

Using these credentials, you can clone a local copy of the repository, make changes in that local repository, and when ready commit any code changes back to the remote code repository in Cloud Manager.

>[!NOTE]
>
>* The **Access Repo Info** option is visible to users with **Developer** or **Deployment Manager** roles.
>* The **Access Repo Info** button only displays the repository access information for Adobe-managed repositories. Access information about [private repositories](private-repositories.md) is not available in Cloud Manager.

## Accessing Repository Information from the Repositories Window {#repositories-window}

An **Access Repo Info** button is also available in the toolbar of the [**Repositories** window](managing-repositories.md) it displays the same information about accessing Adobe-managed repositories.

## Revoking an Access Password {#revoke-password}

You can revoke an access password at any time. To do so, [create a support ticket for this request](https://experienceleague.adobe.com/?support-solution=Experience+Manager&support-tab=home#support).

The ticket will be treated with high priority and should be revoked within one day.
