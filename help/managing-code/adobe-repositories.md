---
title: Add an Adobe Repository in Cloud Manager
description: Learn how to add Adobe-managed repositories in Cloud Manager.
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
TQID: https://experienceleague.adobe.com/LBI6V07enOlxe8yh-XwlkL-mdMWR0MJyKi1gUQtjtK4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
---
# Add an Adobe repository in Cloud Manager {#adobe-repositories}

Learn how to add an Adobe-managed repository in Cloud Manager.

The **Repositories** page lets you add additional Adobe-managed repositories to a selected program.

**To add an Adobe repository in Cloud Manager:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and the program to which you want to add an Adobe-managed repository.

1. From the **Program Overview** page, in the side menu, click the ![Folder icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositories** tab.

1. On the **Repositories** page, near the upper-right, click **Add Repository**.

   ![Add repository button](/help/managing-code/assets/repositories-tab.png)
  
1. In the **Add Repository** dialog box, make sure that **Adobe Repository** is selected as the repository type.

1. In the respective text fields, enter the following:

   * **Repository name** - A descriptive name for your new repository.
   * **Repository URL preview** - You do not need to enter a URL path or edit the existing path because the repository infrastructure is already configured, integrated, and managed by Adobe.
   * **Description (optional)** - A detailed description of the repository.

   ![Add Repository dialog box](/help/managing-code/assets/repository-add-adobe.png)

1. Click **Save**.
   Your new repository is displayed in the table on the **Repositories** page. 

You can now associate a [CI/CD pipeline](/help/overview/ci-cd-pipelines.md) with it or manage it within the [**Repositories** page](/help/managing-code/managing-repositories.md).

>[!TIP]
>
>You can also add GitHub repositories that you manage yourself as [private repositories](/help/managing-code/private-repositories.md).
