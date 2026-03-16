---
title: Introduction to Cloud Manager for AMS
description: Start here to get to know Cloud Manager for Adobe Managed Services (AMS) and how it enables organizations to self-manage Adobe Experience Manager in the cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
---

# Introduction to [!UICONTROL Cloud Manager] for AMS {#introduction-to-cloud-manager}

Start here to get to know Cloud Manager for AMS (Adobe Managed Services) and how it enables organizations to self-manage Adobe Experience Manager in the cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introduction to Cloud Manager for AMS"
>abstract="Enables organizations to self-manage Adobe Experience Manager in the cloud. It includes a continuous integration and continuous delivery (CI/CD) framework that lets IT teams and implementation partners expedite the delivery of customizations or updates without compromising performance or security."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Create Programs"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Create Environments"

## Introduction {#introduction}

[!UICONTROL Cloud Manager] for Adobe Experience Manager gives developers the ability to create impactful customer experiences through streamlined workflows, built upon Adobe Experience Manager best practices. CI/CD pipelines optimized for Adobe Experience Manager let you merge development workflows easily by simply checking in your code, which can then move all the way to being production-ready. During the build phase, your custom code updates are thoroughly tested against best practices to deliver reliable applications for your customers. Cloud Manager uses an open API approach and enables you to integrate with your systems without disrupting existing processes and tools.
 
>[!NOTE]
>
>This documentation specifically describes the features and functions of Cloud Manager for Adobe Managed Services (AMS).
>
>The equivalent documentation for AEM as a Cloud Service can be found in the [AEM as a Cloud Service documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/home).
 
With Cloud Manager, your development team benefits from the following features:

* Continuous integration/continuous delivery (CI/CD) of code to reduce time to market from months/weeks to days/hours.
* Code inspection, performance testing, and security validation based on best practices before pushing to production to minimize production disruptions.
* API connectivity to complement existing DevOps processes.
* Autoscaling that intelligently detects the need for increased capacity and automatically brings online additional Dispatcher/publishing segments.

![CI/CD flow](/help/assets/screen_shot_2018-05-12at73843pm.png)The CI/CD process flow used in [!UICONTROL Cloud Manager]. 

## Key features in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

The following sections highlight key Cloud Manager features.

### Self-service interface {#self-service-interface}

To explore and get started with [!UICONTROL Cloud Manager]'s UI, see [First Time Login](/help/getting-started/first-time-login.md).

The user interface (UI) for [!UICONTROL Cloud Manager] lets you access and manage the cloud environment easily and the CI/CD pipeline easily for your Adobe Experience Manager applications.

You define application-specific key performance indicators (KPIs) like peak page views per minute or expected page load response time. These KPIs serve as the foundation for measuring deployment success. Roles and permissions for different team members can be easily defined. The self-service interface gives you full control. It also provides links to best practice resources and access to Adobe experts for guidance when needed.

### CI/CD pipeline {#ci-cd-pipeline}

One of the key capabilities of [!UICONTROL Cloud Manager] is the ability to exercise an optimized CI/CD pipeline to speed the delivery of custom code or updates such as adding new components on the website.

Through the [!UICONTROL Cloud Manager] UI, you can configure and kick off your CI/CD pipeline. As part of this pipeline, a thorough code scan is executed to ensure that only high-quality applications pass through to the production environment.

To learn more about configuring pipeline from [!UICONTROL Cloud Manager]'s UI, see [Configuring Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md).

### Flexible deployment modes {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offers flexible and configurable deployment modes so you can deliver experiences according to changing business demands.

With an automatic trigger mode, code is automatically deployed to an environment based on specific events such as code commit. You can also schedule code deployments during specified time frames, even outside business hours.

Independent of the deployment trigger, quality checks are always performed as part of the CI/CD pipeline execution every time a deployment is triggered. Quality checks include code inspection, security testing, and performance testing, all of which are delivered out-of-the-box with no effort required from you or your partners.

To learn more about deploying code and quality checks, see [Deploying Code](/help/using/code-deployment.md).

## Optional features in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager offers additional, advanced features, which may be beneficial for your project depending on your particular environment setup and needs. If these features are of interest to you, reach out to your Customer Success Engineer (CSE) or Adobe representative to discuss further.

### Autoscaling {#autoscaling}

When the production environment is subject to unusually high load, [!UICONTROL Cloud Manager] detects the need for additional capacity and automatically brings additional capacity online using its autoscaling feature.

In such an event, [!UICONTROL Cloud Manager] automatically triggers the autoscaling provisioning process, sends a notification of the autoscaling event, and brings additional capacity online within minutes. The additional capacity is provisioned in the production environment, in the same regions, and matching the same system specifications as the running Dispatcher/publishing nodes.

The autoscaling feature applies to the Dispatcher/publishing tier, using horizontal scaling to add one to ten segments of Dispatcher/publishing pairs. Any additional capacity provisioned is manually scaled-in within a period of ten business days as determined by the Adobe CSE (Customer Success Engineer). 

>[!NOTE]
>
>If you are interested in exploring whether autoscaling is appropriate for your application, contact your CSE or Adobe representative.

### Blue/Green deployments {#blue-green}

Blue/green deployment is a technique that reduces downtime and risk by running two identical production environments called blue and green.

At any time, only one of the environments is live, with the live environment serving all production traffic. In general, blue is the currently live environment and green is idle.

* Blue/green deployment is an add-on to Cloud Manager CI/CD pipelines in which a second set of publish and Dispatcher instances (green) is created and used for deployments. The green instances are then attached to the production load balancer and the old instances (blue) are removed and terminated.
* This implementation of blue/green treats instances as transient and every iteration of a blue/green pipeline creates a new set of publish and Dispatcher servers.
* A green load balancer is created as part of the setup. This load balancer never changes and is what you should point your green or "test" URL to.
* During a blue/green deployment, an exact replica of the existing Dispatcher/publishing tiers is created.

#### Blue/green deployment flow {#flow}

When blue/green deployment is enabled, the deployment flow differs from the standard Cloud Service deployment flow.

| Step | Blue/Green Deployment | Standard Deployment |
| --- | --- | --- |
| 1 | Deployment to author | Deployment to author |
| 2 | Pause for testing | - |
| 3 | Green infrastructure is created | - |
| 4 | Deployment to green Publish/Dispatcher tiers | Deployment to publisher |
| 5 | Pause for testing (up to 24 hours) | - |
| 6 | Green infrastructure is added to the production load balancer | - |
| 7 | Blue infrastructure is removed from the production load balancer | - |
| 8 | Pause for final sign-off (up to 24 hours) | - |
| 9 | Blue infrastructure is terminated automatically | - |
| 10 | Pipeline completes | - |

#### Implementing blue/green {#implementing}

All AMS users who are using Cloud Manager for production deployments are eligible to use the blue/green deployment. However, usage of blue/green deployment requires additional validation of your environments and setup by an Adobe CSE.

If you are interested in blue/green deployment, consider the following requirements and limitations and contact your CSE.

#### Requirements and limitations {#limitations}

* Blue/green is only available for Dispatcher/publisher pairs.
* Preview Dispatcher/publish pairs are not part of blue/green deployments.
* Every Dispatcher/publish pair is identical to every other Dispatcher/publisher pair.
* Blue/green is only available in the production environment.
* Blue/green is available in AWS and Azure.
* Blue/green is not available to Assets-only customers.
