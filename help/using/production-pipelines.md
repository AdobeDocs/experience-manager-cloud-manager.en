---
title: Add a Production Pipeline
description: Learn how to use Cloud Manager to create and configure production pipelines to deploy your code.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
---
# Add a production pipeline {#configuring-production-pipelines}

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

   ![Add a production pipeline](/help/assets/configure-pipelines/add-prod7.png)

1. The **Add Production Pipeline** dialog box opens to the **Configuration** tab where a number of options for your pipeline must be defined. These options are grouped into collapsible sections and are described in the following steps.

   1. Provide a descriptive name for your pipeline in the **Pipeline Name** field.

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
   
1. Click **Continue** to advance to the **Source Code** tab where you select the type of code to deploy and configure the source repository.

   1. Under **Select code to deploy**, choose the deployment type:

      * **[Full Stack Code](#full-stack-code)** - Code for your complete AEM application.
      * **[Web Tier Config](#web-tier-config)** - Dispatcher properties to store, process and deliver web pages to the client.

      See [CI/CD Pipelines](/help/overview/ci-cd-pipelines.md#code-sources) for more information about these deployment types. The remaining steps to complete the pipeline configuration depend on the type you selected. Follow the links above to jump to the relevant section of this document.

1. Click **Continue** to advance to the **Stage Testing** tab where you can configure AEM Sites and AEM Assets Performance Testing, depending on which products you have licensed. {#stage-testing}

   >[!TIP]
   >
   >See [Code Quality Testing](/help/using/code-quality-testing.md#performance-testing) for more details on the options available on the **Stage Testing** tab.
   
   1. In the **Sites Content Delivery/Distributed Load Weight** section, you configure site Performance Testing based on the weighting of page requests among three page sets. You can enable or disable the page sets as needed.

      * **Popular Live Pages**
      * **Other Live Pages**
      * **New Pages**

      ![Sites load weight](/help/assets/configure-pipelines/add-prod8.png)

   1. Under the **Assets Performance Testing Distribution** section, you define the test distribution of images and PDFs and define your own test assets.

      * **Images** - Adjust the slider to adjust the test split between images and PDFs.
      * **PDFs** - Adjust the slider to adjust the test split between images and PDFs.

      * Define your own custom assets by uploading them.

        1. **FORMAT** - Choose whether your custom asset is a PDF of an image.
        1. **FILENAME** - Use the file browser button to select an image from your local machine.
        1. **Add Test File** - Click to upload your selected asset.

      ![Assets testing distribution](/help/assets/configure-pipelines/add-prod6.png)

1. Click **Save** to complete adding your production pipeline.

### Full Stack Code {#full-stack-code}

A full-stack code pipeline deploys back-end and front-end code builds along with HTTPD/Dispatcher configuration.

>[!NOTE]
>
>If a full-stack production pipeline already exists, this selection is disabled.

**To configure a full stack code production pipeline:**

1. On the **Source Code** tab, define the following options.

   * **Repository** - Defines which Git repo the pipeline should retrieve the code.

   >[!TIP]
   >
   >See the document [Program Setup](/help/getting-started/program-setup.md) to learn how to add and manage repositories in Cloud Manager.

   * **Git Branch** - Defines from which branch the pipeline should retrieve the code.
   * **Ignore Web Tier Configuration** - When checked, the pipeline does not deploy your web tier configuration. If a web tier config pipeline already exists for the same environment, this check box is automatically selected and disabled because the web tier configuration is managed by that pipeline instead. When no web tier config pipeline exists, you can select or clear this option to control whether the full stack pipeline deploys the Dispatcher configuration.

   ![Full stack code source](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. Click **Continue** to advance to the **Stage Testing** tab. See [Stage Testing](#stage-testing) for details.

### Web Tier Config {#web-tier-config}

A web tier config pipeline deploys only HTTPD/Dispatcher configuration. See [CI/CD Pipelines](/help/overview/ci-cd-pipelines.md#deployment-types) for more details about this pipeline type.

>[!NOTE]
>
>If a web-tier config production pipeline already exists, this selection is disabled.

If you create a web tier config pipeline for an environment with an existing full-stack pipeline, the web tier configuration in the full-stack pipeline is ignored. This change affects only the web tier configuration in that environment.

**To configure a web tier config production pipeline:**

1. On the **Source Code** tab, define the following options.

   * **Repository** - From the drop-down list, select the Git repository that contains the web tier configuration.
   * **Git Branch** - Select the branch in the chosen repository that Cloud Manager uses for the deployment.
   * **Code Location** - Enter the path in the selected repository that contains the web tier configuration to deploy. The default location is the repository root (`/`).

   >[!NOTE]
   >
   >If Code Location does not point to the dispatcher code location, additional application code could be pulled into the artifact package and deployed to the dispatcher, causing Apache to fail on restart and the pipeline to fail. Make sure to set the correct path to the dispatcher files in the repository.

   ![Web tier config source](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. Click **Continue** to advance to the **Stage Testing** tab. See [Stage Testing](#stage-testing) for details.


## About using Smart Build in your production pipeline{#about-smart-build}

**Smart Build** in Cloud Manager is an optimized build strategy for production pipelines. Smart Build reduces build times by caching modules and rebuilding only those modules that have changed since the last successful run. Unchanged modules are reused from cache, while only modified modules and their dependencies are rebuilt, improving efficiency for iterative development workflows.

Smart Build is currently available for the following:

* Code Quality pipelines.
* Development, Stage, and Production full-stack deployment pipelines.

>[!NOTE]
>
>The first run after enabling Smart Build behaves like a Full Build because the cache is empty.

Smart Build is recommended when you have the following:

* You are actively developing and committing frequent incremental changes.
* Your project contains multiple Maven modules.
* Full builds are taking significant time.

Smart Build is not always ideal when you have the following:

* Your build relies heavily on plugins that perform operations outside Maven's dependency graph.
* You require full rebuild validation on every execution.

### Understand build performance{#smart-build-performance}

The performance gain from using Smart Build depends on several factors including the following:

* The number of modules in the project.
* The frequency and scope of code changes.
* The distribution of dependencies across modules.

Generally, projects with many independent modules can see the greatest improvement.

### Per-module cache opt-out{#smart-build-cache-optout}

Smart Build provides fine-grained control that lets you disable caching for specific modules. This ability is useful when certain modules:

* Use plug-ins, such as `exec-maven-plugin` or `maven-antrun-plugin`.
* Perform file operations not tracked by Maven dependencies.
* Produce inconsistent results when cached.

### Disable caching for a module{#smart-build-disable-caching}

You can add the following property to the affected module's `pom.xml`:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

This syntax forces the module to rebuild on every pipeline execution while other modules continue to benefit from caching.

### Limitations and considerations when using Smart Build{#smart-build-limitations}

Keep the following in mind when you use Smart Build:

* Smart Build relies on Maven dependency analysis.
* Changes outside the dependency graph may not trigger rebuilds.
* Some plug-ins may not be fully compatible with caching.
* You can switch back to **Full Build** at any time by editing the non-production pipeline.

If you encounter unexpected build behavior, consider disabling caching for specific modules or temporarily switching your build strategy to **Full Build**.

### Troubleshooting Smart Build issues{#smart-build-troubleshoot}

   | Issue | Suggested solutions |
   | --- | --- |
   | Build results are inconsistent | &bull; Disable caching for affected modules.<br>&bull; Verify plug-in behavior (especially `exec`/`antrun` plug-ins).   |
   | No performance improvement | &bull; Ensure that multiple runs have occurred (cache warm-up).<br>&bull; Check if most modules are changing frequently.  |
   | Unexpected artifacts or missing changes | &bull; Review whether changes are outside Maven dependency tracking.<br>&bull; Use **Full Build** for verification. |

See [Add a production pipeline](#adding-production-pipeline) the enable Smart Build.


## The next steps {#the-next-steps}

After you have configured the pipeline, you deploy your code. See [Code Deployment](/help/using/code-deployment.md) for more details.

## Video tutorial {#video-tutorial-one}

This video provides an overview of the pipeline creation process, which is detailed in this document.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
