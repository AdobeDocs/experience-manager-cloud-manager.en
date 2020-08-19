---
title: Understand your Test Results
seo-title: Understand your Test Results
description: null
seo-description: Follow this page to learn about three tier gates while running a pipeline, code scanning, performance, and security tests validating your program in Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4

---

# Understand your Test Results {#understand-your-test-results}

During the **Pipeline** process, a number of metrics are captured and compared to either the Key Performance Indicators (KPIs) defined by the business owner, or standards set by Adobe Managed Services.

These are reported using the three-tier gating system as defined in this section.

## Three-Tier Gates while Running a Pipeline  {#three-tier-gates-while-running-a-pipeline}

There are three gates in the pipeline:

* Code Quality
* Performance Testing
* Security Testing

For each of these gates, there is a three-tier structure for issues identified by the gate.

* **Critical** - These are issues identified by the gate which cause an immediate failure of the pipeline.
* **Important** - These are issues identified by the gate which cause the pipeline to enter a paused state. A deployment manager, project manager, or business owner can either override the issues, in which case the pipeline proceeds, or they can accept the issues, in which case the pipeline stops with a failure.
* **Info** - These are issues identified by the gate which are provided purely for informational purposes and have no impact on the pipeline execution.

>[!NOTE]
>
>In a Code Quality Only Pipeline, Important failures in the Code Quality Testing gate cannot be overridden since the Code Quality Testing step is the final step in the pipeline.

## Code Quality Testing {#code-quality-testing}

This step evaluates the quality of your application code. It is the core objective of a Code-Quality only pipeline  and is executed immediately following the build step in all non-production and production pipelines. Refer to [Configuring your CI-CD Pipeline](/help/using/configuring-pipeline.md) to learn more about different types of pipelines.

### Understanding Code Quality Testing {#understanding-code-quality-testing}

In Code Quality Testing, the source code is scanned to ensure that it deployments meets certain quality criteria. Currently, this is implemented by a combination of SonarQube and content package-level examination using OakPAL. There are over 100 rules combining generic Java rules and AEM-specific rules. Some of the AEM-specific rules are created based on best practices from AEM Engineering and are referred to as [Custom Code Quality Rules](/help/using/custom-code-quality-rules.md).

You can download the list of rules [here](/help/using/assets/CodeQuality-rules-latest.xlsx).

The results of this step is delivered as *Rating*. The table below summarizes the ratings for various test criteria:

|Name|Definition|Category|Failure Threshold|
|--- |--- |--- |--- |
|Security Rating|A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability|Critical|&lt; B|
|Reliability Rating|A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug<br/>E = at least 1 Blocker Bug|Important|&lt; C|
|Maintainability Rating|Outstanding remediation cost for code smells is: <br/><ul><li>&lt;=5% of the time that has already gone into the application, the rating is A </li><li>between 6 to 10% the rating is a B </li><li>between 11 to 20% the rating is a C </li><li>between 21 to 50% the rating is a D</li><li>anything over 50% is an E</li></ul>|Important|&lt; A|
|Coverage|A mix of unit test line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to 'true' at least once while running unit tests <br/>CF = conditions that have been evaluated to 'false' at least once while running unit tests <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover)|Important|&lt; 50%|
|Skipped Unit Tests|Number of skipped unit tests.|Info|> 1|
|Open Issues|Overall issue types - Vulnerabilities, Bugs, and Code Smells|Info|&gt; 0|
|Duplicated Lines|Number of lines involved in duplicated blocks. <br/>For a block of code to be considered as duplicated: <br/><ul><li>**Non-Java projects:**</li><li>There should be at least 100 successive and duplicated tokens.</li><li>Those tokens should be spread at least on: </li><li>30 lines of code for COBOL </li><li>20 lines of code for ABAP </li><li>10 lines of code for other languages</li><li>**Java projects:**</li><li> There should be at least 10 successive and duplicated statements whatever the number of tokens and lines.</li></ul> <br/>Differences in indentation as well as in string literals are ignored while detecting duplications.|Info|&gt; 1%|
|Cloud Service Compatibility|Number of identified Cloud Service Compatibility issues.|Info|> 0|


>[!NOTE]
>
>Refer to [Metric Definitions](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) for more detailed definitions.

>[!NOTE]
>
>To learn more about the custom code quality rules executed by [!UICONTROL Cloud Manager], please refer to [Custom Code Quality Rules](custom-code-quality-rules.md).

### Dealing with False Positives {#dealing-with-false-positives}

The quality scanning process is not perfect and will sometimes incorrectly identify issues which are not actually problematic. This is referred to as a "false positive".

In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. For example, one common problem is that the SonarQube rule to detect hardcoded passwords can be aggressive about how a hardcoded password is identified.

To look at a specific example, this code would be fairly common in an AEM project which has code to connect to some external service:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube will then raise a Blocker Vulnerability. After reviewing the code, you identify that this is not a vulnerability and can annotate this with the appropriate rule id.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

However, on the other hand, if the code was actually this:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Then the correct solution is to remove the hardcoded password.

>[!NOTE]
>
>While it is a best practice to make the `@SuppressWarnings` annotation as specific as possible, i.e. annotate only the specific statement or block causing the issue, it is possible to annotate at a class level.

## Security Testing {#security-testing}

[!UICONTROL Cloud Manager] runs the existing ***AEM Security Heath Checks*** on stage following the deployment and reports the status through the UI. The results are aggregated from all AEM instances in the environment.

If any of the **Instances** report a failure for a given health check, the entire **Environment** fails that health check. As with Code Quality and Performance Testing, these health checks are organized into categories and reported using the three-tier gating system. The only distinction is that there is no threshold in the case of security testing. All the health checks are simply pass or fail.

The following table lists the current checks:

| **Name** | **Health Check Implementation** |**Category** |
|---|---|---|
| Deserialization firewall Attach API Readiness is in an acceptable state | Deserialization Firewall Attach API Readiness |Critical |
| Deserialization firewall is functional | Deserialization Firewall Functional |Critical |
| Deserialization firewall is loaded | Deserialization Firewall Loaded |Critical |
| AuthorizableNodeName implementation does not expose authorizable ID in the node name/path. | Authorizable Node Name Generation |Critical |
| Default passwords have been changed | Default Login Accounts |Critical |
| Sling default GET servlet is protected from DOS attacks. | Sling Get Servlet |Critical |
| The Sling Java Script Handler is configured appropriately | Sling Java Script Handler |Critical |
| The Sling JSP Script Handler is configured appropriately | Sling JSP Script Handler |Critical |
| SSL is configured correctly | SSL Configuration |Critical |
| No obviously insecure user profile policies found | User Profile Default Access |Critical |
| The Sling Referrer Filter is configured in order to prevent CSRF attacks | Sling Referrer Filter |Important |
| The Adobe Granite HTML Library Manager is configured appropriately | CQ HTML Library Manager Config |Important |
| CRXDE Support bundle is disabled | CRXDE Support |Important |
| Sling DavEx bundle and servlet are disabled | DavEx Health Check |Important |
| Sample content is not installed | Example Content Packages |Important |
| Both the WCM Request Filter and the WCM Debug Filter are disabled | WCM Filters Configuration |Important |
| Sling WebDAV bundle and servlet are configured appropriately | WebDAV Health Check |Important |
| The web server is configured to prevent clickjacking | Web Server Configuration |Important |
| Replication is not using the 'admin' user | Replication and Transport Users |Info |

## Performance Testing {#performance-testing}

*Performance testing* in [!UICONTROL Cloud Manager] is implemented using a 30 minute test.

During pipeline setup, the deployment manager can decide how much traffic to direct to each bucket.

You can learn more about bucket controls, from [Configure your CI/CD Pipeline](configuring-pipeline.md).

>[!NOTE]
>
>To setup your program and define your KPIs, see [Setup your Program](setting-up-program.md).

The following table summarizes the performance test matrix using the three-tier gating system:

| **Metric** |**Category** |**Failure Threshold** |
|---|---|---|
| Page Request Error Rate % |Critical |>= 2% |
| CPU Utilization Rate |Critical |>= 80% |
| Disk IO Wait Time |Critical |>= 50% |
| 95 Percentile Response Time |Important |>= Program-level KPI |
| Peak Response Time |Important |>= 18 seconds |
| Page Views Per Minute |Important |< Program-level KPI |
| Disk Bandwidth Utilization |Important |>= 90% |
| Network Bandwidth Utilization |Important |>= 90% |
| Requests Per Minute |Info |< 6000 |

### Performance Testing Results Graphs {#performance-testing-results-graphs}

New graphs and download options have been added to the Performance Test Results dialog.

When you open the Performance Test dialog, the metric panels can be expanded to display a graph, provide a link to a download, or both.

For [!UICONTROL Cloud Manager] Release 2018.7.0, this functionality is available for the following metrics:

* **CPU Utilization**
  * A graph of CPU Utilization during the test period.

* **Disk I/O Wait Time**
  * A graph of Disk I/O Wait Time during the test period.

* **Page Error Rate**
  * A graph of page errors per minute during the test period.
  * A CSV file listing pages which have produced an error during the test.

* **Disk Bandwidth Utilization**
  * A graph of Disk Bandwidth Utilization during the test period.

* **Network Bandwidth Utilization**
  * A graph of Network Bandwidth Utilization during the test period.

* **Peak Response Time**
  * A graph of peak response time per minute during the test period.

* **95th Percentile Response Time**
  * A graph of 95th percentile response time per minute during the test period.
  * A CSV file listing pages whose 95th percentile response time has exceeded the defined KPI.

The following images display the performance test graphs:

![](assets/understand_test-results-screen1.png)  

![](assets/screen_shot_2018-09-05at83933pm.png)

