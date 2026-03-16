---
title: Source Code Repository
description: Learn about the Git repository that is provisioned for each program you have in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
---

# Source code repository {#source-code-repository}

Learn about the Git repository that is provisioned for each program you have in Cloud Manager.

## Cloud Manager repository {#cloud-manager-repository}

Your [!UICONTROL AEM Managed Services] subscription includes a source code repository provisioned and managed by Adobe. Each program is assigned a single and unique Git repository, where your associated code is stored and secured. 

As a best practice, you should always use the Cloud Manager's Git repository, which comes empty without any branches configured or sample projects. Cloud Manager provides a private access token for its Git repository, letting you use any Git client to create branches, manage code, retrieve commit history, and more.

For more information on how to set up branches in Git, see [Configuring Release Branches](/help/getting-started/configuring-branches.md).

For more information on how to use the Cloud Manager's Git repository with the CI/CD pipeline, See [Configure Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md) to learn more.

## On-premise repository {#on-premise-repository}

You may have an existing Git repository and want to keep using it, in which case you can use Git's feature for multiple remote repositories. Day-to-day development would continue to happen in your Git repository. When a release branch is ready for deployment to production, you can push your latest code to the Cloud Manager's Git repository and trigger the Cloud Manager CI/CD pipeline.

To view common Git commands, see the [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf).
