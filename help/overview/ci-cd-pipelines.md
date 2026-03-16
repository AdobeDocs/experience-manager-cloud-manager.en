---
title: CI/CD Pipelines
description: Learn about CI/CD pipelines and how they handle deployments to staging and production environments in Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
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

### How to set up a CI/CD pipeline {#how-to-setup-a-ci-cd-pipeline}

To learn more about pipeline configuration, see the documents [Configuring Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md).

## Quality gates {#quality-gates}

The CI/CD pipeline provides quality gates, or acceptance criteria, which must be met before the code can be moved from the staging environment to the deployment environment. There are three gates in the pipeline:

* Code Quality
* Performance Testing
* Security Testing

For each of these gates, there are three levels of issues that can be identified:

* **Critical** - Critical issues identified by the gate cause an immediate failure of the pipeline.
* **Important** - Important issues identified by the gate cause the pipeline to enter a paused state. A deployment manager, project manager, or business owner can override the issues, allowing the pipeline to proceed. Alternatively, they can accept the issues, causing the pipeline to stop with a failure.
* **Information** - Information issues identified by the gate are provided purely for informational purposes and have no impact on the pipeline execution.

The following is an example of a code scan with issues identified.

![Code scan example](/help/assets/quality-gate-failed.png) 

### How to set up gates {#how-to-setup-gates}

See the document [Configuring Production Pipelines](/help/using/production-pipelines.md) for details on setting up your code, quality, and performance gates.
