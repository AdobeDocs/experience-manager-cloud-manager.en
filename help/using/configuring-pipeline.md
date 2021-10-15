---
title: Configure your CI/CD Pipeline
seo-title: Configure your CI/CD Pipeline
description: Follow this page to configure your pipeline settings from the Cloud Manager.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager. 
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
---
# Configure your CI/CD Pipeline {#configure-your-ci-cd-pipeline}

>[!NOTE]
>To learn how to configure CI/CD Pipeline for Cloud Manager in AEM as a Cloud Service, see [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager).

The following page explains how to configure the **Pipeline**. To review more conceptual information on how the pipeline works see the [CI/CD pipeline overview](ci-cd-pipeline.md).

## Video Tutorial {#video-tutorial-one}

### Configuring Pipeline in Cloud Manager {#config-pipeline-video}

The CI/CD Production Pipeline configuration defines the trigger that will initiate the pipeline, parameters controlling the production deployment and performance test parameters.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)


## Understanding the Flow {#understanding-the-flow}

You can configure your pipeline from the **Pipeline Settings** tile in the [!UICONTROL Cloud Manager] UI.

The Deployment Manager is responsible for setting up the pipeline. When doing so, you first select a branch from the **Git Repository**. Pipeline configuration consists of:

* defining the trigger that will start the pipeline.
* defining the parameters controlling the production deployment.
* configuring the performance test parameters.

## Setting up the Pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>The pipeline cannot be setup until the Git repository has at least one branch and [Program Setup](setting-up-program.md) is complete.

Before you start to deploy your code, you must configure your pipeline settings from the [!UICONTROL Cloud Manager].

>[!NOTE]
>
>You can change the pipeline settings after initial set up.

## Adding a New Production Pipeline from Pipelines Card {#adding-production-pipeline}

Once you have setup your program and have at least one environment using [!UICONTROL Cloud Manager] UI, you are ready to add a production pipeline.

Follow these steps to configure the behavior and preferences for your production pipeline:

1. Navigate to the **Pipelines** card from the **Program Overview** page.

1. Click on **+Add** and select **Add Production Pipeline**. 

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **Add Production Pipeline** dialog box displays. 

    1. Enter the pipeline name. You can choose the **Repository** and the **Git Branch**.

       ![](/help/using/assets/configure-pipelines/add-prod2.png)

     1. You can set up **Deployment Trigger** and **Important Failure Behavior** from **Deployment Options**.

        ![](/help/using/assets/configure-pipelines/add-prod3.png)


        You can define the trigger to start the pipeline:

        * **Manual** - using the UI manually start the pipeline.
        * **On Git Changes** - starts the CI/CD pipeline whenever there are commits added to the configured git branch. Even if you select this option, you can always start the pipeline manually.  

          >[!NOTE]
          >During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates.

        This is useful for customers who have the desire for more automated processes. The available options are:

         * **Ask every time** - This is the default setting and requires manual intervention on any Important failure.
         * **Cancel Immediately** - If selected, the pipeline will be cancelled whenever an Important failure occurs. This is essentially emulating a user manually rejecting each failure.
         * **Approve immediately** - If selected, the pipeline will proceed automatically whenever an Important failure occurs. This is essentially emulating a user manually approving each failure.

    1. Select the **Deployment Options**.

       ![](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Approve after Stage Deployment** functions similarly to the approval before the production deployment, but occurs immediately after the stage deployment step,that is, before any testing is done, compared with the approval before the production deployment, which is done after all testing is complete.

         * **Skip Load Balancer**

    1. Select the **Dispatcher Configurations** for Stage. Enter the path, select the action from **Type**, and click **Add Path**. You can specify up to 100 paths per environment. 

       ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

    1. Select the **Deployment Options** for Production. Now you define the parameters controlling the production deployment. The three available options are as follows:

       * **Use Go Live Approval** - A deployment must be manually approved by a business owner, project manager, or deployment manager via the [!UICONTROL Cloud Manager] UI.
       * **Use CSE Oversight** - A CSE is engaged to actually start the deployment. During pipeline setup or edit when CSE Oversight is enabled, the Deployment Manager has the option of selecting:

        * **Any CSE**: refers to any available CSE  
        * **My CSE**: refers to a specific CSE assigned to the customer or their backup, if the CSE is out of the office

       * **Scheduled** - This option allows the user to enable the scheduled production deployment.

          >[!NOTE]
          >If **Scheduled** option is selected, you can schedule your production deployment to the pipeline **after** the stage deployment (and **Use GoLive Approval**, if that has been enabled) to wait for a schedule to be set. The user can also choose to execute the production deployment immediately.
          >
          >Please refer to [Deploy your Code](deploying-code.md), to set the deployment schedule or execute the production immediately.

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
      >See [Adding and Managing Repositories](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) to learn how to add and manage repositories in Cloud Manager.


   1. The **Stage Testing** tab provides you an option to re-select your options from **Sites Content Delivery/Distributed Load Weight** and **Assets Performance Testing Distribution**.

1. Click on **Update** once you are done editing the pipeline.

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

   Additionally, you can also set up **Deployment Trigger** and **Important Failure Behavior** from **Deployment Options**. Click on **Continue**.

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
      >See [Adding and Managing Repositories](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) to learn how to add and manage repositories in Cloud Manager.


1. Click on **Update** once you are done editing the non-production pipeline.


## The Next Steps {#the-next-steps}

Once you have configured the pipeline, you need to deploy your code.

Please see [Deploy your Code](deploying-code.md) for more details.
