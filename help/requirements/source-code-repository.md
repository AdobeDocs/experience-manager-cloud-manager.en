---
title: Source Code Repository
description: Learn about the git repository that is provisioned for each program you have in Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
---

# Source Code Repository {#source-code-repository}

Learn about the git repository that is provisioned for each program you have in Cloud Manager.

## Cloud Manager Repository {#cloud-manager-repository}

Your [!UICONTROL AEM Managed Services] subscription includes a source code repository provisioned and managed by Adobe. Each program is assigned a single and unique git repository, where your associated code will be stored and secured. 

As a best practice, you should always use the Cloud Manager's git repository, which comes empty without any branches configured or sample projects. To use the Cloud Manager's git repository, you will be provided with a private access token that will enable you to use any git client to create branches, store and retrieve your code, list the commit history, etc.

For more information on how to setup branches in git, see [Configuring Release Branches.](/help/getting-started/configuring-release-branches.md)

For more information on how to use the Cloud Manager's git repository with the CI/CD pipeline, please refer to the documents [Configure Production Pipelines](/help/using/configuring-production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/configuring-non-production-pipelines.md) to learn more.

## On-Premise Repository {#on-premise-repository}

You may have an existing git repository and want to keep using it in which case you can use git's feature for multiple remote repositories. Day-to-day development would continue to happen in your git repository. When a release branch is ready for a deployment to production, you can push your latest code to the Cloud Manager's git repository and trigger the Cloud Manager CI/CD pipeline.

To view common git commands, see the [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) on the GitHub website.
