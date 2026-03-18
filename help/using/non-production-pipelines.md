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

## Add a non-production pipeline {#add-non-production-pipeline}

Once you have set up your program and have at least one environment using the Cloud Manager UI, you are ready to add a non-production pipeline by following these steps.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. Access the Pipelines card from the Cloud Manager home screen. Click **Add**, then select **Add Non-Production Pipeline**.

   ![Add non-production pipeline](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. On the **Configuration** tab of the **Add Non-Production Pipeline** dialog box, select the type of pipeline you want to create, either  one of the following:

   * **Code Quality Pipeline** - Creates a pipeline that builds the code, runs unit tests, and evaluates code quality without deploying to an environment.
   * **Deployment Pipeline** - Creates a pipeline that builds the code, runs unit tests, evaluates code quality, and deploys to an environment.
   
   ![Choose pipeline type](/help/using/assets/add-non-production-pipeline-cm-ams.png)

   >[!BEGINTABS]

   >[!TAB Code Quality Pipeline - Configuration tab]

   | Section | Option | Description |
   | --- | --- | --- |
   | **Pipeline Configuration** | **Non-production Pipeline Name** | Provide a description for your pipeline in the **Non-Production Pipeline Name** field. |
   |  | **Testing**  | Visible only when editing a non-production pipeline.<br>The UI shows the testing categories that the pipeline runs as part of code quality validation.<ul><li>**Static Code Testing** - Analyzes the code for quality and correctness issues.<li>**Load/Performance Testing** - Evaluates performance-related behavior as part of pipeline testing.<li>**Security Testing** - Checks the code and pipeline output for security-related issues. |
   | **Deployment Options** | **Deployment Trigger** | <ul><li>**Manual** - Lets you manually start the pipeline.<li>**On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required. |
   |  | **Important Metric Failures Behavior** | <ul><li>**Ask every time** - This behavior is the default setting and requires manual intervention on any important failure.<li>**Fail immediately** - If selected, the pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.<li>**Continue immediately** - If selected, the pipeline procedes automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.</li></ul> |
   |  | **Approve after Stage Deployment** check box  | Visible only when editing a non-production pipeline.<br>Select this option to require approval after deployment to the stage environment before the pipeline can continue. If this option is not selected, the pipeline continues based on the configured behavior. |

   >[!TAB Deployment Pipeline - Configuration tab]

   | Section | Option | Description |
   | --- | --- | --- |
   | **Pipeline Configuration** | **Non-production Pipeline Name** | Provide a description for your pipeline in the **Non-Production Pipeline Name** field. |
   |   | **Eligible Deployment Environment** | If your pipeline is a deployment pipeline, you must select which environments where Cloud Manager deploys the code.  | 
   |   | **Testing** | Visible only when editing a non-production pipeline.<br>The UI shows the testing categories that the pipeline runs as part of code quality validation.<ul><li>**Static Code Testing** - Analyzes the code for quality and correctness issues.<li>**Load/Performance Testing** - Evaluates performance-related behavior as part of pipeline testing.<li>**Security Testing** - Checks the code and pipeline output for security-related issues.</li></ul>  |
   | **Deployment Options** | **Deployment Trigger** | <ul><li>**Manual** - Lets you manually start the pipeline.<li>**On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required. |
   |   | **Important Metric Failures Behavior** | <ul><li>**Ask every time** - The default setting and prompts the user to decide how to proceed when an important metric fails.<li>**Fail Immediately** - The pipeline is canceled whenever an important metric fails. It is essentially emulating a user manually rejecting each failure.<li>**Continue Immediately** - The pipeline proceeds automatically whenever an important metric fails. It is essentially emulating a user manually approving each failure.</li></ul> |
   |  | **Approve after Stage Deployment** check box | Visible only when editing a non-production pipeline.<br>Select this option to require approval after deployment to the stage environment before the pipeline can continue. If this option is not selected, the pipeline continues based on the configured behavior. |
   |  | **Skip Load Balancer changes** check box  | Select this option to prevent the pipeline from making load balancer changes during deployment. |
   |  | **Dispatcher Configuration** | The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure `Dispatcher`, do the following:<ul><li>Under **PATH**, provide a content path that you want the pipeline to flush or invalidate.<li>Under **TYPE**, select the action to be taken on that path.<ul><li>**Flush** - Perform a cache deletion on the specified path.</li><li>**Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.</li><li>Click **Add Path** to add your specified path. You can add up to 100 paths per environment.</li></ul> |
   | **Pipeline** | **Experience Audit** check box | Select this option to include an Experience Audit step in the pipeline. When enabled, the pipeline includes the Experience Audit step after the Source Code tab. |

   >[!ENDTABS]

1. In the lower-right corner of the **Add Non-Production Pipeline** dialog box, click **Continue**.
1. Select the type of code the pipeline is configured to build and deploy.

   >[!BEGINTABS]

   >[!TAB Source Code tab - Full Stack Code]

   Deploys the complete AEM application, including application code and, by default, web tier configuration.

   | Section | Option | Description |
   | --- | --- | --- |
   | **Source code** | **Repository** | From the drop-down list, choose the Git repository that the pipeline uses as its source. Cloud Manager builds code from the repository that you choose here. |
   |   | **Git Branch** | From the drop-down list, choose which branch in the selected repository the pipeline should build from. The default is `main`. The pipeline uses the chosen branch as the source for build and deployment. If necessary, click **Refresh** to update the list of available branches for the selected repository. Use this option if a recently created branch does not appear in the list. |
   |   | **Build Strategy** | <ul><li>**Full Build** - Builds all modules in the repository every time<li>BETA **Smart Build** - Builds only modules that have changed since the last commit.<br>Learn more about [using Smart Build in a non-production pipeline](#about-smart-build).</li></ol>**Important**: Smart Build is available only for Code Quality pipelines and Dev Full Stack Code deployment pipelines. |
   |   | **Ignore Web Tier Configuration** check box | Select this option to skip deployment of web tier configuration in a Full Stack code pipeline. Leave the option unselected to deploy web tier configuration together with the pipeline’s code.|
   | **Pipeline** | **Experience Audit** check box | Select this option to include an Experience Audit step in the pipeline. When enabled, the pipeline includes the Experience Audit step after the Source Code tab. |

   >[!TAB Source Code - Web Tier Config]

   Deploys only web tier configuration, such as Dispatcher properties used to store, process, and deliver web pages to the client. When you select **Web Tier Config**, Cloud Manager creates a pipeline dedicated to web tier configuration deployment.

   If a full stack pipeline already exists, Cloud Manager displays a notice that creating a web tier configuration pipeline causes the existing full stack pipeline to ignore web tier configuration. After you create the web tier configuration pipeline, Cloud Manager manages web tier configuration deployments through that pipeline instead of the full stack pipeline.

   | Section | Option | Description |
   | --- | --- | --- |
   | **Source code** | **Repository** | From the drop-down list, select the Git repository that contains the web tier configuration. |
   |   | **Git Branch** | Select the branch in the chosen repository that Cloud Manager uses for the deployment. If necessary, click **Refresh** to update the list of available branches for the selected repository. Use this option if a recently created branch does not appear in the list. |
   |   | **Code Location** | Enter the path in the selected repository that contains the web tier configuration to deploy. The default location is the repository root (`/`). | 

   >[!ENDTABS]

1. Click **Save**.

### About using Smart Build in a non-production pipeline{#about-smart-build}

**Smart Build** in Cloud Manager is an optimized build strategy for non-production pipelines. Smart Build reduces build times by caching modules and rebuilding only those modules that have changed since the last successful run. Unchanged modules are reused from cache, while only modified modules and their dependencies are rebuilt, improving efficiency for iterative development workflows.

Smart Build is currently available only for the following:

* Code Quality pipelines.
* Dev full-stack deployment pipelines.

>[!NOTE]
>
>The first run after enabling Smart Build behaves like a Full Build because the cache is empty.

Smart Build is recommended when you have the following:
* You are actively developing and committing frequent incremental changes.
* Your project contains multiple Maven modules.
* Full builds are taking significant time.

Smart Build is not always ideal when you have the following:
* Your build relies heavily on plugins that perform operations outside Maven’s dependency graph.
* You require full rebuild validation on every execution.

#### Understand build performance

The performance gain from using Smart Build depends on several factors including the following:

* The number of modules in the project.
* The frequency and scope of code changes.
* The distribution of dependencies across modules.

Generally, projects with many independent modules typically see the greatest improvement.

#### Per-module cache opt-out

Smart Build provides fine-grained control that lets you disable caching for specific modules. This ability is useful when certain modules:

* Use plug-ins, such as `exec-maven-plugin` or `maven-antrun-plugin`.
* Perform file operations not tracked by Maven dependencies.
* Produce inconsistent results when cached.

#### Disable caching for a module

You can add the following property to the affected module’s `pom.xml`:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

This syntax forces the module to rebuild on every pipeline execution while other modules continue to benefit from caching.

#### Limitations and considerations when using Smart Build

Keep the following in mind when you use Smart Build:

* Smart Build relies on Maven dependency analysis.
* Changes outside the dependency graph may not trigger rebuilds.
* Some plug-ins may not be fully compatible with caching.
* You can switch back to **Full Build** at any time by editing the non-production pipeline.

If you encounter unexpected build behavior, consider disabling caching for specific modules or temporarily switching your build strategy to **Full Build**.

#### Troubleshooting Smart Build issues

   | Issue | Suggested solutions |
   | --- | --- |
   | Build results are inconsistent | &bull; Disable caching for affected modules.<br>&bull; Verify plug-in behavior (especially `exec`/`antrun` plug-ins).   |
   | No performance improvement | &bull; Ensure that multiple runs have occurred (cache warm-up).<br>&bull; Check if most modules are changing frequently.  |
   | Unexpected artifacts or missing changes | &bull; Review whether changes are outside Maven dependency tracking.<br>&bull; Use **Full Build** for verification. |

See [Add a non-production pipeline](#add-non-production-pipeline) the enable Smart Build.



<!-- 
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
-->

## The next steps {#the-next-steps}

After you configure the pipeline, you can deploy your code. See [Code Deployment](/help/using/code-deployment.md) for more details.

## Video tutorial {#video-tutorial}

This video provides an overview of the pipeline creation process, which is detailed in this document.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
