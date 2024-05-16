---
title: Stage-Only and Prod-Only Pipelines
description: Learn how you can split staging and production deployments using dedicated pipelines.
---

# Stage-Only and Production-Only Pipelines {#stage-prod-only}

Learn how you can split staging and production deployments using dedicated pipelines.

>[!NOTE]
>
>This feature is only available to [the early adopter program.](/help/release-notes/current.md#early-adoption)

## Overview {#overview}

Staging and production environments are tightly coupled. By default, deployments to them are linked to a singular pipeline. That is a deployment pipeline deploys to both the staging and production environments in that program. While this coupling is normally suitable, there are certain use cases where disadvantages are present:

* If you wish to deploy to stage-only, you can only do this by rejecting the **Promote to Prod** step in the pipeline. However the execution will be marked as cancelled.
* If you wish to deploy the latest code in a staging environment to production, you need to redeploy the entire pipeline including the staging deployment even though no code was changed there. 
* Since environments can not be updated during deployments, if you want to pause and test in the staging environment for multiple days before promoting to production, the production environment can not be updated. This makes non-dependent tasks such as updating [environment variables](/help/getting-started/build-environment.md#environment-variables) impossible.

Stage-only and prod-only pipelines offer solutions to these use-cases by providing dedicated deployment options.

* **Stage-Only Deployment Pipelines** deploy only to a staging environment with the execution finishing once the deployment and tests are done.
  * A stage-only pipeline behaves identically to the standard coupled full stack prod pipeline but without the production deployment steps (approval, schedule, deploy).
* **Prod-Only Deployment Pipelines** deploy only to a production environment with the option to select an execution successfully finished and validated on stage and deploy its artifacts on prod.  
  * Prod-only pipelines will reuse the artifacts from the stage deployments, skipping the building phase.

Neither stage-only nor prod-only pipelines will be executed while a full-stack production pipeline is running and vice-versa.

These dedicated pipelines offer more flexibility, but please note the following details of operation and recommendations.

>[!NOTE]
>
>Prod-only pipelines will always use the artifacts from the stage-only pipeline, regardless of what may have been deployed on stage via the standard coupled production pipeline in the meantime.
>
>* This could lead to unwanted code rollbacks.
>* Adobe recommends to stop using the standard coupled production pipeline once you start using the prod-only and stage-only pipelines.
>* If you still decide to run both the standard coupled pipelines and stage/prod-only pipelines, keep in mind the reuse of artifacts to avoid code rollbacks.

## Pipeline Creation {#pipeline-creation}

Prod-only and stage-only pipelines are created in a similar fashion to the standard coupled [production pipelines](/help/using/production-pipelines.md) and [non-production pipelines.](/help/using/non-production-pipelines.md) Please see those documents for details.

1. In the **Pipelines** window, tap or click **Add Pipeline**.

   * Select **Add Non-Production Pipeline** to create a stage-only pipeline.
   * Select **Add Production Only Pipeline** to create a prod-only pipeline.

   ![Creating a prod/stage-only pipeline](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Certain options may be grayed out if the corresponding pipelines already exist.
>
>* **Add Production Only Pipeline** will be unavailable if a stage-only pipeline does not yet exist.
>* **Add Production Pipeline** will be unavailable if a standard coupled pipeline already exists.
>* Only one prod-only and one stage-only pipelines are allowed per program.

### Stage-Only Pipelines {#stage-only}

1. Once you select the **Add Non-Production Pipeline** option, the **Add Non-Production Pipeline** dialog opens.
1. To create a stage-only pipeline, select the stage environment in the **Eligible Deployment Environments** field for your pipeline. Complete the remaining fields and tap or click **Continue**.

   ![Creating a stage-only pipeline](/help/assets/configure-pipelines/stage-only.png)

1. On the **Stage Testing** tab, you can then define testing that should be performed on the staging environment. Tap or click **Save** to save your new pipeline.

   ![Test parameters for a stage-only pipeline](/help/assets/configure-pipelines/stage-only-test.png)

### Prod-Only Pipelines {#prod-only}

1. Once you select the **Add Production Only Pipeline** option, the **Add Production Only Pipeline** dialog opens.
1. Provide a **Pipeline Name**. The remaining options and functionality of the dialog work the same as those in the standard coupled pipeline creation dialog. Tap or click **Save** to save the pipeline.

   ![Creating a production-only pipeline](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Running Prod-Only and Stage-Only Pipelines {#running}

Prod-only and stage-only pipelines are run in the same way as [all other pipelines are run.](/help/using/managing-pipelines.md#running-pipelines) Please see that documentation for details.

In addition, a prod-only pipeline run can be triggered directly from the execution details of a stage-only pipeline.

### Stage-Only Pipelines {#stage-only-run}

A stage-only pipeline runs in nearly the same way as standard coupled pipelines. However at the end of the run, after the testing steps, a **Promote Build** button allows you to start a prod-only pipeline execution that uses the artifacts deployed on stage by this execution and deploys them on production.

![Stage-only pipeline run](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

The **Promote Build** button only appears if you are on the latest successful stage-only pipeline execution. Once tapped or clicked, it will ask you to confirm the run of the prod-only pipeline or to create a prod-only pipeline if one does not already exist.

### Prod-Only Pipelines {#prod-only-run}

For prod-only pipelines it is important to identify the source artifacts that are to be deployed to production. These details can be found in the **Artifact Preparation** step. You can navigate to those executions for further details and logs.

![Artifact details](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
