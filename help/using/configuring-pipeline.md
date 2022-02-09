---
title: Configure Your CI/CD Pipeline
description: Learn how to use Cloud Manager to create and configure your pipelines in order to deploy your code.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
---
# Configure your CI/CD Pipeline {#configure-your-ci-cd-pipeline}

Learn how to use Cloud Manager to create and configure your pipelines in order to deploy your code. if you would first like a more conceptual overview of how pipelines work in Cloud Manager, please see the [CI/CD pipeline overview documentation.](ci-cd-pipeline.md)


>[!NOTE]
>
>To learn how to configure CI/CD pipelines for Cloud Manager in AEM as a Cloud Service, see [the AEMaaCS documentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Overview {#understanding-the-flow}

You configure pipelines using the **Pipeline Settings** tile in the [!UICONTROL Cloud Manager] UI.

You can create two different types of pipelines.

* Production Pipelines - A production pipelines is a purpose-built pipeline made of a series of orchestrated steps to take source code all the way into production.
* Non-Production Pipelines - A non-production pipeline primarily serves to run code-quality scans or to deploy source code into a development environment.

To learn more about the types of pipelines, see the [CI/CD pipeline overview documentation.](ci-cd-pipeline.md)

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

       ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Under the **Source Code** section, you define where the pipeline retrieves the code it will process.

      * **Repository** - This option defines from which git repo the pipeline should retrieve the code.

      >[!TIP]
      >
      >See the document [Set Up Your Program](setting-up-program.md) to learn how to add and manage repositories in Cloud Manager.

      * **Git Branch** - This option defines from which branch in the selected the pipeline should retrieve the code.
      * **Code Location** - This option defines the path in the branch of the selected repo from which the pipeline should retrieve the code.

   1. Under the **Environments** section, you define what triggers a deployment and how it should be rolled out per environment.

      1. In the **STAGE** section, you can define how the pipeline rolls out to your staging environment.

         * **Deployment Trigger** - You have the following options to define the deployment triggers to start the pipeline.

           * **Manual** - Use this option to manually start the pipeline using the Cloud Manager UI.
           * **On Git Changes** - This options starts the CI/CD pipeline whenever commits are added to the configured git branch. With this option, you can still start the pipeline manually as required.

         * **Important Metric Failures Behavior** - During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates. The available options are:

           * **Ask every time** - This is the default setting and requires manual intervention on any important failure.
           * **Fail Immediately** - If selected, the pipeline will be cancelled whenever an important failure occurs. This is essentially emulating a user manually rejecting each failure.
           * **Continue Immediately** - If selected, the pipeline will proceed automatically whenever an important failure occurs. This is essentially emulating a user manually approving each failure.

         * **Deployment Options** - You can accelerate certain deployment tasks.

           * **Approve after Stage Deployment** - This approval occurs after deployment to the staging environment before any testing is done. Otherwise approval occurs before the production deployment, which is done after all testing is complete.

           * **Skip Load Balancer changes** - Load balancer changes are not made.

         * **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths which will either be invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions will be performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:
        
           1.  Under **PATH** provide a content path.
           1.  Under **TYPE**, select the action to be taken on that path.
           
             * **Flush** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
             * **Invalidate** - Performs a cache deletion.
             
           1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

           >[!TIP]
           >
           >In general, the use of the invalidate action is preferable, but there may be cases where flushing is required, especially when using AEM HTML Client Libraries.

      1. In the **PRODUCTION** section, you can define how the pipeline rolls out to your production environment.

         * **Deployment Options** - You can define the parameters controlling the production deployment.

           * **Use Go Live Approval** - A deployment must be manually approved by a user with the **Business Owner**, **Project Manager**, or **Deployment Manager** role via the [!UICONTROL Cloud Manager] UI.
           * **Scheduled** - This option allows production deployment to be scheduled.

           >[!NOTE]
           >
           >If the **Scheduled** option is selected, you can schedule your production deployment to the pipeline **after** the stage deployment (and **Use GoLive Approval**, if that has been enabled) to wait for a schedule to be set. The user can also choose to execute the production deployment immediately.
           >
           >Please refer to the document [Deploy your Code,](deploying-code.md) to learn how to set the deployment schedule or execute the pipeline immediately.

           * **Use CSE Oversight** - If this option is select, a CSE is engaged to actually start the deployment. When creating or editing a pipeline when this option is enabled, the **Deployment Manager** role has the following options.

             * **Any CSE** - This option allows any available CSE to start the deployment.
             * **My CSE** - This option allows only the specific CSE assigned to the customer to start the deployment. This also applies for the designated backup of the CSE if the assigned CSE is unavailable.

         * **Dispatcher Configuration** - Define the dispatcher configuration for your production environment. The options are the same as those for the staging environment.
   
1. Click on **Continue** to advance to the **Stage Testing** tab where you can configure AEM Sites and AEM Assets Performance Testing, depending on which products you have licensed. Refer to the document [Understanding Your Test Results](understand-your-test-results.md#performance-testing) for more details.
   
   1. Under the **Sites Content Delivery/Distributed Load Weight** section, you define where the pipeline retrieves the code it will process.
















   1. You can set up **Deployment Trigger** and **Important Metric Failures Behavior** from **Deployment Options**.

        ![](/help/using/assets/configure-pipelines/add-prod3.png)


        You can assign the following deployment triggers to start the pipeline:

        * **Manual** - using the UI manually start the pipeline.
        * **On Git Changes** - starts the CI/CD pipeline whenever there are commits added to the configured git branch. Even if you select this option, you can always start the pipeline manually.  

         During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates.

        This is useful for customers who have the desire for more automated processes. The available options are:

         * **Ask every time** - This is the default setting and requires manual intervention on any Important failure.
         * **Fail Immediately** - If selected, the pipeline will be cancelled whenever an Important failure occurs. This is essentially emulating a user manually rejecting each failure.
         * **Continue immediately** - If selected, the pipeline will proceed automatically whenever an Important failure occurs. This is essentially emulating a user manually approving each failure.

    1. Select the **Deployment Options**.

       ![](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Approve after Stage Deployment** functions similarly to the approval before the production deployment, but occurs immediately after the stage deployment step,that is, before any testing is done, compared with the approval before the production deployment, which is done after all testing is complete.

         * **Skip Load Balancer changes** skips the changes.

    1. Select the **Dispatcher Configuration** for Stage. Enter the path, select the action from **Type**, and click **Add Path**. You can specify up to 100 paths per environment. 

       ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

    1. Select the **Deployment Options** for Production. Now you define the parameters controlling the production deployment. 
    
       ![](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

       The three available options are as follows:

       * **Use Go Live Approval** - A deployment must be manually approved by a business owner, project manager, or deployment manager via the [!UICONTROL Cloud Manager] UI.

       * **Scheduled** - This option allows the user to enable the scheduled production deployment.

          >[!NOTE]
          >If **Scheduled** option is selected, you can schedule your production deployment to the pipeline **after** the stage deployment (and **Use GoLive Approval**, if that has been enabled) to wait for a schedule to be set. The user can also choose to execute the production deployment immediately.
          >
          >Please refer to [Deploy your Code](deploying-code.md), to set the deployment schedule or execute the production immediately.

         * **Use CSE Oversight** - A CSE is engaged to actually start the deployment. During pipeline setup or edit when CSE Oversight is enabled, the Deployment Manager has the option of selecting:

            * **Any CSE**: refers to any available CSE  
            * **My CSE**: refers to a specific CSE assigned to the customer or their backup, if the CSE is out of the office

    1. Setup the **Dispatcher Configurations** for Production. Enter the path, select the action from **Type**, and click **Add Path**. You can specify up to 100 paths per environment.

       ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

       As a Deployment Manager, you have the opportunity to configure a set of content paths which will either be **invalidated** or **flushed** from the AEM Dispatcher cache for publish instances, while setting up or editing pipeline.

       You can configure a separate set of paths for Stage and Production deployment. If configured, these cache actions will be performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior - invalidate performs a cache invalidation, similar to when content is activated from author to publish; flush performs a cache deletion.

       In general, the use of the invalidate action is preferable but there may be cases where flushing is required, especially when using AEM HTML Client Libraries.

       >[!NOTE]
       >
       >Please refer to [Dispatcher Overview](dispatcher-configurations.md) get more information on Dispatcher caching.

1. Click on **Continue** once you have selected all the options.

1. Select your options from the **Stage Testing** step. You can configure *AEM Sites* and *AEM Assets* Performance Testing, depending on which products you have licensed. Refer to [Performance Testing](understand-your-test-results.md#performance-testing) for more details.

   1. Select your options from **Sites Content Delivery/Distributed Load Weight**. See [AEM Sites in Performance Testing](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) for more details.

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Select your options from **Assets Performance Testing Distribution**. See [AEM Assets in Performance Testing](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) for more details.

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Click on **Save** to complete adding production pipeline.
 
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

## Non-Production & Code Quality Only Pipelines

In addition to the main pipeline which deploys to stage and production, customers are able to set up additional pipelines, referred to as **Non-Production Pipelines**. These pipelines always execute the build and code quality steps. They can optionally also deploy to Adobe Managed Services environment.

## Video Tutorial {#video-tutorial-two}

### Cloud Manager Non-Production & Code Quality Only Pipelines {#non-prod-video}

CI/CD Non-production pipelines are broken into two categories, Code Quality pipelines, and Deployment pipelines. Code Quality pipelines all code from a Git branch to build and be evaluated against Cloud Manager's code quality scan. 

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Adding a Non-Production Pipeline {#add-non-production-pipeline}

On the home screen, these pipelines are listed in a new card:

1. Access the **Pipelines** card from the Cloud Manager home screen. Click on **+Add** and select **Add Non-Production Pipeline**. 

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **Add Non-Production Pipeline**  dialog box displays. Select the type of pipeline you want to create, either **Code Quality Pipeline** or **Deployment Pipeline**.

   Additionally, you can also set up **Deployment Trigger** and **Important Metric Failures Behavior** from **Deployment Options**. Click on **Continue**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. The newly created non-production pipeline now displays in the **Pipelines** card.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   The pipeline is shown on the card on the home screen with three actions, as shown below:
   
   * **Add** - allows adding of a new pipeline.
   * **Access Repo Info** - allows the user to get the information necessary to access Cloud Manager Git repository.
   * **Learn More** - navigates to understanding the CI/CD pipeline documentation resource. 

### Editing a Non-Production Pipeline {#editing-nonprod-pipeline}

You can edit the pipeline configurations from the **Pipelines card** from **Program Overview** page. 

Follow the steps below to edit the configured non-production pipeline:

1. Navigate to **Pipelines** card from the **Program Overview** page.

1. Select the non-production pipeline and click on **...**. Click on **Edit**, as shown in the figure below.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. The **Edit Production Pipeline** dialog box displays that allows you to update the **Pipeline Name**, **Repository**, **Git Branch**, **Deployment Trigger**, and **Important Metrics Failure Behavior**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)
   
      >[!NOTE]
      >See [Adding and Managing Repositories](/help/using/cloud-manager-repositories.md) to learn how to add and manage repositories in Cloud Manager.

      You can assign the following deployment triggers to start the pipeline:

      * **Manual** - using the UI manually start the pipeline.
      * **On Git Changes** - starts the CI/CD pipeline whenever there are commits added to the configured git branch. Even if you select this option, you can always start the pipeline manually.  

      During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates. This is useful for customers who have the desire for more automated processes. The available options are:

      * **Ask every time** - This is the default setting and requires manual intervention on any Important failure.
      * **Fail Immediately** - If selected, the pipeline will be cancelled whenever an Important failure occurs. This is essentially emulating a user manually rejecting each failure.
      * **Continue immediately** - If selected, the pipeline will proceed automatically whenever an Important failure occurs. This is essentially emulating a user manually approving each failure.

1. Click on **Update** once you are done editing the non-production pipeline.

### Additional Non-Production Pipeline Actions {#additional-nonprod-actions}

#### Running a Non-Production Pipeline {#run-nonprod}

You can run the production pipeline from the Pipelines card:

1. Navigate to **Pipelines** card from the **Program Overview** page.

1. Click on **...** from the **Pipelines** card and click on **Run**, as shown in the figure below.

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### Deleting a Non-Production Pipeline {#delete-nonprod}

You can delete the production pipeline from the Pipelines card:

1. Navigate to **Pipelines** card from the **Program Overview** page.

1. Click on **...** from the **Pipelines** card and click on **Delete**, as shown in the figure below.

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## The Next Steps {#the-next-steps}

Once you have configured the pipeline, you need to deploy your code.

Please see [Deploy your Code](deploying-code.md) for more details.
