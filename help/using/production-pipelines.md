---
title: Configure Production Pipelines
description: Learn how to use Cloud Manager to create and configure production pipelines to deploy your code.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
---

# Configure production pipelines {#configuring-production-pipelines}

Learn how to use Cloud Manager to create and configure production pipelines to deploy your code. If you would first like a more conceptual overview of how pipelines work in Cloud Manager, see [CI/CD Pipelines](/help/overview/ci-cd-pipelines.md).

## Overview {#overview}

Using the **Pipeline Settings** tile in [!UICONTROL Cloud Manager] you can create two different types of pipelines.

* **Production Pipelines** - A production pipelines is a purpose-built pipeline made of a series of orchestrated steps to take source code from your Git repository all the way into production.
* **Non-Production Pipelines** - A non-production pipeline primarily serves to run code-quality scans or to deploy source code into a development environment.

This document focuses on production pipelines. For details on how to configure non-production pipelines see the document [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md).

The **Deployment Manager** role is responsible for setting up the pipeline. Pipeline configuration consists of:

1. Defining the trigger that starts the pipeline.
1. Defining the parameters controlling the production deployment.
1. Configuring the performance test parameters.

>[!NOTE]
>
>A pipeline cannot be set up until its associated Git repository has at least one branch and [program setup](/help/getting-started/program-setup.md) is complete.

## Add a new production pipeline {#adding-production-pipeline}

After you have used the [!UICONTROL Cloud Manager] UI to set up your program and have at least one environment, you are ready to add a production pipeline.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page.

1. Click **+Add**, then select **Add Production Pipeline**.

   ![Add a production pipeline](/help/assets/configure-pipelines/add-prod1.png)

1. The **Add Production Pipeline** dialog box opens to the **Configuration** tab where a number of options for your pipeline must be defined. These options are grouped into collapsible sections and are described in the following steps.

   1. Provide a descriptive name for your pipeline in the **Pipeline Name** field.

   1. Under the **Source Code** section, you define where the pipeline retrieves the code it processes.

      * **Repository** - Defines which Git repo the pipeline should retrieve the code.

      >[!TIP]
      >
      >See the document [Program Setup](/help/getting-started/program-setup.md) to learn how to add and manage repositories in Cloud Manager.

      * **Git Branch** - Defines from which branch in the selected pipeline should retrieve the code.
      * **Code Location** - Defines the path in the branch of the selected repo from which the pipeline should retrieve the code.

      ![Define repos for the pipeline](/help/assets/configure-pipelines/add-prod2.png)

   1. Under the **Environments** section, you define what triggers a deployment and how it should be rolled out per environment.

      1. In the **STAGE** section, you can define how the pipeline rolls out to your staging environment.

         * **Deployment Trigger** - You have the following options to define the deployment triggers to start the pipeline.

           * **Manual** - Start the pipeline manually using the Cloud Manager UI.
           * **On Git Changes** - Start the CI/CD pipeline whenever commits are added to the configured Git branch. With this option, you can still start the pipeline manually as required.

         * **Important Metric Failures Behavior** - During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates. The available options are:

           * **Ask every time** - The default setting and requires manual intervention on any important failure.
           * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is emulating a user manually rejecting each failure.
           * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is emulating a user manually approving each failure.

         ![Deployment trigger](/help/assets/configure-pipelines/add-prod3.png)

         * **Deployment Options** - You can accelerate certain deployment tasks.

           * **Approve after Stage Deployment** - This approval occurs after deployment to the staging environment before any testing is done. Otherwise, approval occurs before the production deployment, which is done after all testing is complete.

           * **Skip Load Balancer changes** - Load balancer changes are not made.

         ![Staging deployment options](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure, do the following:
        
           1. Under **PATH** provide a content path.
           1. Under **TYPE**, select the action to be taken on that path.
           
               * **Flush** - Perform a cache deletion.
               * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
             
           1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

         ![Dispatcher configuration](/help/assets/configure-pipelines/dispatcher-stage.png)

           >[!TIP]
           >
           >In general, the use of the invalidate action is preferable, but there may be cases where flushing is required, especially when using AEM HTML Client Libraries.

      1. In the **PRODUCTION** section, you can define how the pipeline rolls out to your production environment.

         * **Deployment Options** - You can define the parameters controlling the production deployment.

           * **Use Go Live Approval** - A user with the **Business Owner**, **Project Manager**, or **Deployment Manager** role by way of the [!UICONTROL Cloud Manager] UI must manually approve a deployment.
           * **Scheduled** - Halts the pipeline before production deployment to allow it to be scheduled. If this option is selected, the pipeline halts after deployment to the staging environment and prompt the user for the action to take.
             * **`Now`** - Deploys to production immediately, effectively completing the pipeline.
             * **Date** - Lets the user schedule a time when the deployment should be completed.
             * **Stop Execution** - Aborts deployment to production.

           >[!TIP]
           >
           >See [Code Deployment](/help/using/code-deployment.md) to learn how to set the deployment schedule or execute the pipeline immediately.

           * **Use CSE Oversight** - If this option is select, a CSE (Customer Success Engineer) is engaged to start the actual deployment. When creating or editing a pipeline when this option is enabled, the **Deployment Manager** role has the following options.

             * **Any CSE** - Allows any available CSE to start the deployment.
             * **My CSE** - Allows only the specific CSE assigned to the customer to start the deployment. This option also applies for the designated backup of the CSE if the assigned CSE is unavailable.

           ![Production deployment options](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher Configuration** - Define the Dispatcher configuration for your production environment. The options are the same as the options for the staging environment.
   
1. Click **Continue** to advance to the **Stage Testing** tab where you can configure AEM Sites and AEM Assets Performance Testing, depending on which products you have licensed.

   >[!TIP]
   >
   >See [Code Quality Testing](/help/using/code-quality-testing.md#performance-testing) for more details on the options available on the **Stage Testing** tab.
   
   1. In the **Sites Content Delivery/Distributed Load Weight** section, you configure site Performance Testing based on the weighting of page requests among three page sets. You can enable or disable the page sets as needed.

      * **Popular Live Pages**
      * **Other Live Pages**
      * **New Pages**

      ![Sites load weight](/help/assets/configure-pipelines/add-prod5.png)

   1. Under the **Assets Performance Testing Distribution** section, you define the test distribution of images and PDFs and define your own test assets.

      * **Images** - Adjust the slider to adjust the test split between images and PDFs.
      * **PDFs** - Adjust the slider to adjust the test split between images and PDFs.

      * Define your own custom assets by uploading them.

        1. **FORMAT** - Choose whether your custom asset is a PDF of an image.
        1. **FILENAME** - Use the file browser button to select an image from your local machine.
        1. **Add Test File** - Click to upload your selected asset.

      ![Assets testing distribution](/help/assets/configure-pipelines/add-prod6.png)

1. Click **Save** to complete adding your production pipeline.

## The next steps {#the-next-steps}

After you have configured the pipeline, you deploy your code. See [Code Deployment](/help/using/code-deployment.md) for more details.

## Video tutorial {#video-tutorial-one}

This video provides an overview of the pipeline creation process, which is detailed in this document.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
