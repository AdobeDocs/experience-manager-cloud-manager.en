---
title: Add External Repositories in Cloud Manager
description: Learn how to add an external repository into Cloud Manager. Cloud Manager supports integration with GitHub Enterprise, GitLab, and Bitbucket repositories.
badge: label="Early Adopter" type="Positive" url="/help/release-notes/current.md#gitlab-bitbucket"
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
---
# Add external repositories in Cloud Manager {#external-repositories}

Learn how to add an external repository into Cloud Manager. Cloud Manager supports integration with GitHub Enterprise, GitLab, and Bitbucket repositories.

>[!NOTE]
>
>The features described in this article are only available through the early adoption program. For more details and to sign up as an early adopter, see [Bring Your Own Git](/help/release-notes/current.md#gitlab-bitbucket).

## Configure an external repository

Configuration of an external repository in Cloud Manager consists of three steps:

1. [Add an external repository](#add-external-repo) to a selected program.
1. Provide an access token to the external repository.
1. Validate ownership of the private GitHub repository.
1. [Configure a webhook](#configure-webhook) to an external repository.


## Add an external repository {#add-ext-repo}

>[!NOTE]
>
>External repositories cannot be linked to Configuration pipelines.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization.

1. On the **[My Programs](/help/getting-started/navigation.md#my-programs-console)** console, select the program to which you want to link an external repository.

1. In the side menu, under **Program**, click ![Folder outline icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositories**.

   ![The Repositories page](/help/managing-code/assets/repositories-tab.png)

1. Near the upper-right corner of the **Repositories** page, click **Add Repository**.

1. In the **Add Repository** dialog box, select **Private Repository** to link an external Git repository to your program.
 
   ![Add own repository](/help/managing-code/assets/repositories-private-repo-type.png)

1. In each respective field, provide the following details about your repository: 

    | Field | Description |
    | --- | --- |
    | **Repository Name** | Required. An expressive name for your new repository. | 
    | **Repository URL** | Required. The URL of the repository.<br><br>If you are using a GitHub-hosted repository, the path must end in `.git`.<br>For example, *`https://github.com/org-name/repo-name.git`* (URL path is for illustration purposes only).<br><br>If you are using an external repository, it must use the following URL path format:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> or<br>`https://self-hosted-domain/org-name/repo-name.git`<br>And match your Git vendor. |
    | **Select Repository Type** | Required. Select the repository type that you are using:<ul><li>**GitHub** (GitHub Enterprise and the self-hosted version of GitHub)</li><li>**GitLab** (both `gitlab.com` and the self-hosted version of GitLab) </li><li>**Bitbucket** (only `bitbucket.org` (cloud version) is supported. The self-hosted version of Bitbucket was deprecated starting February 15, 2024.)</li></ul>If the repository URL path above includes the Git vendor name, such as GitLab or Bitbucket, the repository type is already pre-selected for you. |
    | **Description** | Optional. A detailed description of the repository. |

1. Select **Save** to add the repository.

1. In the **Private Repository Ownership Validation** dialog box, provide an access token to validate ownership of the external repository so you can access it.

    ![Selecting an existing access token for a repository](/help/managing-code/assets/repositories-exisiting-access-token.png)
    *Selecting an existing access token for a Bitbucket repository.*

    | Token type | Description |
    | --- | --- |
    | **Use existing Access Token** | If you have already provided a repository access token for your organization and have access to multiple repositories, you can select an existing token. Use the **Token Name** drop-down list to choose the token you want to apply to the repository. Otherwise, add a new access token. |
    | **Add new Access Token** |**Repository type: GitHub Enterprise**<br><ul><li> In the **Token Name** text field, type a name for the access token you are creating.<li>Create a personal access token by following the instructions in the [GitHub documentation](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<li>Required permissions for the GitHub Enterprise Personal Access Token (PAT)<br>These permissions ensure that Cloud Manager can validate pull requests, manage commit status checks, and access necessary repo details.<br>When you generate the PAT in GitHub Enterprise, make sure it includes the following repository permissions:<ul><li>Pull request (read and write)<li>Commit statuses (read and write)<li>Repository metadata (read-only)</li></li></ul></li></ul></ul></ul><ul><li>In the **Access Token** field, paste the token you just created. |
    | | **Repository type: GitLab**<ul><li>In the **Token Name** text field, type a name for the access token you are creating.<li>Create a personal access token by following the instruction in the [GitLab documentation](https://docs.gitlab.com/user/profile/personal_access_tokens/).<li>Required permissions for the GitLab Personal Access Token (PAT)<br>These scopes allow Cloud Manager to access repository data and user information as needed for validation and webhook integration.<br>When you generate the PAT in GitLab, make sure it includes the following token scopes:<ul><li>api<li>read_user</li></li></ul></li></li></ul></ul></ul><ul><li>In the **Access Token** field, paste the token you just created. | 
    | |**Repository type: Bitbucket**<ul><li>In the **Token Name** text field, type a name for the access token you are creating.<li>Create a repository access token using the [Bitbucket documentation](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<li>Required permissions for the Bitbucket Personal Access Token (PAT)<br>These permissions allow Cloud Manager to access repository content, manage pull requests, and configure or react to webhook events.<br>When you create the app password in Bitbucket, make sure it includes the following required app password permissions:<ul><li>Repository (read-only)<li>Pull requests (read and write)<li>Webhooks (read and write)</li></li></ul></li></li></ul></ul></ul><ul><li>In the **Access Token** field, paste the token you just created. |

    >[!NOTE]
    >
    >The feature **Add new Access Token** is currently in the Early Adopters phase. Additional functionalities are being planned. As a result, the required permissions for access tokens may change. Additionally, the user interface for managing tokens may be updated, potentially including features like token expiration dates. And, automated checks to ensure that tokens linked to repositories remain valid. 

1. Click **Validate**.

After validation, the external repository is ready to use and link to a pipeline.

## Link a validated external repository to a pipeline {#validate-ext-repo}

1. Add or edit a pipeline:
    * [Add a production pipeline](/help/using/production-pipelines.md#adding-production-pipeline)
    * [Add a non-production pipelines](/help/using/non-production-pipelines.md#add-non-production-pipeline)
    * [Edit a pipeline](/help/using/managing-pipelines.md#editing-pipelines)

    ![Pipeline's source code repository and Git branch](/help/managing-code/assets/pipeline-repo-gitbranch.png)
    *Add Non-Production Pipeline dialog box with selected repository and Git branch,*  

1. When adding or editing a pipeline, to specify the **Source Code** location for your new or existing pipeline, choose the external repository you want to use from the **Repository** drop-down list. 

1. In the **Git Branch** drop-down list, select the branch as the source for the pipeline.

1. Click **Save**.


>[!TIP]
>
>For details about managing repositories in Cloud Manager, see [Cloud Manager Repositories](/help/managing-code/managing-repositories.md).

## Configure a webhook for an external repository {#configure-webhook}

Cloud Manager lets you configure webhooks for external Git repositories that you have added. See [Add an external repository](#add-ext-repo). These webhooks permit Cloud Manager to receive events that are related to different actions within your Git vendor solution.

For example, webhooks allow Cloud Manager to trigger actions based on events such as the following:

* Pull request (PR) creation – Initiates PR validation functionality.
* Push events – Starts pipelines when the "On Git Commit" trigger is turned on (enabled).
* Future comment-based actions – Allows workflows, such as direct deployment from a PR, to a Rapid Development Environment (RDE).

Webhook configuration is not required for repositories hosted on `GitHub.com` because Cloud Manager integrates directly through the GitHub app.

For all other external repositories that are onboarded with an access token, such as GitHub Enterprise, GitLab, and Bitbucket, webhook configuration is available and must be set up manually.

**To configure a webhook for an external repository:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization.

1. On the **[My Programs](/help/getting-started/navigation.md#my-programs-console)** console, select the program to which you want to configure a webhook for an external Git repository.

1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to reveal the left side menu.

1. In the left side menu, Under the **Program** heading, click ![Folder outline icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositories**.

1. On the **Repositories** page, using the **Type** column to guide you in your selection, locate the repository you want, then click ![Ellipsis - More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) next to it.

   ![Config Webhook option on drop-down menu for a selected repository](/help/managing-code/assets/repository-config-webhook.png)

1. From the drop-down menu, click **Config Webhook**.

    ![Configure Webhook dialog box](/help/managing-code/assets/config-webhook.png)

1. In the **Config Webhook** dialog box, do the following:

    1. Next to the **Webhook URL** field, click ![Copy icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
    Paste the URL in a plain text file. The copied URL is required for your Git vendor's Webhook settings.
    1. Next to the **Webhook Secret** token/key field, click **Generate**, then click ![Copy icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
    Paste the secret in a plain text file. The copied secret is required for your Git vendor's Webhook settings.
1. Click **Close**. 
1. Navigate to your Git vendor solution (GitHub Enterpriser, GitLab, or Bitbucket).

    All the details on the webhook configuration and the events that are required for each vendor are available in [Add an external repository](#add-ext-repo). Under step 8, see the table.

1. Locate the solution's **Webhook** Settings section.
1. Paste the Webhook URL that you copied earlier into the URL text field.
    1. Replace the `api_key` query parameter in the Webhook URL with your own real API key.

        To generate an API key, you must create an integration project in Adobe Developer Console. See [Creating an API Integration Project](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) for full details.
    
1. Paste the Webhook Secret that you copied earlier into the **Secret** (or **Secret key**, or **Secret token**) text field.
1. Configure the webhook to send the required events that Cloud Manager expects.

    | Repository | Required webhook events |
    | --- | --- |
    | GitHub Enterprise | These events allow Cloud Manager to respond to GitHub activity, such as pull request validation, push-based triggers for pipelines, or Edge Delivery Services code sync.<br>Make sure that the webhook is set up to trigger on the following required webhook events:<ul><li>Pull requests<li>Pushes<li>Issue comments</li></li></li></ul></ul></ul> |
    | GitLab | These webhook events allow Cloud Manager to trigger pipelines when code is pushed or a merge request is submitted. They also track comments related to pull request validation (through note events).<br>Make sure that the webhook is set up to trigger on the following required webhook events<ul><li>Push events<li>Merge request events<li>Note events</li></li></li></ul></ul></ul> | 
    | Bitbucket | These events ensure that Cloud Manager can validate pull requests, respond to code pushes, and interact with comments for pipeline coordination.<br>Make sure that the webhook is set up to trigger on the following required webhook events<ul><li>Pull request: Created<li>Pull request: Updated<li>Pull requests: Merged<li>Pull request: Comment<li>Repository: Push</li></li></li></ul></ul></ul> |

### Validation of pull requests with webhooks

After webhooks are correctly configured, Cloud Manager automatically triggers pipeline executions or PR validation checks for your repository. 

The following behaviors apply:

* **GitHub Enterprise**

    When the check is created, it appears like the following screenshot below. The key difference from `GitHub.com` is that `GitHub.com` uses a check-run, while GitHub Enterprise (using personal access tokens) generates a commit status:

    ![Commit status to indicate PR validation process on GitHub Enterprise](/help/managing-code/assets/repository-webhook-github-pr-validation.png)

* **Bitbucket**

    When code quality validation is running:

    ![Status while code quality validation is running](/help/managing-code/assets/repository-webhook-bitbucket1.png)

    Uses commit status for tracking PR validation progress. In the following case, the screenshot shows what happens when a code quality validation fails due to a customer issue. A comment is added with detailed error information, and a commit check is created, which shows the failure (visible on the right):

    ![Pull request validation status for Bitbucket](/help/managing-code/assets/repository-webhook-bitbucket2.png)

* **GitLab**

    GitLab interactions rely solely on comments. When validation begins, a comment is added. When validation is complete (whether successful or failed), the initial comment is removed and replaced with a new comment containing validation results or error details.

    When code quality validation is running:

    ![When code quality validation is running](/help/managing-code/assets/repository-webhook-gitlab1.png)

    When cold quality validation is finished:

    ![When cold quality validation is finished](/help/managing-code/assets/repository-webhook-gitlab2.png)

    When code quality validation fails with an error:

    ![When code quality validation fails with an error](/help/managing-code/assets/repository-webhook-gitlab3.png)

    When the code quality validation fails due to customer issues:

    ![When the code quality validation fails due to customer issues](/help/managing-code/assets/repository-webhook-gitlab4.png)


## Troubleshoot webhook issues

* Ensure that the Webhook URL includes a valid API key.
* Check that webhook events are correctly configured in your Git vendor settings.
* If PR validation or pipeline triggers are not working, verify that the Webhook Secret is up to date in both Cloud Manager and your Git vendor.