---
title: Configuring Production Pipelines
description: Learn how to use Cloud Manager to create and configure production pipelines in order to deploy your code.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
---
# Configuring Production Pipelines {#configuring-production-pipelines}

Learn how to use Cloud Manager to create and configure production pipelines in order to deploy your code. if you would first like a more conceptual overview of how pipelines work in Cloud Manager, please see the [CI/CD pipeline overview documentation.](ci-cd-pipeline.md)

>[!NOTE]
>
>To learn how to configure CI/CD pipelines for Cloud Manager in AEM as a Cloud Service, see [the AEMaaCS documentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Overview {#understanding-the-flow}

You configure pipelines using the **Pipeline Settings** tile in the [!UICONTROL Cloud Manager] UI.

You can create two different types of pipelines.

* **Production Pipelines** - A production pipelines is a purpose-built pipeline made of a series of orchestrated steps to take source code all the way into production.
* **Non-Production Pipelines** - A non-production pipeline primarily serves to run code-quality scans or to deploy source code into a development environment.

This document focuses on production pipelines. For details on how to configure non-production pipelines see the document [Configuring Non-Production Pipelines.](configuring-non-production-pipelines.md)

The **Deployment Manager** role is responsible for setting up the pipeline. Pipeline configuration consists of:

1. Defining the trigger that will start the pipeline.
1. Defining the parameters controlling the production deployment.
1. Configuring the performance test parameters.

>[!NOTE]
>
>A pipeline can not be setup until its associated git repository has at least one branch and [program setup](setting-up-program.md) is complete.

>[!NOTE]
>
>You can change the pipeline settings after initial set up.

## Video Tutorial {#video-tutorial-one}

Watch this video for an overview of the pipeline creation process.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Adding a New Production Pipeline {#adding-production-pipeline}

Once you have used the [!UICONTROL Cloud Manager] UI to set up your program and have at least one environment, you are ready to add a production pipeline.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click on **+Add** and select **Add Production Pipeline**.

   ![Add a production pipeline](/help/using/assets/configure-pipelines/add-prod1.png)

1. The **Add Production Pipeline** dialog box opens to the **Configuration** tab where a number of options for your pipeline must be defined. These options are grouped into collapsible sections and are described in the following steps.

   1. Provide a descriptive name for your pipeline in the **Pipeline Name** field.

   1. Under the **Source Code** section, you define where the pipeline retrieves the code it will process.

      * **Repository** - This option defines from which git repo the pipeline should retrieve the code.

      >[!TIP]
      >
      >See the document [Set Up Your Program](setting-up-program.md) to learn how to add and manage repositories in Cloud Manager.

      * **Git Branch** - This option defines from which branch in the selected the pipeline should retrieve the code.
      * **Code Location** - This option defines the path in the branch of the selected repo from which the pipeline should retrieve the code.

      ![Define repos for the pipeline](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Under the **Environments** section, you define what triggers a deployment and how it should be rolled out per environment.

      1. In the **STAGE** section, you can define how the pipeline rolls out to your staging environment.

         * **Deployment Trigger** - You have the following options to define the deployment triggers to start the pipeline.

           * **Manual** - Use this option to manually start the pipeline using the Cloud Manager UI.
           * **On Git Changes** - This options starts the CI/CD pipeline whenever commits are added to the configured git branch. With this option, you can still start the pipeline manually as required.

         * **Important Metric Failures Behavior** - During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates. The available options are:

           * **Ask every time** - This is the default setting and requires manual intervention on any important failure.
           * **Fail Immediately** - If selected, the pipeline will be cancelled whenever an important failure occurs. This is essentially emulating a user manually rejecting each failure.
           * **Continue Immediately** - If selected, the pipeline will proceed automatically whenever an important failure occurs. This is essentially emulating a user manually approving each failure.

         ![Deployment trigger](/help/using/assets/configure-pipelines/add-prod3.png)

         * **Deployment Options** - You can accelerate certain deployment tasks.

           * **Approve after Stage Deployment** - This approval occurs after deployment to the staging environment before any testing is done. Otherwise approval occurs before the production deployment, which is done after all testing is complete.

           * **Skip Load Balancer changes** - Load balancer changes are not made.

         ![Staging deployment options](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths which will either be invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions will be performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:
        
           1.  Under **PATH** provide a content path.
           1.  Under **TYPE**, select the action to be taken on that path.
           
             * **Flush** - Performs a cache deletion.
             * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
             
           1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

         ![Dispatcher configuration](/help/using/assets/configure-pipelines/dispatcher-stage.png)

           >[!TIP]
           >
           >In general, the use of the invalidate action is preferable, but there may be cases where flushing is required, especially when using AEM HTML Client Libraries.

      1. In the **PRODUCTION** section, you can define how the pipeline rolls out to your production environment.

         * **Deployment Options** - You can define the parameters controlling the production deployment.

           * **Use Go Live Approval** - A deployment must be manually approved by a user with the **Business Owner**, **Project Manager**, or **Deployment Manager** role via the [!UICONTROL Cloud Manager] UI.
           * **Scheduled** - This option halts the pipeline before production deployment to allow it to be scheduled. If this option is selected, the pipeline will halt after deployment to the staging environment and prompt the user for the action to take.
             * **Now** - This option deploys to production immediately, effectively completing the pipeline.
             * **Date** - This option allows the user to schedule a time when the deployment should be completed.
             * **Stop Execution** - This option aborts deployment to production.

           >[!TIP]
           >
           >Please refer to the document [Deploy your Code,](deploying-code.md) to learn how to set the deployment schedule or execute the pipeline immediately.

           * **Use CSE Oversight** - If this option is select, a CSE is engaged to actually start the deployment. When creating or editing a pipeline when this option is enabled, the **Deployment Manager** role has the following options.

             * **Any CSE** - This option allows any available CSE to start the deployment.
             * **My CSE** - This option allows only the specific CSE assigned to the customer to start the deployment. This also applies for the designated backup of the CSE if the assigned CSE is unavailable.

           ![Production deployment options](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher Configuration** - Define the dispatcher configuration for your production environment. The options are the same as those for the staging environment.
   
1. Click on **Continue** to advance to the **Stage Testing** tab where you can configure AEM Sites and AEM Assets Performance Testing, depending on which products you have licensed.

   >[!TIP]
   >
   >Refer to the document [Understanding Your Test Results](understand-your-test-results.md#performance-testing) for more details on the options available on the **Stage Testing** tab.
   
   1. Under the **Sites Content Delivery/Distributed Load Weight** section, you define how sites performance testing is configured based on the weighting of page requests between the three page sets, which can be enabled or disabled.

      * **Popular Live Pages**
      * **Other Live Pages**
      * **New Pages**

      ![Sites load weight](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Under the **Assets Performance Testing Distribution** section, you define the test distribution of images and PDFs as well as define your own test assets.

      * **Images** - Adjust the slider to adjust the test split between images and PDFs.
      * **PDFs** - Adjust the slider to adjust the test split between images and PDFs.

      * Define your own custom assets by uploading them.

        1. **FORMAT** - Choose whether your custom asset is a PDF of an image.
        1. **FILENAME** - Use the file browser button to select an image from your local machine.
        1. **Add Test File** - Click to upload your selected asset.

      ![Assets testing distribution](/help/using/assets/configure-pipelines/add-prod6.png)

1. Click **Save** to complete adding your production pipeline.












  
 
### Editing a Production Pipeline {#editing-prod-pipeline}

You can edit the pipeline configurations from the **Program Overview** page. 

Follow the steps below to edit the configured pipeline:

1. Navigate to **Pipelines** card from the **Program Overview** page.

1. Click on **...** from the **Pipelines** card and click on **Edit**, as shown in the figure below.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. The **Edit Production Pipeline** dialog box displays.

   1. The **Configuration** tab allows you to update the **Pipeline Name**, **Repository**, **Git Branch**, **Deployment Trigger**, **Important Metrics Failure Behavior**, **Deployment Options** and **Dispatcher Configurations**.

      >[!NOTE]
      >See [Adding and Managing Repositories](/help/using/cloud-manager-repositories.md) to learn how to add and manage repositories in Cloud Manager.


   1. The **Stage Testing** tab provides you an option to re-select your options from **Sites Content Delivery/Distributed Load Weight** and **Assets Performance Testing Distribution**.

1. Click on **Update** once you are done editing the pipeline.

### Additional Production Pipeline Actions {#additional-prod-actions}

#### Running a Production Pipeline {#run-prod}

You can run the production pipeline from the Pipelines card:

1. Navigate to **Pipelines** card from the **Program Overview** page.

1. Click on **...** from the **Pipelines** card and click on **Run**, as shown in the figure below.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Deleting a Production Pipeline {#delete-prod}

You can delete the production pipeline from the Pipelines card:

1. Navigate to **Pipelines** card from the **Program Overview** page.

1. Click on **...** from the **Pipelines** card and click on **Delete**, as shown in the figure below.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >A user in Deployment Manager role can now delete Production pipeline in a self-service manner via the **Delete** option from the Pipeline card.

