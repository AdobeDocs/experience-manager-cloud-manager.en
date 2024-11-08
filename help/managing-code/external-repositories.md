---
title: Add External Repositories in Cloud Manager (Early Adopter)
description: Learn how to add an external repository into Cloud Manager. Cloud Manager supports integration with GitHub, GitLab, and Bitbucket repositories.
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
---
# Add external repositories in Cloud Manager {#external-repositories}

Learn how to add an external repository into Cloud Manager. Cloud Manager supports integration with GitHub, GitLab, and Bitbucket repositories.

>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/release-notes/current.md#early-adoption).

## Configure an external repository

Configuration of an external repository in Cloud Manager consists of three steps:

1. [Add an external repository](#add-external-repo) to a selected program.
1. Provide an access token to the external repository.
1. Validate ownership of the external repository.


## Add an external repository {#add-ext-repo}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization.

1. On the **[My Programs](/help/getting-started/navigation.md#my-programs-console) console, select the program to which you want to link an external repository.


1. In the side menu, under **Services**, select ![Folder icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositories**.

   ![The Repositories page](/help/managing-code/assets/repositories-tab.png)

1. Near the upper-right corner of the **Repositories** page, click **Add Repository**.

1. In the **Add Repository** dialog box, select **Private Repository** to link an external Git repository to your program.
 
   ![Add own repository](/help/managing-code/assets/repositories-private-repo-type.png)

1. In each respective field, provide the following details about your repository:

    | Field | Description |
    | --- | --- |
    | **Repository Name** | Required. An expressive name for your new repository. | 
    | **Repository URL** | Required. The URL of the repository.<br><br> If you are using a GitHub-hosted repository, the path must end in `.git`.<br>For example, *`https://github.com/org-name/repo-name.git`* (URL path is for illustration purposes only).<br><br>If you are using an external repository, it must use the following URL path format:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> or<br>`https://self-hosted-domain/org-name/repo-name.git`<br>And match your Git vendor. |
    | **Select Repository Type** | Required. Select the repository type that you are using: **GitHub**, **GitLab**, or **BitBucket**. If the repository URL path above includes the Git vendor name, such as GitLab or Bitbucket, the repository type is already pre-selected for you. |
    | **Description** | Optional. A detailed description of the repository. |

1. Select **Save** to add the repository.

1. In the **Private Repository Ownership Validation** dialog box, provide an access token to validate ownership of the external repository so you can access it.

    ![Selecting an existing access token for a repository](/help/managing-code/assets/repositories-exisiting-access-token.png)
    *Selecting an existing access token for a BitBucket repository.*

    | Token type | Description |
    | --- | --- |
    | **Use existing Access Token** | If you have already provided a repository access token for your organization and have access to multiple repositories, you can select an existing token. Use the **Token Name** drop-down list to choose the token you want to apply to the repository. Otherwise, add a new access token. |
    | **Add new Access Token** |**Repository type: GitHub**<br>&bull; In the **Token Name** text field, type a name for the access token you are creating.<br>&bull; Create a personal access token by following the instructions in the [GitHub documentation](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<br>&bull; Permissions required:<br>&nbsp;&nbsp;&bull; `Read access to metadata`.<br>&nbsp;&nbsp;&bull; `Read and write access to code and pull requests`.<br>&bull; In the **Access Token** field, paste the token you just created. | 
    |  | **Repository type: GitLab**<br>&bull; In the **Token Name** text field, type a name for the access token you are creating.<br>&bull; Create a personal access token by following the instruction in the [GitLab documentation](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html).<br>&bull; Permissions required:<br>&nbsp;&nbsp;&bull; `api`<br>&nbsp;&nbsp;&bull; `read_api`<br>&nbsp;&nbsp;&bull; `read_repository`<br>&nbsp;&nbsp;&bull; `write_repository`<br>&bull; In the **Access Token** field, paste the token you just created. |    
    |  | **Repository type: Bitbucket**<br>&bull; In the **Token Name** text field, type a name for the access token you are creating.<br>&bull; Create a repository access token using the [Bitbucket documentation](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>&bull; Permissions required:<br>&nbsp;&nbsp;&bull; `Read and write access to code and pull requests`. |

    >[!NOTE]
    >
    >The feature **Add new Access Token** is currently in the Early Adopters phase. Additional functionalities are being planned. As a result, the required permissions for access tokens may change. Additionally, the user interface for managing tokens may be updated, potentially including features like token expiration dates. And, automated checks to ensure that tokens linked to repositories remain valid. 

1. Click **Validate**.

After validation, the external repository is ready to use and link to a pipeline.

## Link a validated external repository to a pipeline {#validate-ext-repo}

1. Add or edit a pipeline:
    * [Add a production pipeline](/help/using/production-pipelines.md)
    * [Add a non-production pipelines](/help/using/non-production-pipelines.md)
    * [Edit a pipeline](/help/using/managing-pipelines.md#editing-pipelines)

    ![Pipeline's source code repository and Git branch](/help/managing-code/assets/pipeline-repo-gitbranch.png)
    *Add Non-Production Pipeline dialog box with selected repository and Git branch,*  

1. When adding or editing a pipeline, to specify the **Source Code** location for your new or existing pipeline, choose the external repository you want to use from the **Repository** drop-down list. 

1. In the **Git Branch** drop-down list, select the branch as the source for the pipeline.

1. Click **Save**.


>[!TIP]
>
>For details about managing repositories in Cloud Manager, see [Cloud Manager Repositories](/help/managing-code/managing-repositories.md).


## Limitations

* External repositories cannot be linked to Configuration pipelines.
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started.
