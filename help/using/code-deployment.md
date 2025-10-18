---
title: Code Deployment
description: Learn how to deploy your code and what happens in Cloud Manager when you do.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
---

# Code deployment {#code-deployment}

Learn how to deploy your code and what happens in Cloud Manager when you do.

## Deploy code with Cloud Manager {#deploying-code-with-cloud-manager}

Once you have configured your production pipeline, including the necessary repository and environments, you are ready to deploy your code.

1. Click **Deploy** from the Cloud Manager to start the deployment process.

   ![Deploy button](/help/assets/Deploy1.png)

1. The **Pipeline Execution** screen displays. Click **Build** to start the process.

   ![Build button](/help/assets/Deploy2.png)

The build process starts the code deployment process including the following steps:

* Stage deployment
* Stage testing
* Production deployment

You can review the steps from various deployment processes by viewing logs, or reviewing results for the testing criteria.

## Deployment steps {#deployment-steps}

A number of actions occur during each step of the deployment, which is described in this section. See [Deployment Process Details](#deployment-process) for technical details of how the code itself is deployed behind-the-scenes.

### Stage deployment step {#stage-deployment}

The **Stage deployment** step includes the following actions:

* **Validation**: This step ensures that the pipeline is configured to use the currently available resources. For example, that the configured branch exists and that the environments are available.
* **Build &amp; Unit Testing**: This step runs a containerized build process. See [The Build Environment](/help/getting-started/build-environment.md) for details.
* **Code Scanning**: This step evaluates the quality of your application code. See [Understanding Test Results](/help/using/code-quality-testing.md) for details on the testing process.
* **Deploy to Stage**

![Stage deployment](/help/assets/Stage_Deployment1.png)

### Stage testing step {#stage-testing}

The **Stage testing** step includes the following actions:

* **Security Testing**: This step evaluates the security impact of your code on the AEM environment. See the document [Understanding Test Results](/help/using/code-quality-testing.md) for details on the testing process.
    * **Performance Testing**: This step evaluates the performance of your code. See [Understanding Test Results](/help/using/code-quality-testing.md) for details on the testing process.

### Production deployment step {#production-deployment}

The **Production Deployment** step includes the following actions:

* **Application for Approval**
  * This option is enabled while configuring the pipeline.
  * Using this option, you can either schedule your production deployment or click **Now** to execute the production deployment immediately.
* **Schedule Production Deployment**
  * This option is enabled while configuring the pipeline.
  * The scheduled date and time are specified in terms of the user's timezone.
    ![Schedule deployment](/help/assets/Production_Deployment1.png)
* **CSE Support** (if enabled)
* **Deploy to Production**

![Production deployment](/help/assets/Prod_Deployment1.png)

Once your deployment is complete, your code is in its targeted environment and you can view the logs.

![Deployment complete](/help/assets/Production_Deployment2.png)

## Timeouts {#timeouts}

The following steps time out if left waiting for user feedback:

|Step|Timeout|
|--- |--- |
|Code Quality Testing|7 days|
|Security Testing|7 days|
|Performance Testing|7 days|
|Application for Approval (stage)|7 days|
|Application for Approval (production)|14 days|
|Schedule Production Deployment|14 days|
|Managed Production Deployment|14 days|

## Deployment process details {#deployment-process}

Cloud Manager uploads all target/*.zip files produced by the build process to a storage location. These artifacts are retrieved from this location during the deploy phases of the pipeline.

When Cloud Manager deploys to non-production topologies, the goal is to complete the deployment as quickly as possible and therefore the artifacts are deployed to all nodes simultaneously as follows:

1. Cloud Manager determines whether each artifact is an AEM or Dispatcher package.
1. Cloud Manager removes all dispatchers from the load balancer to isolate the environment during the deployment.

   * Unless configured otherwise, you can skip load balancer changes in development and staging Deployments. That is, for the development environment, detach and attach steps in both non-production pipelines, and for staging environment the production pipeline.

   ![Skip load balancer](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >It is expected that 1-1-1 customers are going to use this feature.

1. Each AEM artifact is deployed to each AEM instance via Package Manager APIs, with package dependencies determining the deployment order.

   * To learn more about how you can use packages to install new functionality, transfer content between instances, and back up repository content. See [Package Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

   >[!NOTE]
   >
   >All AEM artifacts are deployed to both the author and the publishers. Run modes should be leveraged when node-specific configurations are required. To learn more about how the run-modes allow you to tune your AEM instance for a specific purpose, See the [Run Modes section of the document Deploying to AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes).

1. The Dispatcher artifact is deployed to each Dispatcher as follows:

   1. Current configurations are backed up and copied to a temporary location.
   1. All configurations are deleted except the immutable files. See [Dispatcher Configurations](/help/getting-started/dispatcher-configurations.md) for more details. This approach clears the directories to ensure that no orphaned files are left behind.
   1. The artifact is extracted to the `httpd` directory. Immutable files are not overwritten. Any changes you make to immutable files in your Git repository are ignored at the time of deployment. These files are core to the AMS Dispatcher framework and cannot be changed.
   1. Apache performs a configuration test. If no errors are found, the service is reloaded. If errors are found, configurations are restored from backup, the service is reloaded, and the error is reported back to Cloud Manager.
   1. Each path specified in the pipeline configuration is invalidated or flushed from the Dispatcher cache.
   
   >[!NOTE]
   >
   >Cloud Manager expects the Dispatcher artifact to contain the full file set. All Dispatcher configuration files must be present in the Git repository. Missing files or folders result in deployment failure.

1. Following the successful deployment of all AEM and Dispatcher packages to all nodes, the dispatchers are added back to the load balancer and the deployment is complete.

   >[!NOTE]
   >
   >You can skip load balancer changes in development and staging Deployments. That is, for development environment, detach, and attach steps in both non-production pipelines, and for staging environment the production pipeline.

### Deployment to production phase {#deployment-production-phase}

The process for deploying to production topologies differs slightly to minimize impact to AEM site visitors. 

Production deployments generally follow the same steps as above, but in a rolling manner:

1. Deploy AEM packages to author.
1. Detach dispatcher1 from the load balancer.
1. Deploy AEM packages to publish1 and the Dispatcher package to dispatcher1 in parallel, flush Dispatcher cache.
1. Put dispatcher1 back into the load balancer.
1. Once dispatcher1 is back in service, detach dispatcher2 from the load balancer.
1. Deploy AEM packages to publish2 and the Dispatcher package to dispatcher2 in parallel, flush Dispatcher cache.
1. Put dispatcher2 back into the load balancer.

This process continues until the deployment has reached all publishers and dispatchers in the topology.

## Emergency pipeline execution mode {#emergency-pipeline}

In critical situations, Adobe Managed Services customers might need to deploy code changes to their stage and production environments immediately. This ability lets them bypass the full Cloud Manager test cycle.

To address these situations, the Cloud Manager production pipeline may be executed in an emergency mode. When this mode is used, the security and performance test steps are not executed. All other steps, including any configured approval steps, are executed as in the normal pipeline execution mode. 

>[!NOTE]
>
>The emergency pipeline execution mode feature is activated on a program-by-program basis. The activation is done by Customer Success Engineers.

### Use emergency pipeline execution mode {#using-emergency-pipeline}

When you start a production pipeline execution, you can choose between normal or emergency mode from a dialog box. This option is available if the emergency pipeline execution mode feature is activated for the program. This choice is available once the feature is enabled.

![Run pipeline options](/help/assets/execution-emergency1.png)

When viewing the pipeline execution details page for an execution run in emergency mode, the breadcrumbs at the top of the screen show an indicator that the pipeline is executing in emergency mode.

![Emergency mode breadcrumbs](/help/assets/execution-emergency2.png)

Executing a pipeline in emergency mode can also be done through the Cloud Manager API or CLI. To start an execution in emergency mode, submit a `PUT` request to the pipeline's execution endpoint with the query parameter `?pipelineExecutionMode=EMERGENCY` or, when using the CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Re-executing a production deployment {#reexecute-deployment}

In rare cases, production deployment steps may fail for transient reasons. In these cases, you can re-execute the production deployment step as long as it was completed, regardless of whether it was successful, canceled, or unsuccessful. Re-execution is supported by using the same pipeline that consists of the following three steps: 

1. **The validate step** - The same validation that occurs during a normal pipeline execution.
1. **The build step** - In the context of a re-execution, the build step copies artifacts and does not actually execute a new build process.
1. **The production deployment step** - Uses the same configuration and options as the production deployment step in a normal pipeline execution.

In such circumstances where a re-execution is possible, the production pipeline status page provides the **Re-execute** option next to the usual **Download build log** option.

![The Re-execute option in the pipeline overview window](/help/assets/re-execute.png)

>[!NOTE]
>
>In a re-execution, the build step is labeled in the UI to reflect that it is copying artifacts, not re-building.

### Limitations {#limitations}

* Re-executing the production deployment step is only available for the last execution.
* Re-execution is not available for rollback executions or "push update" executions.
* If the last execution failed at any point prior to the production deployment step, re-execution is not possible.


### Re-execute API {#reexecute-api}

In addition to being available in the UI, you can use [the Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) to trigger re-executions and identify executions that were triggered as re-executions.

#### Trigger a re-execution {#triggering}

To trigger a re-execution, a `PUT` request needs to be made to the HAL Link `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` on the production deploy step state.

* If this link is present, the execution can be restarted from that step.
* If it is absent, the execution cannot be restarted from that step.

This link is only ever available for the production deploy step.

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

The syntax of the HAL link's `href` value is only an example and the actual value should always be read from the HAL link and not generated.

Submitting a `PUT` request to this endpoint results in a `201` response if successful. The response body is the representation of the new execution. This functionality is similar to starting a regular execution through the API.

#### Identify a re-executed execution {#identifying}

The system identifies re-executed executions by the value `RE_EXECUTE` in the trigger field.