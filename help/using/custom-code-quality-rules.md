---
title: Custom Code Quality Rules
description: Discover the specifics of the custom code quality rules executed by Cloud Manager during code quality testing. These rules are grounded in best practices from AEM Engineering.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
---

# Custom code quality rules {#custom-code-quality-rules}

Learn details about the custom code quality rules executed by Cloud Manager as part of [code quality testing](/help/using/code-quality-testing.md), based on best practices from AEM Engineering.

>[!NOTE]
>
>The code samples provided here are for illustrative purposes only. See [SonarQube's Concepts documentation](https://docs.sonarsource.com/sonarqube-server/latest/) to learn about its concepts and quality rules.

Full SonarQube rules are not available for download due to Adobe proprietary information. You can download the complete list of rules [using this link](/help/assets/CodeQuality-rules-latest-AMS.xlsx). Continue reading this document for descriptions and examples of the rules.

>[!IMPORTANT]
>
>Starting Thursday, February 13, 2025 (Cloud Manager 2025.2.0), Cloud Manager Code Quality is using an updated SonarQube 9.9 version and an updated list of rules that you can [download here](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx).

## SonarQube rules {#sonarqube-rules}

The following section details SonarQube rules executed by Cloud Manager.

### Do Not Use Potentially Dangerous Functions {#do-not-use-potentially-dangerous-functions}

* **Key**: CQRules:CWE-676
* **Type**: Vulnerability
* **Severity**: Major
* **Since**: Version 2018.4.0

The methods `Thread.stop()` and `Thread.interrupt()` can produce hard-to-reproduce issues and, sometimes, security vulnerabilities. Their usage should be tightly monitored and validated. In general, message passing is a safer way to accomplish similar goals.

#### Non-compliant code {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Compliant code {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Do not use format strings that may be externally controlled {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Key**: CQRules:CWE-134
* **Type**: Vulnerability
* **Severity**: Major
* **Since**: Version 2018.4.0

Using a format string from an external source (such as a request parameter or user-generated content) can expose an application to denial of service attacks. There are circumstances where a format string may be externally controlled, but is only allowed from trusted sources.

#### Non-compliant code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP requests should always have socket and connect timeouts {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Key**: CQRules:ConnectionTimeoutMechanism
* **Type**: Bug
* **Severity**: Critical
* **Since**: Version 2018.6.0

When executing HTTP requests from inside an AEM application, it is critical that proper timeouts are configured to avoid unnecessary thread consumption. Unfortunately, both Java&trade;'s default HTTP Client, `java.net.HttpUrlConnection`, and the widely used Apache HTTP Components client do not have a default timeout. Therefore, timeouts must be explicitly configured. As a best practice, these timeouts should be no more than 60 seconds.

#### Non-compliant code {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Compliant code {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### The objects `ResourceResolver` should always be closed {#resourceresolver-objects-should-always-be-closed}

* **Key**: CQRules:CQBP-72
* **Type**: `Code Smell`
* **Severity**: Major
* **Since**: Version 2018.4.0

`ResourceResolver` Objects obtained from the `ResourceResolverFactory` consume system resources. Although there are measures in place to reclaim these resources when a `ResourceResolver` is no longer in use, it is more efficient to close any opened `ResourceResolver` objects explicitly by calling the `close()` method.

A common misconception is that `ResourceResolver` objects created using an existing JCR Session should not be explicitly closed. Another misconception is that closing these objects closes the underlying JCR Session. Such is not the case. Regardless of how a `ResourceResolver` is opened, it should be closed when no longer used. Because `ResourceResolver` implements the `Closeable` interface, it is also possible to use the `try-with-resources` syntax instead of explicitly invoking `close()`.

#### Non-compliant code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Compliant code {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Do not use sling servlet paths to register servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Key**: CQRules:CQBP-75
* **Type**: `Code Smell`
* **Severity**: Major
* **Since**: Version 2018.4.0

As described in the [Sling documentation](https://sling.apache.org/documentation/the-sling-engine/servlets.html), bindings servlets by paths are discouraged. Path-bound servlets cannot use standard JCR access controls and, as a result, require additional security rigor. Rather than using path-bound servlets, it is recommended to create nodes in the repository and register servlets by resource type.

#### Non-compliant code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Caught exceptions should be logged or thrown, not both {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Key**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

In general, an exception should be logged exactly one time. Logging exceptions multiple times can cause confusion because it is unclear how many times an exception occurred. The most common pattern that leads to this issue is logging and throwing a caught exception.

#### Non-compliant code {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Compliant code {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Avoid log statements immediately followed by throw statements {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Key**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

Another common pattern to avoid is to log a message and then immediately throw an exception. This issue generally indicates that the exception message ends up duplicated in log files.

#### Non-compliant code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Compliant code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Avoid logging at INFO when handling GET or HEAD requests {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Key**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Type**: `Code Smell`
* **Severity**: Minor

In general, the INFO log level should be used to demarcate important actions and, by default, AEM is configured to log at the INFO level or above. GET and HEAD methods should only ever be read-only operations and thus do not constitute important actions. Logging at the INFO level in response to GET or HEAD requests is likely to create significant log noise, making it harder to identify useful information in log files. When handling GET or HEAD requests, logging should be at the WARN or ERROR levels if something has gone wrong. For deeper troubleshooting information, logging should be at the DEBUG or TRACE levels.

>[!NOTE]
>
>This workflow does not apply to access.log-type logging for each request.

#### Non-compliant code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Compliant code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Do not use `Exception.getMessage()` as the first parameter of a logging statement {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Key**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

As a best practice, log messages should provide contextual information about where in the application an exception has occurred. While context can also be determined by using stack traces, in general the log message is going to be easier to read and understand. As a result, when logging an exception, it is a bad practice to use the exception's message as the log message. The exception message should detail what went wrong. In contrast, the log message should inform the reader about what the application was doing when the exception occurred. The exception message is still logged. By specifying your own message, the logs are easier to understand.

#### Non-compliant code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Compliant code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Logging in catch blocks should be at the WARN or ERROR level {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Key**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

As the name suggests, Java&trade; exceptions should always be used in exceptional circumstances. As a result, when an exception is caught, it is important to ensure that log messages are logged at the appropriate level: either WARN or ERROR. Doing so ensures that those messages appear correctly in the logs.

#### Non-compliant code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Compliant code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Do not print stack traces to the console {#do-not-print-stack-traces-to-the-console}

* **Key**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

Context is critical when understanding log messages. Using `Exception.printStackTrace()` causes only the stack trace to be output to the standard error stream, losing all context. Further, in a multi-threaded application like AEM, if multiple exceptions are printed using this method in parallel, their stack traces may overlap which produces significant confusion. Exceptions should be logged through the logging framework only.

#### Non-compliant code {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Compliant code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Do not output to standard output or standard error {#do-not-output-to-standard-output-or-standard-error}

* **Key**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

Logging in AEM should always be done through the logging framework, SLF4J. Outputting directly to the standard output or standard error streams loses the structural and contextual information provided by the logging framework and may, sometimes, cause performance issues.

#### Non-compliant code {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Compliant code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Avoid hardcoded `/apps` and `/libs` paths {#avoid-hardcoded-apps-and-libs-paths}

* **Key**: CQRules:CQBP-71
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2018.4.0

Paths starting with `/libs` and `/apps` should generally not be hardcoded. These paths are typically stored relative to the Sling search path, which defaults to `/libs,/apps`. Using the absolute path may introduce subtle defects that would only appear later in the project lifecycle.

#### Non-compliant code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Compliant code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling scheduler should not be used {#sonarqube-sling-scheduler}

* **Key**: CQRules:AMSCORE-554
* **Type**: `Code Smell` / Cloud Service Compatibility
* **Severity**: Minor
* **Since**: Version 2020.5.0

Do not use the Sling Scheduler for tasks that require a guaranteed execution. Sling Scheduled Jobs guarantee execution and better suited for both clustered and non-clustered environments. 

See [Apache Sling Eventing and Job Handling documentation](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) to learn more about how Sling Jobs are handled in clustered environments.

### AEM deprecated APIs should not be use {#sonarqube-aem-deprecated}

* **Key**: AMSCORE-553
* **Type**: `Code Smell` / Cloud Service Compatibility
* **Severity**: Minor
* **Since**: Version 2020.5.0

The AEM API surface is under constant revision to identify APIs for which usage is discouraged and thus considered deprecated. 

Often, these APIs are deprecated using the standard Java&trade; *@Deprecated* annotation and, as such, as identified by `squid:CallToDeprecatedMethod`. 

However, there are cases where an API is deprecated in the context of AEM but may not be deprecated in other contexts. This rule identifies this second class.

## OakPAL content rules {#oakpal-rules}

The following section details the OakPAL checks executed by Cloud Manager.

>[!NOTE]
>
>OakPAL is a framework, which validates content packages using a standalone Oak repository. An AEM Partner and winner of the 2019 AEM Rock Star North America award developed it.

### Customers should not implement or extend product APIs annotated with @ProviderType {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Key**: CQBP-84
* **Type**: Bug
* **Severity**: Critical
* **Since**: Version 2018.7.0

The AEM API contains Java&trade; interfaces and classes that are only meant to be used, but not implemented, by custom code. For example, only AEM implements the interface `com.day.cq.wcm.api.Page`.

Adding new methods to these interfaces does not affect existing code, making the addition of new methods backwards-compatible. However, if custom code implements one of these interfaces, that custom code has introduced a backwards-compatibility risk for the customer.

AEM annotates interfaces and classes intended solely for its implementation with `org.osgi.annotation.versioning.ProviderType` or, occasionally, the legacy annotation `aQute.bnd.annotation.ProviderType`. This rule detects instances where custom code implements such an interface or extends a class.

#### Non-compliant Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Customer packages should not create or edit nodes under `/libs` {#oakpal-customer-package}

* **Key**: BannedPath
* **Type**: Bug
* **Severity**: Blocker
* **Since**: Version 2019.6.0

It has been a long-standing best practice that the `/libs` content tree in the AEM content repository should be considered read-only by customers. Modifying nodes and properties under `/libs` creates significant risk for major and minor updates. Edits to `/libs` are only made by Adobe through official channels.

### Packages should not contain duplicate OSGi configurations {#oakpal-package-osgi}

* **Key**: DuplicateOsgiConfigurations
* **Type**: Bug
* **Severity**: Major
* **Since**: Version 2019.6.0

A common problem that occurs in complex projects is where the same OSGi component is configured multiple times. This issue creates an ambiguity about which configuration is operable. This rule is "runmode-aware" in that it only identifies issues where the same component is configured multiple times in the same run mode or combination of run modes.

#### Non-compliant code {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Compliant code {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Config and install folders should only contain OSGi nodes {#oakpal-config-install}

* **Key**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Type**: Bug
* **Severity**: Major
* **Since**: Version 2019.6.0

For security reasons, paths containing `/config/` and `/install/` are only readable by administrative users in AEM and should be used only for OSGi configuration and OSGi bundles. Placing other types of content under paths that contain these segments results in application behavior that unintentionally varies between administrative and non-administrative users.

A common problem is use of nodes named `config` within component dialog boxes or when specifying the rich text editor configuration for inline editing. To resolve this issue, the offending node should be renamed to a compliant name. For the rich text editor configuration, use the `configPath` property on the `cq:inplaceEditing` node to specify the new location.

#### Non-compliant code {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Compliant code {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Packages should not overlap {#oakpal-no-overlap}

* **Key**: PackageOverlaps
* **Type**: Bug
* **Severity**: Major
* **Since**: Version 2019.6.0

Similar to the [Packages Should Not Contain Duplicate OSGi Configurations rule](#oakpal-package-osgi), this issue is a common problem on complex projects where the same node path is written to by multiple separate content packages. While using content package dependencies can be used to ensure a consistent result, it is better to avoid overlaps entirely. 

### The default authoring mode should not be Classic UI {#oakpal-default-authoring}

* **Key**: ClassicUIAuthoringMode
* **Type**: `Code Smell` / Cloud Service Compatibility
* **Severity**: Minor
* **Since**: Version 2020.5.0

The OSGi configuration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` defines the default authoring mode within AEM. Because the Classic UI has been deprecated since AEM 6.4, an issue is now raised when the default authoring mode is configured to Classic UI.

### Components with dialog boxes should have touch UI dialog boxes {#oakpal-components-dialogs}

* **Key**: ComponentWithOnlyClassicUIDialog
* **Type**: `Code Smell` / Cloud Service Compatibility
* **Severity**: Minor
* **Since**: Version 2020.5.0

AEM Components with a Classic UI dialog should also have a Touch UI dialog for optimal authoring and compatibility with the Cloud Service deployment model, which does not support Classic UI. This rule verifies the following scenarios:

* A component with a Classic UI dialog (that is, a `dialog` child node) must have a corresponding Touch UI dialog (that is, a `cq:dialog` child node).
* A component with a Classic UI design dialog (that is, a `design_dialog` node) must have a corresponding Touch UI design dialog (that is, a `cq:design_dialog` child node).
* A component with both a Classic UI dialog and a Classic UI design dialog must have both a corresponding Touch UI dialog and a corresponding Touch UI design dialog.

The AEM Modernization Tools documentation provides details and tooling for how to convert components from Classic UI to Touch UI. See [The AEM Modernization Tools documentation ](https://opensource.adobe.com/aem-modernize-tools/) for more details.

### Reverse replication agents should not be used {#oakpal-reverse-replication}

* **Key**: ReverseReplication
* **Type**: `Code Smell` / Cloud Service Compatibility
* **Severity**: Minor
* **Since**: Version 2020.5.0

Support for reverse replication is not available in Cloud Service deployments, as described in [Release Notes: Removal of Replication Agents](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents).

Customers using reverse replication should contact Adobe for alternative solutions.

### Resources contained in proxy-enabled client libraries should be in a folder named resources {#oakpal-resources-proxy}

* **Key**: ClientlibProxyResource
* **Type**: Bug
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM client libraries may contain static resources like images and fonts. As described in the [Using Client-Side Libraries documentation](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors), when using proxied client libraries these static resources must be contained in a child folder named `resources` to be effectively referenced on the publish instances.

#### Non-compliant code {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Compliant code {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Usage of Cloud Service incompatible workflow processes {#oakpal-usage-cloud-service}

* **Key**: CloudServiceIncompatibleWorkflowProcess
* **Type**: `Code Smell`
* **Severity**: Blocker
* **Since**: Version 2021.2.0

With the move to Asset micro-services for asset processing on AEM Cloud Service, several workflow processes that were used in on-premise and AMS versions of AEM have become either unsupported or unnecessary.

The migration tool in the [AEM Assets as a Cloud Service GitHub repository](https://github.com/adobe/aem-cloud-migration) can be used to update workflow models during migration to AEM as a Cloud Service.

### Usage of static templates is discouraged in favor of editable templates {#oakpal-static-template}

* **Key**: StaticTemplateUsage
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

While the use of static templates has historically been common in AEM Projects, editable templates are highly recommended as they provide the most flexibility and support additional features not present in static templates. More information can be found in the [Page Templates - Editable documentation](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable).

Migration from static to editable templates can be largely automated using the [AEM Modernization Tools](https://opensource.adobe.com/aem-modernize-tools/).

### Usage of legacy foundation components is discouraged {#oakpal-usage-legacy}

* **Key**: LegacyFoundationComponentUsage
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

The legacy Foundation Components (that is, components under `/libs/foundation`) have been deprecated for several AEM releases in favor of the [Core Components](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction). Usage of the legacy Foundation Components as the basis for custom components, whether by overlay or inheritance, is discouraged and should be converted to the corresponding core component.

[AEM Modernization Tools](https://opensource.adobe.com/aem-modernize-tools/) can facilitate this conversion. 

### Custom search index definition nodes must be direct children of `/oak:index` {#oakpal-custom-search}

* **Key**: OakIndexLocation
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM Cloud Service requires that custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) be direct child nodes of `/oak:index`. Indexes in other locations must be moved to be compatible with AEM Cloud Service. More information on search indexes can be found in the [Content Search and Indexing documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing).

### Custom search index definition nodes must have a compatVersion of 2 {#oakpal-custom-search-compatVersion}

* **Key**: IndexCompatVersion
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM Cloud Service requires that custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) must have the `compatVersion` property set to `2`. AEM Cloud Service does not support any other value. More information on search indexes can be found in the [Content Search and Indexing documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing).

### Descendent nodes of custom search index definition nodes must be of type `nt:unstructured` {#oakpal-descendent-nodes}

* **Key**: IndexDescendantNodeType
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

Hard-to-troubleshoot issues can occur when a custom search index definition node has unordered child nodes. To avoid such nodes, Adobe recommends that all descendent nodes of an `oak:QueryIndexDefinition` node be of type `nt:unstructured`.

### Custom search index definition nodes must contain a child node named `indexRules` that has children {#oakpal-custom-search-index}

* **Key**: IndexRulesNode
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

A properly defined custom search index definition node must include a child node named `indexRules` and this node must have at least one child. More information can be found in the [Oak documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Custom search index definition nodes must follow naming conventions {#oakpal-custom-search-definitions}

* **Key**: IndexName
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM Cloud Service requires that custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) must be named following a specific pattern described on [Content Search and Indexing](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### Custom search index definition nodes must use the index type lucene {#oakpal-index-type-lucene}

* **Key**: IndexType
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM Cloud Service requires that custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) have a `type` property with the value set to `lucene`. Indexing using legacy index types must be updated before migration to AEM Cloud Service. See the [Content Search and Indexing documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) for more information.

### Custom search index definition nodes must not contain a property named `seed` {#oakpal-property-name-seed}

* **Key**: IndexSeedProperty
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM Cloud Service prohibits custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) from containing a property named `seed`. Indexing using this property must be updated before migration to AEM Cloud Service. See the [Content Search and Indexing documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) for more information.

### Custom search index definition nodes must not contain a property named `reindex` {#oakpal-reindex-property}

* **Key**: IndexReindexProperty
* **Type**: `Code Smell`
* **Severity**: Minor
* **Since**: Version 2021.2.0

AEM Cloud Service prohibits custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) from containing a property named `reindex`. Indexing using this property must be updated before migration to AEM Cloud Service. See the [Content Search and Indexing documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) for more information.

### Index definition nodes must not be deployed in UI content package {#oakpal-ui-content-package}

* **Key**: IndexNotUnderUIContent
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.6.0

AEM Cloud Service prohibits custom search index definitions (nodes of type `oak:QueryIndexDefinition`) from being deployed in the UI Content package.

>[!WARNING]
>
>You are urged to address this issue as soon as possible because it can cause pipelines to fail starting with the [Cloud Manager August 2024 release](/help/release-notes/current.md).

### Custom full-text index definition of type `damAssetLucene` must be correctly prefixed with `damAssetLucene` {#oakpal-dam-asset-lucene}

* **Key**: CustomFulltextIndexesOfTheDamAssetCheck
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.6.0

AEM Cloud Service prohibits custom full-text index definitions of type `damAssetLucene` from being prefixed with anything other than `damAssetLucene`.

>[!WARNING]
>
>You are urged to address this issue as soon as possible because it can cause pipelines to fail starting with the [Cloud Manager August 2024 release](/help/release-notes/current.md).

### Index definition nodes must not contain properties with the same name {#oakpal-index-property-name}

* **Key**: DuplicateNameProperty
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.6.0

AEM Cloud Service prohibits custom search index definitions (that is, nodes of type `oak:QueryIndexDefinition`) from containing properties with the same name

>[!WARNING]
>
>You are urged to address this issue as soon as possible because it can cause pipelines to fail starting with the [Cloud Manager August 2024 release](/help/release-notes/current.md).

### Customizing of certain out-of-the-box index definitions is prohibited {#oakpal-customizing-ootb-index}

* **Key**: RestrictIndexCustomization
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.6.0

AEM Cloud Service prohibits unauthorized modifications of the following OOTB indexes:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>You are urged to address this issue as soon as possible because it can cause pipelines to fail starting with the [Cloud Manager August 2024 release](/help/release-notes/current.md).

### Configuration of the tokenizers in analyzers should be created with the name `tokenizer` {#oakpal-tokenizer}

* **Key**: AnalyzerTokenizerConfigCheck
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.6.0

AEM Cloud Service prohibits the creation of tokenizers with incorrect names in analyzers. Tokenizers should always be defined as `tokenizer`.

### Configuration of indexing definitions should not contain spaces {#oakpal-indexing-definitions-spaces}

* **Key**: PathSpacesCheck
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.7.0

AEM Cloud Service prohibits the creation of indexing definitions that contain properties with spaces.

### Configuration of indexing definitions should not contain haystack0 property {#oakpal-indexing-haystack0-property}

* **Key**: HayStackPropertyCheck
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2024.12.0

AEM Cloud Service prohibits the creation of indexing definitions that contain haystack properties.

### Configuration of indexing definitions should not contain the async-previous and temp-async properties {#oakpal-indexing-async-previous-property}

* **Key**: IndexAsyncPreviousCheck
* **Type**: Improvement
* **Severity**: Minor
* **Since**: Version 2025.2.0

AEM Cloud Service prohibits the creation of indexing definitions that contain async-previous, temp-async, temp-fulltext-async, temp-elastic-async properties.

## Dispatcher optimization tool {#dispatcher-optimization-tool-rules}

The following section lists the Dispatcher Optimization Tool (DOT) checks executed by Cloud Manager. Follow the links for each check for its GitHub definition and details.

* [Dispatcher configuration unexpected tokens](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Dispatcher configuration unmatched quote](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Dispatcher configuration missing brace](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Dispatcher configuration extra brace](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Dispatcher configuration missing mandatory Property](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Dispatcher configuration deprecated property](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Dispatcher configuration not found](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Httpd configuration includes file not found](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcher configuration general](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [The Dispatcher publish farm cache should have `serveStaleOnError` enabled](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [The Dispatcher publish farm filters should contain the default deny rules from the 6.x.x version of the AEM archetype](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [The Dispatcher publish farm cache `statfileslevel` property should be >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [The Dispatcher publish farm `gracePeriod` property should be >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Each Dispatcher farm should have a unique name](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [The Dispatcher publish farm cache should have its `ignoreUrlParams` rules configured in an allowlist manner](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [The Dispatcher publish farm filters should specify the allowed Sling selectors in an allowlist manner](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [The Dispatcher publish farm filters should specify the allowed Sling suffix patterns in an allowlist manner](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [Do not use the 'Require all granted' directive in a VirtualHost Directory section with a root directory-path](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
