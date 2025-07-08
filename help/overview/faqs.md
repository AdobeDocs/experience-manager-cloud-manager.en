---
title: Cloud Manager FAQs
description: Learn about answers to the most frequently asked questions about Cloud Manager for AMS customers.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
---

# Cloud Manager FAQs {#cloud-manager-faqs}

This document provides answers to the most frequently asked questions about Cloud Manager for AMS customers.

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). -->

## My build fails with an error about maven-scr-plugin after switching from Java 8 to Java 11. What can I do? {#maven-src-plugin}

Your AEM Cloud Manager build may fail when attempting to switch the build from Java 8 to 11. If you encounter the following error, then you need to remove `maven-scr-plugin` and convert all OSGi annotations to OSGi R6 annotations.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

For instructions on how to remove this plug-in, [see here](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## My build fails with an error about RequireJavaVersion after switching from Java 8 to Java 11. What can I do? {#requirejavaversion}

For Cloud Manager builds, the `maven-enforcer-plugin` may fail with this error

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

This known issue is due to Cloud Manager using a different version of Java to run the Maven command versus compiling code. Omit `requireJavaVersion` from your `maven-enforcer-plugin` configurations.

## The code quality check failed and now deployment is stuck. Is there a way to bypass this check? {#deployment-stuck}

Yes. All code quality failures, except for security ratings, are non-critical metrics. As such, they can be bypassed as part of a deployment pipeline by expanding the items in the results UI.  

A user with the [Deployment Manager, Project Manager, or Business Owner](/help/requirements/users-and-roles.md#role-definitions) role can override the issues. In such a case, the pipeline proceeds. Or, they can accept the issues, in which case the pipeline stops with a failure.

See the documents [Three-Tier Gates while Running a Pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md#understanding-the-flow) for more details.

## Cloud Manager deployments fail at the performance test step in Adobe Managed Services environments. How can this issue be debugged to pass the critical metrics? {#debug-critical-metrics}

There is no single answer to this question. However, you may find the following points about the performance test step helpful:

* This step is a web performance step. That is, it is about the time to load the page using a web browser.
* The URLs listed in the result .csv file are loaded in a Chrome browser in the Cloud Manager infrastructure during the test.
* A common metric that fails is the error rate. So, for a URL to pass, the main URL must load with `200` status and in less than `20` seconds. If a page load exceeds `20` seconds, it is marked as a `504` error.
* If your site requires user authentication, see [Understand Your Test Results](/help/using/code-quality-testing.md#authenticated-performance-testing) for configuring the test so you can authenticate to your site.

See [Understanding Test Results](/help/using/code-quality-testing.md) for more information about quality checks.

## Can I use SNAPSHOT for the version of the Maven project? {#snapshot}

Yes. For developer deployments, the Git branch `pom.xml` files must contain `-SNAPSHOT` at the end of the `<version>` value.

Doing so lets subsequent deployments still be installed when the version did not change. In developer deployments, no automatic version is added or generated for the maven build.

You can also set the version to `-SNAPSHOT` for stage and production builds or deployments. Cloud Manager automatically sets a proper version number and creates a tag for you in Git. This tag can be referred to later, if required.

Further details about version handling are [documented here](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## How does package and bundle versioning work for staging and production deployments? {#staging-production}

In staging and production deployments, an automatic version is generated [as documented here](/help/managing-code/maven-project-version.md).

For custom versioning in stage and production deployments, set a proper three-part maven version like `1.0.0`. Increase the version each time you deploy to production.

Cloud Manager automatically adds its version to stage and production builds and creates a Git branch. No special configuration is required. If you do not set a maven version as described previously, the deployment still succeeds and a version is automatically set.

## My maven build fails for Cloud Manager deployments but it builds locally without errors. What is wrong? {#maven-build-fail}

See this [Git resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) for more details.

## I am unable to set a variable using an aio command. What can I do? {#set-variable} 

You may receive a 403 error such as the following when attempting to list or set pipeline variables via `aio` commands.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In this case, the user executing these commands needs to be added to the **Deployment Manager** role in the Admin Console.

See [API Permissions](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) for more details.
