---
title: Source Code Repository
description: Learn about the Git repository that is provisioned for each program you have in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
---
# Source code repository {#source-code-repository}

Learn about the Git repository that is provisioned for each program you have in Cloud Manager.

## Cloud Manager repository {#cloud-manager-repository}

Your [!UICONTROL AEM Managed Services] subscription includes a source code repository provisioned and managed by Adobe. Each program is assigned a unique Git repository, where your associated code is stored and secured. 

As a best practice, always use the Cloud Manager Git repository, which comes empty, without any branches configured or sample projects. Cloud Manager provides a private access token for its Git repository, letting you use any Git client to create branches, manage code, retrieve commit history, and more.

For more information on how to set up branches in Git, see [Configuring Release Branches](/help/getting-started/configuring-branches.md).

To learn more about how to use the Cloud Manager Git repository with the CI/CD pipeline, see [Configure Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md).

## On-premises repository {#on-premise-repository}

If you have an existing Git repository and want to continue using it, use Git's feature for multiple remote repositories. Development continues in your Git repository. When a release branch is ready for deployment to production, you can push your latest code to the Cloud Manager Git repository and trigger the Cloud Manager CI/CD pipeline.

To view common Git commands, see the [Git Reference Guide](https://education.github.com/git-cheat-sheet-education.pdf).
