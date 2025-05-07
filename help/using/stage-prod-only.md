---
title: Stage-Only and Prod-Only Pipelines
description: Learn how you can split staging and production deployments using dedicated pipelines.
badge: label="Early Adopter" type="Positive" url="/help/release-notes/current.md#staging-production-only-pipelines"
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
---
# Stage-only and production-only pipelines {#stage-prod-only}

Learn how you can split staging and production deployments using dedicated pipelines.

>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/release-notes/current.md#staging-production-only-pipelines).

## Overview {#overview}

Staging and production environments are tightly coupled. By default, deployments to them are linked to a singular pipeline. That is, a deployment pipeline deploys to both the staging and production environments in that program. While this coupling is normally suitable, there are certain use cases where disadvantages are present:

* If you want to deploy to stage-only, you reject the **Promote to Prod** step in the pipeline. However, the execution becomes marked as canceled.
* If you want to deploy the latest code in a staging environment to production, you need to redeploy the entire pipeline including the staging deployment even though no code was changed there.
* Environments cannot be updated during deployments. If you pause to test in the staging environment for several days before promoting to production, the production environment remains locked and cannot be updated. This scenario makes non-dependent tasks such as updating [environment variables](/help/getting-started/build-environment.md#environment-variables) impossible.

Stage-only and prod-only pipelines offer solutions to these use-cases by providing dedicated deployment options.

* **Stage-Only Deployment Pipelines:** Deploys only to a staging environment with the execution finishing once the deployment and tests are done. A stage-only pipeline behaves identically to the standard coupled full stack prod pipeline but without the production deployment steps (approval, schedule, deploy).
* **Production-Only Deployment Pipelines:** Deploys only to production by selecting the most recent successful stage execution. Then deploying its artifacts to production. Prod-only pipelines reuse stage deployment artifacts, bypassing the build phase.

Stage-only and prod-only pipelines are not executed while a full-stack production pipeline is in progress, and vice versa. If both the stage-only and the full-stack production pipeline have the **On Git Changes** trigger configured and are pointing to the same branch and repository, only the stage-only pipeline is automatically started. Prod-only pipelines do not start **`On Git Changes`** because they are not directly linked to a repository.

Prod-only pipelines are triggered manually, as they are not directly linked to a repository for **On Git Changes**.

These dedicated pipelines offer more flexibility, but you should note the following details of operation and recommendations.

>[!NOTE]
>
>Prod-only pipelines always use artifacts from the stage-only pipeline. This process remains true even if the standard coupled production pipeline has deployed something else to stage in the meantime.
>
>* Such as scenario could lead to unwanted code rollbacks.
>* Adobe recommends to stop using the standard coupled production pipeline once you start using the prod-only and stage-only pipelines.
>* If you still decide to run both the standard coupled pipelines and stage/prod-only pipelines, keep in mind the reuse of artifacts to avoid code rollbacks.

## Pipeline creation {#pipeline-creation}

Prod-only and stage-only pipelines are created in a similar fashion to the standard coupled [production pipelines](/help/using/production-pipelines.md) and [non-production pipelines](/help/using/non-production-pipelines.md). See those documents for details.

1. In the **Pipelines** window, click **Add Pipeline**.

   * Select **Add Non-Production Pipeline** to create a stage-only pipeline.
   * Select **Add Production Only Pipeline** to create a prod-only pipeline.

   ![Creating a prod/stage-only pipeline](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Certain options may be grayed out if the corresponding pipelines already exist.
>
>* **Add Production Only Pipeline** is unavailable if a stage-only pipeline does not yet exist.
>* **Add Production Pipeline** is unavailable if a standard coupled pipeline already exists.
>* Only one prod-only and one stage-only pipelines are allowed per program.

### Stage-only pipelines {#stage-only}

1. After you select the **Add Non-Production Pipeline** option, the **Add Non-Production Pipeline** dialog box opens.
1. To create a stage-only pipeline, select the stage environment in the **Eligible Deployment Environments** field for your pipeline.
1. Complete the remaining fields.
1. Click **Continue**.

   ![Creating a stage-only pipeline](/help/assets/configure-pipelines/stage-only.png)

1. On the **Stage Testing** tab, define the testing to perform in the staging environment. 
1. Click **Save**.

   ![Test parameters for a stage-only pipeline](/help/assets/configure-pipelines/stage-only-test.png)

### Prod-only pipelines {#prod-only}

1. After you select the **Add Production Only Pipeline** option, the **Add Production Only Pipeline** dialog box opens.
1. In the **Pipeline Name** field, type the name you want. The remaining options and functionality of the dialog box work the same as those options found in the standard coupled pipeline creation dialog box. 
1. In the lower-right corner of the dialog box, click **Save**.

   ![Creating a production-only pipeline](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Run prod-only and stage-only pipelines {#running}

Prod-only and stage-only pipelines are run in largely the same way as [all other pipelines are run](/help/using/managing-pipelines.md#running-pipelines). See that documentation for details. However, there are two new features of these pipelines.

* Stage-only and prod-only pipelines offer a new [emergency mode](#emergency-mode) to skip testing.
* Prod-only pipeline run can be triggered directly from the execution details of a [stage-only pipeline](#stage-only-run).

### Emergency Mode {#emergency-mode}

When starting production-only and staging-online pipelines, you are prompted to confirm the start and how it starts.

* **Normal Mode** is a standard run and includes stage testing steps.
* **Emergency Mode** skips stage testing steps.

![Emergency Mode](/help/assets/configure-pipelines/emergency-mode.png)

### Stage-only pipelines {#stage-only-run}

A stage-only pipeline runs in nearly the same way as standard coupled pipelines. However, at the end of the run, after the testing steps, a **Promote Build** button appears. This button lets you start a prod-only pipeline execution using the artifacts that were deployed on stage in the run and deploy them to production.

![Stage-only pipeline run](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Clicking **Promote Build** prompts you to confirm the run of the related stage-only pipeline either normally or in [emergency mode](#emergency-mode).

If a prod-only pipeline does not exist, you are prompted to create one.

### Prod-only pipelines {#prod-only-run}

For prod-only pipelines, be sure you identify the source artifacts that you want deployed to production. These details are found in the **Artifact Preparation** step. You can navigate to those executions for more details and logs.

![Artifact details](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

