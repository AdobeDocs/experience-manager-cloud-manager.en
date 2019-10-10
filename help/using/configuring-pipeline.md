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

---

# Configure your CI/CD Pipeline {#configure-your-ci-cd-pipeline}

The following page explains how to configure the **Pipeline**. To review more conceptual information on how the pipeline works see the [CI/CD pipeline overview](ci-cd-pipeline.md).

## Video Tutorial {#video-tutorial}

### Configuring Pipeline in Cloud Manager {#config-pipeline-video}

The CI/CD Production Pipeline configuration defines the trigger that will initiate the pipeline, parameters controlling the production deployment and performance test parameters.

>[!VIDEO](https://video.tv.adobe.com/v/26314/?quality=12)


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

### Configuring the Pipeline Settings from [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Once you have setup your program using [!UICONTROL Cloud Manager] UI, you are ready to setup your pipeline.

Follow these steps to configure the behavior and preferences for your pipeline:

1. Click **Setup Pipeline** to setup and configure your pipeline.

   ![](assets/Configure_ci-cd-1.png)

1. The **Setup Pipeline** screen displays.

   The three-step wizard allows you to setup your **Branch**, **Environments**, and **Testing** environment. 
   Select your Git branch and click **Next**.
   
   >[!NOTE]
   >
   >Branches found in the Git repository are linked to your program.

   ![](assets/Configure_ci-cd-2.png)


1. Access the **Environments** tab to select **Stage** and **Production** options.

   You can define the trigger to start the pipeline:

    * **On Git Changes** - starts the CI/CD pipeline whenever there are commits added to the configured git branch. Even if you select this option, you can always start the pipeline manually.  
    * **Manual** - using the UI manually start the pipeline.
    * **Scheduled** - this option will be coming soon in an upcoming release.



    During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates such as Code Quality, Security Testing, and Performance Testing.

   This is useful for customers who have the desire for more automated processes. The available options are:

* **Ask every time** - This is the default setting and requires manual intervention on any Important failure.
* **Fail immediately** - If selected, the pipeline will be cancelled whenever an Important failure occurs. This is essentially emulating a user manually rejecting each failure.
* **Continue immediately** - If selected, the pipeline will proceed automatically whenever an Important failure occurs. This is essentially emulating a user manually approving each failure.

  Now you define the parameters controlling the production deployment. The three available options are as follows:

* **Use Go Live Approval** - A deployment must be manually approved by a business owner, project manager, or deployment manager via the [!UICONTROL Cloud Manager] UI.
* **Use CSE Oversight** - A CSE is engaged to actually start the deployment. During pipeline setup or edit when CSE Oversight is enabled, the Deployment Manager has the option of selecting:

  * **Any CSE**: refers to any available CSE  
  * **My CSE**: refers to a specific CSE assigned to the customer or their backup, if the CSE is out of the office

* **Scheduled** - This option allows the user to enable the scheduled production deployment.

 >[!NOTE]
 >
 >If **Scheduled** option is selected, you can schedule your production deployment to the pipeline **after** the stage deployment (and **Use GoLive Approval**, if that has been enabled) to wait for a schedule to be set. The user can also choose to execute the production deployment immediately.
 >
 >Please refer to [**Deploy your Code**](deploying-code.md), to set the deployment schedule or execute the production immediately.

 ![](assets/Configure_ci-cd-3.png)

>[!NOTE]
>
>The **Use CSE Oversight** option is not available to all customers.

**Approve after Stage Deployment**

There is an optional step **Approve after Stage Deployment** which can be configured in the Production Pipeline. 
This is enabled in a new option on the **Pipeline Edit** screen:

![](assets/post_deployment1.png) 

It is then shown as a separate step during pipeline execution:

![](assets/post_deployment2.png) 
  
 >[!NOTE]
 >
 >**Approve after Stage Deployment** functions similarly to the approval before the production deployment, but occurs immediately after the stage deployment step,that is, before any testing is done, compared with the approval before the production deployment, which is done after all testing is complete.

**Dispatcher Invalidation**

As a Deployment Manager, you have the opportunity to configure a set of paths which will either be **invalidated** or **flushed** from the AEM Dispatcher cache, while setting up or editing pipeline.

You can configure a separate set of paths for Stage and Production deployment. If configured, these cache actions will be performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior - invalidate performs a cache invalidation, similar to when content is activated from author to publish; flush performs a cache deletion.

In general, the use of the invalidate action is preferable but there may be cases where flushing is required, especially when using AEM HTML Client Libraries.

>[!NOTE]
>
>Please refer to [Dispatcher Overview](dispatcher-configurations.md) get more information on Dispatcher caching.

Follow the steps below to configure Dispatcher Invalidations:

1. Click **Configure** under the Dispatcher Configuration heading

   ![](assets/image2018-8-7_14-53-24.png)

1. Enter the path, select the action from **Type**, and click **Add**. You can specify up to 100 paths per environment. Once you have added the paths, click **Apply**.

   ![](assets/image2018-8-7_14-58-11.png)

1. Once you are back on the **Pipeline Settings** page, you will see an updated summary of the selections.

   Click **Save** to persist this configuration.

   ![](assets/image2018-8-7_15-4-30.png)

    
1. Access the **Testing** tab to define your testing criteria for your program.

   Now, you can configure the performance test parameters.

   You can configure *AEM Sites* and *AEM Assets* Performance Testing, depending on which products you have licensed.

   **AEM Sites:**

   Cloud Manager executes performance testing for AEM Sites programs by requesting pages (as an unauthenticated user) on the stage publish server for a 30 minute test period and measuring the response time for each page as well as various system-level metrics.Pages are selected by three **page sets**; you can choose anywhere from one to all three sets. The distribution of traffic is based on the number of sets selected, that is, if all three are selected, 33% of the total page views are put toward each set; if two are selected, 50% goes to each set; if one is selected, 100% of the traffic goes to that set.

   For example, let us say that there is a 50%/50% split between the Popular Live Pages and New Pages set (in this example, Other Live Pages is not used) and the New Pages set contains 3000 pages. The page views per minute KPI is set to 200. Over the 30 minute test period:

   * Each of the 25 pages in the Popular Live Pages set will be hit 240 times – ((200 * 0.5) / 25) * 30 = 120

   * Each of the 3000 pages in the New Pages set will be hit once - ((200 * 0.5) / 3000) * 30 = 1

   ![](assets/Configuring_Pipeline_AEM-Sites.png)

   **AEM Assets:**

   Cloud Manager executes performance testing for AEM Assets programs by uploading assets repeatedly for a 30 minute test period and measuring the processing time for each asset as well as various system-level metrics. This capability can upload both images and PDF documents. The distribution of how many assets of each type are uploaded per minute is set in the Pipeline Setup or Edit screen.

   For example, if a 70/30 split is used, as seen in the figure below. There are 10 assets uploaded per minute, 7 images will be uploaded per minute and 3 documents.

   ![](assets/Configuring_Pipeline_AEM-Assets.png)

   >[!NOTE]
   >
   >There is a default image and PDF document, but in most cases, customers will want to upload their own assets. This can be done from the Pipeline Setup or Edit screen. Common image formats such as JPEG, PNG, GIF and BMP are supported along with Photoshop, Illustrator and Postscript files.

1. Click **Save** to complete the setup of pipeline process.

   >[!NOTE]
   >
   >Additionally, once you have setup the pipeline, you can still edit settings for the same using **Production Pipeline Settings** tile from the [!UICONTROL Cloud Manager] UI.

   ![](assets/Prod-Pipeline-Settings-Dialog.png)

## Non-Production & Code Quality Only Pipelines

In addition to the main pipeline which deploys to stage and production, customers are able to set up additional pipelines, referred to as **Non-Production Pipelines**. These pipelines always execute the build and code quality steps. They can optionally also deploy to Adobe Managed Services environment.

## Video on Non-Production & Code Quality Only Pipelines

## Video Tutorial {#video-tutorial}

### Cloud Manager Non-Production & Code Quality Only Pipelines {#non-prod-video}

CI/CD Non-production pipelines are broken into two categories, Code Quality pipelines, and Deployment pipelines. Code Quality pipelines all code from a Git branch to build and be evaluated against Cloud Manager's code quality scan. 

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

On the home screen, these pipelines are listed in a new card:

1. Access the **Non-Production Pipelines** tile from the the Cloud Manager home screen.

   ![](assets/Configuring_Pipeline_Add-Production.png)

1. Clicking on the Add button, to specify the Pipeline Name, Pipeline Type, and the Git Branch.

   Additionally, you can also set up Deployment Trigger and Important Failure Behavior from Pipeline Options.

   ![](assets/Configuring_Pipeline_Add-Production2.png)

1. Click **Save** and the pipeline is shown on the card on the home screen with three actions:

   * **Edit** - allows editing of the pipeline settings
   * **Detail** - displays the last pipeline execution (if there is one)
   * **Build** - navigates to the execution page, from which the pipeline can be executed

   ![](assets/Configuring_Pipeline_Add-Production3.png)

   >[!NOTE]
   >
   >While the pipeline is running, the current step is displayed and only the **Details** action is available.

## The Next Steps {#the-next-steps}

Once you have configured the pipeline, you need to deploy your code.

Please see [Deploy your Code](deploying-code.md) for more details.
