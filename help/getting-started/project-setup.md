---
title: Setting up the Project
description: Learn how to set up your project so you can manage and deploy it with Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
---

# Project Setup {#setting-up-your-project}

Learn how to set up your project so you can manage and deploy it with Cloud Manager.

## Modifying Existing Projects {#modifying-project-setup-details}

Existing AEM projects need to adhere to some basic rules in order to be built and deployed successfully with Cloud Manager.

* Projects must be built using Apache Maven.
* There must be a `pom.xml` file in the root of the git repository.
  * This `pom.xml` file can refer to as many sub-modules (which in turn may have other sub-modules) as necessary.
  * You can add references to additional Maven artifact repositories in your `pom.xml` files.
  * Access to [password-protected artifact repositories](#password-protected-maven-repositories) is supported when configured. However, access to network-protected artifact repositories is not supported.
* Deployable content packages are discovered by scanning for content package .zip files contained in a directory named `target`.
  * Any number of sub-modules may produce content packages.
* Deployable Dispatcher artifacts are discovered by scanning for `zip` files contained subdirectories of `target` named `conf` and `conf.d`.
* If there is more than one content package, the ordering of package deployments is not guaranteed. 
 * Should a specific order be needed, content package dependencies can be used to define the order.
* Packages may be [skipped](#skipping-content-packages) from deployment.

## Activating Maven Profiles in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In some limited cases, you may need to vary your build process slightly when running inside Cloud Manager as opposed to when it runs on developer workstations. For these cases, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) can be used to define how the build should be different in different environments, including Cloud Manager.

Activation of a Maven Profile inside the Cloud Manager build environment should be done by looking for `CM_BUILD` [environment variable](/help/getting-started/build-environment.md#environment-variables) environment variable. Conversely, a profile intended to be used only outside of the Cloud Manager build environment should be done by looking for the absence of this variable.

For example, if you wanted to output a simple message only when the build is run inside Cloud Manager, you would do this:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>To test this profile on a developer workstation, you can either enable it on the command line (with `-PcmBuild`) or in your Integrated Development Environment (IDE).

And if you wanted to output a simple message only when the build is run outside of Cloud Manager, you would do this:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Password-Protected Maven Repository Support {#password-protected-maven-repositories}

Artifacts from a password-protected Maven repository should only be used very cautiously as code deployed through this mechanism is not run through all of the quality rules implemented in Cloud Manager's quality gates. It is advised to also deploy the Java sources as well as the whole project source code alongside with the binary.

>[!TIP]
>
>Artifacts from password-protected Maven repositories should only be used in rare cases and for code not tied to AEM.

In order to use a password-protected Maven repository from Cloud Manager, specify the password (and optionally, the username) as a secret [Pipeline Variable](/help/getting-started/build-environment.md#pipeline-variables) and then reference that secret inside a file named `.cloudmanager/maven/settings.xml` in the git repository. This file follows the [Maven Settings File](https://maven.apache.org/settings.html) schema.

When the Cloud Manager build process starts, the `<servers>` element in this file will be merged into the default `settings.xml` file provided by Cloud Manager. Server IDs starting with `adobe` and `cloud-manager` are considered reserved and should not be used by custom servers. Server IDs not matching one of these prefixes or the default ID `central` will never be mirrored by Cloud Manager. 

With this file in place, the server ID would be referenced from inside a `<repository>` and/or `<pluginRepository>` element inside the `pom.xml` file. Generally, these `<repository>` and/or `<pluginRepository>` elements would be contained inside a [Cloud Manager-specific profile](#activating-maven-profiles-in-cloud-manager), although that is not strictly necessary.

As an example, let's say that the repository is at `https://repository.myco.com/maven2`, the username Cloud Manager should use is `cloudmanager` and the password is `secretword`.

First, set the password as a secret on the pipeline:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Then reference this from the `.cloudmanager/maven/settings.xml` file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

And finally reference the server id inside the `pom.xml` file:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Deploying Sources {#deploying-sources}

It is a good practice to deploy the Java sources alongside with the binary to a Maven repository. 
 
Configure the `maven-source-plugin` in your project:

 ```xml
         <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-source-plugin</artifactId>
             <executions>
                 <execution>
                     <id>attach-sources</id>
                     <goals>
                         <goal>jar-no-fork</goal>
                     </goals>
                 </execution>
             </executions>
         </plugin>
 ```

### Deploying Project Sources {#deploying-project-sources}

It is a good practice to deploy the whole project source alongside with the binary to a Maven repository. This allows rebuilding the exact artifact. 
 
Configure the `maven-assembly-plugin` in your project:

 ```xml
         <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-assembly-plugin</artifactId>
             <executions>
                 <execution>
                     <id>project-assembly</id>
                     <phase>package</phase>
                     <goals>
                         <goal>single</goal>
                     </goals>
                     <configuration>
                         <descriptorRefs>
                             <descriptorRef>project</descriptorRef>
                         </descriptorRefs>
                     </configuration>
                 </execution>
             </executions>
         </plugin>
 ```

## Skipping Content Packages {#skipping-content-packages}

In Cloud Manager, builds may produce any number of content packages. For a variety of reasons, it may be desirable to product a content package but not deploy it. This may be useful, for example, when building content packages used only for testing or which will be repackaged by another step in the build process, that is, as a sub-package of another package.

To accommodate these scenarios, Cloud Manager will look for a property named `cloudManagerTarget` in the properties of built content packages. If this property is set to `none`, the package will be skipped and not deployed. The mechanism to set this property depends upon the way the build is producing the content package. For example, with the `filevault-maven-plugin` you would configure the plugin like this:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

With the `content-package-maven-plugin` it is similar:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Build Artifact Reuse {#build-artifact-reuse}

In many cases, the same code is deployed to multiple AEM environments. Where possible, Cloud Manager will avoid rebuilding the code base when it detects that the same git commit is used in multiple full-stack pipeline executions.

When an execution is started, the current HEAD commit for the branch pipeline is extracted. The commit hash is visible in the UI and via the API. When the build step completes successfully, the resulting artifacts are stored based on that commit hash and may be reused in subsequent pipeline executions.

Packages are reused across pipelines if they are in the same program. When looking for packages that can be reused, AEM disregards branches and reuses artifacts across branches.

When a reuse occurs, the build and code quality steps are effectively replaced with the results from the original execution. The log file for the build step will list the artifacts and the execution information which was used to build them originally.

The following is an example of such log output.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

The log of the code quality step will contain similar information.

### Examples {#example-reuse}

#### Example 1 {#example-1}

Consider that your program has two development pipelines:

* Pipeline 1 on branch `foo`
* Pipeline 2 on branch `bar`

Both branches are on the same commit ID.

1. Running pipeline 1 first will build the packages normally.
1. Then running pipeline 2 will reuse packages created by pipeline 1.

#### Example 2 {#example-2}

Consider that your program has two branches:

* Branch `foo`
* Branch `bar`

Both branches have the same commit ID.

1. A development pipeline builds and executes `foo`.
1. Subsequently a production pipeline builds and executes `bar`.

In this case, the artifact from `foo` will be reused for the production pipeline since the same commit hash was identified.

### Opting Out {#opting-out}

If desired, the reuse behavior can be disabled for specific pipelines by setting the pipeline variable `CM_DISABLE_BUILD_REUSE` to `true`. If this variable is set, the commit hash is still extracted and the resulting artifacts will be stored for later use, but any previously stored artifacts will not be reused. To understand this behavior, consider the following scenario.

1. A new pipeline is created.
1. The pipeline is executed (execution #1) and the current HEAD commit is `becdddb`. The execution is successful and the resulting artifacts are stored.
1. The `CM_DISABLE_BUILD_REUSE` variable is set.
1. The pipeline is re-executed without changing code. Although there are stored artifacts associated with `becdddb`, they are not reused due to the `CM_DISABLE_BUILD_REUSE` variable.
1. The code is changed and the pipeline is executed. The HEAD commit is now `f6ac5e6`. The execution is successful and the resulting artifacts are stored.
1. The `CM_DISABLE_BUILD_REUSE` variable is deleted.
1. The pipeline is re-executed without changing the code. Since there are stored artifacts associated with `f6ac5e6`, those artifacts are reused.

### Caveats {#caveats}

* Build artifacts are not reused across different programs, regardless if the commit hash is identical.
* Build artifacts are reused within the same program even if the branch and/or pipeline is different.
* [Maven version handling](/help/managing-code/activating-maven-project.md) replace the project version only in production pipelines. Therefore if the same commit is used on both a development deploy execution and a production pipeline execution and the development deploy pipeline is executed first, the versions will be deployed to stage and production without being changed. However, a tag will still be created in this case.
* If the retrieval of the stored artifacts is not successful, the build step will be executed as if no artifacts had been stored.
* Pipeline variables other than `CM_DISABLE_BUILD_REUSE` are not considered when Cloud Manager decides to reuse previously created build artifacts.

## Develop your Code Based on Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html)
