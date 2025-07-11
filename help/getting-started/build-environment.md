---
title: The Build Environment
description: Learn about the specialized build environment that Cloud Manager users to build and test your code.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
---

# The build environment {#build-environment}

Learn about the specialized build environment that Cloud Manager users to build and test your code.

## Environment details {#details}

Cloud Manager's build environments have the following attributes.

* The build environment is Linux-based, derived from Ubuntu 22.04.
* Apache Maven 3.9.4 is installed.
  * Adobe recommends users [update their Maven repositories to use HTTPS instead of HTTP](#https-maven).
* The Java versions installed are Oracle JDK 8u401 and Oracle JDK 11.0.22.
  * `/usr/lib/jvm/jdk1.8.0_401`
  * `/usr/lib/jvm/jdk-11.0.22`
* By default, the `JAVA_HOME`  environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. See the section [Alternate Maven Execution JDK Version](#alternate-maven) section for more details.
* There are some additional system packages installed which are necessary.
  * `bzip2`
  * `unzip`
  * `libpng`
  * `imagemagick`
  * `graphicsmagick`
* Other packages may be installed at build time as described in the section [Installing Additional System Packages](#installing-additional-system-packages).
* Every build is done in a pristine environment. The build container does not keep any state between executions.
* Maven is run with these three commands: 
  * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
  * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
  * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven is configured at a system level with a `settings.xml` file, which automatically includes the public Adobe artifact repository using a profile named `adobe-public`. See the [Adobe public Maven repository](https://repo1.maven.org/) for more details.
* Node.js 18 is available for [front end pipelines](/help/overview/ci-cd-pipelines.md).

>[!NOTE]
>
>Although Cloud Manager does not define a specific version of the `jacoco-maven-plugin`, the version used must be at least `0.7.5.201505241946`.

>[!TIP]
>
>See the following additional resources to learn how to use Cloud Manager APIs:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Creating an API Integration](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API Permissions](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## HTTPS Maven repositories {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) began a rolling update to the build environment (completing with 2023.12.0 release), which included an update to Maven 3.8.8. A significant change introduced in Maven 3.8.1 was a security enhancement aimed at mitigating potential vulnerabilities. Specifically, Maven now disables all insecure `http://*` mirrors by default, as outlined in the [Maven release notes](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

As a result of this security enhancement, some users may face issues during the build step, particularly when downloading artifacts from Maven repositories that use insecure HTTP connections.

To ensure a smooth experience with the updated version, Adobe recommends that users update their Maven repositories to use HTTPS instead of HTTP. This adjustment aligns with the industry's growing shift towards secure communication protocols and helps maintain a secure and reliable build process.

## Using a specific Java version {#using-java-version}

By default, projects built by the Cloud Manager build process use the Oracle 8 JDK. Customers wishing to use an alternate JDK have two options.

* [Maven Toolchains](#maven-toolchains) 
* [Selecting an alternate JDK version for the entire Maven execution process](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>

```

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details.

### Alternate Maven execution JDK version {#alternate-maven}

It is also possible to select Oracle 8 or Oracle 11 as the JDK for the entire Maven execution. Unlike the toolchains options, this changes the JDK used for all plug-ins unless the toolchains configuration is also set, in which case the toolchains configuration is still applied for toolchains-aware Maven plug-ins. As a result, checking and enforcing the Java version using the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) works.

To do this process, create a file named `.cloudmanager/java-version` in the Git repository branch used by the pipeline. This file can have either the content `11` or `8`. Any other value is ignored. If `11` is specified, the system uses Oracle 11 and sets the `JAVA_HOME` environment variable to `/usr/lib/jvm/jdk-11.0.22`. If `8` is specified, the system uses Oracle 8 and sets the `JAVA_HOME` environment variable to `/usr/lib/jvm/jdk1.8.0_401`.

## Environment variables {#environment-variables}

### Standard environment variables {#standard-environ-variables}

In some cases, you may find it necessary to vary the build process based on information about the program or pipeline. 

For instance, when using a tool like gulp for JavaScript minification, you might prefer different minification levels for development versus staging and production environments.

To support this, Cloud Manager adds standard environment variables to the build container for every execution.

| Variable Name | Description |
|---|---|
| `CM_BUILD` |  Always set to `true` | 
| `BRANCH` | The configured branch for the execution  |
| `CM_PIPELINE_ID` |  The numeric pipeline identifier | 
| `CM_PIPELINE_NAME` |  The pipeline name | 
| `CM_PROGRAM_ID` |  The numeric program identifier | 
| `CM_PROGRAM_NAME` |  The program name | 
| `ARTIFACTS_VERSION` |  For a staging or production pipeline, the synthetic version generated by Cloud Manager | 

### Standard environment variable availability {#availability}

Standard environment variables can be used in a number of places.

#### Author, preview, and publish environments {#author-preview-publish}

Both regular environment variables and secrets can be used in the authoring, preview, and publishing environments.

#### Dispatcher {#dispatcher}

Only regular environment variables can be used with [the Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/dispatcher). Secrets cannot be used.

However, environment variables cannot be used in `IfDefine` directives.

>[!TIP]
>
>Validate your use of environment variables with the [Dispatcher locally](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) before deploying.

#### OSGi configurations {#osgi}

Both regular environment variables and secrets can be used in [OSGi configurations](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Pipeline variables {#pipeline-variables}

In some cases, your build process may depend on specific configuration variables that would be inappropriate to place in the Git repository or need to vary between pipeline executions using the same branch. 

Cloud Manager allows for these variables to be configured through the Cloud Manager API or Cloud Manager CLI on a per-pipeline basis. Variables may be stored as either plain text or encrypted at rest. In either case, variables are made available inside the build environment as an environment variable, which can then be referenced from inside the `pom.xml` file or other build scripts. 

To set a variable using the CLI, run a command similar to the following.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Current variables can be listed using a command similar to the following.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Variables must adhere to certain limitations.

* Variable names may only contain alphanumeric characters and the underscore (`_`).
  * By convention, the names should be all uppercase.
* There is a limit of 200 variables per pipeline.
* Each name must be fewer than 100 characters.
* Each string value must be fewer than 2048 characters.
* Each `secretString` value must be fewer than 500 characters.

When used inside a Maven `pom.xml` file, it is typically helpful to map these variables to Maven properties using a syntax similar to the following.

``` xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Installing additional system packages {#installing-additional-system-packages}

To function fully, some builds require additional system packages to be installed. For example, a build may invoke a Python or Ruby script and, as a result, need to have an appropriate language interpreter installed. This scenario can be done by calling the [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) to invoke APT. This execution should generally be wrapped in a Cloud Manager-specific Maven profile. For example, to install Python you can do the following:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

This technique can also be used to install language specific packages. That is, using `gem` for RubyGems or `pip` for Python Packages.

>[!NOTE]
>
>Installing a system package in this manner does not install it in the runtime environment used for running Adobe Experience Manager. If you need a system package installed on the AEM environment, contact your Adobe Representative.
