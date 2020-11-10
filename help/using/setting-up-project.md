---
title: Setting up the Project
description: Follow this page to learn how to set up a Project
---

# Setting up your Project {#setting-up-your-project}

## Modifying Project Setup Details {#modifying-project-setup-details}

In order to be built and deployed successfully with Cloud Manager, existing AEM projects need to adhere to some basic rules:

* Projects must be built using Apache Maven.
* There must be a *pom.xml* file in the root of the Git repository. This *pom.xml* file can refer to as many sub-modules (which in turn may have other sub-modules, etc.) as necessary.

* You can add references to additional Maven artifact repositories in your *pom.xml* files. Access to [password-protected artifact repositories](#password-protected-maven-repositories) is supported when configured. However, access to network-protected artifact repositories is not supported.
* Deployable content packages are discovered by scanning for content package *zip* files which are contained in a directory named *target*. Any number of sub-modules may produce content packages.

* Deployable Dispatcher artifacts are discovered by scanning for *zip* files (again, contained in a directory named *target*) which have directories named *conf* and *conf.d*.

* If there is more than one content package, the ordering of package deployments is not guaranteed. Should a specific order be needed, content package dependencies can be used to define the order. Packages may be [skipped](#skipping-content-packages) from deployment.


## Activating Maven Profiles in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In some limited cases, you may need to vary your build process slightly when running inside Cloud Manager as opposed to when it runs on developer workstations. For these cases, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) can be used to define how the build should be different in different environments, including Cloud Manager.

Activation of a Maven Profile inside the Cloud Manager build environment should be done by looking for CM_BUILD environment variable described above. Conversely, a profile intended to be used only outside of the Cloud Manager build environment should be done by looking for the absence of this variable.

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

>[!NOTE]
>Artifacts from a password-protected Maven repository should only be used very cautiously as code deployed through this mechanism is currently not run through Cloud Manager's Quality Gates. Therefore it should only be used in rare cases and for code not tied to AEM. It is advised to also deploy the Java sources as well as the whole project source code alongside with the binary.

In order to use a password-protected Maven repository from Cloud Manager, specify the password (and optionally, the username) as a secret [Pipeline Variable](/help/using/build-environment-details.md#pipeline-variables) and then reference that secret inside a file named `.cloudmanager/maven/settings.xml` in the git repository. This file follows the [Maven Settings File](https://maven.apache.org/settings.html) schema. When the Cloud Manager build process starts, the `<servers>` element in this file will be merged into the default `settings.xml` file provided by Cloud Manager. Server IDs starting with `adobe` and `cloud-manager` are considered reserved and should not be used by custom servers. Server IDs **not** matching one of these prefixes or the default ID `central` will never be mirrored by Cloud Manager. With this file in place, the server id would be referenced from inside a `<repository>` and/or `<pluginRepository>` element inside the `pom.xml` file. Generally, these `<repository>` and/or `<pluginRepository>` elements would be contained inside a [Cloud Manager-specific profile](#activating-maven-profiles-in-cloud-manager), although that is not strictly necessary.

As an example, let's say that the repository is at https://repository.myco.com/maven2, the username Cloud Manager should use is `cloudmanager` and the password is `secretword`.

First, set the password as a secret on the pipeline:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

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
    </profile>
</profiles>
```

### Deploying Sources {#deploying-sources}

It is a good practice to deploy the Java sources alongside with the binary to a Maven repository. 
 
Configure the maven-source-plugin in your project:

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

It is a good practice to deploy the whole project source alongside with the binary to a Maven repository - this allows as to rebuild the exact artifact. 
 
Configure the maven-assembly-plugin in your project:

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

In Cloud Manager, builds may produce any number of content packages. 
For a variety of reasons, it may be desirable to product a content package but not deploy it. This may be useful, for example, when building content packages used only for testing or which will be repackaged by another step in the build process, that is, as a sub-package of another package. 

To accommodate these scenarios, Cloud Manager will look for a property named ***cloudManagerTarget*** in the properties of built content packages. If this property is set to none, the package will be skipped and not deployed. The mechanism to set this property depends upon the way the build is producing the content package. For example, with the filevault-maven-plugin you would configure the plugin like this:

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

With the content-package-maven-plugin it is similar:

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

## Develop your Code Based on Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
