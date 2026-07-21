---
title: CI/CD Pipelines
description: Learn about CI/CD pipelines and how they handle deployments to staging and production environments in Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
    internal-label: Environments
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
    internal-label: Implementation
subfeature_v2:
  - id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
    internal-label: CI/CD Pipelines
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
---
# CI/CD pipelines {#ci-cd-pipeline}

Learn about CI/CD pipelines and how they handle deployments to staging and production environments in Cloud Manager.

## Overview {#overview}

[!UICONTROL Cloud Manager] includes a continuous integration/continuous delivery (CI/CD) framework, which allows implementation teams to test quickly and deliver new or updated code. Implementation teams can set up, configure, and start an automated CI/CD pipeline. This pipeline follows Adobe coding best practices to perform a comprehensive code scan and ensure the highest code quality.

The CI/CD pipeline also automates unit and performance testing processes to increase deployment efficiency and proactively identify critical issues that are expensive to fix after deployment. Implementation teams can access a comprehensive code performance report to gain visibility into potential impact on KPIs and critical security validations if the code gets deployed to production.

## About the pipeline process {#pipeline-process}

The following diagram illustrates what happens when a release is triggered in [!UICONTROL Cloud Manager] using a pipeline.

![The pipeline process](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipeline Step | Description |
| --- | --- |
| 1. Start a release | A deployment manager triggers a release either manually, with a Git commit, or based on a recurring schedule. |
| 2. Create a release tag | [!UICONTROL Cloud Manager] creates a Git tag to mark the release using an automatically generated version number, for example, `2018.531.245527.0000001222`. |
| 3. Built as release with auto-generated version | [!UICONTROL Cloud Manager] builds the application with the newly assigned version number.  |
| 4. Evaluate code quality | [!UICONTROL Cloud Manager] scans the source code and provides a summary before the code can be deployed to the staging environment. |
| 5. Versioned artifacts stored | The release artifacts are stored for later usage in the deployment steps. |
| 6. Automatic deployment of artifacts to AMS AEM staging | The release artifact is deployed to the staging environment. |
| 7. Trigger automated tests | [!UICONTROL Cloud Manager] runs performance and security tests on the artifact. |
| 8. Production trigger deployment | After the automated tests are complete, [!UICONTROL Cloud Manager] starts the deployment to production. |
| 9. [!UICONTROL Cloud Manager] gets artifacts(s) to deploy | [!UICONTROL Cloud Manager] pulls the stored release artifacts. |
| 10. Deploy artifacts to production | The release artifacts are deployed to the production environment. |

### Code sources {#code-sources}

Pipelines can also differ by the type of code they deploy, besides production and non-production.

* **[Full stack pipelines](#full-stack-pipeline)** - Deploy the complete AEM application code along with HTTPD/Dispatcher configurations.
* **[Web tier config pipelines](#web-tier-config-pipelines)** - Deploy HTTPD/Dispatcher configurations only.

### Full stack pipelines {#full-stack-pipeline}

Full-stack pipelines deploy the complete AEM application code to the AEM runtime, and by default, also deploy web tier configurations.

The following restrictions apply.

* A user must be logged in with the **Deployment Manager** role to configure or run pipelines.
* At any time, there can only be one full-stack pipeline per environment.

The following describes how the full-stack pipeline interacts with a [web tier config pipeline](#web-tier-config-pipelines).

* The full-stack pipeline for an environment ignores the Dispatcher configuration if the corresponding web tier config pipeline exists.
* If the corresponding web tier config pipeline for the environment does not exist, the user can include or ignore the Dispatcher configuration when configuring the full-stack pipeline.

Full-stack pipelines can be code quality pipelines or deployment.

#### Configure full-stack pipelines {#configure-full-stack}

See [Add a production pipeline](/help/using/production-pipelines.md#full-stack-code).
See [Add a non-production pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Web tier config pipelines {#web-tier-config-pipelines}

Web tier config pipelines allow exclusive deployment of HTTPD/Dispatcher configuration to the AEM runtime, decoupling it from other code changes. It is a streamlined pipeline that provides users who want to deploy only Dispatcher configuration changes an efficient means to do so quickly.

>[!TIP]
>
>Web tier config pipelines let you store your web config in the same or a different source location as the full stack pipeline, depending on what best suits your project structure.

The following restrictions apply.

* A user must be logged in with the **Deployment Manager** role to configure or run pipelines.
* At any time, there can only be one web tier config pipeline per environment.
* The user cannot configure a web tier config pipeline when its corresponding full-stack pipeline is running.

The following describes how the web tier config pipeline interacts with the [full stack pipeline](#full-stack-pipeline).

* If a web tier config pipeline is not set up for an environment, the user can choose to include or ignore the Dispatcher configuration while configuring the full-stack pipeline.
* Once a web tier config pipeline is configured for an environment, its corresponding full-stack pipeline (if one exists) ignores the Dispatcher configuration during execution and deployment.
* After a web tier config pipeline is deleted, its corresponding full-stack pipeline (if one exists) is reset to deploy Dispatcher configurations during its execution.

>[!NOTE]
>
>For AMS programs with blue-green deployment enabled, web tier updates use rolling deployment by default. Use a full stack pipeline if you need blue-green deployment for web tier changes.

#### Configure web tier pipelines {#configure-web-tier}

See [Add a production pipeline](/help/using/production-pipelines.md#web-tier-config).
See [Add a non-production pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Faster builds using Smart Build {#use=smart-build}

Cloud Manager now uses an optimized build strategy called **Smart Build**, which uses module-level caching to accelerate the build process. During each build, only modules that have changed are rebuilt, while unchanged modules are reused from the cache.

Smart Build is available for Code Quality and Full Stack deployment pipelines (Development, Stage, Production).

See [Add a non-production pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline) and [About using Smart Build in a non-production pipeline](/help/using/non-production-pipelines.md#about-smart-build).


### How to set up a CI/CD pipeline {#how-to-setup-a-ci-cd-pipeline}

To learn more about pipeline configuration, see the documents [Configuring Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md).

## Quality gates {#quality-gates}

The CI/CD pipeline provides quality gates, or acceptance criteria, which must be met before the code can be moved from the staging environment to the deployment environment. There are three gates in the pipeline:

* Code Quality
* Performance Testing
* Security Testing

For each of these gates, there are three levels of issues that can be identified:

* **Critical** - Critical issues identified by the gate cause an immediate failure of the pipeline.
* **Important** - Important issues identified by the gate cause the pipeline to enter a paused state. A deployment manager, project manager, or business lead can override the issues, allowing the pipeline to proceed. Alternatively, they can accept the issues, causing the pipeline to stop with a failure.
* **Information** - Information issues identified by the gate are provided purely for informational purposes and have no impact on the pipeline execution.

The following is an example of a code scan with issues identified.

![Code scan example](/help/assets/quality-gate-failed.png) 

### How to set up gates {#how-to-setup-gates}

See the document [Configuring Production Pipelines](/help/using/production-pipelines.md) for details on setting up your code, quality, and performance gates.
