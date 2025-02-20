---
title: Add a Non-Production Pipeline
description: Learn how to use Cloud Manager to create and configure non-production pipelines to deploy your code.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
---
# Add a non-production pipeline {#configuring-non-production-pipelines}

Learn how to use Cloud Manager to create and configure non-production pipelines to deploy your code. If you would first like a more conceptual overview of how pipelines work in Cloud Manager, see [CI/CD Pipelines](/help/overview/ci-cd-pipelines.md).

## Overview {#overview}

Using the **Pipelines** tile in [!UICONTROL Cloud Manager], the **Deployment Manager** can create two different types of pipelines.

* **Production Pipelines** - A production pipelines is a purpose-built pipeline made of a series of orchestrated steps to take source code all the way into production.
* **Non-Production Pipelines** - A non-production pipeline primarily serves to run code-quality scans or to deploy source code into a development environment.

This document focuses on non-production pipelines. For details on how to configure production pipelines see the document [Configuring Production Pipelines](/help/using/production-pipelines.md).

There are two types of non-production pipelines:

* **Code Quality Pipelines** - These run code quality scans on the code in a Git branch and executes the build and code quality steps.
* **Deployment Pipelines** - Along with performing the build and code quality steps like the code quality pipelines, these pipelines also deploy the code to a non-production environment.

>[!NOTE]
>
>A pipeline cannot be set up until its associated Git repository has at least one branch and [program setup](/help/getting-started/program-setup.md) is complete. See [Cloud Manager Repositories](/help/managing-code/managing-repositories.md) to learn how to add and manage repositories in Cloud Manager.

## Add a new non-production pipeline {#add-non-production-pipeline}

Once you have set up your program and have at least one environment using the Cloud Manager UI, you are ready to add a non-production pipeline by following these steps.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. Access the Pipelines card from the Cloud Manager home screen. Click **Add**, then select **Add Non-Production Pipeline**.

   ![Add non-production pipeline](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. On the **Configuration** tab of the **Add Non-Production Pipeline** dialog, select the type of pipeline you want to create, either a **Code Quality Pipeline** or a **Deployment Pipeline**.
   
   ![Choose pipeline type](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Provide a description for your pipeline in the **Non-Production Pipeline Name** field.

1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.

## The next steps {#the-next-steps}

After you configure the pipeline, you can deploy your code. See [Code Deployment](/help/using/code-deployment.md) for more details.

## Video tutorial {#video-tutorial}

This video provides an overview of the pipeline creation process, which is detailed in this document.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
