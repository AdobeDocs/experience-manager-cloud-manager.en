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
index: y
internal: n
snippet: y
---

# Configure your CI/CD Pipeline{#configure-your-ci-cd-pipeline}

The following page explains how to configure the **Pipeline**. To review more conceptual information on how the pipeline works see the [CI/CD pipeline overview](ci-cd-pipeline.md).

## Understanding the Flow {#understanding-the-flow}

You can configure your pipeline from the **Pipeline Settings** tile in the [!UICONTROL Cloud Manager] UI.

The Deployment Manager is responsible for setting up the pipeline. When doing so, you first select a branch from the **Git Repository**. Pipeline configuration consists of:

* defining the trigger that will start the pipeline.
* defining the parameters controlling the production deployment.
* configuring the performance test parameters.

## Setting up the Pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>The pipeline cannot be setup until the Git repository has at least one branch.

Before you start to deploy your code, you must configure your pipeline settings from the [!UICONTROL Cloud Manager].

>[!NOTE]
>
>You can change the pipeline settings after initial set up.

### Configuring the Pipeline Settings from [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Once you have setup your program using [!UICONTROL Cloud Manager] UI, you are ready to setup your pipeline.

Follow these steps to configure the behavior and preferences for your pipeline:

1. Click **Setup Pipeline** to setup and configure your pipeline.

   ![](assets/screen_shot_2018-07-18at105633pm.png)

1. The **Edit Deployment Pipeline** screen displays.

   You will see three tabs namely **Branch**, **Environments**, and **Testing**.

   ![](assets/screen_shot_2018-06-04at23950pm.png)

1. Access the **Branch** tab to set up the application branch.

   Select the Git branch to set up.

   >[!NOTE]
   >
   >Branches found in the Git repository are linked to your program.

   ![](assets/screen_shot_2018-06-04at124228pm.png)

1. Access the **Environments** tab to select **Stage** and **Production** options.

   You can define the trigger to start the pipeline:

    * **On Git Changes** - starts the CI/CD pipeline whenever there are commits added to the configured git branch. Even if you select this option, you can always start the pipeline manually.  
    
    * **Manual** - using the UI manually start the pipeline.
    * **Scheduled** - this option will be coming soon in an upcoming release.



During pipeline setup or edit, the Deployment Manager has the option of defining the behavior of the pipeline when an important failure is encountered in any of the quality gates such as Code Quality, Security Testing, and Performance Testing.

This is useful for customers who have the desire for more automated processes. The available options are:

* **Ask every time** - This is the default setting and requires manual intervention on any Important failure.
* **Fail immediately** - If selected, the pipeline will be cancelled whenever an Important failure occurs. This is essentially emulating a user manually rejecting each failure.
* **Continue immediately **- If selected, the pipeline will proceed automatically whenever an Important failure occurs. This is essentially emulating a user manually approving each failure.

Now you define the parameters controlling the production deployment. The three available options are as follows:

* **Use Go Live Approval **- A deployment must be manually approved by a business owner, project manager, or deployment manager via the [!UICONTROL Cloud Manager] UI.
* **Use CSE Oversight** - A CSE is engaged to actually start the deployment. During pipeline setup or edit when CSE Oversight is enabled, the Deployment Manager has the option of selecting:

  * **Any CSE**: refers to any available CSE  
  * **My CSE**: refers to a specific CSE assigned to the customer or their backup, if the CSE is out of the office

* **Scheduled** - This option allows the user to enable the scheduled production deployment.

>[!NOTE]
>
>If **Scheduled** option is selected, you can schedule your production deployment to the pipeline **after** the stage deployment (and **Use GoLive Approval**, if that has been enabled) to wait for a schedule to be set. The user can also choose to execute the production deployment immediately.
>
>Please refer to [**Deploy your Code**](deploying-code.md), to set the deployment schedule or execute the production immediately.

![](assets/screen_shot_2018-08-10at22408pm.png)

>[!NOTE]
>
>The **Use CSE Oversight** option is not available to all customers.

**Dispatcher Invalidation**

As a Deployment Manager, you have the opportunity to configure a set of paths which will either be **invalidated** or **flushed** from the AEM Dispatcher cache, while setting up or editing pipeline.

You can configure a separate set of paths for Stage and Production deployment. If configured, these cache actions will be performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior - invalidate performs a cache invalidation, similar to when content is activated from author to publish; flush performs a cache deletion.

In general, the use of the invalidate action is preferable but there may be cases where flushing is required, especially when using AEM HTML Client Libraries.

>[!NOTE]
>
>Please refer to [Dispatcher Overview](dispatcher.md#HowDispatcherperformsCaching) get more information on Dispatcher caching.

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

During pipeline setup, the deployment manager can decide how much traffic to direct to each bucket. They can choose anywhere from one to all three buckets. The distribution of traffic is based on the number of buckets selected, i.e. if all three are selected, 33% of the total page views are put toward each bucket; if two are selected, 50% goes to each set; if one is selected, 100% of the traffic goes to that set.

For example, let us say that there is a 50%/50% split between the Popular Live Pages and New Pages set (in this example, Other Live Pages is not used) and the New Pages set contains 3000 pages. The page views per minute KPI is set to 200. Over the 30 minute test period:

* Each of the 25 pages in the Popular Live Pages set will be hit 240 times - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Each of the 3000 pages in the New Pages set will be hit once - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/screen_shot_2018-06-04at23503pm.png)

1. Click **Save** to complete the setup of pipeline process.

>[!NOTE]
>
>Additionally, once you have setup the pipeline, you can still edit settings for the same using **Pipeline** **Settings** tile from the [!UICONTROL Cloud Manager] UI.

![](assets/screen_shot_2018-06-04at125751pm.png) 

### The Next Steps {#the-next-steps}

Once you have configured the pipeline, you need to deploy your code.

Please see [Deploy your Code](deploying-code.md) for more details.
